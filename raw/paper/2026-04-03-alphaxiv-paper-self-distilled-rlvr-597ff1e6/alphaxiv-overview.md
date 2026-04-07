# Self-Distilled RLVR

- alphaXiv: https://www.alphaxiv.org/abs/2604.03128
- Source paper: https://arxiv.org/abs/2604.03128

The post-training of Large Language Models (LLMs) has shifted toward enhancing complex reasoning capabilities through two primary strategies: Reinforcement Learning with Verifiable Rewards (RLVR) and On-Policy Distillation (OPD). While RLVR methods like Group Relative Policy Optimization (GRPO) use external signals (e.g., a binary indicator of mathematical correctness) to guide the model, they suffer from "coarse credit assignment." Every token in a long reasoning chain receives the same update signal, regardless of whether it was a brilliant logical deduction or a minor calculation error.

On the other hand, On-Policy Self-Distillation (OPSD) attempts to solve this by using the model itself as a teacher. The teacher is given "privileged information"—such as the correct final answer—to generate dense, token-level supervision for the student (the same model without the answer). However, this work identifies a critical failure in current self-distillation: it often leads to "information leakage," where the model learns to hallucinate reference solutions during inference, eventually causing performance to collapse.

![Average performance dynamics and reasoning task comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v1/x1.png)
*Figure 1: Performance dynamics on validation sets show that while OPSD (red) peaks early and then degrades, RLSD (green) achieves a higher convergence ceiling and maintains stability compared to standard GRPO (blue).*

To address these issues, the researchers propose **RLSD (RLVR with Self-Distillation)**. RLSD redefines the role of self-distillation: instead of the teacher serving as a target for the student to imitate, the teacher’s privileged knowledge is used only to modulate the *magnitude* of the update, while the environment reward (correctness) strictly controls the *direction*.

## The Structural Failure of Existing Self-Distillation

The paper begins by diagnosing why current OPSD methods fail. In a typical OPSD setup, a teacher policy $P_T(y_t | x, r, y_{<t})$ (conditioned on input $x$ and privileged information $r$) is used as a target for a student policy $P_S(y_t | x, y_{<t})$. The goal is to minimize the distribution difference between them.

Through empirical testing, the authors found that models trained with OPSD eventually start "leaking" information. For example, during testing (where no reference answer $r$ is provided), the model might suddenly output phrases like "The reference solution is..." or include internal indices that were only present in the training metadata. This indicates that the model has encoded statistical correlations between the input $x$ and the privileged answer $r$ directly into its weights.

![Leakage occurrence dynamics during training](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v1/x2.png)
*Figure 2: The count of "leakage" events—where the model references privileged information—increases significantly over time in OPSD, correlating with the eventual performance drop.*

The authors provide a formal theoretical diagnosis for this failure. They prove that because of the information asymmetry (the teacher knows $r$ but the student does not), there exists an irreducible mutual information gap $I(Y_t; R | X, Y_{<t})$. This gap acts as a lower bound on the loss function that the student can never reach. Because the student is forced to match a target it cannot fully see, the resulting gradients contain a "noise" term. While this noise averages out to zero across a full dataset, the per-sample updates drive the model to find spurious ways to "guess" $r$ from $x$, leading to the observed leakage and training instability.

![KL Divergence and validation performance](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v1/x3.png)
*Figure 3: Under OPSD, the KL divergence between teacher and student plateaus early, and performance declines after an initial peak, unlike stable distillation methods.*

## Bridging RLVR and Self-Distillation with RLSD

RLSD is designed to capture the dense, token-level insights of distillation without the risks of distribution matching. The core innovation is **Directional Isolation**. 

In RLSD, the environment provides a sequence-level advantage $A$. This $A$ is positive if the model's answer was correct and negative if it was wrong. This $A$ is the *only* component that decides whether to reinforce or penalize a sequence of tokens. The self-distillation signal—the difference between what the teacher knows and what the student knows—is used solely to adjust how much we should reinforce or penalize *each specific token*.

![RLSD Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v1/x4.png)
*Figure 4: The RLSD framework. The environment reward determines the update direction (sign), while the self-distillation signal (the difference between Teacher and Student modes) modulates the magnitude of the update for each token.*

This approach avoids the "Impossibility Trilemma" identified by the authors: that a model cannot simultaneously achieve objective stability, sustained improvement, and leakage-free training when the teacher is used as a generative target. By using the teacher only as a "magnitude evaluator," RLSD keeps the gradient direction anchored to the verifiable ground truth.

## The Mechanics of RLSD

The implementation of RLSD follows a three-step process integrated into the standard RL training loop:

### 1. Privileged Information Gain ($\Delta_t$)
For every token $y_t$ generated by the student, RLSD calculates the "gain" provided by the privileged information $r$. This is defined as:
$$\Delta_t = \text{sg}(\log P_T(y_t | x, r, y_{<t}) - \log P_S(y_t | x, y_{<t}))$$
The `sg` operator (stop-gradient) is crucial; it ensures that we are only using this value as a scalar weight and not backpropagating through the teacher's calculation. This $\Delta_t$ essentially asks: "Knowing the correct answer, how much more (or less) likely is this specific token?"

### 2. Direction-Aware Weighting ($w_t$)
The gain is then converted into a weight $w_t$ that respects the outcome of the entire reasoning chain. The weight is calculated as:
$$w_t = \exp(\text{sign}(A) \cdot \Delta_t) = \left( \frac{P_T}{P_S} \right)^{\text{sign}(A)}$$
- If the trajectory was **correct** ($A > 0$), then $w_t = P_T/P_S$. Tokens that the teacher strongly supports get a larger weight, receiving more "credit" for the correct answer.
- If the trajectory was **incorrect** ($A < 0$), then $w_t = P_S/P_T$. Tokens that the teacher strongly disfavors (where the student was much more confident than the teacher who knew the answer) get a larger weight, receiving more "blame" for the failure.

Because $w_t$ is always positive, the sign of the original advantage $A$ is never flipped. The environment reward remains the "source of truth" for the direction of learning.

### 3. Clipped Credit Assignment ($\hat{A}_t$)
To prevent any single token from dominating the training update, the weights are clipped within a range $[1-\epsilon_w, 1+\epsilon_w]$. The final token-level advantage $\hat{A}_t$ is:
$$\hat{A}_t = A \cdot \text{clip}(w_t, 1-\epsilon_w, 1+\epsilon_w)$$
This creates a "trust region" where the internal self-distillation signal can refine the reward, but the external environment reward always maintains control.

## Experimental Evaluation and Findings

The researchers evaluated RLSD on five major multimodal reasoning benchmarks: MMMU, MathVista, MathVision, ZeroBench, and WeMath. Using a Qwen2-VL-8B-Instruct model as the base, they compared RLSD against standard GRPO and various self-distillation baselines.

**Superior Performance:** RLSD consistently achieved the highest average accuracy. On average, it outperformed the base model by 4.69% and standard GRPO by 2.32%. The gains were particularly significant on math-heavy tasks like MathVision (+3.91% over GRPO), suggesting that fine-grained credit assignment is highly effective for complex multi-step deductions.

**Training Stability:** Unlike OPSD, which collapses after a certain number of steps, RLSD remains stable throughout training. It achieves a higher convergence ceiling than GRPO, proving that the dense token-level signals help the model learn more efficiently.

![Training dynamics: reward, entropy, and clipping](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03128v1/x5.png)
*Figure 5: RLSD maintains higher training entropy compared to GRPO, which often suffers from "entropy collapse" where it prematurely converges to a few common patterns. The clipping ratios show that the model actively uses the self-distilled signal throughout training.*

**Qualitative Impact:** Through case studies, the authors demonstrated that RLSD effectively identifies "pivotal" tokens. In a correct reasoning trace, higher credit was assigned to the exact moments of logical transition (e.g., performing a subtraction or counting items in an image). In incorrect traces, the model was able to pinpoint specific calculation errors and apply more "blame" to those tokens than to the rest of the response.

## Significance of the Work

The primary contribution of this research is the theoretical and practical decoupling of the teacher's role in self-distillation. By identifying the inherent "mutual information gap" that makes distribution-matching OPSD ill-posed, the authors provide a clear explanation for why many reasoning models fail during long-duration post-training.

RLSD provides a robust, scalable solution that:
1.  **Eliminates Information Leakage:** Because the teacher cannot influence the sign of the gradient, the model is prevented from learning spurious correlations to the privileged answer.
2.  **Solves the Credit Assignment Problem:** It provides a principled way to turn sequence-level rewards into token-level insights without needing expensive human-annotated process rewards or external teacher models.
3.  **Maintains Exploration:** By avoiding uniform reward assignment, RLSD prevents the rapid entropy collapse seen in standard RLVR, allowing the model to continue exploring diverse reasoning paths.

As a drop-in replacement for existing RLVR pipelines, RLSD offers a more efficient path toward building models that not only get the right answer but understand which parts of their internal logic were responsible for that success.

## Relevant Citations

- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper introduces Group Relative Policy Optimization (GRPO), which is the foundational Reinforcement Learning with Verifiable Rewards (RLVR) method that the main paper builds upon and compares against. The proposed RLSD method is presented as a direct enhancement to GRPO's advantage estimation, making this citation central to understanding the baseline and contribution.
- Self-distilled reasoner: On-policy self-distillation for large language models: This paper introduces a key On-Policy Self-Distillation (OPSD) method. The main paper's core motivation is to diagnose the structural failures of the OPSD paradigm, such as information leakage and performance degradation, making this work fundamental to the problem being solved.
- On-policy distillation of language models: Learning from self-generated mistakes: This paper introduces On-Policy Distillation (OPD), which serves as a crucial point of comparison to On-Policy Self-Distillation (OPSD). The authors frame their core research question around why OPD succeeds while OPSD fails, making this work essential for the theoretical context of the paper.
- Reinforcement learning via self-distillation: This work, along with reference [7], defines the On-Policy Self-Distillation (OPSD) paradigm that is critically analyzed by the authors. The paper's experiments explicitly include this method (as SDPO) as a key baseline for comparison, demonstrating its direct relevance.
- Proximal policy optimization algorithms: This paper introduces Proximal Policy Optimization (PPO), a foundational algorithm in modern reinforcement learning. Its clipped surrogate objective is explicitly mentioned as the design philosophy behind both the GRPO baseline and the proposed RLSD method, making it a key conceptual precursor to the paper's methodology.
