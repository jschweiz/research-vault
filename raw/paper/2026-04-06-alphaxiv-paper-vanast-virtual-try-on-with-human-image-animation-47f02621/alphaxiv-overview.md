# Vanast: Virtual Try-On with Human Image Animation via Synthetic Triplet Supervision

- alphaXiv: https://www.alphaxiv.org/abs/2604.04934
- Source paper: https://arxiv.org/abs/2604.04934

## Virtual Try-On and Animation in a Single Stage

Virtual try-on (VTON) technology has evolved from simple image overlays to sophisticated generative models that can realistically drape garments onto diverse human bodies. However, a significant gap remains between static image try-on and dynamic video animation. Standard approaches typically treat these as two separate problems: first, an image-based model performs the garment transfer, and then a second video-generation model animates that static image. This two-stage pipeline often suffers from compounding errors, leading to "identity drift" where the person's face changes during movement, or "garment distortion" where clothing flickers or loses its structure across frames.

![Vanast Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04934v1/x1.png)
*Figure 1: The Vanast framework employs a single-stage video diffusion architecture. It integrates a Human Animation Module (HAM) and a Garment Transfer Module (GTM) with a frozen Video Diffusion Transformer backbone to generate temporally consistent, garment-transferred human animations from a single human image and target garment.*

Vanast addresses these issues by proposing a unified, single-stage framework that simultaneously handles garment transfer and human animation. Built upon a pre-trained Video Diffusion Transformer (DiT), the model generates a coherent video sequence directly from a target human image, one or more garment images, and a pose guidance video. By processing all constraints within a single architecture, the system maintains better temporal consistency and preserves fine details of both the person's identity and the garment's texture.

## The Challenge of Supervision: Synthetic Triplet Generation

The primary obstacle in training a single-stage model for virtual try-on animation is the lack of suitable data. A model needs "triplet" supervision to learn effectively. This triplet consists of:
1.  **A human image** $(I_G')$ of a person wearing an arbitrary, different outfit.
2.  **Target garment images** ($G$) that the person should "change into."
3.  **A ground-truth video** ($V_G$) of the *same* person wearing the *target* garments ($G$) while performing a specific motion.

Existing datasets usually provide either paired images (human and garment) or videos of people moving in their own clothes. They rarely provide a video of a person wearing a specific garment alongside an image of that same person in a different outfit. To solve this, the researchers developed an automated pipeline to synthesize these triplets from existing shopping videos and "in-the-wild" footage.

### Synthesizing the Human Reference
To create $(I_G', G, V_G)$, the system starts with a high-quality video $V_G$ where the person is already wearing the target garment $G$. The challenge is creating $I_G'$—a static image of that person wearing *something else*. If the model were trained using an image of the person already wearing $G$, it would simply learn to copy the clothes rather than transfer them.

The pipeline uses a Vision-Language Model (VLM) to select the best "identity" frame from the video, ensuring the face is clear and unoccluded. It then uses a text-to-image diffusion model (like FLUX) to "inpaint" new clothes onto that person. Crucially, the inpainting mask is not just the original clothes' shape; the system synthesizes an auxiliary "target" garment shape to ensure the new clothes in $I_G'$ have a different silhouette than the original $G$. This forces the model to learn the actual transfer process $I_G' \rightarrow V_G \text{ given } G$ during training.

### In-the-Wild and Multi-Garment Data
The researchers also extended this to "in-the-wild" videos where no separate catalog image of the garment exists. They used VLMs to automatically extract and segment the cleanest view of the garment from the video to serve as the reference $G$. Additionally, they captured a dedicated studio dataset to support complex scenarios like transferring both upper and lower garments simultaneously, a feature many current VTON models struggle with.

## Architectural Innovation: The Dual Module Design

Integrating multiple, often conflicting, conditioning signals—pose, identity, and garment details—into a single video diffusion model is technically difficult. If all inputs are simply concatenated, the model might prioritize one (like the pose) while ignoring the fine details of the garment or losing the person's identity.

![Vanast Architecture and Conditioning](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04934v1/x2.png)
*Figure 2: The architecture utilizes distributed modules. The Human Animation Module (HAM) processes pose and identity, while the Garment Transfer Module (GTM) focuses on garment features. These outputs are integrated into a frozen pre-trained backbone.*

Vanast utilizes a "Dual Module" architecture. Instead of modifying the core weights of a massive pre-trained Video Diffusion Transformer (which is kept frozen to preserve its generative quality), the researchers added two specialized, trainable components:

1.  **Human Animation Module (HAM):** This module focuses on the temporal and structural aspects. It takes the human reference image $I_G'$ and the pose video $K$ as input. It ensures the generated person looks like the reference and follows the target motion.
2.  **Garment Transfer Module (GTM):** This module is dedicated to the garment $G$. It extracts high-frequency details (textures, patterns, logos) and ensures they are correctly mapped onto the human body as it moves.

These modules are "distributed and cascaded." Their outputs are added to the hidden states of the frozen backbone at specific intervals. For example, at every other transformer block $l$, the integrated feature is calculated as:

$$
h_l = h_{l-1} + \alpha \cdot \text{HAM}_k(h_{l-1}) + \beta \cdot \text{GTM}_k(h_{l-1})
$$

where $l = 2k$ represents the specific block index. The researchers found that using fixed weights like $\alpha = 0.5$ and $\beta = 0.5$ provides a stable balance between following the motion and preserving the garment's appearance.

## Advanced Features: Interpolation and Multi-Garment Support

The modular nature of this architecture allows for capabilities that go beyond simple "copy-paste" garment transfer.

### Zero-Shot Garment Interpolation
Because the garment information is processed through a dedicated GTM, the model can perform "garment interpolation." If a user provides two different garments $(G_A, G_B)$, the system can mathematically blend their representations in the latent space. By adjusting an interpolation ratio $\gamma \in [0, 1]$, the model generates an animation where the person wears a "hybrid" garment that smoothly transitions between the two styles.

$$
H_{interp} = (1 - \gamma) H_A + \gamma H_B
$$

This occurs in a "zero-shot" manner, meaning the model does not need to be retrained or fine-tuned to understand how to blend styles; it emerges naturally from the modular feature integration.

![Garment Interpolation Results](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04934v1/x9.png)
*Figure 3: Demonstration of zero-shot garment interpolation. By varying the ratio $\gamma$, the model generates smooth transitions between two different garment styles while maintaining motion and identity.*

### Full Outfit Transfer
While many virtual try-on systems are limited to just a single T-shirt or a dress, Vanast's training on specialized multi-garment datasets allows it to handle full outfits. It can simultaneously condition on an upper garment (e.g., a jacket) and a lower garment (e.g., jeans), maintaining the correct layering and interaction between them even during complex movements.

## Evaluation and Performance

The researchers evaluated Vanast against a rigorous set of 16 baseline combinations. These included state-of-the-art image-based VTON models (like OOTDiffusion and CatVTON) paired with human animation models (like StableAnimator). They also compared it against VACE, a recent diffusion-based model designed for subject-driven video generation.

### Quantitative Metrics
The model was tested on two datasets: "Internet" (sourced from shopping malls) and "ViViD" (a standard benchmark). The evaluation used several key metrics:
*   **LPIPS and SSIM:** To measure how closely the generated frames match the ground truth in terms of visual structure and perception.
*   **FID (Fréchet Inception Distance):** To assess the overall realism and quality of the generated images.
*   **VFID (Video FID):** Specifically designed to measure temporal consistency and motion fluidity in videos.

In almost every category, Vanast outperformed the multi-stage baselines. Notably, the VFID scores were significantly lower than two-stage methods, confirming that the unified approach effectively eliminates the flickering and jitter common in chained models.

![Qualitative Comparison vs Baselines](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04934v1/x3.png)
*Figure 4: Qualitative comparison showing Vanast's superior ability to preserve identity and garment details compared to existing 1-stage and 2-stage baselines.*

### Qualitative Superiority
Visually, the differences are striking. Two-stage models often struggle when the person turns around; since the initial image try-on only provides a front view, the animation stage has to "guess" what the back of the garment looks like, often leading to blurred textures or sudden changes in color. Vanast, having been trained on full video sequences with the Dual Module architecture, maintains a consistent 360-degree representation of the garment.

## Significance for the Future of Digital Fashion

The development of Vanast marks a move toward more integrated and robust human-centric video generation. By solving the data scarcity problem through synthetic triplet supervision and addressing the conditioning problem through the Dual Module architecture, the research provides a framework for high-fidelity virtual experiences.

The potential impacts are diverse:
*   **E-commerce:** Customers could see themselves moving in clothes before buying, seeing how a dress flows or how a jacket fits during a walk.
*   **Content Creation:** Digital creators can generate high-quality animations for virtual influencers or avatars with specific, detailed clothing without needing expensive motion capture or 3D modeling.
*   **AI Research:** The synthetic data pipeline demonstrates how to train complex video models when real paired data is impossible to collect at scale.

By unifying try-on and animation, Vanast demonstrates that the most effective way to handle complex human-garment interactions is not through a sequence of specialized models, but through a single, well-conditioned generative process that understands both form and motion simultaneously.

## Relevant Citations

- Vace: All-in-one video creation and editing: This paper is a direct and crucial point of comparison. The Vanast paper positions its 'Dual Module' architecture as an improvement over VACE's 'single auxiliary module' for handling joint conditioning. VACE is also used as a key baseline in both single-stage and two-stage experimental comparisons.
- Wan: Open and advanced large-scale video generative models: This work provides the foundational video diffusion transformer (DiT) backbone upon which the Vanast model is built. The paper explicitly states that it adopts and modifies the architecture from this T2V model, making it a fundamental building block for their proposed method.
- Dispose: Disentangling pose guidance for controllable human image animation: This paper represents a state-of-the-art approach for the pose-driven human animation task, which is one of the two core problems Vanast unifies. It is used as a primary component in the two-stage baseline pipelines for experimental comparison, demonstrating its relevance to the animation aspect of Vanast's contributions.
- Omnitry: Virtual try-on anything without masks: OmniTry is a state-of-the-art image-based virtual try-on model that Vanast aims to improve upon by creating a unified video-native framework. It is used as a key baseline in the quantitative comparisons, representing the performance of the separate try-on stage that Vanast's single-stage approach replaces.
