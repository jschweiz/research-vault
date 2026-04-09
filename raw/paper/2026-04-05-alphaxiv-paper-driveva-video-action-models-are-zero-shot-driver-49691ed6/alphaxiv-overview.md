# DriveVA: Video Action Models are Zero-Shot Drivers

- alphaXiv: https://www.alphaxiv.org/abs/2604.04198
- Source paper: https://arxiv.org/abs/2604.04198

Autonomous driving systems have historically struggled with generalization—the ability to perform reliably in environments, weather conditions, or sensor configurations they have never seen before. While current approaches like Vision-Language-Action (VLA) models have improved the understanding of driving scenes by pre-training on large-scale text and image datasets, they often lack a deep understanding of how scenes evolve over time. This leads to a disconnect between what the model "imagines" will happen and what the vehicle actually does.

DriveVA addresses these challenges by reimagining the driving task as a joint video-generation and trajectory-planning problem. By leveraging the power of large-scale video generation models, DriveVA functions as a "Video Action Model" (VAM) that can drive zero-shot in unseen domains. It does this by ensuring that the vehicle's planned actions are mathematically and logically consistent with a predicted future video of the scene.

![DriveVA Overview: Unified Video-Action Modeling and Zero-Shot Generalization](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04198v1/x1.png)
*Figure 1: DriveVA integrates spatiotemporal priors from video generation models to achieve consistent future prediction and planning across diverse datasets.*

## The Challenge of Generalization and Consistency

The primary bottleneck for modern autonomous driving is the "domain gap." A model trained on the sunny streets of California may fail when deployed in a rainy European city or when its camera resolution changes. Traditional models are often benchmark-specific; they memorize the patterns of a particular dataset (like NAVSIM or nuScenes) but fail to transfer that knowledge to others.

Furthermore, existing "world models"—systems that try to predict the future to improve planning—often separate video prediction from action planning. They might use a video generator to imagine the future and a separate planning head to decide where to go. This decoupling frequently results in inconsistencies: the video might show the car turning right while the planner suggests going straight, or vice-versa. DriveVA seeks to solve this by unifying these two tasks into a single generative process where video frames and action coordinates are treated as part of the same data sequence.

## Unified Video-Action Architecture

At its core, DriveVA is built upon a large-scale pre-trained video generation model (Wan2.2-TI2V-5B). The architecture is designed to handle multiple streams of information—visual history, language instructions, and the current vehicle state—to predict both a future video and a future trajectory.

![DriveVA Architecture: Unified Diffusion Transformer and Progressive Continuation](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04198v1/x2.png)
*Figure 2: The model uses a shared latent space where future video tokens and action tokens interact through a Unified Diffusion Transformer.*

The process begins with **Conditional Signal Embedding**:
1.  **History Observations ($O_h$):** A buffer of $m$ past frames is encoded into a latent space using a 3D-causal Variational Autoencoder (VAE).
2.  **Language Instructions ($L$):** Optional text prompts (e.g., "Turn right at the intersection") are encoded into tokens.
3.  **Ego State ($s_0$):** The current velocity and orientation of the vehicle are embedded as state tokens.

The unique contribution of DriveVA is its **Unified Diffusion Transformer (DiT)**. Unlike standard models that predict actions and pixels separately, DriveVA places future video latents and action tokens into a shared sequence. During the denoising process of the diffusion model, the video tokens and action tokens can "talk" to each other through self-attention. This bidirectional interaction forces the model to ensure that the predicted trajectory ($A$) and the predicted future video ($F$) are mutually conditioning each other.

The goal is to model the joint distribution $P(F, A | O_h, L, s_0)$, where $F$ is a sequence of $N$ future frames and $A$ is a chunk of $K$ future actions (3D vectors containing coordinates and yaw angles).

## Methodology: Flow Matching for Planning

DriveVA utilizes a generative technique called **Flow Matching**. In this framework, the model learns to map a simple distribution of noise to the complex distribution of realistic driving videos and trajectories. The training objective, $\mathcal{L}_{FM}$, is defined as:

$$\mathcal{L}_{FM} = \mathbb{E}_{t, x_0, \epsilon} [ \| v_\theta(x_t, t | c) - u_t(x_t) \|^2 ]$$

In this equation:
- $v_\theta$ represents the velocity field predicted by the network.
- $x_t = (1 - t)x_0 + tx_1$ is a linear interpolation between noise ($x_0$) and the target clean data ($x_1$).
- $t \in [0, 1]$ is the time step of the diffusion process.
- $u_t(x_t) = x_1 - x_0$ is the target velocity the model aims to regress.
- $c = \{O_h, L, s_0\}$ represents the condition set including history, language, and state.

By training on this objective with high-resolution video ($832 \times 480$), the model learns the physics of the world—how objects move, how light changes, and how the ego-vehicle's movement affects the visual scene. During inference, DriveVA can generate a coherent future and an accompanying plan in as few as 2 sampling steps, making it efficient enough for real-time consideration.

## Zero-Shot Generalization Results

The most significant finding of this work is DriveVA's performance on datasets it was never trained on. Typically, a model trained on the NAVSIM benchmark would see its performance drop significantly when tested on nuScenes or the CARLA simulator (Bench2Drive).

DriveVA, however, demonstrated a high level of "zero-shot" transfer:
- **nuScenes:** Without any fine-tuning, DriveVA reduced the average collision rate by 83.3% compared to PWM, a leading world-model planner. Its average position error (L2) was reduced by 78.9%.
- **Bench2Drive (Real-to-Sim):** Moving from real-world data to a simulation environment is notoriously difficult. DriveVA reduced position errors by 52.5% compared to PWM and outperformed DriveVLA-W0, showing that its learned priors are robust to changes in graphics and physics.

This zero-shot capability suggests that DriveVA is not just memorizing maps; it is learning the "language of motion" and the physical constraints of driving that apply regardless of the specific camera or location.

![Zero-Shot Performance on nuScenes and CARLA](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04198v1/x3.png)
*Figure 3: DriveVA exhibits superior generalization across real-world and simulated domains compared to existing world models.*

## Ensuring Video-Trajectory Consistency

A common failure mode for world-model planners is the "hallucination" of a future that does not match the planned action. DriveVA's joint modeling ensures high consistency. To prove this, the researchers used an independent Visual Odometry system (DPVO) to calculate the vehicle's movement *based solely on the video DriveVA generated*. 

They found that the trajectory calculated from the pixels matched the model's predicted mathematical coordinates with an average error of only 0.15 meters. This confirms that when DriveVA predicts a right turn, the "imagined" video actually depicts a right turn with the correct perspective shift, and the "planned" trajectory follows that exact curve.

![Consistency Visualization across Lane-Changes and Turns](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04198v1/x4.png)
*Figure 4: Qualitative results showing that predicted trajectories (blue) align closely with ground truth (red) and visual predictions (yellow/cyan).*

## Limitations and Failure Cases

Despite its strong performance, DriveVA is not perfect. The researchers identified failure cases where the model's visual causal reasoning failed. For instance, in some scenarios involving cyclists or complex intersections, the model might predict an unnecessary stop. 

Interestingly, even in these failure cases, the **consistency** remained: if the model incorrectly predicted that the car should stop in the video, its planned trajectory also stopped. This indicates that the unified architecture is working as intended—the "brain" (planner) and the "eyes" (video generator) are always in agreement, even if the model's overall interpretation of the scene is flawed.

![Failure Case Analysis: Consistency persists even when the prediction is incorrect](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04198v1/x9.png)
*Figure 5: In cases of incorrect stop predictions, the predicted trajectory still aligns with the generated video, highlighting the model's internal consistency.*

## Significance for the Future of Autonomous Driving

DriveVA represents a shift toward more generalizable autonomous agents. By treating driving as a spatiotemporal generation task rather than a simple regression or classification task, the model captures the rich dynamics of the real world. 

The key takeaways from this research are:
1.  **Unified Modeling is Vital:** Jointly predicting video and actions in a shared latent space is far more effective than training them separately or using one as a secondary task.
2.  **Video Priors are Powerful:** Large-scale video generation models contain "common sense" about physics and motion that can be directly harnessed for driving.
3.  **Generalization is Possible:** Zero-shot transfer across datasets is achievable when a model focuses on the fundamental consistency between vision and action.

DriveVA provides a scalable path forward for autonomous systems that can operate safely in the "long tail" of rare and unseen real-world scenarios, moving us closer to truly universal autonomous drivers.

## Relevant Citations

- Wan: Open and advanced large-scale video generative models: This paper is fundamentally important as it provides the pre-trained video generation backbone (Wan2.2-TI2V-5B) upon which DriveVA is built. DriveVA leverages the rich spatiotemporal priors from this model to enable its strong generalization capabilities, making this citation a cornerstone of the proposed method.
- From forecasting to planning: Policy world model for collaborative state-action prediction: This citation, referred to as PWM, represents a key state-of-the-art competitor that DriveVA is directly and repeatedly compared against, particularly for zero-shot generalization. The paper uses PWM as the primary baseline to demonstrate DriveVA's superior performance and improved video-trajectory consistency, highlighting it as the benchmark to beat.
- Scalable diffusion models with transformers: This paper introduces the Diffusion Transformer (DiT) architecture, which is the core component of DriveVA's novel decoder. DriveVA's central contribution of jointly generating video and action tokens in a shared latent space is implemented using a DiT, making this citation crucial for understanding the paper's methodology.
- Drivevla-w0: World models amplify data scaling law in autonomous driving: This work is cited as a major contemporary world model-based method and is used as a baseline for comparison in both closed-loop performance on NAVSIM and zero-shot transfer to Bench2Drive. It represents a highly relevant approach that also integrates world models, making it an important benchmark for contextualizing DriveVA's performance and contributions.
