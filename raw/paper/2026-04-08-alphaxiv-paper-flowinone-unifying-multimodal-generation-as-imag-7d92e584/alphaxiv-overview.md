# FlowInOne:Unifying Multimodal Generation as Image-in, Image-out Flow Matching

- alphaXiv: https://www.alphaxiv.org/abs/2604.06757
- Source paper: https://arxiv.org/abs/2604.06757

## The Vision-Centric Paradigm Shift in Multimodal Generation

Multimodal generation has traditionally operated under a text-dominant paradigm. In standard text-to-image systems, language serves as the primary control signal, with visual models acting as secondary translators that map textual embeddings into pixel space. This architecture creates an inherent asymmetry: while language can govern visual generation, the visual modality itself is rarely structured to reason or generate independently. Consequently, tasks that require precise spatial control—such as image editing based on doodles, bounding boxes, or physical trajectories—often require fragmented, task-specific modules or complex cross-modal alignment branches.

FlowInOne addresses this fragmentation by reformulating multimodal generation as a purely vision-centric "image-in, image-out" process. Instead of treating text and images as fundamentally different data types that must be aligned, this framework converts all inputs—including textual instructions, spatial layouts, and editing cues—into a single visual representation. By doing so, it leverages the inherent expressiveness of the visual modality to handle both understanding and generation within a unified latent space.

![Figure 2: Comparison of traditional text-to-image and text-image-to-image paradigms with the FlowInOne image-in, image-out approach.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06757v1/x2.png)

This shift moves multimodal AI toward a more cohesive architecture. Rather than building a "Swiss Army knife" of modality-specific encoders, FlowInOne treats the generative process as a continuous visual flow. This approach aims to eliminate the bottlenecks associated with cross-modal alignment and the architectural complexities of diffusion-based denoising schedules.

## Unified Visual Semantics: Turning Text into Pixels

The core innovation of FlowInOne is the transformation of discrete language and spatial markers into a continuous visual semantic space. To achieve this, the system renders all instructions—be they text descriptions, bounding boxes, or directional arrows—directly onto a source image canvas, $I_v$. This rendering preserves the spatial context and structural priors of the input instruction relative to the image.

For example, if a user wants to "add a red hat" to a person in an image, they do not just provide the text; the text is placed on the canvas at the relevant location. If they provide a bounding box, it is drawn on the same canvas. This "visual prompt" is then processed by a Janus-Pro-1B visual encoder, specifically a SigLIP Vision Transformer, which extracts patch-level semantic features. These features are projected into a target embedding space $X_{fuse} \in \mathbb{R}^{N \times D}$, capturing both the semantic meaning of the words and the geometric constraints of the visual markers.

![Figure 14: The data generation pipeline showing how diverse inputs like text, bounding boxes, and physical vectors are unified into a visual prompt canvas.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06757v1/x14.png)

By representing instructions as pixels, the model avoids the modality gap that often plagues text-to-image models. The visual modality becomes the foundational language for both perception and creation. This unification allows the model to treat text-to-image generation, image editing, and even physics-based trajectory following as instances of the same fundamental task: evolving an input visual state into a target output state.

## Generative Visual Flow: Modeling Continuity

FlowInOne employs Flow Matching (FM) rather than the more common diffusion-based denoising. Flow matching treats generation as the problem of learning a continuous transport map between two distributions: a source distribution $p_0$ (representing the input visual prompt) and a target distribution $p_1$ (representing the desired output image).

In this framework, the model learns a velocity field $v_{\theta}$ that dictates how to transform a source latent state $z_0$ into a target latent state $z_1$ over a time interval $t \in [0, 1]$. The probability path between these states is defined as:

$$
z_t = tz_1 + (1 - (1 - \sigma_{\min})t) z_0
$$

The network is trained to predict the ground-truth velocity $v^{\star}_t$, which is the direct vector from the source to the target:

$$
v^{\star}_t = z_1 - (1 - \sigma_{\min})z_0
$$

Unlike diffusion models, which rely on Gaussian noise as a starting point and require complex noise schedules to manage the denoising process, Flow Matching allows the source distribution $z_0$ to be non-Gaussian. In FlowInOne, $z_0$ is the latent representation of the visual instruction itself. Inference then becomes a matter of solving an Ordinary Differential Equation (ODE) to transport the visual instruction's latent state to the target image's latent state. This deterministic principle provides a more stable and efficient bridge between the perception of an instruction and the generation of the corresponding content.

## The FlowInOne Architecture: Dual-Path Modulation

To handle the variety of generative tasks—ranging from creating images from scratch to modifying existing ones—FlowInOne uses a DiT (Diffusion Transformer) variant enhanced with a **Dual-Path Spatially-Adaptive Modulation (SAM)** mechanism. This architectural choice is critical for balancing two often-conflicting goals: adhering to new instructions and preserving the structural integrity of the original source image.

![Figure 4: The FlowInOne architecture featuring the DiT variant backbone and the Dual-Path Spatially-Adaptive Modulation mechanism.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06757v1/x4.png)

The SAM mechanism operates differently depending on the task. A binary task indicator $I_{edit}$ determines the processing path:

1.  **Text-to-Image Generation ($I_{edit} = 0$):** When the model generates an image from text alone, the cross-attention layer is bypassed. This ensures the model focuses entirely on the semantic evolution from the visual prompt to the target image without being biased by external structural priors.
2.  **Image Editing ($I_{edit} = 1$):** When editing a source image $I_{src}$, the model must maintain the background and non-edited regions. The source image is encoded into a reference sequence $S$, and a cross-attention mechanism calculates a structural increment $\Delta H_{struct}$.

To prevent the source image's structure from "leaking" into areas that need to be completely changed (like replacing an object), an **Adaptive Gating Network** predicts a token-level weight vector $\Lambda \in [0, 1]^N$. This gating mechanism allows the model to selectively inject source priors only where they are needed, such as in the background, while allowing the instruction-driven generation to dominate in the edited regions. The final hidden state $H^{(l)}_{out}$ for a transformer layer is integrated as:

$$
H^{(l)}_{out} = \tilde{H}^{(l)} + I_{edit} \cdot (\Lambda \odot \Delta H_{struct})
$$

Where $\tilde{H}^{(l)}$ is the self-attention updated state. This design ensures that FlowInOne can perform precise local edits without sacrificing the realism of the global scene.

## Scaling Vision-Centric Instructions: VisPrompt-5M

To train a model capable of such diverse tasks, the researchers compiled **VisPrompt-5M**, a large-scale dataset of 5 million visual prompt pairs. This dataset moves beyond simple text-image pairs to include eight distinct task types that test different aspects of visual reasoning and generation:

*   **Standard Tasks**: Text-to-image and class-to-image generation.
*   **Editing Tasks**: Text-in-image editing, bounding box control, and "doodle" editing.
*   **Advanced Reasoning**: Visual marker editing (using arrows to indicate changes), trajectory understanding (predicting movement), and force understanding (simulating physical dynamics like wind or impact).

![Figure 3: Overview of the diverse task types and data distribution within the VisPrompt-5M dataset.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06757v1/x3.png)

The inclusion of physics-aware tasks like force and trajectory understanding is a unique aspect of this work. By training on these samples, the model learns to interpret visual markers not just as static shapes, but as indicators of physical intent. For example, an arrow pointing at a ball can be interpreted as a force vector, prompting the model to generate the ball's resulting position and state in the target image.

## Evaluation and Performance: The VP-Bench Benchmark

Evaluating a unified multimodal model requires more than standard metrics like CLIP score, which often fail to capture spatial precision or instruction faithfulness. To address this, the researchers introduced **VP-Bench**, a benchmark of 1,060 curated image pairs evaluated across four dimensions: Instruction Faithfulness, Content Consistency, Visual Realism, and Spatial Precision.

![Figure 5: Comparison of FlowInOne against open-source and commercial models across various unified generation and editing tasks.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06757v1/x5.png)

In head-to-head comparisons, FlowInOne demonstrated superior performance over existing open-source models like OmniGen2 and Kontext. Evaluation by large multimodal models (such as GPT-5.2 and Qwen3.5) and human judges showed that FlowInOne achieved the highest average "pass rates"—a metric requiring a successful score across all four evaluation dimensions. Specifically, it reached a 39.2% pass rate under GPT-5.2 evaluation, significantly higher than the 13.9% achieved by OmniGen2.

A key finding from the performance analysis was the model's ability to handle fine-grained spatial control. While commercial models sometimes ignored the precise dimensions of a bounding box or the direction of a visual marker, FlowInOne consistently adhered to these visual constraints. This success is attributed to the combination of the visual prompt rendering strategy and the adaptive modulation in the transformer blocks.

## Implications for Unified Multimodal AI

FlowInOne represents a step toward simplifying the architecture of multimodal generative models. By demonstrating that diverse tasks—from simple generation to complex physical simulation—can be unified as a single visual flow, the work challenges the necessity of complex, modality-specific subsystems. The "image-in, image-out" paradigm provides a consistent interface for both the model and the user, where the visual modality acts as the universal medium for interaction.

The success of the Flow Matching approach in this context suggests that generative modeling is moving toward more continuous, transport-based formulations. As models grow in scale, the ability to treat instructions as a starting point for a visual transport process, rather than a conditional signal for a denoising process, may prove to be a more robust way to achieve high-fidelity, instruction-faithful generation. Through the release of VisPrompt-5M and VP-Bench, this work provides the community with the resources to further explore the potential of vision-centric multimodal AI.

## Relevant Citations

- Flow matching for generative modeling: This paper is fundamental as it introduces Flow Matching, the core generative mechanism that FlowInOne is built upon. The authors explicitly position their work as an application of this principle, using it as a deterministic and efficient alternative to diffusion models.
- High-resolution image synthesis with latent diffusion models: This work introduced Latent Diffusion Models (LDM), which serve as a major point of comparison for FlowInOne. Critically, the FlowInOne architecture directly incorporates the pre-trained and frozen VAE from LDM to operate within a shared latent space.
- Flowing from words to pixels: A noise-free framework for cross-modality evolution: This citation is highly relevant because the paper explicitly states that the FlowInOne model is based on the CrossFlow framework from this work. The authors initialize their model from pre-trained CrossFlow weights, making it the direct architectural backbone of their implementation.
- Instructpix2pix: Learning to follow image editing instructions: This paper is a seminal work in instruction-guided image editing, which is one of the key tasks that FlowInOne aims to unify and solve. It provides essential context for the problem domain and represents a significant prior approach that FlowInOne's vision-centric paradigm improves upon.
