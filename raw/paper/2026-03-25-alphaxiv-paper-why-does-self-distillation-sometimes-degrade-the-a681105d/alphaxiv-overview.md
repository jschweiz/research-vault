# Why Does Self-Distillation (Sometimes) Degrade the Reasoning Capability of LLMs?

- alphaXiv: https://www.alphaxiv.org/abs/2603.24472
- Source paper: https://arxiv.org/abs/2603.24472

## The Self-Distillation Paradox in LLMs

Self-distillation has become a standard post-training method for Large Language Models (LLMs), intended to improve performance and efficiency. In many fields, such as chemistry, physics, or general tool-use, this process works as expected: a model learns to imitate a "teacher" that has access to more information, leading to shorter, more efficient reasoning paths that still reach the correct answer. This efficiency is often viewed as a sign of model improvement—stripping away redundant thoughts while maintaining accuracy.

However, recent research identifies a paradox when self-distillation is applied to complex mathematical reasoning. While the models do indeed become more concise, their actual reasoning capability and ability to solve new, unseen problems (generalization) often suffer. Instead of becoming "smarter and faster," the models often become "faster but more brittle."

![Reasoning with Epistemic Verbalization](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/Reasoning_with_Epistemic_Verbalization.png)
*Figure 1: A comparison between procedural reasoning only and reasoning that includes epistemic verbalization. While the former focuses on a direct path to the answer, the latter uses uncertainty markers to mitigate premature commitment and adjust hypotheses.*

The core of this issue lies in how self-distillation handles uncertainty. In mathematical tasks, the "thought traces" or reasoning steps often contain expressions of doubt, such as "Wait," "Hmm," "Perhaps," or "Let me re-check." This research introduces the term **epistemic verbalization** to describe these signals. The paper argues that when self-distillation prunes these expressions to favor conciseness, it removes the model's internal mechanisms for self-correction and hypothesis testing, leading to a degradation in reasoning quality.

## Core Principle: Epistemic Verbalization and Reasoning

Mathematical reasoning in LLMs is not a simple linear path from question to answer; it is a "self-Bayesian" process where the model continuously updates its internal beliefs as it generates each token. Epistemic verbalization serves as the explicit manifestation of this process. When a model says "Hmm" or "Wait," it is signaling that its current reasoning path has high uncertainty, allowing it to pause and explore alternative hypotheses.

In a self-distillation framework, we have a student policy $\pi_\theta(y | x)$ and a teacher policy $\pi^T_\theta(y | x, c) = \pi_\theta(y | x, c)$. The teacher is the same model as the student but is provided with an additional conditioning context $c$, such as the ground-truth solution or feedback from a environment. The goal of self-distillation is for the student (without $c$) to match the output distribution of the teacher (with $c$).

The researchers found that when the teacher has access to the solution ($c=s$), it becomes highly confident and concise. It skips the "uncertainty" steps because it already "knows" where it is going. When the student is trained to imitate this behavior, it learns to be confident and concise even when it *doesn't* have access to the solution. It essentially learns to "blindly" jump to conclusions without the necessary internal checks that uncertainty markers provide.

## Information-Theoretic Perspectives: How Context Suppresses Uncertainty

The researchers used an information-theoretic approach to quantify why teachers become so concise. They used **conditional mutual information** to measure how much the context $c$ reduces the uncertainty of the reasoning path $y$:

$$
I(y; c | x) = H(y | x) - H(y | x, c)
$$

By testing different levels of context—ranging from no context ($c = \emptyset$) to full solution guidance ($c = s$)—they observed a strict monotonic relationship. As the information richness of the context increases, the average response length $E[L(y)]$ and the frequency of epistemic markers $E[E(y)]$ both decrease.

![Unguided vs Teacher Guided](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/unguided_vs_teacher_guided.png)
*Figure 2: Conceptual illustration showing that unguided generation involves higher uncertainty and longer reasoning, while solution-guided generation is concise and confident.*

When the teacher has the solution, it provides a "hint" that effectively eliminates the need for the model to "think through" the uncertainties. This creates a distribution for the student to follow that is devoid of the very signals—the "waits" and "hmms"—that the student needs to navigate the problem-solving process autonomously.

## Empirical Evidence: The Impact of Concise Training Data

To confirm that the style of the reasoning trace (concise vs. rich) matters more than just the correctness of the answer, the authors performed Supervised Finetuning (SFT) experiments. They created two datasets of 800 correct mathematical responses:
1.  **$D_{ug}$ (Unguided):** Responses generated without a solution hint, characterized by long, uncertain reasoning traces.
2.  **$D_{sg}$ (Solution-guided):** Responses generated with solution hints, characterized by concise, confident reasoning.

Even though both datasets contained only correct answers, the model trained on $D_{sg}$ saw its performance on difficult math benchmarks like AIME24 collapse. For example, a DeepSeek-R1-based model's score dropped from 54.79% to 20.21% when trained on the concise $D_{sg}$ data, while training on the rich $D_{ug}$ data maintained its performance. This suggests that "learning to be concise" is actually harmful for the model's ability to reason through complex, unseen problems.

## On-Policy Comparison: SDPO vs. GRPO

The research compared two popular post-training algorithms: **SDPO (Reinforcement Learning via Self-Distillation)** and **GRPO (Generalized Reinforcement with Policy Optimization)**. 

SDPO explicitly encourages the model to follow the teacher's distribution, while GRPO uses verifiable rewards (is the answer correct?) to guide the model without a fixed teacher distribution.

![SDPO vs GRPO Training Scores](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/x1.png)
![SDPO vs GRPO Response Length](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/x2.png)
*Figures 3 & 4: Training score and response length trajectories for GRPO and SDPO. Note how SDPO leads to significantly shorter responses while the training score struggles compared to the more expressive GRPO.*

The results across multiple models (Qwen3, DeepSeek-Distill, OLMo-3) were consistent:
*   **SDPO** led to a sharp decrease in response length and epistemic tokens, which was followed by a significant drop in performance on out-of-distribution (OOD) benchmarks.
*   **GRPO** allowed the model to maintain or even increase its reasoning length and epistemic verbalization, leading to better generalization and higher scores on difficult problems.

![AIME24 Performance Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/x4.png)
*Figure 5: Performance on the AIME24 benchmark. SDPO shows a degradation in performance over time, while GRPO maintains or improves its reasoning capability.*

The researchers also found that if the teacher context is made *less* informative—for example, by removing the "think" tags from the teacher's solution ($c = s_{\setminus\text{think}}$)—the performance degradation in SDPO is mitigated. This further supports the theory that the "perfection" and "conciseness" of the teacher are exactly what harms the student.

## The Crucial Role of Task Coverage

An important question remains: why does self-distillation work for science or tool-use but fail for math? The researchers hypothesized that it depends on **task coverage**.

If a dataset has low coverage (a few recurring task patterns), the model can learn a direct mapping from question to answer. In these cases, conciseness is efficient and doesn't hurt. However, mathematical reasoning often involves "broad coverage," where the model frequently encounters novel problems that require deep search and uncertainty handling.

![Scaling with Task Coverage GRPO](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/x25.png)
![Scaling with Task Coverage SDPO](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24472v1/x26.png)
*Figures 6 & 7: Performance scaling as the number of training questions $|D| \in \{1, 8, 64, 128, 512\}$ increases. GRPO scales positively with more data, while SDPO performance plateaus or declines as it forces conciseness onto a diverse set of tasks.*

In their experiments, when the training set size $|D|$ was very small, SDPO reached high training scores quickly by becoming concise. But as the dataset grew to include more diverse problems, SDPO's forced conciseness became a hindrance. GRPO, by contrast, continued to scale and improve as more data was added, precisely because it allowed the model to use as much "thought" (and uncertainty) as needed to solve the problems.

## Conclusion: Rethinking Post-Training for Robust Generalization

This work reveals a fundamental trade-off in LLM training: **Efficiency vs. Robustness.** 

Self-distillation, as currently practiced, prioritizes efficiency by forcing models to imitate high-confidence, concise teacher traces. While this might work for narrow, repetitive tasks, it strips away the "epistemic verbalization" necessary for high-level reasoning and generalization in domains like mathematics.

The findings suggest that the goal of post-training should not be simply to make models "faster" or "shorter," but to preserve their ability to navigate uncertainty. Effective reasoning requires a model to be able to say "Wait" or "Let me check" when it encounters a difficult path. Future post-training strategies should likely focus on incentivizing these self-correcting behaviors rather than pruning them in the name of stylistic conciseness. As LLMs are tasked with increasingly complex and novel problems, the ability to handle uncertainty will be more valuable than the ability to provide a short, potentially wrong, answer.

## Relevant Citations

- Reinforcement learning via self-distillation: This paper introduces SDPO, the specific self-distillation algorithm that is the primary subject of analysis in the main paper. The authors' investigation into why SDPO degrades mathematical reasoning performance is a direct response to and analysis of the method proposed in this citation.
- Understanding reasoning in llms through strategic information allocation under uncertainty: This work is foundational to the main paper's central hypothesis, as it introduces the concept of 'epistemic verbalization'. The authors build directly on this concept to argue that self-distillation degrades reasoning by suppressing these crucial uncertainty signals during problem-solving.
- Learning by distilling context: Cited in the first sentence of the introduction, this paper is credited with establishing the general paradigm of self-distillation. It provides the essential background for the techniques and problems discussed in the main paper.
- Self-distilled reasoner: On-policy self-distillation for large language models: This is a key contemporary paper on the same topic of on-policy self-distillation, which is cited multiple times for context on technical issues like training instability. The main paper also directly compares its setup and findings with the methods from this work, making it highly relevant for context and contrast.
