# Let Geometry GUIDE: Layer-wise Unrolling of Geometric Priors in Multimodal LLMs

- alphaXiv: https://www.alphaxiv.org/abs/2604.05695
- Source paper: https://arxiv.org/abs/2604.05695

## Bridging the Gap Between Semantic Reasoning and Physical Perception

Multimodal Large Language Models (MLLMs) have achieved high performance in interpreting 2D images and engaging in complex semantic dialogues. However, these models often encounter significant difficulties when required to understand the physical and spatial dimensions of the real world. For tasks such as navigating a robot through a room, estimating the distance between objects in a standard photograph, or understanding complex occlusions, current MLLMs frequently fail because they treat visual data primarily as a collection of 2D semantic features rather than a 3D physical environment.

Existing approaches to solve this problem generally fall into two categories. Some researchers introduce explicit 3D data like point clouds or depth maps. While effective, this requires specialized hardware and complex reconstruction pipelines that are difficult to scale to real-world video streams. Others attempt to improve spatial awareness using only 2D images, often by training models on large-scale synthetic datasets. While these models improve, they struggle with the underlying geometry of the scene because they lack a dedicated 3D physical inductive bias.

![Comparison of existing fusion paradigms versus the GUIDE framework and its performance across spatial benchmarks.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05695v1/x1.png)

The research presented here introduces GUIDE (Geometric Unrolling Inside MLLM Early-layers), a framework designed to integrate spatial geometric information directly into the internal architecture of MLLMs. Instead of providing 3D data as an input or relying on implicit learning, GUIDE extracts multi-layered geometric priors from a dedicated geometric encoder and "unrolls" them progressively into the early layers of the language model. This method allows the model to gradually build a 3D internal representation from 2D visual inputs, matching the hierarchical nature of human spatial perception.

## Limitations of Current Geometry-Aware Models

Previous attempts to incorporate geometric priors into MLLMs typically followed a paradigm of "Input-Level Fusion and Deep-Layer Extraction." In these models, geometric features are extracted from the very last layers of a 3D encoder and then merged once with the visual tokens at the entrance of the Large Language Model (LLM). The authors identify two primary architectural flaws in this standard approach:

1.  **Deep-Layer Smoothing:** The features found in the final layers of a geometric encoder are highly abstract. While they capture global scene context well, they often lose high-frequency local details. Critical information like depth discontinuities at object edges or precise boundaries for occlusions—essential for metric measurements—is often "smoothed" out.
2.  **Single-Shot Injection Bottleneck:** Restricting the injection of geometric information to the input layer forces the LLM to process all spatial information at once. This prevents the model from accessing different levels of geometric granularity (from simple edges to complex topologies) at different stages of its internal reasoning process. It also creates a "semantic mismatch" in the early layers, where the model is trying to reconcile raw visual patches with complex, abstract 3D features.

GUIDE addresses these issues by shifting from a static, single-point fusion to a dynamic, multi-layer injection process.

## The GUIDE Architecture: Progressive Geometric Unrolling

The GUIDE framework operates using a dual-stream encoder system. When presented with an image sequence $I = \{I_i\}$ and a text prompt $Q$, the model processes them through a 2D visual encoder and a parallel geometric encoder. The core of the methodology lies in how these two streams are synchronized and fused.

### Grid Alignment and Multi-Granularity Extraction

To ensure that the geometric information correctly maps to the visual tokens, the framework implements a strict "Grid Alignment" step. Since different encoders may use different patch sizes, the input image is resized to $I'$ to ensure the spatial grid of the geometric encoder matches that of the 2D visual tokens exactly. This alignment is defined by the resolution $\lfloor H/P_v \rfloor \times \lfloor W/P_v \rfloor$, where $P_v$ is the visual patch size.

Instead of taking only the final layer of the geometric encoder, GUIDE samples $m$ layers across the encoder's depth. Shallow layers, which capture redundant 2D textures, are bypassed. The remaining layers provide a "multi-granularity" feature set $S_{\text{geo}} = \{f^{k_j}\}$, representing a spectrum of information from local geometric edges to global scene layouts.

### Layer-wise Injection

Rather than flattening these features into the input, GUIDE unrolls them step-by-step. The input layer receives a macroscopic geometric anchor to set the coordinate system. Then, the $m$ layers of geometric features are injected into the first $m$ layers of the LLM decoder. This allows the model's early perception layers to receive continuous, fine-grained geometric constraints as they begin the process of semantic abstraction.

![Detailed architecture of GUIDE, showing grid alignment, layer-wise unrolling into the LLM, and the dual context-aware gating mechanism.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05695v1/x2.png)

## Adaptive Control via Dual Context-Aware Gating

Injecting raw geometric data into a language model can be counterproductive if the data is irrelevant to the task at hand. Unfiltered geometric "noise" can disrupt the language model's pre-trained semantic manifolds, leading to performance degradation in general tasks. To prevent this, the researchers developed a "Dual Context-Aware Gating" mechanism that allows the model to selectively "fetch" spatial cues on demand.

The gating mechanism consists of two components:

1.  **Token-wise Semantic-Guided Gate ($G^{\text{sem}}_l$):** This gate uses the current hidden state of the LLM ($h_l$) to predict which specific visual tokens require spatial information. For example, if the model is processing a token related to a "chair," this gate will increase the intensity of geometric injection for that specific spatial region.
2.  **Layer-wise Global Gate ($G^{\text{glo}}_l$):** This uses a learnable scalar $\alpha_l$ to control the overall intensity of geometric information being allowed into a specific layer of the LLM.

The final modulated geometric feature $\hat{g}_l$ is calculated by combining these gates with the extracted geometric features $g_l$ through element-wise multiplication $\odot$:

$$\hat{g}_l = G^{\text{glo}}_l \cdot (G^{\text{sem}}_l \odot g_l)$$

This value is then added to the LLM's internal state:

$$h^{\text{out}}_l = h_l + \hat{g}_l$$

## Performance in Spatial Reasoning and Scene Understanding

The GUIDE framework was tested across several rigorous benchmarks designed to evaluate 3D awareness and spatial logic.

### Results in Spatial Reasoning

On the VSI-Bench, a benchmark specifically targeting visual spatial intelligence, GUIDE-9B achieved an average score of 64.2. This performance outperformed VLM-3R (60.9) and several other current geometry-aware models. Notably, GUIDE-5B (a smaller version) reached a score of 55.6, surpassing closed-source proprietary models like Gemini-1.5-Pro (53.6).

Across a suite of four benchmarks including ViewSpatial and CV-Bench, GUIDE-9B maintained the highest average score (56.8), demonstrating its ability to generalize across different types of spatial questions, such as "which object is closer?" or "how many objects are in this room?".

### Results in 3D Scene Understanding

The researchers also evaluated the model on tasks that traditionally require explicit 3D point cloud data: ScanRefer (3D Visual Grounding) and Scan2Cap (3D Dense Captioning).

*   **ScanRefer:** In tasks requiring the model to locate an object in 3D space based on a description, GUIDE-9B achieved significantly higher accuracy than previous models that use only 2D inputs. When paired with a proposal refinement tool, it even outperformed models like Video-3D LLM, which have access to actual 3D data.
*   **Scan2Cap:** For describing 3D scenes, GUIDE-9B achieved a CIDEr score of 81.2, again outperforming dedicated 3D-input models. This suggests that the progressive unrolling of geometric priors allows the LLM to develop a sensitivity to absolute physical metrics (like centimeters or meters) that is usually missing in standard 2D vision-language models.

## Analyzing the Architecture

Ablation studies were conducted to determine which parts of the GUIDE framework contributed most to its success. The researchers found a "Goldilocks zone" for injection depth. Injecting geometric features into the first 6 layers of the LLM yielded the best results (55.6 on VSI-Bench). If the injection was limited to only 3 layers, the model lacked sufficient spatial detail. Conversely, if injection was pushed into 24 layers, the geometric noise began to interfere with high-level semantic reasoning, causing performance to drop.

The gating mechanism proved to be critical. When the researchers removed the gates and directly injected geometric features into the LLM, performance fell below the baseline. This confirms that without a way to filter out redundant geometric information, the language model becomes confused by the "noise" of the 3D data, highlighting the importance of the dual-gate design for maintaining semantic integrity.

## Conclusion and Future Directions

The GUIDE framework demonstrates that it is possible to significantly enhance the spatial and physical awareness of MLLMs without the need for expensive explicit 3D data inputs. By aligning geometric and visual features and unrolling them progressively through the early layers of the model, GUIDE provides a scalable way to give AI a sense of "physicality."

This research suggests a shift in how we might build future multimodal models. Instead of viewing 3D understanding as an "add-on" at the input layer, it can be treated as a guided, layer-wise learning process. As AI moves toward applications in Embodied AI and autonomous systems, the ability to reason about the physical world with the same fluidity as semantic language will be an essential capability. GUIDE provides a structural template for achieving this synthesis, bridging the gap between what a model "sees" and what it "understands" about the physical space it inhabits.

## Relevant Citations

- Vggt: Visual geometry grounded transformer: This paper introduces VGGT, the feed-forward geometric foundation model that the GUIDE framework directly integrates as its parallel geometric encoder. The multi-granularity geometric features that GUIDE injects into the MLLM are extracted from the VGGT backbone, making this citation fundamental to the proposed method's architecture.
- Learning from videos for 3d world: Enhancing mllms with 3d vision geometry priors: This work, known as VG LLM, represents a primary baseline and the 'input-level fusion' paradigm that the GUIDE paper explicitly contrasts its novel layer-wise unrolling approach against. The paper's ablation study establishes a 'VG LLM-style model' as its baseline, making this citation essential for contextualizing GUIDE's architectural contribution.
- Thinking in space: How multimodal large language models see, remember, and recall spaces: This paper introduces VSI-Bench, which the main paper adopts as its primary evaluation benchmark for the core spatial reasoning tasks. The strong performance of the GUIDE framework on VSI-Bench is the central evidence used to validate its effectiveness and superiority over previous methods.
- Vlm-3r: Vision-language models augmented with instruction-aligned 3d reconstruction: VLM-3R is a key state-of-the-art geometry-aware MLLM that exemplifies the single-shot, input-level fusion approach. The main paper cites it as an example of this paradigm and directly compares its performance against GUIDE in the main results table, positioning it as a significant competitor to demonstrate GUIDE's advantages.
