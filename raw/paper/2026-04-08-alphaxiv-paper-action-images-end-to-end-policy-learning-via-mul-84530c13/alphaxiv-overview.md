# Action Images: End-to-End Policy Learning via Multiview Video Generation

- alphaXiv: https://www.alphaxiv.org/abs/2604.06168
- Source paper: https://arxiv.org/abs/2604.06168

## Bridging the Gap Between Video Prediction and Policy Generalization

In the pursuit of generalist robot policies, world models have emerged as a powerful tool. These models learn to predict the visual future of an environment, effectively "hallucinating" how a scene evolves in response to a robot's actions. However, a significant discrepancy remains: while contemporary video generation models can produce visually realistic future frames, they often struggle to translate this predictive ability into robust policy generalization, particularly when faced with unseen environments or novel robot embodiments. 

![Action Images Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06168v1/x1.png)
*Figure 1: Overview of the Action Images framework. It unifies robot observation and action into a common video space, enabling a pre-trained video backbone to serve as a zero-shot policy.*

A primary reason for this bottleneck is the way actions are traditionally represented within these models. Most existing methods treat actions as low-dimensional tokens or abstract latent vectors that are detached from the spatial context of the image. This detachment shifts the burden of generalization to a specialized control head or action module, which often fails to leverage the rich, spatially-grounded knowledge inherent in large-scale pre-trained video backbones. 

The "Action Images" framework addresses this by reformulating policy learning as a multiview video generation task. By representing robot actions as pixel-grounded images that explicitly track the motion of the robot arm in 3D space, the model makes actions "native" to the video space. This allows the video backbone itself to function as a zero-shot policy, directly generating actions as visual signals without the need for additional, non-spatial modules.

## Action Images: Grounding Control in Pixels

The core of this approach is the transformation of a 7-Degrees-of-Freedom (7-DoF) robot action into a visual format. A standard robot action at time $t$, denoted as $a_t = [p_t, \theta_t, g_t]$, consists of the end-effector's 3D position $p_t$, its orientation $\theta_t$, and a binary gripper state $g_t$ (open or closed). 

To make this action interpretable by a video model, it is first mapped to three semantic 3D points that capture the pose of the gripper:
1.  **Position Point**: $q_{\text{pos}_t} = p_t$, representing the center of the end-effector.
2.  **Up Point**: $q_{\text{up}_t} = p_t + \ell R(\theta_t)e_x$, representing a canonical in-plane direction.
3.  **Normal Point**: $q_{\text{normal}_t} = p_t + \ell R(\theta_t)(-e_z)$, representing the normal to the gripper plane.

In these equations, $R(\theta_t)$ is the rotation matrix derived from the orientation, and $\ell$ is a small constant length. These 3D points are then projected into the image space of each camera view $v$ using the camera's known intrinsic and extrinsic parameters. 

![Action Image Rendering](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06168v1/x2.png)
*Figure 2: The rendering process of an Action Image. The position, normal, and up points are encoded into the Red, Green, and Blue channels of an RGB image as Gaussian heatmaps.*

The resulting 2D points are rendered into an "Action Image" $A^{(v)}_t \in \mathbb{R}^{H \times W \times 3}$ using Gaussian heatmaps across the three color channels:
*   **Red Channel**: Encodes the 2D projection of the position point.
*   **Green Channel**: Encodes the 2D projection of the normal point.
*   **Blue Channel**: Encodes the 2D projection of the up point. 

To handle the binary gripper state $g_t$ without adding extra channels, it is injected into the background of the blue channel (pixels where the Gaussian response is low). This creates a unified visual representation where action videos share the same spatial and temporal structure as the observation videos $O^{(v)}$.

## A Unified World Action Model Architecture

With actions represented as images, the framework employs a large pre-trained video generator—specifically Wan 2.2—to jointly model observation and action. The model treats both as sequences of latent tokens.

For each camera view $v$, the RGB observation clip $V^{(v)}$ and the aligned action-frame clip $A^{(v)}$ are encoded into a latent space using a 3D Variational Autoencoder (VAE). These sequences are concatenated temporally to form a single input sequence $X_v = [V^{(v)}, A^{(v)}]$, effectively creating a unified timeline for each view.

![Unified Training Strategy](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06168v1/x4.png)
*Figure 3: The unified model architecture and masking strategies. Diverse masks allow the same backbone to perform joint generation, action-conditioned video prediction, and video-to-action labeling.*

To enable a single model to perform multiple robotic tasks, the authors utilize a variety of masking strategies during training:
1.  **Joint Video-Action Generation**: Both $V$ and $A$ tokens are masked (except for the initial frame), training the model to predict future scenes and the actions required to achieve them.
2.  **Action-Conditioned Video Generation**: Action tokens are kept visible while observation tokens are masked, training the model to synthesize video consistent with a given control sequence.
3.  **Video-to-Action Labeling**: Observation tokens are visible while action tokens are masked, training the model to infer the underlying actions from a video of a robot moving.

The model is optimized using a flow-matching objective, where it learns to predict the "velocity" of noise towards the target data, conditioned on text prompts and camera Plücker embeddings. This camera conditioning is crucial for maintaining consistency across multiple views.

## Decoding Actions from Visual Predictions

When the model generates an Action Image sequence, these visual signals must be converted back into physical 7-DoF robot commands to be executable. This decoding process leverages multi-view geometry to resolve the depth ambiguities inherent in 2D projections.

The decoding for a single time step follows these steps:
1.  **Gripper State**: The state $g_t$ is recovered by averaging the blue channel's background values across all views.
2.  **3D Point Reconstruction**: For each semantic point (position, normal, up), the model identifies a 2D anchor point in a "main" view heatmap. It then casts a ray from that camera's center through the anchor.
3.  **Cross-View Matching**: Candidate 3D points are sampled along this ray. Each candidate is projected into a "side" view, and the point that best matches the response in the side-view heatmap is selected as the reconstructed 3D point.
4.  **Pose Recovery**: Once the three 3D points ($q_{\text{pos}_t}$, $q_{\text{up}_t}$, $q_{\text{normal}_t}$) are reconstructed, the end-effector position $p_t$ and orientation $\theta_t$ are calculated by deriving the orthogonal axes $e_x$, $e_y$, and $e_z$ from the vectors between these points.

![Decoding Mechanism](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06168v1/x3.png)
*Figure 4: The decoding process. Multi-view heatmaps are used via ray casting and back-projection to reconstruct the 3D semantic points required for robot control.*

## Experimental Performance and Generalization

The Action Images framework was evaluated on its ability to perform zero-shot tasks in both simulated and real-world environments. In the zero-shot setting, the model is tested on tasks, objects, or environments it did not see during training.

In **RLBench** simulations, Action Images significantly outperformed established baselines like π0.5 and Cosmos-Policy. For example, on the "pick cup" task, Action Images achieved a 30% success rate compared to the 0-10% seen in other models. On "close drawer," it reached a 50% success rate.

The model's generalization was further tested in the **real world** using an xArm robot. Even when facing entirely unseen objects and environments, the model demonstrated the ability to generate coherent video-action sequences. It achieved a 40% success rate on "Place Cup" and a 45% success rate on "Close Drawer" in a zero-shot manner. These results suggest that grounding action in pixels allows the model to transfer the visual-spatial common sense learned from massive video datasets to the domain of robotic control.

![Real-World Zero-Shot Performance](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06168v1/x5.png)
*Figure 5: Qualitative results of zero-shot real-world rollouts. The model accurately predicts the motion trajectories and executes the "Close the paper box" task on an unseen robot arm.*

Beyond policy execution, the unified model showed superior performance in auxiliary tasks. In **action-conditioned video generation**, it outperformed specialized models like Tora in video quality metrics (PSNR, SSIM, FVD). In **video-to-action labeling**, it surpassed point-tracking baselines like CoTracker3, demonstrating a more robust understanding of the robot's physical movement within a scene.

## Significance and Future Directions

The significance of this work lies in its unification of action and perception. By treating robot control as just another set of pixels to be predicted, it removes the need for complex, task-specific architectures that often fail to generalize. The Action Images representation provides an interpretable, spatially-grounded bridge between high-level video generation and low-level physical control.

Currently, the system primarily operates in an open-loop fashion, generating a sequence of actions based on initial observations. A key area for future development is the transition to high-frequency closed-loop control. This will likely involve techniques like model distillation or diffusion acceleration to reduce inference latency, allowing the robot to react dynamically to changes in the environment in real-time. 

By demonstrating that pixel-grounded actions can inherit the strong generalization of large video models, the framework provides a promising path toward truly general-purpose robotic agents capable of operating in the complexity of the real world.

## Relevant Citations

- Tesseract: learning 4d embodied world models: This paper is a direct world-model-based baseline that 'Action Images' is compared against in its experimental evaluations. The authors of the main paper also worked on Tesseract, suggesting it is a closely related work whose limitations likely motivated the development of the pixel-grounded action representation.
- Cosmos policy: Fine-tuning video models for visuomotor control and planning: This is a key competitive baseline used throughout the experiments. The main paper cites Cosmos-Policy as an example of an approach that uses action representations which are not spatially grounded, a core problem that 'Action Images' aims to solve by grounding actions directly in the pixel space.
- World action models are zero-shot policies: This paper, referred to as DreamZero in the text, is highlighted as a model with strong zero-shot generalization. However, 'Action Images' critiques its reliance on separate action modules, which motivates its own approach of creating a unified video backbone that acts as a zero-shot policy without needing an extra module.
- Unified video action model: This citation is presented as a key prior work that explores joint video-action generation. The 'Action Images' paper builds on this direction but differentiates itself by proposing a pixel-grounded action representation to create a more tightly integrated model, addressing the limitations of using separate action modules.
