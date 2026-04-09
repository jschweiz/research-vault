# Fast Spatial Memory with Elastic Test-Time Training

- alphaXiv: https://www.alphaxiv.org/abs/2604.07350
- Source paper: https://arxiv.org/abs/2604.07350

## Addressing the Memory Bottleneck in 4D Reconstruction

Spatiotemporal reconstruction, often referred to as 4D reconstruction, involves modeling the geometry and appearance of dynamic scenes over time. This capability is essential for generating 4D assets in media, virtual reality, and developing world models for embodied AI and robotics. While Large Reconstruction Models (LRMs) have made progress in 3D reconstruction, extending these to 4D remains computationally expensive.

The primary challenge lies in processing long sequences of visual observations. Standard Transformer-based architectures are constrained by activation memory, which limits the length of the sequences they can process in a single pass. When a model's input context exceeds its training length, reconstruction quality typically degrades. Recent research introduced Large Chunk Test-Time Training (LaCT) to address this by allowing a model to update small internal parameters—known as fast weights—during inference. However, these updates are often unstable. In dynamic scenes, fully plastic updates lead to "fast-weight drift," where the model overfits to recent frames and forgets previously learned spatial structures, resulting in temporal artifacts or a total collapse of the representation.

![Fast Spatial Memory Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.07350v1/x2.png)
*Figure 2: The architecture of Fast Spatial Memory (FSM) and the internal mechanism of the Large Chunk Elastic Test-Time Training (LaCET) block. The model processes posed input images to predict novel views by stabilizing fast-weight updates via an elastic consolidation step.*

To resolve these instabilities, researchers have introduced Fast Spatial Memory (FSM), a model that utilizes a mechanism called Elastic Test-Time Training (LaCET). By incorporating principles from continual learning, LaCET stabilizes the fast-weight adaptation process, enabling the model to handle long sequences across multiple chunks without catastrophic forgetting or parameter drift.

## The Problem of Fast-Weight Drift

In the context of Test-Time Training (TTT), a model is not static during inference. Instead, it processes input data in chunks and performs a gradient-based update on a subset of its weights. This allows the model to compress the information from the input sequence into its own parameters, effectively acting as a "spatial memory."

However, existing TTT methods like LaCT suffer from a lack of regularization. Because the weights are updated freely based on local statistics of the current chunk, they can drift significantly from their initial state. In 4D reconstruction, this manifests as a failure to maintain a consistent global coordinate system or the loss of structural details from earlier frames. This drift is especially problematic when dealing with dynamic objects or moving cameras, where the model might prioritize local temporal interpolation over a coherent 3D representation. Consequently, LaCT is typically forced to use a single large chunk, which reintroduces the memory bottleneck it was intended to solve.

## Elastic Test-Time Training (LaCET)

The proposed solution, LaCET, introduces a "consolidate" operation after the standard weight update. This step is inspired by Elastic Weight Consolidation (EWC), a technique used in continual learning to prevent a neural network from forgetting old tasks when learning new ones. In LaCET, this is applied to the fast-weight trajectory during a single inference pass.

The consolidation step introduces a quadratic penalty that pulls the updated weights back toward an "anchor state." This prevents the parameters from moving too far in directions that are not supported by the overall history of the sequence. The core operation for updating the weights from chunk $c$ to $c+1$ is defined as:

$$\theta_{c+1} = \theta'_c - \lambda F_c \odot (\theta'_c - \theta^*_c)$$

In this equation, $\theta'_c$ represents the weights after a standard gradient update, $\lambda$ is a hyperparameter controlling the strength of the consolidation, and $\odot$ denotes element-wise multiplication. Two critical components of this mechanism are the importance matrix $F_c$ and the anchor parameters $\theta^*_c$.

### Importance Estimates and Anchors

The importance matrix $F_c$ determines which weights are most critical to preserve. The model estimates this using an online statistic updated via an Exponential Moving Average (EMA). The researchers found that a variant inspired by Synaptic Intelligence (SI) was particularly effective. This method tracks the product of the weight update and the drift from the current anchor:

$$\phi(S_c) = |S_c| \text{ where } S_c = (\theta'_c - \theta_c) \odot (\theta'_c - \theta^*_c)$$

The anchor $\theta^*$ represents a stable reference of past knowledge. The research investigated several strategies for updating this anchor. The most effective policy, termed Streaming-EMA, allows the anchor to evolve slowly as a low-pass filter of the fast-weight trajectory:

$$\theta^* \leftarrow \beta \theta^* + (1-\beta) \theta$$

where $\beta$ is a decay factor. This policy balances plasticity—allowing the model to learn new scene information—with stability, ensuring it does not lose the global spatial context. This elastic behavior allows FSM to process sequences in multiple smaller chunks, significantly reducing memory overhead while maintaining high reconstruction quality.

## Fast Spatial Memory (FSM) Architecture

FSM is designed as an end-to-end feedforward network that integrates these LaCET blocks. The architecture is modular and can support different rendering decoders depending on the application requirements.

### Input Tokenization and Representation

The model takes a sequence of posed images as input. To ensure the model understands the underlying 3D geometry and temporal sequence, each input image is augmented with:
1.  **Plücker Ray Maps:** These maps represent each pixel as a ray in 3D space, providing explicit geometric conditioning for the model.
2.  **Timestamp Maps:** A normalized scalar value for each frame that encodes the relative time of the observation.

These components are concatenated and projected into a sequence of token embeddings. These tokens are then passed through a stack of LaCET blocks. Within each block, the fast-weight network is implemented as a SwiGLU-MLP. Crucially, the model only uses the input-view tokens to generate the gradients for the fast-weight updates, ensuring that target-view queries do not contaminate the internal memory.

### Decoding Strategies

FSM supports two primary decoding variants:
*   **FSM-LVSM:** Adopting a Large View Synthesis Model approach, this variant does not create an explicit geometric representation like a point cloud. Instead, it uses query tokens for the target view-time combinations and decodes RGB patches directly from the output embeddings using a linear layer.
*   **FSM-LRM:** This variant predicts an explicit 4D representation. It outputs 4D Gaussian Splatting (4DGS) primitives. Each primitive is defined by its position, rotation, scale, opacity, and color, which are then rendered into the target view using traditional rasterization techniques.

## Experimental Findings

The performance of FSM was evaluated across several 3D and 4D benchmarks, including Stereo4D, NVIDIA, and DL3DV.

### 4D Scene Reconstruction

On the Stereo4D dataset, FSM-LVSM achieved a PSNR of 32.16, significantly higher than previous rendering-based 4D methods such as MoVieS (27.19) and 4DGT (24.62). Qualitative results showed that FSM successfully avoids "ghosting" artifacts—where dynamic objects appear as transparent or blurred streaks—which are common in models that fail to maintain temporal consistency.

![Comparison of 4D Reconstruction](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.07350v1/x8.png)
*Figure 8: Qualitative comparison on the Stereo4D dataset. FSM-LVSM preserves significantly more detail in dynamic regions compared to baselines like MoVieS and 4DGT.*

### Generalization and Stability

A key finding of the research was the mitigation of the "camera-pose interpolation shortcut." Standard LaCT models often learn to interpolate between nearby camera frames rather than building a true spatial representation. When tested on sparse views, LaCT performance often collapses. In contrast, LaCET demonstrated robust generalization. Even when input views were sparse, the elastic regularization ensured the model maintained a coherent representation of the scene.

Ablation studies confirmed that the Streaming-EMA anchor policy was essential for this stability. Without it, the model either suffered from drift (standard LaCT) or lacked the temporal continuity needed for dynamic scenes (global anchoring).

## Significance and Broader Impact

The introduction of FSM and LaCET represents a shift in how sequential models can adapt to long-context data. By stabilizing test-time training, the model can compress observations into a unified spatiotemporal representation without being limited by the quadratic memory scaling of standard attention mechanisms.

For robotics and embodied AI, this means agents can potentially build and maintain a "mental map" of their environment from a continuous stream of visual data. In content creation, it enables the efficient generation of 4D assets from long video sequences, such as handheld camera captures of dynamic performances.

Despite these achievements, the researchers noted certain limitations. The model currently requires posed input images, meaning the camera positions must be known beforehand. Additionally, while the model is efficient, its ability to maintain motion consistency during extreme temporal extrapolation—predicting motion far beyond the observed window—remains a challenging area for future work. Nonetheless, FSM provides a scalable foundation for learning complex 4D environments from extensive visual experience.

## Relevant Citations

- Test-time training done right: This paper introduces Large-Chunk Test-Time Training (LaCT), the direct predecessor to the proposed LaCET method. The main paper's core contribution is an enhancement of the LaCT framework to address its stability issues, making this citation fundamental to understanding the work's context and motivation.
- Overcoming catastrophic forgetting in neural networks: This work introduces Elastic Weight Consolidation (EWC), which provides the core algorithmic inspiration for the 'Elastic' component in the paper's proposed Elastic Test-Time Training. The authors explicitly adapt the EWC regularizer to stabilize the fast-weight updates during inference.
- 4d-lrm: Large space-time reconstruction model from and to any view at any time: This paper is a key related work in the specific application domain of 4D reconstruction. The main paper's FSM-LRM architecture directly follows the parameterization and conditioning methods from 4D-LRM, making it a critical reference for the model's design choices.
- Learning to (learn at test time): Rnns with expressive hidden states: This citation introduces the foundational concept of Test-Time Training (TTT), where a model's parameters are updated during inference. The main paper's method is an advancement within this TTT paradigm, making this a crucial reference for the underlying principles.
