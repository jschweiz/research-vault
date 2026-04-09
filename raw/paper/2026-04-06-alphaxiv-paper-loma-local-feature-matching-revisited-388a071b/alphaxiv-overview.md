# LoMa: Local Feature Matching Revisited

- alphaXiv: https://www.alphaxiv.org/abs/2604.04931
- Source paper: https://arxiv.org/abs/2604.04931

## Scaling Local Feature Matching for the Modern Era

Local feature matching is a cornerstone of computer vision, essential for tasks that involve relating two or more images of the same scene. For decades, this process has followed a standard pipeline: detecting interest points (keypoints), describing the local area around those points with a vector (descriptors), and then finding pairs of descriptors that look similar across images (matching). These correspondences are the foundation for building 3D models from photos (Structure-from-Motion) and determining the position of a camera in a known environment (visual localization).

In recent years, the field has seen a significant shift toward "detector-free" methods. These approaches skip the explicit keypoint detection step, instead performing dense matching across the entire image. This shift was largely driven by the observation that traditional detector-based methods seemed to struggle with extreme viewpoint changes, lighting variations, and repetitive patterns. Simultaneously, feed-forward reconstruction models have emerged, promising to infer 3D geometry directly without the need for traditional matching pipelines.

![LoMa Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04931v1/x2.png)
*Figure 1: An overview of the LoMa pipeline compared to prior work. By scaling both data diversity and model capacity, LoMa re-establishes the competitiveness of detector-based local feature matching.*

The research presented in "LoMa: Local Feature Matching Revisited" challenges the assumption that detector-based matching has reached its fundamental limits. The authors argue that the performance gap between detector-based and detector-free methods is not due to architectural flaws but rather a disparity in training scale. While detector-free models have benefited from massive, diverse datasets and high-capacity neural networks, local feature matchers have largely remained confined to smaller, more specialized datasets. LoMa seeks to bridge this gap by applying modern data-driven practices—including large-scale data mixtures and increased model capacity—to the traditional local feature matching paradigm.

## The LoMa Pipeline: Components and Architecture

The LoMa system follows a three-stage approach: detection, description, and matching. Rather than proposing entirely new architectures for these stages, the authors select high-performing existing modules and focus on how to train them more effectively at scale.

For the detection stage, the model utilizes the DaD detector. This component identifies points in an image that are likely to be found in other views of the same scene. These points serve as the anchors for the subsequent stages.

The description stage uses the DeDoDe architecture. A descriptor network, denoted as $g_{\theta}$, processes the image and the detected keypoints to produce high-dimensional vectors. These vectors are designed to be "discriminative," meaning they should be unique to the specific visual patch they represent, and "invariant," meaning they should look similar even if the camera moves or the lighting changes.

The final stage is the matching, which uses the LightGlue architecture. The matcher, denoted as $h_{\phi}$, takes the descriptors from two images, $I^A$ and $I^B$, and refines them using a series of transformer blocks. These blocks use self-attention to look at other points within the same image and cross-attention to look at points in the other image. This iterative process allows the model to understand the spatial context of each point, making the final matching decision much more robust.

The LoMa family includes several variants to accommodate different computational budgets:
- **LoMa-B (Base):** Uses an embedding dimension $d_{\text{emb}}$ of 256.
- **LoMa-L (Large):** Increases $d_{\text{emb}}$ to 512.
- **LoMa-G (Gigantic):** Uses a $d_{\text{emb}}$ of 1024.

All variants typically use 9 transformer layers, though the architecture supports early stopping at any layer $L$ to trade accuracy for speed. For example, using $L=3$ can significantly speed up inference while maintaining high performance.

## Large-Scale Data Mixture and Modern Training

The most significant contribution of LoMa is the scale and diversity of its training data. While previous models were often trained on a single dataset like MegaDepth, LoMa uses a mixture of 17 different 3D datasets. This collection includes indoor scenes (ScanNet++), outdoor landmarks (MegaDepth, MegaScenes), aerial imagery (AerialMD), and synthetic environments (TartanAir, Aria).

Curating this data required more than just gathering files. The researchers re-processed several datasets to generate higher-quality "ground truth" correspondences. For instance, in the SpatialVID dataset, they used advanced matching and reconstruction techniques to create more accurate depth and pose information than was originally available.

The training process itself was also modernized. The models were trained using a global batch size of 64 on $560 \times 560$ resolution images. The optimization used a learning rate of $2 \times 10^{-4}$ with a weight decay of $5 \times 10^{-5}$ and an exponential moving average (EMA) factor of $0.999$. By exposing the model to such a wide variety of environments and camera motions during training, LoMa learns to be far more generalizable than its predecessors.

## Addressing Benchmark Saturation with HardMatch

As feature matching models have improved, established benchmarks like MegaDepth have become "saturated." Most modern matchers can solve these datasets with nearly 100% accuracy, making it impossible to distinguish which methods are truly better or where they still fail.

To solve this, the authors introduced **HardMatch**, a new dataset consisting of 1000 manually annotated image pairs. These pairs were specifically selected to be difficult for current state-of-the-art models. The images were scraped from Wikimedia Commons and categorized into nine challenging groups:

![HardMatch Categories](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04931v1/x4.png)
*Figure 2: Examples from the HardMatch dataset, showcasing the diversity of challenges including extreme viewpoint changes, temporal gaps, and different artistic styles.*

1.  **Viewpoint Change:** Significant shifts in the camera's position or angle.
2.  **Temporal Gap:** Images of the same place taken years or even decades apart.
3.  **Illumination:** Day-to-night transitions or harsh shadows.
4.  **Nature:** Scenes dominated by trees, rocks, and water, which lack clear geometric structure.
5.  **Aerial:** High-altitude views from planes or satellites.
6.  **Celestial:** Night skies and star constellations.
7.  **Seasonal Change:** The same scene in winter (snow) versus summer.
8.  **Doppelgänger:** Pairs of different buildings or objects that look nearly identical.
9.  **Hand Drawing:** Matching a real-world photo to a sketch or painting.

By providing manual annotations (8 to 28 ground truth points per pair), HardMatch allows for a precise evaluation of matching accuracy even in cases where automated 3D reconstruction fails.

## Experimental Findings and Performance

The results of the LoMa models across various tasks demonstrate the effectiveness of the data-driven approach. 

### HardMatch and WxBS
On the new HardMatch benchmark, LoMa-G achieved a score of 54.3 mAA@10px. To put this in perspective, it outperformed the popular ALIKED+LightGlue combination by over 18 points. It even surpassed leading dense matchers like RoMa v2. On the Wide Baseline Stereo (WxBS) benchmark, LoMa-G reached 73.4 mAA, setting a new record.

### Visual Localization
Visual localization is the task of finding exactly where a camera is within a pre-mapped area. LoMa showed dramatic improvements in this area:
- **InLoc:** For indoor localization, LoMa-G achieved 73.3% accuracy at a strict threshold of $0.25\text{m}$ and $2^{\circ}$, a gain of more than 20 points over previous sparse matchers.
- **Oxford Day-and-Night:** In a benchmark designed to test day-to-night matching, LoMa-G improved night query accuracy by 14 points at the narrowest threshold.

### Structure-from-Motion
The models were also tested on the Image Matching Challenge 2022 and MegaDepth relative pose tasks. LoMa-G set a new state-of-the-art on the IMC 2022 benchmark with 89.3 mAA. On the RUBIK dataset, which tests matching across very wide viewpoints, LoMa-G outperformed others by 24 points at both $10^{\circ}$ and $20^{\circ}$ thresholds.

![Scaling Analysis](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04931v1/x25.png)
*Figure 3: An analysis of how model performance improves as we increase the embedding dimension (model capacity) and the amount of training data. The loss decreases consistently as we scale up.*

## Speed vs. Accuracy Trade-offs

One of the practical advantages of detector-based methods like LoMa is their efficiency. Because they only process a sparse set of keypoints (usually 2048 or 4096) rather than every pixel in the image, they are often much faster than dense methods. 

The LoMa models maintain this advantage. The LoMa-B variant can process hundreds of image pairs per second on a modern GPU. Because the training objective is applied to every layer of the transformer, users can choose to stop the matcher after only 3 or 6 layers instead of the full 9. This allows for a flexible trade-off: using more layers for maximum accuracy on difficult pairs, or fewer layers for high-speed processing on easier pairs.

## Significance and Future Directions

The LoMa project serves as a "revisitation" of a classic paradigm. It demonstrates that the traditional pipeline of detection, description, and matching is far from obsolete. By applying the same "scaling laws" that have revolutionized other areas of AI—more data, bigger models, and better training recipes—the authors have shown that sparse matching can meet or exceed the performance of much more complex dense systems.

The introduction of HardMatch also provides the community with a vital tool for measuring future progress. It shifts the focus from "solved" benchmarks toward the extreme edge cases that still pose a challenge for computer vision. By making the code, models, and dataset publicly available, the researchers have provided a new high-performance baseline for 3D vision tasks.

Ultimately, LoMa suggests that the future of 3D reconstruction and localization may not lie in abandoning keypoint detectors, but in teaching them to handle the vast complexity of the real world through massive, diverse data. Establishing correspondences is established if the following dual-softmax condition is met:

$$P_{ij} = \max_k P_{ik} = \max_l P_{lj} \text{ and } P_{ij} > \mu$$

where $\mu = 0.1$ is the confidence threshold. This simple logic, backed by powerful data-driven features, remains a highly effective way to link images across time, space, and style.

## Relevant Citations

- LightGlue: Local Feature Matching at Light Speed: LoMa's matcher component is directly based on the LightGlue architecture. The paper's improvements are demonstrated by applying a novel large-scale training strategy to this foundational model, making it a critical architectural reference.
- DeDoDe: Detect, Don’t Describe – Describe, Don’t Detect for Local Feature Matching: LoMa utilizes the DeDoDe architecture for its feature descriptor. The paper highlights that its novel data-driven training approach significantly enhances the performance of this existing descriptor, forming a core part of the LoMa pipeline.
- Aliked: A lighter keypoint and descriptor extraction network via deformable transformation: The combination of ALIKED and LightGlue is consistently used throughout the paper as the primary state-of-the-art sparse matching baseline. LoMa's superior performance is established by directly outperforming this method, making it the key competitor to surpass.
- LoFTR: Detector-free local feature matching with transformers: This paper introduced the popular detector-free matching paradigm, which the LoMa paper explicitly challenges. LoMa's central argument is to revive and advance traditional detector-based methods, positioning its work as a direct counterpoint to the trend initiated by LoFTR.
- WxBS: Wide baseline stereo generalizations: The creation of the new HardMatch benchmark is a major contribution of the LoMa paper. The authors explicitly cite WxBS as the inspiration for their benchmark's design, which focuses on challenging, manually annotated image pairs, but notes that LoMa's dataset is significantly larger and more difficult.
