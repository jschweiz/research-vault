# HiPolicy: Hierarchical Multi-Frequency Action Chunking for Policy Learning

- alphaXiv: https://www.alphaxiv.org/abs/2604.06067
- Source paper: https://arxiv.org/abs/2604.06067

## The Challenge of Temporal Resolution in Robotic Imitation Learning

Robotic imitation learning (IL) has emerged as a powerful paradigm for teaching robots complex manipulation skills. By learning from human demonstrations, robots can acquire behaviors that are difficult to program explicitly, such as folding laundry, preparing food, or handling delicate electronics. Modern generative policies, particularly those based on diffusion models like Diffusion Policy or Action Chunking Transformer (ACT), have pushed the boundaries of what robots can achieve by modeling continuous action distributions with high fidelity.

![HiPolicy Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06067v1/x1.png)
*Figure 1: HiPolicy introduces a hierarchical multi-frequency action chunking framework that jointly models visionary long-horizon goals and precise short-term adjustments.*

A central concept in these methods is "action chunking," where the policy predicts a sequence of future actions (a "chunk") rather than just the immediate next step. This improves temporal coherence and helps the robot avoid jittery behavior. However, action chunking introduces a fundamental trade-off governed by the relationship between the action frequency and the chunk size. If a policy operates at a high frequency, it can perform fine-grained adjustments and reactive control, but its temporal "view" is limited, making it difficult to capture long-horizon dependencies. Conversely, a low-frequency policy can look further into the future to plan complex multi-stage tasks but lacks the precision required for delicate maneuvers.

Humans do not face this limitation in the same way. Biological motor control naturally integrates multiple frequencies: we perform low-frequency, long-duration motions for overarching goals (e.g., reaching for a cup) while simultaneously executing high-frequency, short-duration motions for precise adjustments (e.g., stabilizing the fingers during contact). The research paper "HiPolicy: Hierarchical Multi-Frequency Action Chunking for Policy Learning" proposes a robotic policy architecture that mimics this hierarchical structure.

## Addressing the Fixed-Frequency Trade-off

The core problem HiPolicy addresses is that standard action chunking methods are constrained to a single, fixed frequency. In traditional formulations, a policy $\pi$ maps an observation history $O^f_{t,L_h}$ to an action chunk $A^f_{t,L_c}$ at a single frequency $f$. This frequency dictates both how the robot "sees" the past and how it "plans" the future.

When $f$ is low, the time interval between actions is large. This allows the action chunk to cover a longer physical duration for the same sequence length, which is beneficial for modeling non-Markovian behaviors and long-horizon tasks. However, the sparse nature of these actions means the robot cannot react quickly to small changes in the environment, leading to error accumulation. When $f$ is high, the robot can perform rapid closed-loop corrections, but the action chunk covers only a short physical duration, causing the robot to "lose sight" of the long-term objective.

HiPolicy resolves this by reformulating the imitation learning problem to incorporate hierarchical multi-frequency observations and actions. Instead of a single frequency, it jointly encodes multiple frequency observation histories $O^h_{t,L_h} = \bigcup^M_{m=1} O^{f_m}_{t,L_h}$ and predicts a single hierarchical multi-frequency action chunk $A^h_{t,L_c} = \bigcup^M_{m=1} A^{f_m}_{t,L_c}$. Here, $M$ represents the number of different frequency components (e.g., a high-frequency component for precision and a low-frequency component for planning). This allows the model to reconcile the competing demands of planning and control.

![Problem Formulation Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06067v1/x2.png)
*Figure 2: Comparison between traditional single-frequency action chunking and the proposed hierarchical multi-frequency approach.*

## The HiPolicy Framework: Hierarchical Action Chunking

HiPolicy is built as a diffusion-based model capable of predicting action sequences with different temporal resolutions concurrently. The framework consists of three main stages: feature extraction, multi-frequency action generation, and adaptive execution.

### Hierarchical Feature Extraction
The process begins by processing raw observations (such as 2D images or 3D point clouds) and robot proprioceptive states. Unlike standard methods that take a uniform stack of recent frames, HiPolicy extracts frames at different temporal resolutions. For example, the high-frequency feature set might include every frame from the last 0.5 seconds, while the low-frequency set includes every 10th frame from the last 5 seconds. These are processed through an encoder (like a ResNet for images or a PointNet++ for 3D data) to generate hierarchical features $F^{f_m}_O$ for each frequency $f_m$.

### Multi-Frequency Action Chunk Prediction
The heart of HiPolicy is a diffusion-based U-Net that predicts noise to refine a set of candidate action chunks. The architecture uses specialized fusion modules to ensure that information is shared effectively across different frequencies:

1.  **Hierarchical FiLM Fusion:** The model uses Feature-wise Linear Modulation (FiLM) to condition the action generation process. The observation features $F^{f_m}_O$ at a specific frequency are used to modulate the action features $F^{f_m}_A$ at the same frequency. This ensures that the high-frequency control actions are specifically grounded in high-resolution temporal observations.
2.  **Global Feature Fusion:** While each frequency has its own focus, they must coordinate. HiPolicy implements a global fusion module using a cross-attention mechanism. A special "CLS token" aggregates local action features from all frequencies into a global feature $F^{global}_A$. This global information is then distributed back to the individual frequency components, allowing the low-frequency "planner" to inform the high-frequency "controller" and vice versa.

![HiPolicy Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06067v1/x3.png)
*Figure 3: Detailed architecture of HiPolicy, illustrating hierarchical feature extraction, FiLM fusion, and global feature fusion.*

## Entropy-Guided Adaptive Execution

A unique contribution of HiPolicy is its adaptive execution strategy. In a robot's workflow, some phases require extreme precision (like inserting a key into a lock), while others are less critical (like moving the hand toward the door). Standard policies often run at a fixed, high frequency throughout, which is computationally expensive and sometimes unnecessary.

HiPolicy uses the concept of "action entropy" to measure the uncertainty of its own predictions. During inference, the policy generates multiple candidate action chunks in parallel. By calculating the variance across these samples, the model estimates the Shannon entropy $\hat{H}_t$:

$$
\hat{H}_j = \log(\sqrt{2\pi e} \cdot \hat{\sigma}_j)
$$

Where $\hat{\sigma}_j$ is the variance of the $j$-th action in the chunk. If the entropy is low, it indicates that the policy is very "certain" about its path—this often occurs during critical, high-precision phases of a task. In these instances, the robot switches to executing its high-frequency action chunk to maintain fine-grained control.

If the entropy is high, the policy is less certain about specific joint positions but knows the general direction. This typically happens during transit or approach phases. In these cases, the robot switches to a low-frequency action chunk. This not only allows the robot to follow its long-term plan more effectively but also speeds up execution because it needs to generate and process fewer action commands over the same physical distance. This mechanism is governed by a set of thresholds $\{\hat{H}_{th,1}, \dots, \hat{H}_{th,M+1}\}$ that map the calculated entropy to a specific execution frequency.

![Adaptive Execution Visualized](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06067v1/x4.png)
*Figure 4: During high-precision tasks like grasping, entropy is low, triggering high-frequency control. During approach phases, entropy is higher, favoring low-frequency planning.*

## Experimental Evaluation and Results

The researchers evaluated HiPolicy on 21 challenging tasks from the RoboTwin simulation benchmarks. These tasks were selected to cover a wide range of requirements, including fine-grained manipulation (e.g., stacking blocks, beating a hammer) and super-long-horizon tasks (e.g., scanning objects, putting bottles in a dustbin).

HiPolicy was compared against two strong baselines: Diffusion Policy (DP), which uses 2D image inputs, and DP3, which uses 3D point cloud inputs. The results showed that HiPolicy consistently outperformed single-frequency methods. On the RoboTwin 1.0 benchmark, it achieved a 62% relative improvement in success rate over DP. On RoboTwin 2.0, it showed a 44% advantage over DP3.

Notably, the performance gains were most significant in tasks that required both long-term planning and high precision. For example, in the "block hammer beat" task, the standard Diffusion Policy failed completely (0% success), while HiPolicy achieved a 67% success rate. Similarly, in the "put bottles dustbin" task—a long-horizon challenge—HiPolicy significantly outperformed the baselines by maintaining a coherent plan throughout the sequence.

Ablation studies confirmed that both the hierarchical structure and the fusion modules were critical. Removing the hierarchical observation condition led to a drop in success rate, and removing the global feature fusion (cross-attention) resulted in a 6% performance decline, highlighting the necessity of inter-frequency communication.

![Simulation Task Visualization](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06067v1/x8.png)
*Figure 5: Snapshots of various long-horizon and high-precision tasks used for evaluation in the simulation environment.*

## Real-World Robustness and Efficiency

The framework's effectiveness was further validated through real-world experiments using a Franka Emika Panda robot arm. The robot was tasked with eight different activities, such as "Store Vegetables," "Stack Cube," and "Close Microwave Door."

In the real-world setting, HiPolicy achieved a 42% higher average success rate and a 14% faster average execution speed compared to the Diffusion Policy baseline. One of the most telling results was in the "Close Microwave Door" task. Standard policies often failed because they would stop after a partial movement, failing to engage the door's latch—a classic error in non-Markovian tasks where the robot loses the "intent" of the action. HiPolicy, with its hierarchical modeling, maintained the long-term intention until the latch was fully secured, achieving a 100% success rate.

The adaptive execution mechanism was also verified in the real world. In the "Store Vegetables" task, the entropy curve clearly showed low values during the picking phase (demanding high precision) and higher values during the transit phase (allowing for faster, low-frequency movement). This validated the hypothesis that entropy can serve as a reliable guide for switching temporal resolutions.

![Real-World Task Setup](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.06067v1/x5.png)
*Figure 6: Real-world tasks including picking vegetables, sweeping a board, and manipulating a microwave door.*

## Conclusion and Significance

HiPolicy introduces a structured way to handle the temporal complexities of robotic manipulation. By moving away from fixed-frequency action chunking and adopting a hierarchical, multi-frequency approach, the framework allows robots to concurrently manage high-level planning and low-level control.

The significance of this work lies in several areas:
1.  **Resolution of the Planning-Control Trade-off:** It provides a systematic method to gain the benefits of both high-frequency reactivity and low-frequency long-horizon planning without sacrificing one for the other.
2.  **Adaptive Efficiency:** The entropy-guided execution allows robots to be "smart" about how they spend their computational and temporal budget, speeding up during simple phases and slowing down for precision.
3.  **Modularity:** HiPolicy is designed to be integrated into existing generative policy frameworks (like DP or DP3), making it a versatile upgrade for current imitation learning systems.

While evaluated on relatively small datasets, the core principles of HiPolicy—hierarchical temporal modeling and uncertainty-aware execution—represent a significant step toward more capable and efficient embodied agents. Future work may see these hierarchical structures integrated into larger vision-language-action models to further enhance the versatility of general-purpose robots.

## Relevant Citations

- Diffusion policy: Visuomotor policy learning via action diffusion: This paper introduces Diffusion Policy, a foundational generative model that the HiPolicy framework is built upon and directly integrates with. It serves as a primary baseline (DP) in the experiments, and the significant improvements shown over it highlight the effectiveness of HiPolicy's hierarchical approach.
- Learning fine-grained bimanual manipulation with low-cost hardware: This work (also known as ACT) is cited for introducing the concept of action chunking, which is central to the problem HiPolicy addresses. HiPolicy is motivated by the trade-off between long-horizon dependency and fine-grained control inherent in the fixed-frequency chunking used in this prior work.
- 3d diffusion policy: Generalizable visuomotor policy learning via simple 3d representations: This paper extends diffusion policies to 3D perception and serves as the second major experimental baseline (DP3). HiPolicy's ability to boost DP3's performance demonstrates that the proposed multi-frequency chunking is a generalizable improvement for different input modalities, not just 2D vision.
- Reactive diffusion policy: Slow-fast visual-tactile policy learning for contact-rich manipulation: This paper is highlighted in the related work section as another approach to hierarchical policy learning. It is relevant because it helps distinguish HiPolicy's unique contribution, which is a hierarchy of temporal resolutions for actions, from prior works that focused on hierarchical structures for perceptual inputs.
