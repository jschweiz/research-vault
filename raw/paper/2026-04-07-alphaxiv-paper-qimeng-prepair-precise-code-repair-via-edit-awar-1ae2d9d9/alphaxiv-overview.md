# QiMeng-PRepair: Precise Code Repair via Edit-Aware Reward Optimization

- alphaXiv: https://www.alphaxiv.org/abs/2604.05963
- Source paper: https://arxiv.org/abs/2604.05963

## The Challenge of Over-editing in Code Repair

Automated program repair (APR) has evolved significantly with the advent of Large Language Models (LLMs). These models can often identify and correct bugs in a wide range of programming languages, from Python to hardware description languages like Verilog. However, a persistent issue in LLM-based repair is "over-editing." When tasked with fixing a bug, many models do not just perform a surgical correction; instead, they rewrite large sections of the code, even those that were originally correct.

This behavior, while sometimes resulting in code that passes unit tests, presents several practical problems. Over-editing makes the code significantly harder for human developers to review, as the original logic and style are lost in the rewrite. It also obscures the location of the original bug, making it difficult to understand the root cause of the error. Furthermore, from a computational perspective, generating large amounts of new code is slower and less efficient than making targeted edits.

![Comparison of Over-editing vs Precise Repair](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05963v1/x3.png)
*Figure 1: A comparison between a vanilla LLM's tendency to over-edit code and the precise, targeted repair achieved by PRepair. Precise repair preserves the original structure while fixing only the faulty components.*

The research introduces **PRepair**, a framework designed to achieve "precise repair." The goal is to maximize the reuse of the original, correct logic while performing minimal, targeted fixes only on the erroneous parts. This approach aims to align model behavior with human development practices, where surgical fixes are preferred over complete rewrites for the sake of maintainability and clarity.

## Quantifying Precision: The Edit Cost and $fix_p@k$ Metric

To address over-editing, it is first necessary to quantify it. The researchers model code as a sequence of lines and define the **Edit Cost** ($D_{EC}$) as the Levenshtein distance between the buggy code and the corrected code, normalized by the number of lines in the source program.

If we represent the buggy code as $X$ and the corrected version as $Y$, the normalized edit cost is defined as:

$$D_{EC}(X, Y) = \frac{\text{Levenshtein}(X, Y)}{\max(1, \text{Lines}(X))}$$

Standard metrics like $pass@k$ only measure whether a model's output passes unit tests. To measure precision, the paper introduces a new metric called $fix_p@k$. This metric considers a repair successful only if it is both functionally correct and falls within an acceptable edit budget. Specifically, a repair is considered "fixed" if it passes all tests and its edit cost relative to the "golden" (ideal) fix is within a factor $p$.

The indicator function for a precise fix for a candidate $Y'$ is:

$$fix_p(X, Y, Y') = \mathbb{I}(\text{pass tests}) \wedge \mathbb{I}\left(\frac{D_{EC}(X, Y')}{D_{EC}(X, Y)} \leq p\right)$$

The overall $fix_p@k$ score is then calculated by sampling $n$ candidates and determining the probability that at least one of the $k$ selected samples is both correct and precise:

$$fix_p@k = 1 - \frac{\binom{n-m}{k}}{\binom{n}{k}}$$

where $m$ is the number of candidates that satisfy the precision criteria. This metric forces models to compete not just on accuracy, but on the efficiency and minimalism of their solutions.

## The PRepair Framework: Self-Breaking and Data Diversity

One major hurdle in training models for precise repair is the scarcity of high-quality data. Most existing code repair datasets contain pairs of buggy and fixed code, but the bugs are often artificial or the fixes involve excessive changes. PRepair addresses this through a two-stage process: **Self-Breaking** and **Self-Repairing**.

### Self-Breaking for Data Generation
In the Self-Breaking stage, an LLM is used to generate its own training data. Given a correct "golden" program and its description, the model is prompted to inject realistic bugs into the code. This ensures the resulting buggy code is fundamentally similar to the correct version, retaining most of the original logic.

To prevent the model from generating repetitive or trivial bugs, the framework employs a **Min-Max Sampling** strategy. When the model generates multiple buggy versions of a program, the framework selects a subset that maximizes the diversity between them. This is achieved by minimizing the maximum pairwise similarity between sampled buggy programs, where similarity is defined as $1 - D_{EC}(X_i, X_j)$. This diversity is crucial for teaching the model to recognize and fix a wide variety of bug patterns.

![PRepair Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05963v1/x4.png)
*Figure 2: The two-stage PRepair framework. First, the Self-Breaking stage generates diverse buggy code. Second, the Self-Repairing stage uses EA-GRPO to train the model with an edit-aware reward system.*

## Edit-Aware Group Relative Policy Optimization (EA-GRPO)

The core of PRepair's training is **Edit-Aware Group Relative Policy Optimization (EA-GRPO)**. This is an extension of Group Relative Policy Optimization (GRPO), a reinforcement learning algorithm that optimizes models based on the relative performance of a group of generated samples.

Standard GRPO for code repair typically uses a binary reward: 1 if the code passes tests, and 0 otherwise. However, this often encourages over-editing because the model learns that more extensive rewrites are a "safer" way to pass the tests. EA-GRPO introduces a **Dynamic Edit-Aware Reward Shaping** mechanism to counteract this.

### Group Accuracy Threshold
To ensure the model doesn't prioritize minimal edits at the expense of actually fixing the bug, EA-GRPO uses a group accuracy threshold $\alpha$. The edit penalty is only activated for a group of samples if their average accuracy $Acc_G$ exceeds $\alpha$:

$$Acc_G = \frac{1}{m} \sum_{i=1}^m \mathbb{I}(Y'_i \text{ is correct})$$

If the group is struggling to find any correct solution, the model is encouraged to focus purely on correctness. Once the model becomes "confident" enough to generate correct solutions regularly, the edit penalty kicks in to refine those solutions.

### The Edit Penalty
For correct samples in high-accuracy groups, a standardized edit penalty $P_G$ is calculated. This penalty compares the edit cost of a specific sample $Y'_i$ to the average edit cost of other correct samples in the same group:

$$P_G(Y'_i) = \text{Sigmoid}\left(\frac{D_{EC}(X, Y'_i) - \text{mean}(D_{EC}^c)}{\text{std}(D_{EC}^c) + \epsilon}\right)$$

where $D_{EC}^c$ represents the edit costs of the correct samples in the group, and $\epsilon$ is a small constant for stability. This relative penalty ensures the model is always pushing to be more efficient than its own average performance. The final reward $R_G$ is scaled by a coefficient $\beta$:

$$R_G(Y'_i) = 1 - \beta \cdot P_G(Y'_i)$$

This reward structure allows the model to learn bug localization implicitly. To minimize edits while maintaining correctness, the model must learn exactly which lines are faulty and leave the rest untouched.

## Improving Inference with Speculative Edits

The benefits of precise repair extend beyond code quality to inference speed. PRepair integrates with **speculative decoding** (specifically Prompt Lookup Decoding) to accelerate code generation. 

Speculative decoding works by using a fast "drafting" mechanism to predict the next few tokens, which are then verified by the larger model in parallel. In the context of code repair, the buggy input code itself can serve as a draft. If the repair is precise (i.e., it reuses most of the input code), the acceptance rate of these draft tokens increases significantly. 

The research demonstrates a direct mathematical link: as the edit cost $D_{EC}$ decreases, the acceptance rate of draft tokens grows, leading to a non-linear increase in decoding throughput. Experiments showed that PRepair models achieved up to 15% faster inference compared to standard models, while models trained with naive GRPO (which over-edit) saw throughput drops of up to 35% because their drafts were constantly rejected.

![Inference Throughput and Acceptance Rate](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05963v1/x8.png)
*Figure 3: PRepair significantly increases the acceptance rate of draft tokens during speculative decoding, leading to higher throughput in tokens per second across both Verilog and Python.*

## Experimental Results and Generalization

The PRepair framework was evaluated on both general-purpose programming (Python) and specialized hardware description languages (Verilog). The results showed consistent improvements across several dimensions:

1.  **Precision Gains:** On the Python HumanEval-Fix benchmark, PRepair increased the $fix_1@1$ metric (which requires a perfect match in edit cost) by over 20% compared to base models. In Verilog, the improvement was even more pronounced, reaching 31%.
2.  **Maintaining Correctness:** Unlike simple prompt engineering, which often trades off accuracy for brevity, EA-GRPO maintained or slightly improved the overall $pass@k$ rates. This suggests that teaching the model to be precise actually helps it understand the code structure better.
3.  **Cross-Domain Robustness:** One of the most striking findings was PRepair's ability to generalize. Models trained on Python and then evaluated on Verilog (and vice-versa) maintained high precision. In contrast, models trained with naive GRPO showed a significant drop in performance when moved to a new domain, often reverting to extreme over-editing.
4.  **Implicit Localization:** Analysis of the model's attention maps revealed that PRepair-trained models focus more intently on the specific buggy lines during generation, whereas standard models distribute their attention more broadly, leading to unnecessary changes.

![Performance Comparison across Domains](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05963v1/x7.png)
*Figure 4: Comparing in-domain and cross-domain code repair performance. EA-GRPO (red) consistently outperforms naive GRPO (blue) in both correctness and precision, especially when generalizing to new programming languages.*

## Conclusion

The QiMeng-PRepair framework demonstrates that "more editing" does not equal "better repair." By introducing edit-awareness into the reinforcement learning loop and creating a high-quality synthetic dataset through Self-Breaking, PRepair produces models that are surgical, efficient, and developer-friendly. 

The introduction of the $fix_p@k$ metric provides a necessary benchmark for evaluating the real-world utility of coding assistants. As LLMs become more integrated into software development pipelines, the ability to perform precise, minimal modifications will be essential for maintaining codebases that remain readable, maintainable, and efficient to generate. PRepair offers a robust path forward for achieving this balance between functional correctness and structural integrity.

## Relevant Citations

- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper introduces Group Relative Policy Optimization (GRPO), the reinforcement learning algorithm that serves as the foundation for the PRepair framework. The main paper's core method, Edit-Aware GRPO (EA-GRPO), is a direct modification of GRPO designed to penalize excessive edits.
- Octopack: Instruction tuning code large language models: This work is central to the paper as it introduces the HumanEval-Fix benchmark, one of the key datasets used for evaluation. It also represents a primary example of prior methods that optimize for correctness alone, which the PRepair paper identifies as a cause of the 'over-editing' problem it aims to solve.
- Evaluating large language models trained on code: This paper is foundational to the evaluation methodology, as it introduced the pass@k metric. The main paper uses pass@k to measure repair correctness and proposes its own novel metric, fix_p@k, which extends the concept of pass@k to jointly consider correctness and edit cost.
- Leetcodedataset: A temporal dataset for robust evaluation and efficient training of code llms: This citation is important as it provides the dataset of Python programming tasks used in the 'Self-Breaking' stage to generate the training data. The effectiveness of the PRepair framework for Python repair is directly dependent on the quality and nature of this source dataset.
