# Temporal Straightening for Latent Planning

- alphaXiv: https://www.alphaxiv.org/abs/2603.12231
- Source paper: https://arxiv.org/abs/2603.12231

## Overview

This paper introduces temporal straightening, a geometric regularization technique that improves representation learning for latent world models in model-based reinforcement learning. The method addresses a fundamental challenge in latent planning: how to learn representations that not only capture the essential dynamics of an environment but also enable efficient gradient-based optimization for planning tasks.

The core insight stems from neuroscience, specifically the "perceptual straightening hypothesis" which suggests that biological visual systems internally straighten complex visual trajectories. The authors apply this principle to artificial systems by regularizing latent trajectories to be geometrically straighter, thereby creating representations that are more amenable to planning algorithms.

## Problem Setting and Motivation

Latent world models aim to address the computational challenges of planning in high-dimensional observation spaces by learning compressed representations of the environment. While these models offer efficiency benefits over planning directly in raw pixel space, they introduce a new challenge: the learned latent spaces are often highly curved, making gradient-based optimization difficult and unreliable.

Current approaches face several limitations. Pre-trained visual encoders like DINOv2, while semantically rich, are not optimized for the specific requirements of planning tasks. Reconstruction-based methods can overemphasize low-level visual details irrelevant to planning. Most critically, when latent trajectories are curved, the Euclidean distance between states in latent space poorly approximates the true geodesic distance - the shortest feasible path between states in the actual environment.

This misalignment between latent geometry and true state relationships leads to suboptimal planning. Gradient-based optimizers struggle with the highly non-convex planning objectives that result from curved latent spaces, often requiring computationally expensive search-based methods like the Cross-Entropy Method (CEM) or Model Predictive Path Integral (MPPI).

## Methodology

The temporal straightening approach centers on a joint training objective that combines standard predictive modeling with a geometric regularization term designed to encourage straighter latent trajectories.

**World Model Architecture**

The world model consists of three primary components:
- A sensory encoder that maps high-dimensional observations to compact latent representations
- An action encoder that embeds actions into the latent space  
- A Vision Transformer predictor that learns the latent dynamics

Two encoder setups are explored: using a pre-trained DINOv2 backbone with a trainable projector, and training a ResNet architecture from scratch.

**Temporal Straightening Regularization**

The key innovation is a regularization term that penalizes curvature in latent trajectories. For three consecutive latent states $z_t$, $z_{t+1}$, and $z_{t+2}$, the method defines velocity vectors:

$$
v_t = z_{t+1} - z_t, \quad v_{t+1} = z_{t+2} - z_{t+1}
$$

The straightening objective maximizes the cosine similarity between consecutive velocity vectors:

$$
C = \frac{v_t \cdot v_{t+1}}{||v_t||_2 \cdot ||v_{t+1}||_2}
$$

The regularization loss is then:

$$
L_{curv} = 1 - C
$$

This encourages consecutive velocity vectors to be collinear, effectively straightening the trajectory. For spatial features with multiple patches, a learnable pooling head aggregates features before computing the cosine similarity.

The total training objective combines prediction accuracy with straightening:

$$
L_{total} = L_{pred} + \lambda L_{curv}
$$

where $L_{pred}$ is the mean squared error between predicted and actual next states, and $\lambda$ controls the regularization strength.

**Theoretical Foundation**

The paper provides theoretical justification for why straightening improves planning. Under a linear dynamics assumption where $z_{t+1} = Az_t + Ba_t$, the authors define an "ε-straight" transition as one where $||A - I||_2 \leq \varepsilon$. They prove that for such transitions, the condition number of the planning Hessian is bounded, leading to faster convergence for gradient-based optimizers. The straightening regularization effectively encourages this condition by making the latent dynamics closer to identity mappings perturbed by actions.

## Experimental Validation

The method is evaluated on four 2D goal-reaching environments: Wall, PointMaze variants (UMaze and Medium-Maze), PushT, and a custom Teleported-PointMaze environment designed to test dynamics-aware representation learning.

**Embedding Space Analysis**

Quantitative analysis confirms that temporal straightening successfully reduces trajectory curvature. The regularized models show higher average cosine similarities between consecutive velocity vectors compared to baselines. Principal Component Analysis visualizations reveal smoother, less curved trajectories in the straightened latent space.

Importantly, the method improves the alignment between Euclidean distances in latent space and true geodesic distances in the environment. Distance heatmaps show that straightened representations produce landscapes closely approximating the minimum steps required to reach targets, similar to ground-truth A-star distances.

**Planning Performance**

The results demonstrate substantial improvements in planning success rates:

- Open-loop planning success rates improved by 20-60% across tasks
- Model Predictive Control (MPC) success rates increased by 20-30%
- For PointMaze-UMaze with DINOv2 projector, open-loop success increased from 44% to 94%
- When training ResNet from scratch, success rates jumped from 15% to 65%

The straightened models achieve high performance rapidly with MPC, reaching 100% success within a few steps in simpler environments. Crucially, the method substantially reduces the performance gap between gradient-based and search-based planning methods, sometimes achieving comparable results with much lower computational cost.

**Architecture Insights**

Training encoders from scratch with straightening generally yields better results than using fixed pre-trained backbones, suggesting the importance of jointly optimizing representation and dynamics. Moderate feature dimensions (around 8 channels) prove optimal - too few channels are insufficient while too many can hinder planning performance. For spatial features, applying straightening to globally aggregated representations while preserving local patch-level flexibility works best.

## Validation on Complex Dynamics

The Teleported-PointMaze environment provides a critical test case where visual similarity is decoupled from temporal dynamics. In this environment, the agent can teleport between visually similar locations, making visual-similarity-based planning misleading. The straightened model successfully learns to leverage the teleportation mechanic, demonstrating that it captures dynamics-aware representations rather than merely visual patterns.

## Significance and Impact

This work makes several important contributions to model-based reinforcement learning and representation learning more broadly. By demonstrating that geometric properties of latent spaces significantly impact planning performance, it opens new research directions focused on optimizing representations specifically for downstream control tasks rather than just predictive accuracy.

The bio-inspired approach provides a compelling example of translating neuroscientific insights into practical AI improvements. The method's ability to enable efficient gradient-based planning could substantially reduce computational requirements for model-based RL, making it more practical for real-time applications like robotics.

The theoretical analysis connecting trajectory straightness to planning optimization provides a foundation for future work on geometric properties of learned representations. The consistent improvements across different architectures and environments suggest the approach's generalizability, while the straightforward implementation makes it readily adoptable by practitioners.

Perhaps most significantly, this work challenges the common assumption that any sufficiently expressive representation will work for planning, instead demonstrating that the geometric structure of the latent space is crucial for optimization success. This insight could influence how the field approaches representation learning for control tasks more broadly.

## Relevant Citations

- Perceptual straightening of natural videos: This paper introduces the 'perceptual straightening hypothesis' in human visual processing, which serves as the core biological inspiration for the temporal straightening method proposed in the main paper. The authors explicitly state they are motivated by the idea that visual systems transform complex videos into straighter internal representations.
- Dino-wm: World models on pre-trained visual features enable zero-shot planning: This work, DINO-WM, is the primary baseline and the closest related work discussed in the paper. The main paper's method is presented as a direct improvement over DINO-WM's approach of planning directly in a frozen DINOv2 feature space, showing that straightening the latent trajectories leads to significantly better planning outcomes.
- World models: This is a foundational paper that popularized the concept of learning a compressed latent space model of the world for planning. The main paper's approach of learning an encoder and a predictive model to enable latent planning is a direct contribution to this established 'world model' paradigm.
- DINOv2: Learning robust visual features without supervision: This paper introduces the DINOv2 model, which provides the pretrained visual features used as a starting point by both the baseline and the proposed method. The main paper's key argument is that while DINOv2 features are powerful, they are not tailored for planning, thus motivating the development of the temporal straightening technique to improve them.
