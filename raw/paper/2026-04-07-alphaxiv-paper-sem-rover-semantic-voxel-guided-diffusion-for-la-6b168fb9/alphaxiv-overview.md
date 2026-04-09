# SEM-ROVER: Semantic Voxel-Guided Diffusion for Large-Scale Driving Scene Generation

- alphaXiv: https://www.alphaxiv.org/abs/2604.06113
- Source paper: https://arxiv.org/abs/2604.06113

The generation of large-scale, 3D-consistent driving scenes is essential for the safe development and testing of autonomous vehicles. High-fidelity synthetic data allows researchers to simulate rare or dangerous edge cases that are difficult to capture in the real world. However, existing generative approaches often face a trade-off: they either produce high-quality 2D images that lack persistent 3D structure, or they generate 3D geometry that is too computationally heavy to scale beyond small, bounded environments.

![SEM-ROVER Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06113v1/x2.png)
*Figure 1: The SEM-ROVER framework consists of four main components: a semantic voxel grid input, a transformer-based diffusion model for 3D tokens, a spatial outpainting strategy for large-scale expansion, and a deferred rendering engine for photorealistic image synthesis.*

The research presented in **SEM-ROVER** introduces a system designed to bridge this gap. By combining a discrete surface representation with a transformer-based diffusion model and a progressive outpainting strategy, the framework generates persistent 3D scenes that span tens of thousands of square meters. Unlike methods that synthesize views one by one and attempt to reconstruct geometry later, this approach generates the 3D surface and appearance directly, ensuring geometric coherence from any arbitrary viewpoint.

## The Σ-Voxfield 3D Representation

To process 3D data efficiently within a diffusion model, the choice of representation is critical. Driving scenes are sparse and vast, making dense volumetric grids (like standard voxels) inefficient. Conversely, raw point clouds lack the structured nature required for many neural architectures. The researchers address this by introducing the **Σ-Voxfield**, a hybrid representation that discretizes the scene into a grid of voxels while maintaining local geometric detail.

In this formulation, each occupied voxel (with a size $v_s$, typically set to 0.6m) stores a fixed number of points $n$ (specifically $n=20$). Each point within a voxel is defined by its 3D position relative to the voxel center and its RGB color. By keeping the number of points per voxel constant, each voxel can be treated as a single "token" with a fixed feature dimensionality. This fixed cardinality is a key design choice that allows the 3D scene to be processed by transformer architectures, which are traditionally optimized for sequences of tokens.

![Σ-Voxfield Gaussian Alignment](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06113v1/x5.png)
*Figure 2: To render the Σ-Voxfield, each point is converted into a 2D Gaussian. Local normals are estimated using Principal Component Analysis (PCA) over neighboring points to align the rotation of the Gaussians with the underlying surface.*

To render these points into a 2D image, the system employs a technique similar to Gaussian Splatting. Because a raw point cloud can appear "holey" or incomplete at low densities, each point is expanded into a 2D Gaussian splat. To ensure these splats cover the surface realistically, the system calculates local surface normals using Principal Component Analysis (PCA) on a point's spatial neighbors. These normals define the orientation of the Gaussian, allowing it to lie flat against the implicit surface of the road, buildings, or vehicles.

## Semantic-Conditioned 3D Diffusion

The core of the generative process is a diffusion model that learns to produce Σ-Voxfield tokens. Diffusion models work by gradually removing noise from a signal until a coherent structure emerges. In SEM-ROVER, this denoising process is performed by a 1D Diffusion Transformer.

The model takes a local set $X_\xi$ of adjacent Σ-Voxfields as input tokens. Each token represents a $6n$-dimensional feature vector (3D coordinates and RGB values for each of the $n$ points). To guide the generation, the model is conditioned on a 3D semantic grid. Every voxel in the input grid has a label (e.g., "road," "sidewalk," "car," "vegetation"), and these labels act as a global layout prior.

![Diffusion Transformer Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06113v1/x6.png)
*Figure 3: The diffusion transformer architecture utilizes 3D positional encodings and semantic conditioning to denoise the Σ-Voxfield features over multiple timesteps.*

Spatial structure is maintained through 3D positional embeddings. Since transformers are permutation-invariant (they don't inherently know where a token is in space), the researchers compute sinusoidal encodings based on the 3D center coordinates of each voxel. These encodings are added to the noisy tokens, ensuring the model understands the relative distances and orientations of different scene elements. The training objective follows a standard $L_2$ loss, where the model predicts the noise added to the original Σ-Voxfield representation.

## Scalability via Progressive Spatial Outpainting

A significant challenge in 3D generation is memory consumption. Generating a city block all at once would require an enormous amount of VRAM. To solve this, the researchers implement a progressive spatial outpainting strategy. This allows the model to generate arbitrarily large scenes by processing them in overlapping local sets.

The strategy utilizes the **Repaint** scheduler. For any given local region $X_\xi$, the model partitions the tokens into a "known" part (geometry already generated in a previous step) and a "target" part (new geometry to be created). During each denoising step, the known part is reset to its fixed values, while the target part is updated. Because each generation step only considers a bounded number of tokens $N_\xi$ (usually between 50 and 150 voxels), the computational cost per step remains constant regardless of total scene size.

![Infinite Scene Generation](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06113v1/x3.png)
*Figure 4: Spatial outpainting allows the system to expand the 3D scene linearly. Overlapping regions ensure that geometry and colors transition smoothly between adjacent generated blocks.*

This iterative approach decouples the inference cost from the total area. As a result, the system can synthesize scenes spanning over 100,000 $m^2$ with a memory footprint as low as 8 GB. This represents a significant reduction in resource requirements compared to previous methods that often require 40 GB to 75 GB of VRAM for similar tasks.

## Deferred Diffusion Rendering for Photorealism

While the Σ-Voxfield grid captures consistent 3D structure, raw splat rendering often lacks the high-frequency details, lighting effects, and background elements (like the sky) required for photorealism. To address this, the framework uses a **Deferred Diffusion Rendering** module.

This module is a modified Stable Diffusion model that takes the initial 2D rendering, denoted as $I_\Sigma(w)$, as a condition. The model is trained to transform this simplified 3D buffer into a high-fidelity image $I_{DR}(w)$. To prevent the model from "hallucinating" details where no 3D geometry exists, a visibility mask is provided as an additional input. This mask explicitly tells the renderer which parts of the image correspond to the generated 3D surface and which correspond to the empty background or sky.

![Deferred Rendering Module](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06113v1/x7.png)
*Figure 5: The deferred rendering engine uses a 2D UNet to denoise a latent representation conditioned on the 3D buffer, the sky mask, and the previously generated frame for temporal consistency.*

To ensure that video sequences are smooth, the researchers explored two temporal consistency variants:
1.  **Autoregressive Stable Diffusion (ASD):** The renderer is conditioned on the previous frame, encouraging the model to maintain color and texture consistency over time.
2.  **Video Stable Diffusion (VSD):** A spatiotemporal model generates batches of frames simultaneously, leveraging temporal attention to reduce flickering.

## Findings and Significance

Evaluation of the SEM-ROVER system on datasets like Waymo Open Dataset and PandaSet demonstrates several key advantages over current approaches. 

Quantitative results using metrics like Fréchet Inception Distance (FID) and Kernel Inception Distance (KID) show that the model is particularly robust to viewpoint shifts. While image-based models often degrade when the camera moves significantly away from the original path, SEM-ROVER maintains high quality and geometric integrity. Achieved FID scores on novel views (unseen during training) are significantly better than those of baselines like GEN3C and InfiniCube.

The primary contributions of this work can be summarized as:
- **Efficiency:** The Σ-Voxfield representation allows for 3D generation with a constant memory budget. The system operates on consumer-grade hardware (8 GB VRAM), making it more accessible than many competing methods.
- **Consistency:** By generating in 3D space first and rendering second, the model inherently avoids the "flickering" and geometric distortions common in 2D-to-3D lifting methods.
- **Flexibility:** The semantic conditioning enables direct control over the scene. Users can edit the semantic grid—for example, by adding or removing a car—and the model will coherently regenerate the 3D geometry and textures to match the new layout.

In addition to driving simulations, the system supports applications like scene inpainting. By masking a local area of voxels and re-running the diffusion process, the system can produce diverse variations of a single street corner, varying the types of vehicles, the condition of the pavement, or the appearance of buildings while keeping the rest of the environment unchanged. This capability provides a powerful tool for large-scale data augmentation in the training of AI models for autonomous navigation.

## Relevant Citations

- InfiniCube: Unbounded and controllable dynamic 3D driving scene generation with world-guided video models: This paper is a primary state-of-the-art competitor that SEM-ROVER is compared against. InfiniCube represents a multi-stage pipeline for large-scale scene generation, and the authors use it for direct qualitative and quantitative comparisons to demonstrate their own method's advantages in geometric consistency and reduced computational cost.
- GEN3C: Generalizable 3d scene generation from video diffusion with 3D cache: GEN3C is another key competitor representing an alternative video-diffusion-based approach to driving scene generation. SEM-ROVER includes it in its quantitative evaluation table to benchmark its performance and highlight the benefits of its direct 3D generation approach over methods that distill 2D video information.
- Re-Paint: Inpainting using denoising diffusion probabilistic models: This citation is fundamental to a core contribution of the main paper: scalability. The SEM-ROVER framework explicitly uses the Repaint outpainting strategy to progressively expand the generated scene, allowing the model to create large-scale environments while only operating on small, local neighborhoods.
- Scalable Diffusion Models with Transformers: This paper provides the architectural backbone for the central generative model in SEM-ROVER. The authors state they employ a 1D Diffusion Transformer (DiT) to perform the diffusion process on their novel Σ-Voxfield tokens, making this reference essential to understanding the design of their core 3D model.
- High-resolution image synthesis with latent diffusion models: This paper, which introduced Stable Diffusion, is foundational to the rendering pipeline of SEM-ROVER. The authors use a modified Stable Diffusion model as a deferred renderer to convert their generated Σ-Voxfield grid into final, photorealistic images, which is a critical step for visual quality and evaluation.
