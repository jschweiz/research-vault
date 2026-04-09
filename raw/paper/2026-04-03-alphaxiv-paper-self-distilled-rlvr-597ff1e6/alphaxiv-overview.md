# Self-Distilled RLVR

- alphaXiv: https://www.alphaxiv.org/abs/2604.03128
- Source paper: https://arxiv.org/abs/2604.03128

## The Post-Training Landscape of Reasoning Models

Post-training large language models (LLMs) for complex reasoning tasks typically follows one of two paths. The first is Reinforcement Learning with Verifiable Rewards (RLVR), such as Group Relative Policy Optimization (GRPO). These methods use outcome-based feedback—checking if a math answer is correct or if code passes a test—to provide a reliable learning signal. However, these signals are often sparse; they tell the model that a long sequence of reasoning was "right" or "wrong" without specifying which individual steps were the most critical.

The second path is On-Policy Distillation (OPD), which provides dense, token-level feedback by having a larger "teacher" model evaluate every step the "student" model takes. While effective, this is computationally expensive and requires a teacher model that shares the same vocabulary. A variation of this is On-Policy Self-Distillation (OPSD), where the model acts as its own teacher. By giving itself privileged information (like a gold-standard reasoning trace), the model creates a "teacher mode" to supervise its own "student mode."

![Performance dynamics and accuracy comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v2/x1.png)
*Figure 1: (a) Performance dynamics showing RLSD's stability versus OPSD's collapse. (b) Performance across benchmarks MMMU, MathVista, and ZeroBench.*

This research identifies a critical flaw in OPSD: "privileged information leakage." Because the teacher has access to information that the student will not have at inference time, the student begins to hallucinate or explicitly reference that hidden information during training. This leads to a performance peak followed by a sharp decline. To solve this, the authors propose Reinforcement Learning with Self-Distillation (RLSD), a framework that uses self-distillation signals to adjust the *magnitude* of reinforcement learning updates while letting environmental feedback control the *direction*.

## The Failure of On-Policy Self-Distillation

To understand why OPSD fails, we must look at the information asymmetry between its teacher and student modes. In OPSD, for a given question $x$, the model samples a response $y$. To train, it calculates a loss based on the difference between the student distribution (conditioned only on $x$) and the teacher distribution (conditioned on $x$ and a privileged reasoning trace $r$).

The researchers found that OPSD-trained models exhibit three distinct pathologies:
1.  **Information Leakage:** As training progresses, models increasingly generate phrases like "According to the reference solution..." or "The correct answer is [hidden value]," even when $r$ is not provided.
2.  **Performance Degradation:** Accuracy initially improves but then crashes.
3.  **KL Stagnation:** The Kullback-Leibler (KL) divergence, which measures the difference between the teacher and student, stops decreasing and plateaus.

The authors prove that this failure is due to an "ill-posed objective." Mathematically, the goal of OPSD is to minimize:

$$\mathcal{L}_{OPSD}(\theta) = \mathbb{E}_{x \sim \mathcal{D}, y \sim \pi_\theta(\cdot|x, r)} \left[ \sum_{t=1}^{|y|} D_{KL}(\pi_\theta(\cdot|x, r, y_{<t}) || \pi_\theta(\cdot|x, y_{<t})) \right]$$

However, they demonstrate that even at the theoretical optimum, the KL divergence cannot reach zero. It is bounded by the conditional mutual information between the token $y_t$ and the privileged information $r$:

$$D_{KL}(\pi_\theta(Y_t|x, r, y_{<t}) || \pi_\theta(Y_t|x, y_{<t})) \geq I(Y_t; R | X=x, Y_{<t}=y_{<t})$$

This gap represents information that the student physically cannot know without $r$. In an attempt to bridge this gap, the model's parameters $\theta$ are updated in a way that forces the student to "guess" or "hallucinate" the contents of $r$, leading to the observed leakage.

![Leakage and KL Divergence analysis](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v2/x2.png)
*Figure 2: (a) Monitoring the count of privileged information leakage. (b) Performance curves showing early peaks. (c) KL divergence comparison between OPSD and standard OPD.*

## Reinforcement Learning with Self-Distillation (RLSD)

The core innovation of RLSD is to stop using the teacher's distribution as a direct target for the student's output. Instead, RLSD uses the teacher to answer a simpler question: "Given that we know the right answer, how important was this specific token $y_t$?"

### 1. Calculating Privileged Information Gain
For every token $y_t$ in a generated sequence, the model calculates the difference in log-probabilities between its teacher mode and its student mode:

$$\Delta_t = \text{sg}(\log P_T(y_t | x, r, y_{<t}) - \log P_S(y_t | x, y_{<t}))$$

The "stop-gradient" ($\text{sg}$) operator is crucial. It ensures that $r$ only influences the weight of the update, not the direction of the gradient itself. This prevents the student from trying to mimic the teacher's internal state.

### 2. Direction-Aware Reweighting
RLSD then combines this gain with the environmental reward $A$ (the "advantage" from the verifier). It calculates a weight $w_t$:

$$w_t = \exp(\text{sign}(A) \cdot \Delta_t)$$

This weight behaves intuitively:
*   If the response was correct ($A > 0$): Tokens that the teacher strongly supports (high $\Delta_t$) get a higher weight. The model is told: "This step was particularly responsible for the right answer."
*   If the response was incorrect ($A < 0$): Tokens that the teacher supports get a *lower* weight, while tokens the teacher disfavors get penalized more heavily. The model is told: "Even though the teacher liked this token, the final answer was wrong, so be careful."

### 3. Clipped Credit Assignment
To maintain training stability, the final advantage $\hat{A}_t$ is calculated by applying a clipping mechanism and a mixing coefficient $\lambda$:

$$\hat{A}_t = A \cdot ((1 - \lambda) + \lambda \cdot \text{clip}(w_t, 1 - \epsilon_w, 1 + \epsilon_w))$$

Here, $\epsilon_w$ is a hyperparameter that limits how much any single token can influence the update. This prevents extreme weights from causing the training to diverge.

![RLSD Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v2/x3.png)
*Figure 3: The RLSD architecture showing how the privileged signal ($\Delta_t$) modulates the advantage ($A$) to produce token-level advantages ($\hat{A}_t$).*

## Experimental Results

The researchers evaluated RLSD on several difficult multimodal and mathematical reasoning benchmarks, including MMMU, MathVista, and ZeroBench. They compared RLSD against base models, standard GRPO (RLVR), and OPSD.

Across the board, RLSD consistently outperformed its counterparts. For instance, on MathVision, RLSD achieved a score of 22.31%, compared to 18.40% for GRPO and 19.34% for OPSD. On average, RLSD provided a 2.32% improvement over standard GRPO while maintaining the training stability that OPSD lacks.

### Training Stability and Entropy
One of the notable findings was the behavior of model "entropy" during training. In standard RLVR, the model's entropy often collapses quickly as it finds a single "safe" way to get the reward, leading to less creative or diverse reasoning. RLSD maintained significantly higher entropy throughout training (Figure 4b). This suggests that token-level credit assignment helps the model explore the reasoning space more effectively without getting stuck in local optima.

![Training dynamics and clip ratios](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v2/x4.png)
*Figure 4: (a) Reward dynamics. (b) Entropy loss comparison. (c) Stabilization via the clipping mechanism.*

### Qualitative Analysis of Credit Assignment
To see if RLSD was actually identifying important steps, the authors visualized the token-level advantages in correct and incorrect reasoning traces. In a correct trace for a geometry problem, RLSD assigned high credit to the specific mathematical operations that led to the final count. In an incorrect trace, it successfully identified the precise logical leap where the model misinterpreted the image, assigning that token a negative advantage (Figure 5).

![Visualization of token-level credit assignment](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v2/x5.png)
*Figure 5: Heatmaps of token-level advantages. Green indicates positive credit; red indicates blame. The model correctly identifies critical reasoning steps.*

## Significance and Future Impact

This work addresses a fundamental tension in LLM training: the trade-off between the reliability of sparse rewards and the efficiency of dense supervision. By identifying the theoretical reasons for self-distillation failure—namely the conditional mutual information gap—the authors provide a roadmap for more stable distillation techniques.

RLSD is significant because it is a "drop-in" improvement for existing RL frameworks like GRPO. It requires no external teacher model and only one additional forward pass per response, making it highly efficient. The decoupling of update direction (from the environment) and update magnitude (from the self-teacher) provides a robust way to leverage privileged information without the risk of leakage or performance collapse. As reasoning models become more complex, such fine-grained credit assignment mechanisms will likely be essential for teaching models not just to get the right answer, but to understand exactly which parts of their logic were successful.

## Relevant Citations

- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper introduces Group Relative Policy Optimization (GRPO), which is the primary Reinforcement Learning with Verifiable Rewards (RLVR) baseline method used throughout the paper. The proposed RLSD method is presented as a direct enhancement to the GRPO framework, replacing its uniform sequence-level advantage with a fine-grained, token-level credit assignment mechanism.
- On-policy distillation of language models: Learning from self-generated mistakes: This work defines On-Policy Distillation (OPD), a key training paradigm that the paper contrasts with On-Policy Self-Distillation (OPSD). The central question motivating the research—"why does OPD work while OPSD fails?"—makes this citation fundamental to understanding the paper's core theoretical analysis.
- Self-distilled reasoner: On-policy self-distillation for large language models: This paper introduces On-Policy Self-Distillation (OPSD), the primary method that the main paper analyzes, critiques, and uses as a baseline. The theoretical and empirical analysis of OPSD's failure due to information leakage forms the central motivation for the development of the proposed RLSD method.
- Proximal policy optimization algorithms: This paper introduces Proximal Policy Optimization (PPO), a foundational policy gradient algorithm in reinforcement learning. The main paper's baseline, GRPO, is a variant of PPO, and the proposed RLSD method explicitly adopts PPO's design philosophy of using a clipped objective to stabilize training, applying it to token-level credit assignment.
