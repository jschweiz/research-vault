# OmniCamera: A Unified Framework for Multi-task Video Generation with Arbitrary Camera Control

- alphaXiv: https://www.alphaxiv.org/abs/2604.06010
- Source paper: https://arxiv.org/abs/2604.06010

## Introduction to OmniCamera

The evolution of video generation has transitioned from simple text-to-video synthesis to highly controlled cinematic creation. While modern models can generate high-fidelity visuals from text or images, they often struggle to separate the movement of the camera from the motion of the subjects within the scene. In natural video, dynamic scene content and continuous camera motion are intrinsically linked, yet for professional content creation, the ability to control these two elements independently is essential.

OmniCamera is a unified framework designed to address this challenge by explicitly disentangling video generation into two independent control dimensions: scene content and camera pose. Unlike prior models that typically support only a single type of camera control (such as just text or just 3D trajectories), OmniCamera allows for arbitrary combinations of content sources (text, image, or video) and camera conditions (textual descriptions, 3D trajectory matrices, or motion reference videos). This unified approach enables nine distinct generation tasks within a single model architecture, providing a level of creative flexibility previously unavailable in specialized, task-specific models.

![OmniCamera Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06010v1/x1.png)
*Figure 1: The OmniCamera framework supports nine distinct combinations of content and camera conditions, allowing for flexible multi-task video generation with a single set of model weights.*

## Decoupling Scene Content and Camera Motion

The core philosophy of OmniCamera is "conceptual decoupling." In many existing Diffusion Transformer (DiT) architectures, camera motion is often treated as part of the overall scene dynamics. This entanglement leads to "modality conflict," where a model might confuse a command for a camera "pan right" with an instruction for an object in the scene to move to the right.

To achieve true decoupling, the framework treats the target video generation as a function of separate content and camera latents. Specifically, the model aims to predict a target video $z_0$ by conditioning on a content source (which could be a prompt $T$ or an image/video $z_c$) and a camera motion hint (which could be a trajectory $M$, a motion reference video $z_m$, or a text description). By defining these as independent inputs, the framework allows a user to, for example, take the visual content of a still image and apply the exact 3D camera trajectory extracted from a different, unrelated action movie.

## The OmniCAM Hybrid Dataset

A significant barrier to training precise camera-control models is the scarcity of high-quality, real-world data with accurate camera annotations. Real-world videos often lack precise 3D metadata, while synthetic data, though perfectly annotated, can suffer from a "domain gap" that makes generated videos look artificial or "video-game-like."

The authors address this by constructing OmniCAM, a hybrid dataset that combines the precision of synthetic environments with the visual richness of real-world footage.

### Synthetic Data Generation
Using Unreal Engine 5 (UE5), the researchers defined approximately 50 distinct camera motion patterns, ranging from basic moves like "Dolly In" to complex polyline trajectories. They synthesized 500,000 video clips, creating specialized data structures:
- **Same-Scene, Diverse-Trajectory:** Multiple cameras moving through the same static scene to teach the model how different paths affect the same visual content.
- **Same-Trajectory, Diverse-Scene:** The same camera path applied to various environments to help the model generalize motion across different subjects.
- **Motion-Content-Target Triplets:** Sets denoted as $\{z_m, z_d, z_0\}$, where the target $z_0$ shares its camera motion with $z_m$ and its visual content with $z_d$.

### Real-World Data Processing
To maintain photorealism, the team curated 600,000 raw internet videos. They developed a rigorous four-step pipeline to extract usable camera information:
1. **Trajectory Estimation:** Using advanced tools like MegaSaM to extract 3D paths.
2. **Trajectory Filtering:** Removing unstable or "jumpy" motions based on smoothness thresholds $r_{jump}$ and $r_{complex}$.
3. **Trajectory Classification:** Mapping these real paths to the 50 predefined motion categories.
4. **Intra-class Matching:** Finding pairs of real videos that happen to share similar camera movements, effectively creating real-world versions of the "same-trajectory, diverse-scene" data.

![OmniCAM Dataset Construction](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06010v1/x4.png)
*Figure 2: The construction process of the OmniCAM dataset, featuring both synthetic triplets from UE5 and curated, annotated real-world video pairs.*

## Architecture: 3D Condition RoPE and Decoupled Injection

OmniCamera is built upon a 5-billion parameter Diffusion Transformer. To handle the diverse and sometimes conflicting input modalities, the researchers introduced two primary architectural innovations: Decoupled Condition Injection and 3D Condition RoPE.

### Decoupled Condition Injection
When providing multiple conditions (like an image for content and a video for motion), a naive approach would be to simply stack them. However, this often leads to optimization instability. OmniCamera unifies textual prompts and visual conditions as sequence-level representations that interact with the noise latent $z_t$ through joint attention. For precise geometric inputs like 3D trajectory matrices, the model uses a specialized Multi-Layer Perceptron (MLP) to process the coordinates before they are integrated into the DiT blocks.

### 3D Condition RoPE (Rotary Positional Embeddings)
A major challenge in multi-modal generation is "spatial-temporal ambiguity." If the model receives both a content video and a camera-motion video, how does it know which frame of the content video corresponds to which frame of the motion video? 

The 3D Condition RoPE solves this by assigning distinct spatial-temporal base offsets to each modality. This explicitly separates the coordinate structures of the noise latent, the content latent, and the camera-motion latent. By shifting the positional codes for each input, the model can effectively "read" multiple control signals simultaneously without them interfering with each other's spatial-temporal structure.

![OmniCamera Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06010v1/x3.png)
*Figure 3: The model architecture showing how different conditions are tokenized and processed through 3D Condition RoPE before entering the Unified Diffusion Transformer.*

## Dual-Level Curriculum Training Strategy

Training a single model to handle nine different tasks is notoriously difficult. If all tasks are introduced at once, the model may fail to converge or may prioritize one modality (like text) while ignoring others (like trajectories). OmniCamera employs a "Dual-Level Curriculum" to manage this complexity.

### Condition-Level Curriculum
The model is trained in three stages of increasing difficulty:
1. **Stage I (Text-conditioning):** Focuses on basic semantic guidance (e.g., "camera zooms in"). This aligns the model with the general concepts of motion.
2. **Stage II (Reference-video Control):** Introduces "in-context learning," where the model learns to transfer motion from a reference video. This is more difficult as it requires global motion understanding.
3. **Stage III (Camera Trajectory Control):** Introduces precise 3D coordinates. This is the finest level of granularity and requires the model to have a deep geometric understanding of the scene.

### Data-Level Curriculum
Within Stages II and III, the model follows a two-substage data path:
- **Substage 1:** Heavy training on synthetic UE5 data to establish precise camera motion accuracy.
- **Substage 2:** Brief fine-tuning on high-quality real-world videos to restore photorealism and ensure the model doesn't lose its ability to generate realistic textures and lighting.

![Curriculum Training Strategy](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06010v1/x5.png)
*Figure 4: The three-stage training process that progressively introduces more complex camera control modalities and transitions from synthetic to real-world data.*

## Multi-Task Performance and Control Modalities

OmniCamera demonstrates strong performance across text, reference video, and trajectory controls. Quantitative evaluations using Motion Accuracy (MotionAcc) and geometric error metrics like $\text{TransErr}$ (translation error) and $\text{RotErr}$ (rotation error) show that OmniCamera often outperforms specialized models.

### Text and Reference Control
In text-to-video tasks, OmniCamera achieved a MotionAcc of 92.4%, a significant increase over baseline models. When using a reference video for motion, it successfully preserves the content of the source while mirroring the camera movement of the reference, avoiding the visual distortions (such as "melting" objects or background artifacts) often seen in competing methods.

### 3D Trajectory Control
The model allows for extremely precise control using polylines or complex 3D paths. For instance, in trajectory-controlled T2V, it recorded a $\text{TransErr}$ of 2.064, compared to much higher errors in previous state-of-the-art models. This precision is particularly evident when the camera follows non-linear paths, such as "triangular" or "circular" orbits.

### Modality Dominance
A unique finding of the research is the "dominance hierarchy" when multiple conditions are provided. If a user provides a text prompt saying "zoom in" but a 3D trajectory that "pans left," the model must choose which to follow. The study found a consistent hierarchy:
$$ \text{Trajectory} > \text{Reference Video} > \text{Text} $$
This suggests that the model correctly prioritizes explicit geometric information over coarser semantic descriptions.

![Qualitative Results Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06010v1/x10.png)
*Figure 5: A comparison of OmniCamera against other leading methods across text, trajectory, and reference video controls. OmniCamera shows higher structural stability and motion accuracy.*

## Significance and Future Applications

OmniCamera is the first framework to successfully unify nine distinct video generation tasks involving arbitrary combinations of content and camera control into a single, parameter-efficient model. By decoupling motion from content and introducing a robust training curriculum, it bridges the gap between high-level creative intent and low-level geometric precision.

The practical implications of this work are significant for industries like film pre-visualization, where directors can prototype complex shots using simple reference videos or hand-drawn trajectories. It also opens new doors for "video editing" by allowing users to change the camera angle of an existing video clip while keeping the action and characters intact. While future work may explore even more granular controls—such as localized subject motion alongside camera paths—OmniCamera provides a foundational step toward truly professional-grade, controllable video synthesis.

## Relevant Citations

- Wan: Open and advanced large-scale video generative models: This paper provides the foundational architecture for OmniCamera. The authors explicitly state they build upon the 5B-parameter Wan2.2-TI2V architecture from this work, making it essential for understanding the base model upon which OmniCamera's novel control mechanisms are implemented.
- Recammaster: Camera-controlled generative rendering from a single video: ReCamMaster is a key state-of-the-art competitor for one of OmniCamera's primary functionalities: trajectory-controlled video-to-video generation. OmniCamera is directly compared against it in quantitative tables and qualitative figures to demonstrate superior performance, highlighting its relevance as a benchmark for precise geometric control.
- Camclonemaster: Enabling reference-based camera control for video generation: This paper is a direct competitor for another core feature of OmniCamera: reference-video-controlled generation. OmniCamera's authors cite and compare their results to CamCloneMaster to showcase improvements in motion accuracy and artifact reduction, establishing its importance in the context of reference-based control.
- Cameractrl: Enabling camera control for text-to-video generation: This is a significant prior work that introduced an adapter-based method for injecting trajectory-based camera motion into text-to-video models. It represents an important foundational step towards the explicit camera control that OmniCamera seeks to unify and expand across multiple modalities and tasks.
