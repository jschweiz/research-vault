# Embarrassingly Simple Self-Distillation Improves Code Generation

- alphaXiv: https://www.alphaxiv.org/abs/2604.01193
- Source paper: https://arxiv.org/abs/2604.01193

## Simple Self-Distillation for Code Generation

Large language models (LLMs) have become remarkably proficient at generating computer code, but continuing to improve them often hits a resource bottleneck. Traditional methods for enhancing these models typically require high-quality supervised signals, such as human-written solutions, a more powerful "teacher" model for knowledge distillation, or complex reinforcement learning (RL) loops that rely on code execution and automated test cases.

![Figure 1: Overview of Simple Self-Distillation (SSD) results and comparative advantages over existing methods.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01193v1/x1.png)

A recent research effort introduces a method called Simple Self-Distillation (SSD), which attempts to bypass these dependencies entirely. The core premise is that an LLM can improve its code generation capabilities by training solely on its own unverified outputs. Unlike existing self-improvement techniques, SSD does not use any external verification (like checking if the code actually runs correctly), nor does it use a teacher model to provide labels. This "embarrassingly simple" approach aims to determine if a model can refine its own internal logic and token distributions through a basic loop of generation and fine-tuning.

## The Core Concept: Avoiding External Signals

The significance of SSD lies in its independence. Most current state-of-the-art code models are trained using one of the following:
*   **Supervised Fine-Tuning (SFT):** Requires human-written or teacher-generated reference solutions.
*   **Execution-Based Filtering:** Generates many solutions and keeps only those that pass unit tests (e.g., CodeContests or AlphaCode).
*   **Reinforcement Learning (RL):** Uses a reward model or an execution environment to provide feedback on generated code.

![Figure 2: Comparing SSD with other training paradigms in terms of signal density and external dependencies.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01193v1/x2.png)

SSD, by contrast, operates under a much stricter constraint. It takes a pre-trained model and a set of coding problem prompts. The model generates solutions for these prompts, and then the same model is fine-tuned on these self-generated responses. The researchers found that even without knowing which solutions are correct, this process consistently leads to better performance on standardized coding benchmarks.

## The SSD Methodology

The SSD process follows a straightforward three-stage pipeline:

1.  **Data Synthesis:** A frozen, pre-trained LLM ($p_{\theta}$) is given a set of coding prompts. For every prompt, the model generates exactly one candidate solution ($N=1$). This generation uses specific training-time decoding settings ($T_{\text{train}}$, $\rho_{\text{train}}$), which include temperature and truncation (like top-k or top-p). Crucially, these solutions are not verified for correctness; the model simply produces its best guess or a diverse sample.
2.  **Fine-Tuning:** The raw, unverified outputs are collected into a dataset ($D_{\text{SSD}}$). The base model is then fine-tuned on this dataset using standard supervised fine-tuning. The training objective is to minimize the cross-entropy loss:
$$L(\theta) = -\mathbb{E}_{(x,y) \sim D_{\text{SSD}}} \sum_{t=1}^{|y|} \log p_{\theta}(y_t | x, y_{<t})$$
Essentially, the model is being taught to prefer the types of distributions it generated during the synthesis stage.
3.  **Inference:** The resulting fine-tuned model ($p_{\theta}^*$) is then evaluated using different evaluation-time decoding settings ($T_{\text{eval}}$, $\rho_{\text{eval}}$).

The researchers tested this on several model families, including Llama-3.1 and Qwen, across various sizes (4B to 30B parameters). Across the board, models showed significant gains in pass@1 and pass@5 metrics, especially on difficult problems. For example, Qwen3-30B-Instruct saw its pass@1 score on LiveCodeBench v6 jump from 42.4% to 55.3%, a 12.9 percentage point increase.

## The Mechanism: The Precision-Exploration Conflict

A major contribution of this work is the explanation for *why* such a simple method works. The authors hypothesize that LLMs face a "precision-exploration conflict" when decoding code.

In coding, certain parts of a file require absolute precision—for example, a colon at the end of an `if` statement or the correct syntax for a library call. These are "Locks." At these positions, the model needs to be very sharp, and low temperatures are helpful to avoid distractors. However, other parts of the code represent algorithmic choices or structural decisions where multiple valid paths exist. These are "Forks." Here, the model needs to explore different possibilities to find a successful path, which usually requires higher temperatures.

![Figure 3: Illustration of the "Fork" (exploration-bound) and "Lock" (precision-bound) contexts in code generation.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01193v1/x7.png)

A single global temperature setting is always a compromise:
*   **Low temperature:** Sharpens "Locks" (good) but kills diversity at "Forks" (bad).
*   **High temperature:** Allows exploration at "Forks" (good) but introduces errors at "Locks" by raising the probability of distractor tokens (bad).

SSD reshapes the model's internal distributions to alleviate this conflict. By training on truncated samples at a specific temperature, the model learns to suppress the "tail" of the distribution (the unlikely distractors) while preserving the diversity of the "head" (the plausible alternatives). This allows the model to maintain precision at "Locks" even when a high temperature is used during evaluation to encourage exploration at "Forks."

## Robustness and the "Gibberish" Experiment

One of the most striking findings of the paper is the "Bad Data, Good Results" experiment. The researchers intentionally generated training data using a very high temperature ($T_{\text{train}}=2.0$) and no truncation. This resulted in "gibberish" training data—responses that were largely incoherent or garbled.

![Figure 4: Results of training on "gibberish" data synthesized at high temperature, showing performance gains despite low data quality.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01193v1/x10.png)

Despite the poor quality of individual samples, fine-tuning on this data still led to significant performance improvements over the base model. This suggests that the benefits of SSD are not necessarily derived from the "correctness" of the individual solutions in the training set. Instead, the benefit comes from the *distributional reshaping*—the mathematical process of how the fine-tuning objective changes the model's probability mass across different ranks of tokens.

## Detailed Results and Trends

The performance improvements were particularly pronounced on harder problems. In benchmarks like LiveCodeBench, problems are categorized by difficulty: easy, medium, and hard. For the Qwen3-30B-Instruct model, while "easy" problems saw a 6.5 percentage point gain, "hard" problems saw a 15.3 percentage point gain.

![Figure 5: Detailed performance table showing pass@1 and pass@5 gains across different difficulty levels and model sizes.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01193v1/x3.png)

Furthermore, SSD significantly improved the "pass@5" score—a metric that measures if any of five independent samples for a problem is correct. This indicates that SSD is not just making the model more confident in its first guess, but is also improving the overall quality and diversity of its possible solutions.

The researchers also conducted a grid search to understand the interaction between training temperature ($T_{\text{train}}$) and evaluation temperature ($T_{\text{eval}}$). They found that performance is often governed by an "effective temperature" ($T_{\text{eff}} = T_{\text{train}} \cdot T_{\text{eval}}$). Without truncation, performance peaked around $T_{\text{eff}} \approx 1.2$. However, adding truncation (like top-k) during data synthesis pushed the performance ceiling even higher, showing that removing distractors from the training data is a key component of SSD's success.

## Theoretical Foundations

To validate the "precision-exploration conflict" theory, the authors used a controlled toy simulation using a Finite-State Machine (FSM). They created a world with distinct "fork" states and "lock" states and mathematically calculated success probabilities. The simulation confirmed that a base model is always stuck in a compromise, while a model trained via SSD can achieve higher success rates by allowing for higher evaluation temperatures without failing at the "locks."

Theoretical decomposition of the cross-entropy loss also showed that SSD performs two main actions:
1.  **Support Compression:** It pushes probability mass away from low-ranked distractor tokens toward a smaller set of high-ranked tokens.
2.  **Within-Support Reshaping:** It smooths the probabilities among the high-ranked tokens, preserving their relative diversity.

This dual action explains why the model becomes more robust. It clears the "noise" (the distractors) but keeps the "signal" (the viable alternatives).

## Significance and Future Impact

The introduction of Simple Self-Distillation represents a shift toward more resource-efficient model improvement. By proving that models can improve by simply "talking to themselves" and refining their internal distributions, the research opens several doors:

*   **Democratic Model Refinement:** Smaller organizations that lack massive clusters for RL or the resources for massive human-labeling campaigns can potentially use SSD to squeeze more performance out of existing open-weights models.
*   **Scale and Scope:** SSD can be applied to any prompt set, regardless of whether a ground-truth solution exists. This makes it highly scalable for niche domains where labeled data is scarce.
*   **Complementary Training:** SSD is not a replacement for RL or teacher-based distillation; instead, it is a complementary post-training step. It can be used as a final "polishing" phase to optimize how a model uses its learned knowledge during inference.

In conclusion, SSD demonstrates that the way a model chooses its next token is as important as the information it contains. By alleviating the fundamental conflict between needing precision and needing exploration, SSD allows LLMs to better navigate the complexities of code generation without requiring external guidance.

## Relevant Citations

- Distilling the Knowledge in a Neural Network: This is the seminal paper that introduced the concept of knowledge distillation. The main paper's method, simple self-distillation (SSD), is a form of distillation that learns from the model's own outputs, and the authors explicitly contrast their teacher-free approach with the classic paradigm established by Hinton et al.
- Competition-Level Code Generation with AlphaCode: The AlphaCode paper represents a major paradigm in synthetic data generation for code which relies on massive-scale sampling followed by execution-based verification. The current work repeatedly emphasizes that its SSD method is simple because it requires no verifier or execution, making AlphaCode a key point of contrast for the complexity of alternative approaches.
- STaR: Bootstrapping Reasoning With Reasoning: This paper introduces a key self-improvement method where a model is fine-tuned on its own correctly-solved problems. The current work explicitly contrasts SSD with STaR to highlight a critical difference: SSD trains directly on raw, unverified model outputs, whereas STaR requires a correctness filter, demonstrating the novelty and simplicity of the SSD approach.
- Forking Paths in Neural Text Generation: This citation provides the core terminology for the paper's mechanistic explanation of why SSD works. The authors' central hypothesis, the 'precision-exploration conflict,' is built on the distinction between 'locks' and 'forks' in generation, explicitly citing this paper for the concept of a 'fork,' making it fundamental to their analysis.
