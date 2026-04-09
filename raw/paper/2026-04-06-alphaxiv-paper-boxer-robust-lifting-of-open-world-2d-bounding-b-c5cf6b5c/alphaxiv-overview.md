# Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D

- alphaXiv: https://www.alphaxiv.org/abs/2604.05212
- Source paper: https://arxiv.org/abs/2604.05212

Detecting and localizing objects in three-dimensional (3D) space is a cornerstone of modern computer vision, powering applications from autonomous robots to augmented reality (AR) headsets. While 2D object detection has reached high levels of maturity—allowing models to recognize thousands of categories from "open-world" prompts—3D object localization remains a difficult frontier. The primary bottleneck is data: while 2D images are abundant on the internet, metric 3D data requires specialized sensors like LiDAR or depth cameras and complex calibration, making it expensive to collect and label.

**Boxer** is a research framework designed to bridge this gap. It introduces a robust method for "lifting" 2D bounding boxes into 3D world space. By decoupling the semantic recognition of an object (the 2D part) from its geometric localization (the 3D part), Boxer leverages powerful off-the-shelf 2D detectors to handle the "open-world" variety of objects while using a specialized network, **BoxerNet**, to estimate their 3D physical size and position.

![Boxer Algorithm Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05212v1/boxernetv12.jpg)
*Figure 1: The Boxer pipeline takes posed images and text prompts as input, uses a 2D detector to find objects, and then "lifts" those detections into metric 3D space using BoxerNet before fusing them across multiple views.*

## The Architecture of 3D Lifting

The Boxer algorithm operates in three distinct stages: open-world 2D detection, 2D-to-3D lifting via BoxerNet, and multi-view temporal fusion. This modular approach is designed to be "universal," meaning it can work with different camera types (like fisheye or pinhole) and various types of depth cues (dense depth maps or sparse point clouds).

### 1. Open-World 2D Detection
The process begins with a standard 2D detector such as OWLv2 or DETIC. A user provides text prompts (e.g., "chair," "guitar," "coffee table"), and the detector outputs 2D bounding boxes in the image plane along with a confidence score $c_{2d} \in [0, 1]$. Because these 2D models are trained on massive internet-scale datasets, they can find objects that a traditional 3D-only model might have never seen.

### 2. BoxerNet: The Lifting Engine
BoxerNet is the heart of the system. It is a transformer-based network that takes a 2D box and the surrounding image context and predicts a 7-Degrees of Freedom (7-DoF) 3D bounding box. This 3D box is defined by its center $(x, y, z)$, its physical extent $(w, h, d)$, and its rotation $\theta$ (yaw) around the gravity axis. 

Unlike previous models that required specific types of depth input, BoxerNet uses a flexible **Median Depth Patch Encoding**. The image is divided into patches, and for each patch, the model calculates the median depth value from whatever geometric data is available (like a sparse point cloud). This allows the model to "fill in the gaps" when depth data is noisy or sparse.

![BoxerNet Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05212v1/boxerv12.jpg)
*Figure 2: BoxerNet integrates visual features from a DINOv3 backbone with ray features and depth information. It uses cross-attention to condition the 3D output on the initial 2D bounding box proposals.*

### 3. Multi-View Temporal Fusion
A single 2D detection from one frame might be slightly inaccurate. To solve this, Boxer aggregates predictions across time and different camera views. It clusters detections that represent the same physical object and averages their position, size, and orientation. This step ensures that if a user walks around a room with an AR headset, the "3D chair" they see remains stable in the same spot, rather than flickering or drifting.

## Handling Ambiguity with Aleatoric Uncertainty

Lifting a 2D box to 3D is inherently ambiguous. For example, a small object close to the camera can look exactly like a large object far away. To handle this, BoxerNet predicts **aleatoric uncertainty**—a measure of how "unsure" the model is about its geometric prediction due to observational noise.

The model outputs a 3D confidence score $c_{3d} \in [0, 1] \text{ where } c_{3d} = \exp(-\sigma_{box})$ and $\sigma_{box} \in \mathbb{R}$ is the predicted uncertainty. This is combined with the 2D detector's confidence to create a final, robust ranking score:

$$\bar{c} = \frac{c_{2d} + c_{3d}}{2}$$

This score is crucial during inference. If the 2D detector is sure it found a "mug" but BoxerNet is unsure about its 3D location (perhaps due to motion blur or low light), the final confidence will be lower, preventing the system from placing "hallucinated" objects in the 3D map.

The training loss function $L$ also incorporates this uncertainty, allowing the model to "down-weight" examples it finds geometrically confusing:

$$L = L_{box} \exp(-\sigma_{box}) + \sigma_{box}$$

Where $L_{box}$ is the geometric error (Chamfer loss) between the predicted and ground-truth 3D box corners.

## Innovation in Feature Encoding

A key technical contribution of Boxer is how it represents the camera's geometry to the transformer. It uses **Ray Features**, which encode the 3D direction of the light rays hitting every patch of the image. This is calculated using the camera's calibration and its pose relative to gravity. By feeding these rays directly into the transformer as tokens, the model learns to understand the perspective of different camera lenses—including distorted fisheye lenses—without needing specialized mathematical adjustments for each camera type.

Combined with a pretrained **DINOv3** backbone for visual features, BoxerNet achieves a deep understanding of both "what" an object is and "where" it should sit in a 3D scene.

## Experimental Performance

The researchers tested Boxer on several diverse datasets, including egocentric video from Project Aria and public datasets like CA-1M and ADT. A frequent baseline for comparison was **CuTR**, a prior DETR-style 3D detector. 

Results showed that BoxerNet consistently outperformed existing methods. For instance, on the NymeriaPlus dataset—which features egocentric video with very sparse point clouds—Boxer achieved a mean Average Precision (mAP) of 0.296, while the CuTR baseline only reached 0.010. This massive performance gap highlights Boxer's superior ability to handle real-world, noisy data.

![3D Detection Results on SUN-RGBD](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05212v1/sunrgbd_boxermood2drgb.jpg)
*Figure 3: Qualitative results showing Boxer's ability to accurately lift 2D detections into 3D boxes that align well with the actual room geometry (shown here on the SUN-RGBD dataset).*

Boxer also proved particularly effective at localizing **small objects**, which are notoriously difficult for 3D sensors. Because it relies on high-resolution 2D detections to start the process, it can "pinpoint" small items like light switches or remote controls that traditional 3D-only detectors might miss.

## Impact and Applications

The significance of Boxer lies in its **universal interface** for 3D perception. By allowing any 2D detector to be transformed into a 3D detector, it democratizes 3D perception for developers who don't have access to massive 3D datasets.

Some of the potential applications include:
*   **Contextual AI:** Helping AI assistants understand exactly where objects are in a room (e.g., "The keys are on the table to your left").
*   **Robotic Embodiment:** Providing robots with the metric coordinates needed to grasp or avoid objects in unknown environments.
*   **Digital Twins:** Rapidly creating 3D maps of real-world spaces by simply walking through them with a camera.

By effectively combining 2D semantics with 3D metric geometry, Boxer provides a scalable and robust path toward machines that can "see" and "reason" about the 3D world as naturally as humans do.

## Relevant Citations

- Cubify anything: Scaling indoor 3d object detection: This work, which introduces the CuTR model and the CA-1M dataset, is the most critical citation. The Boxer paper explicitly states its model is an extension of the CuTR architecture and uses it as the primary baseline for performance comparison throughout the experiments.
- Omni3D: A large benchmark and model for 3D object detection in the wild: This paper introduces the Omni3D benchmark, a key dataset used to evaluate Boxer's performance. It also proposes Cube-RCNN, which is used as a baseline method for comparison in the experimental section, making this reference crucial for both evaluation and context.
- Scaling open-vocabulary object detection: This citation is for OWLv2, an open-vocabulary 2D object detector. It is fundamentally important because Boxer's pipeline is built upon using such off-the-shelf 2D detectors as its first stage. The experiments extensively use OWLv2 to generate the initial 2D boxes that Boxer then lifts to 3D.
- 3d-mood: Lifting 2d to 3d for monocular open-set object detection: This paper presents a similar and competing approach for lifting 2D detections to 3D. It is used as a key state-of-the-art baseline in the experimental results (Table 2) to demonstrate the performance improvements offered by the Boxer model.
- Detecting twenty-thousand classes using image-level supervision: This paper introduces DETIC, one of the primary off-the-shelf 2D object detectors explicitly mentioned in the abstract and used in the Boxer pipeline. This citation is significant as it represents the foundational 2D detection stage that Boxer decouples from and builds upon to achieve open-world 3D lifting.
