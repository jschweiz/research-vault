# HOIGS: Human-Object Interaction Gaussian Splatting

- alphaXiv: https://www.alphaxiv.org/abs/2604.04016
- Source paper: https://arxiv.org/abs/2604.04016

## Understanding Human-Object Interaction in 4D

The reconstruction of dynamic scenes from monocular video is a significant challenge in computer vision, particularly when those scenes involve complex human-object interactions (HOI). Whether it is a person picking up a backpack, manipulating a tool, or interacting with furniture, capturing these moments in 3D over time (4D) requires modeling both the articulated motion of the human body and the rigid or semi-rigid motion of the objects involved. High-quality reconstruction of these interactions is essential for advancing technologies in virtual reality, 3D animation, and the development of immersive digital content.

![Human-object interaction reconstruction](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04016v1/intro.jpg)
*Figure 1: HOIGS enables high-quality 4D reconstruction of complex human-object interactions from a single monocular video.*

Existing methodologies for dynamic scene reconstruction generally take one of two paths. Human-centric methods utilize parametric models like SMPL to capture body poses but often treat objects as static background or fail to represent them altogether, resulting in visual artifacts like "ghosting" where objects appear blurred or translucent. Conversely, general 4D dynamic reconstruction methods, such as 4D Gaussian Splatting, treat all moving elements in a scene uniformly. While flexible, these general methods often struggle with the fine-grained details of human articulation and the specific rigid trajectories of manipulated objects, especially during close contact or occlusion.

HOIGS (Human-Object Interaction Gaussian Splatting) addresses these limitations by introducing a framework that explicitly disentangles human and object representations. By applying specialized motion models to each entity and coupling them through an interaction-aware refinement module, the system captures the bidirectional dependencies that define realistic interactions.

## Disentangled Representations for Humans and Objects

A core principle of HOIGS is the recognition that humans and objects possess fundamentally different physical and kinematic properties. The human body is articulated and capable of complex deformations, whereas manipulated objects often move as rigid bodies following continuous paths. To capture these nuances, HOIGS separates the scene into three distinct components: the human, the interacting object, and the static background.

![HOIGS Pipeline](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04016v1/x1.png)
*Figure 2: The HOIGS pipeline disentangles the scene into human, object, and background components, using entity-specific deformation models.*

The framework utilizes 3D Gaussian Splatting (3DGS) as its primary rendering engine. In this representation, the scene is composed of millions of small, 3D ellipsoids (Gaussians), each defined by its position, rotation, scale, color, and opacity. For a dynamic scene, these Gaussians must move and deform over time. HOIGS assigns different "motion laws" to the Gaussians representing the human and those representing the object, allowing each to be optimized according to its specific nature.

## Articulated Human Modeling with HexPlanes and SMPL-X

For the human component, the framework adopts a hybrid approach that combines implicit spatial-temporal features with explicit parametric priors. The human body is represented in a canonical (T-pose) space. To handle the deformation from this canonical space to the dynamic posed space seen in each video frame, HOIGS employs a HexPlane-based feature representation.

The HexPlane decomposes a 4D space into six planes (XY, XT, YT, ZT, YZ, XZ) to efficiently encode spatial and temporal features. For any point in space at time $t$, features are sampled from these planes and processed by a shallow Multi-Layer Perceptron (MLP). This MLP predicts the necessary Gaussian attributes, such as position offsets, rotations, and skinning weights.

To ensure the reconstructed human remains anatomically plausible, the framework leverages SMPL-X, a sophisticated parametric human model. The final position of the human Gaussians in world space is determined via Linear Blend Skinning (LBS), driven by the SMPL-X pose parameters. This combination of feature-based learning and parametric priors allows the model to capture both the general articulation of the body and fine-grained surface details like clothing wrinkles or facial expressions.

## Rigid Object Trajectories via Cubic Hermite Splines

Interacting objects present a different challenge. Unlike the articulated human body, many manipulated objects are rigid but follow complex, non-linear trajectories as they are moved. To model this, the authors introduce a trajectory representation based on Cubic Hermite Splines (CHS).

Instead of predicting the object's position frame-by-frame—which can lead to jittery or discontinuous motion—the motion is modeled as a continuous curve. The object's path is defined by a set of learnable control points (positions) at specific keyframes and corresponding velocity vectors (tangents).

![Object trajectory modeling](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04016v1/x2.png)
*Figure 3: Object motion is parameterized using Cubic Hermite Splines, ensuring smooth and continuous trajectories in both position and velocity.*

For any intermediate time $t$ between keyframes $i$ and $i+1$, the position of the object is calculated using the interpolation formula:

$$P(t) = (2t^3 - 3t^2 + 1)P_i + (t^3 - 2t^2 + t)\tau_i + (-2t^3 + 3t^2)P_{i+1} + (t^3 - t^2)\tau_{i+1}$$

In this equation, $P_i$ represents the position at keyframe $i$, and $\tau_i$ represents the tangent (velocity) at that keyframe. This spline-based approach ensures that both the position and the velocity of the object remain continuous throughout the sequence. The object's rotation is handled separately using Spherical Linear Interpolation (SLERP) between keyframe rotations, while its scale is kept constant to enforce physical rigidity.

## Modeling Mutual Dependencies: The Interaction Module

The most distinct contribution of the HOIGS framework is the Interaction-aware (HOI) module. In real-world interactions, human motion and object motion are not independent; the hand's position is dictated by the object it holds, and the object's trajectory is a direct result of human manipulation.

To capture this mutual influence, the framework uses a cross-attention mechanism. First, features are extracted for both entities. For the human, the body is divided into 16 semantic parts (e.g., head, torso, left hand, right hand). Features for each part are averaged from the HexPlane to create human part tokens $F_{Human}$. For the object, continuous motion features $F_{Object}$ are generated from the spline velocities and learnable embeddings.

![Interaction Module](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04016v1/HOI_SUB_3.jpg)
*Figure 4: The bidirectional cross-attention module models how the human and object influence each other's motion during interaction.*

The module performs bidirectional cross-attention:
1.  **Human-to-Object:** The object "queries" the human features to adjust its own trajectory based on which body part it is near.
2.  **Object-to-Human:** The human parts "query" the object features to refine their pose based on the object's motion.

The queries $Q$, keys $K$, and values $V$ are projected from these features. A distance-based mask is applied to the attention calculation to ensure that only relevant body parts (like the hands) influence the object, while distant parts (like the feet during a hand-based task) are ignored. The output of this module is a set of residual corrections—$F'_{Human}$ and $F'_{Object}$—which are added to the baseline deformations to refine the SMPL-X pose and the object's position. This ensures that the hand and object stay perfectly aligned even during rapid movement or occlusion.

## Joint Optimization and Training

The entire system is trained by minimizing the difference between the rendered images and the original video frames. The optimization process jointly refines the human deformation field, the object splines, the interaction module parameters, and the static background.

The total objective function $L$ is a weighted combination of several specialized loss terms:

$$L = \lambda_{human} L_{human} + \lambda_{object} L_{object} + \lambda_{scene} L_{scene} + \lambda_{depth} L_{depth}$$

- **Photometric Losses ($L_{human}$, $L_{object}$, $L_{scene}$):** These measure the color and structural similarity between the rendered views and the ground truth frames for each specific region (human, object, or background).
- **Depth Loss ($L_{depth}$):** This ensures the 3D structure is consistent with depth estimates provided by off-the-shelf depth estimation models, helping to resolve ambiguities in the monocular view.
- **Regularization:** Additional terms are used to maintain the stability of the human body shape and facial expressions.

By optimizing these terms together, the model learns to distribute the "responsibility" for each pixel correctly between the human, the object, and the background, leading to a coherent 3D scene representation.

## Quantitative and Qualitative Evaluation

HOIGS was evaluated on several prominent datasets, including HOSNeRF, BEHAVE, and ARCTIC, which contain diverse sequences of people interacting with objects like backpacks, chairs, and tools.

Quantitatively, HOIGS consistently outperformed state-of-the-art baselines across multiple metrics. On the HOSNeRF dataset, it achieved a $PSNR$ (Peak Signal-to-Noise Ratio) of 25.89, significantly higher than general 4DGS methods (24.96) and specialized human-centric models like ExAvatar (24.35). Lower $LPIPS$ scores—a metric that measures perceptual similarity—further confirmed that the reconstructions are visually more realistic and closer to the original video.

![Qualitative Results](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04016v1/ours_results.jpg)
*Figure 5: Comparative results demonstrate that HOIGS produces sharper interaction details and fewer artifacts compared to existing methods.*

Qualitatively, the benefit of the disentangled representation is evident. While other methods often produce "ghosting" artifacts where the human and object seem to merge or fade, HOIGS maintains clear boundaries and sharp textures. The interaction module is particularly effective in hand-object contact zones, where it prevents the object from "drifting" away from the hand—a common failure mode in previous 4D reconstruction frameworks.

Ablation studies performed by the authors confirmed that both the spline-based object modeling and the cross-attention interaction module are critical. Removing the interaction module, for example, led to a measurable drop in reconstruction quality, as the system could no longer precisely coordinate the dependent motions of the human and the object.

## Significance and Future Outlook

The introduction of HOIGS represents a shift in how dynamic human-object interactions are handled in the context of Gaussian Splatting. By explicitly modeling the "dialogue" between human and object motion through cross-attention, the framework achieves a level of fidelity that was previously difficult to reach with monocular video.

The system's ability to run inference at real-time speeds (over 40 frames per second) makes it a viable candidate for practical applications in content creation. Users can take a standard video and transform it into a high-quality 4D asset that can be viewed from any angle.

Despite its performance, the authors note that the method currently relies on pre-computed human pose parameters (SMPL-X) and masks from off-the-shelf tools. Future research could focus on making the system more end-to-end, potentially learning these priors directly during the optimization. Additionally, while the current spline model is ideal for rigid objects, expanding the framework to handle highly deformable objects (like cloth or soft bags) remains an area for exploration. Nevertheless, HOIGS provides a robust foundation for capturing the complexities of the physical world in a digital, interactive format.

## Relevant Citations

- 3d gaussian splatting for real-time radiance field rendering: This is the seminal paper that introduced 3D Gaussian Splatting, the core real-time rendering and scene representation technique upon which the main paper, HOIGS, is fundamentally built. HOIGS extends this foundational framework to handle the complexities of dynamic human-object interactions.
- 4d gaussian splatting for real-time dynamic scene rendering: This paper introduces the extension of Gaussian Splatting to dynamic scenes (4DGS), representing a primary category of methods that HOIGS is directly compared against. The main paper argues that such general dynamic scene methods fail to capture the specific details of human articulation and interaction, a limitation HOIGS aims to overcome.
- Expressive whole-body 3d gaussian avatar: This paper, referred to as ExAvatar, is a state-of-the-art human-centric reconstruction method that HOIGS frequently uses as a key baseline for comparison. It is cited to highlight the limitations of prior art that focuses solely on the human actor while failing to render interacting dynamic objects, which is the central problem HOIGS addresses.
- Hosnerf: Dynamic human-object-scene neural radiance fields from a single video: This work addresses the exact same problem of dynamic human-object-scene reconstruction, but with a NeRF-based approach. Critically, it also introduces the HOSNeRF dataset, which is a primary benchmark used for quantitative and qualitative evaluation in the main paper, making this citation essential for understanding the experimental context.
- Hexplane: A fast representation for dynamic scenes: This paper introduces the HexPlane representation, which is a core technical component adopted by HOIGS for modeling human deformation. The main paper explicitly uses a HexPlane-based deformation field to capture fine-grained human motion and spatiotemporal features, making this citation key to understanding the proposed methodology.
