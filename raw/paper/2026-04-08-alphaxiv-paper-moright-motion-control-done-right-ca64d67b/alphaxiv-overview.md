# MoRight: Motion Control Done Right

- alphaXiv: https://www.alphaxiv.org/abs/2604.07348
- Source paper: https://arxiv.org/abs/2604.07348

## Introduction: The Challenge of Controlled Motion

Controllable video generation is the art of producing dynamic visual content that strictly adheres to user-provided specifications, such as how an object should move or how the camera should rotate. While recent advancements in generative AI have made it possible to create stunning videos from simple text prompts, providing fine-grained control remains a significant hurdle. Existing models often struggle with two fundamental issues: entanglement and a lack of causal reasoning.

Entanglement occurs because most models represent all motion—whether it is a person walking or the camera zooming in—as a series of shifting pixels. When a user tries to control both simultaneously, the model becomes confused. For instance, if you specify that a car should move forward while the camera orbits around it, the pixel-wise trajectories for the car are constantly changing due to the camera's perspective. This makes it extremely difficult for a model to maintain the integrity of the object's motion while also respecting the camera's path.

Furthermore, current systems typically treat motion through the lens of "kinematics"—simply calculating where pixels should land in the next frame. They lack an internal understanding of "causality," or the cause-and-effect relationships between objects. In the real world, if a hand pushes a cup, the cup reacts by sliding. Requiring a user to manually draw the trajectory for every single object involved in an interaction is impractical. A truly intelligent video generator should be able to infer the reaction from the action.

"MoRight: Motion Control Done Right" addresses these gaps by introducing a unified framework for disentangled camera-object control and causal motion reasoning. By separating the "what" (object action) from the "where" (camera viewpoint) and teaching the model to predict consequences, MoRight enables a more intuitive and physically plausible form of video creation.

![MoRight Overview: The framework enables forward and inverse motion reasoning while maintaining independent control over camera and object dynamics.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.07348v1/x22.png)

## Disentangling Camera and Object Dynamics

To solve the entanglement problem, MoRight moves away from the standard practice of modeling motion in a single, perspective-dependent view. Instead, it employs a dual-stream architecture based on a Diffusion Transformer (DiT). This design logic is built on the premise that object motion is unambiguous when viewed from a fixed, "canonical" perspective.

### The Dual-Stream Architecture
The MoRight framework operates two parallel generation streams that share the same underlying neural network weights:

1.  **The Canonical Stream:** This stream serves as a virtual anchor. It models the motion of objects in the source image plane as if the camera were completely static. Users define their desired object trajectories in this stable view.
2.  **The Target Stream:** This stream is responsible for generating the final video. it incorporates the user's specific camera movements (e.g., pans, tilts, or zooms) to produce the desired cinematic effect.

Crucially, these two streams are not isolated. They interact through a mechanism called Cross-View Self-Attention. At every layer of the transformer, tokens from the target view "attend" to tokens from the canonical view. This allows the model to synchronize the object motion learned in the stable canonical view with the dynamic perspective of the target view.

### Condition Injection
The model receives instructions through different latent embeddings. For the target stream, the camera pose $C_i$ is used to warp the initial image, which is then encoded into a camera condition $z_{cam}$. For the canonical stream, the user's object trajectories are encoded into a motion embedding $e_{trk}$. The features $f_i$ at each transformer block are updated as follows:

$$
f_i = f_i + W_{cam} z_{cam} + W_{trk} e_{trk} \text{ at each block } i
$$

Following this injection, the features from both streams are concatenated and processed through the self-attention layer:

$$
[f^{can}, f^{tgt}] = \text{Self-Attn}([f^{can}, f^{tgt}])
$$

This ensures that the target stream inherits the correct object dynamics from the canonical stream while maintaining the perspective required by the user's camera path.

![Architecture of MoRight: The dual-stream DiT uses shared weights and cross-view attention to transfer motion cues from a canonical static view to a dynamic target view.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.07348v1/x32.png)

## Motion Causality: Beyond Pixel Displacement

The second major contribution of MoRight is its ability to reason about motion causality. Rather than just moving pixels from point A to point B, the model learns the relationship between an "active" agent (the cause) and a "passive" object (the effect).

### Active and Passive Decomposition
MoRight categorizes all foreground motion into two types:
*   **Active Motion ($\tau_{act}$):** This represents the user-driven action, such as a hand reaching out to grab a teapot.
*   **Passive Motion ($\tau_{pas}$):** This represents the resulting consequence, such as the teapot being lifted or liquid pouring out.

By training the model on these distinct categories, MoRight gains the ability to perform complex visual reasoning. This is achieved through a "motion dropout" strategy during training. The model is sometimes shown only the active motion and asked to generate the full scene, forcing it to "fill in" the passive reactions. At other times, it is shown the passive goal and must infer the active cause.

### Forward and Inverse Reasoning
This causal understanding enables two powerful inference modes:
*   **Forward Reasoning ($\tau_{act} \to \tau_{pas}$):** The user specifies an action (e.g., "push this box"). The model then predicts and generates how the box should slide, tumble, or collide with other objects.
*   **Inverse Reasoning ($\tau_{pas} \to \tau_{act}$):** The user specifies a desired outcome (e.g., "the soccer ball should move into the net"). The model then automatically generates the plausible action that causes it, such as a player's foot kicking the ball.

This leap from kinematics to causality means users no longer need to be expert animators. They can specify high-level intents, and the model handles the complex physical interactions.

![Causal Reasoning Examples: MoRight can predict consequences from actions (forward) and infer actions from desired outcomes (inverse).](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.07348v1/x250.png)

## Data Curation and Training Strategy

To train a model capable of such sophisticated reasoning, the researchers developed a multi-stage data curation pipeline. Standard video datasets are often "flat"—they lack the paired information needed for dual-stream learning or causal decomposition.

### The Pipeline
The pipeline consists of several specialized stages:
1.  **Motion Extraction and Canonicalization:** Using foundation models like ViPE for camera poses and AllTracker for pixel trajectories, raw videos are converted into a structured format. The trajectories are then reprojected into a static canonical view to create the training signals for the canonical stream:
    $$\tau_{can} = \text{Project}(\text{Unproject}(\tau_{pix}, \text{Depth}), C_0)$$
2.  **Causal Labeling:** A vision-language model (Qwen) identifies which objects in a video are "active" and which are "passive." Instance segmentation models like SAM2 then extract the specific masks and trajectories for each.
3.  **Synthetic Multi-View Generation:** Because paired videos of the same scene from different viewpoints are rare, the researchers used a camera-controlled video-to-video model to synthesize dynamic-camera versions of static-camera real-world footage. This provides the "ground truth" for how motion should look when the camera moves.

The model is trained using a flow matching loss, which optimizes the probability paths for the diffusion process. By mixing synthetic multi-view data with abundant real-world single-view data, the model learns both the geometric precision of camera control and the complex textures of real-world physics.

![Data Curation Pipeline: The three-stage process involves motion extraction, active-passive decomposition, and paired multi-view synthesis.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.07348v1/x254.png)

## Evaluation and Impact

MoRight was evaluated against several state-of-the-art benchmarks, including DynPose-100K (for camera control) and WISA (for object interaction). The results consistently showed that MoRight outperforms baseline methods that couple camera and object dynamics.

### Key Findings
*   **Superior Controllability:** In human perceptual studies, participants preferred MoRight's outputs over 53% of the time for controllability and motion realism. This is particularly impressive because MoRight uses less input information (only trajectories on the first frame) compared to baselines that often require trajectories for every frame.
*   **Physical Commonsense:** Quantitative metrics showed that MoRight produces videos with significantly higher "physical commonsense" scores. It avoids common artifacts where objects pass through each other or disappear into thin air during interactions.
*   **Generalization:** Despite being trained on specific datasets, MoRight demonstrates robust generalization to a wide variety of scenes, from complex cooking tasks to outdoor sports.

### Significance and Impact
The implications of MoRight extend beyond simple video editing. Its ability to disentangle camera and object motion makes it a prime candidate for **Embodied AI**, where agents need to simulate the outcomes of their actions before executing them. It also serves as a powerful **World Model**, providing a way to simulate physical interactions in a purely visual domain without the need for expensive physics engines.

For content creators, MoRight offers a new paradigm of "interaction-based" editing. Instead of meticulously keyframing every movement, a creator can simply "drag" an object and let the model handle the cinematic camera work and the causal reactions, drastically reducing the time required to produce high-quality dynamic content.

While limitations remain—such as occasional hallucinations in very complex scenes or difficulty with extremely fast camera transitions—MoRight represents a significant step toward video generation models that truly understand the physical and causal structure of the world they are creating.

## Relevant Citations

- Wan: Open and advanced large-scale video generative models: This paper introduces the Wan2.1-14B model, which serves as the foundational pretrained backbone for MoRight. The authors of MoRight explicitly state they build upon and fine-tune this large-scale video generation model, making it a critical dependency for their work.
- Motion prompting: Controlling video generation with motion trajectories: This is a key prior work in trajectory-based video generation that MoRight directly compares against in its experiments. MoRight positions its own contributions, such as disentangled motion control and causality reasoning, as solutions to the limitations of existing methods like Motion Prompting, which entangle camera and object motion.
- Wan-move: Motion-controllable video generation via latent trajectory guidance: WanMove is another state-of-the-art motion-conditioned model that serves as a primary baseline for comparison in MoRight's evaluation. By benchmarking against WanMove, the paper demonstrates the superiority of its disentangled framework in terms of generation quality, motion controllability, and physical plausibility.
- Syncammaster: Synchronizing multi-camera video generation from diverse viewpoints: This paper is cited as a direct inspiration for MoRight's core architectural choice. The authors explicitly credit this work for the dual-stream generation framework, which they adapt to decouple object motion (in a canonical view) from camera transformations (in a target view), a central contribution of their paper.
