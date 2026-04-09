# Can Large Language Models Reinvent Foundational Algorithms?

- alphaXiv: https://www.alphaxiv.org/abs/2604.05716
- Source paper: https://arxiv.org/abs/2604.05716

The question of whether Large Language Models (LLMs) can generate truly foundational scientific discoveries or if they are primarily sophisticated retrieval engines remains a central debate in artificial intelligence. While LLMs have demonstrated the ability to optimize existing code or solve competitive programming problems, these successes often draw upon a vast training corpus that already contains the solutions. To determine if a model can "invent" a concept rather than just "remember" it, researchers have introduced a methodology known as the "Unlearn-and-Reinvent" pipeline.

This approach involves two distinct steps: first, the model is subjected to a targeted unlearning process to remove specific algorithmic knowledge. Second, the model is tasked with solving a problem that necessitates the reinvention of that forgotten algorithm. By removing the model's access to the "answer key" provided during pre-training, researchers can more accurately assess its intrinsic capacity for algorithmic reasoning and innovation.

![Figure 1: Overview of the Unlearn-and-Reinvent pipeline, illustrating the transition from a model containing algorithmic knowledge to one that must reconstruct it through iterative reasoning and feedback.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05716v1/x1.png)

## The Unlearning Phase: Removing Specific Knowledge

To ensure that the reinvention process is authentic, the pipeline begins by purging the model of ten foundational algorithms: Dijkstra, Floyd-Warshall, Bellman-Ford, Prim, Euclidean, KMP, Manacher, Moore Vote, Gray, and Strassen. This is not a simple deletion but a complex fine-tuning process designed to break the associations between problem descriptions and their corresponding algorithmic solutions.

The researchers employed a Group Relative Policy Optimization (GRPO)-based unlearning method. This technique optimizes the model to forget specific information while preserving its general utility on unrelated tasks. The unlearning objective balances three components:
1.  **Forgetting:** Increasing the loss on a "forget set" $D_{\text{forget}}$, which contains queries about the target algorithms.
2.  **Utility Preservation:** Minimizing the divergence from the original model's behavior on a "retain set" $D_{\text{retain}}$ of general knowledge.
3.  **Reward Function:** An LLM-as-a-judge evaluates the model's responses during unlearning. A reward is granted only if the response contains no target knowledge ($k_j = 0$), does not corrupt the algorithm's name ($c_j = 0$), and remains readable ($u_j = 1$).

To prevent the model from generating gibberish or simply refusing to answer any questions, a "cold start" stage is used. In this stage, the model is fine-tuned on an initialization set $D_{\text{init}}$ that pairs algorithm-related queries with polite refusals or alternative (non-target) explanations. This guides the model toward a state where it "knows" it should not provide the specific algorithm without losing its ability to communicate effectively.

## The Reinvention Challenge: Discovery Through Interaction

Once the model has successfully "forgotten" the target algorithms—verified by a near-100% forgetting rate on multiple-choice and open-ended probes—it enters the reinvention phase. In this phase, the model is presented with a programming task described in natural language without using the name of the algorithm. For instance, instead of being asked to "implement Dijkstra's algorithm," the model is asked to "invent a single-source shortest path algorithm for non-negative graphs with a time complexity of $O(N^2)$."

The reinvention environment is interactive, consisting of:
*   **The Problem Instance:** Defined by a prompt $I_g$, a test suite $T_g$, and specific resource constraints like runtime $\tau_g$ and memory $\mu_g$.
*   **A Python Interpreter:** The model generates code and receives immediate execution results.
*   **A Generative Verifier:** When a submission fails (e.g., due to a timeout or incorrect output), the model generates its own diagnostic feedback to guide its next attempt.

The difficulty of the task is modulated using three hint levels. Level 0 (No Hint) provides only the task description. Level 1 provides a high-level conceptual hint, such as suggesting a "greedy approach." Level 2 provides a detailed, step-by-step natural language explanation of the algorithm's logic.

![Figure 2: Example of the interactive reinvention process for the single-source shortest path problem. The model iterates through multiple rounds of coding and receives feedback from the verifier until it either succeeds or reaches the round limit.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05716v1/x2.png)

## Findings on Algorithmic Reinvention

The study found that LLMs, particularly those optimized for reasoning like Qwen3-4B-Thinking-2507, are indeed capable of reinventing several foundational algorithms. Without any hints, the strongest models achieved a Reinvention Success Rate (RSR) of 21.8% across the ten algorithms. 

However, success varied significantly depending on the nature of the algorithm. Algorithms that could be reached through intuitive leaps or incremental improvements were more likely to be reinvented. For example:
*   **Euclidean Algorithm and Gray Code:** These were frequently reinvented without hints because their problem constraints strongly guide the search space toward the correct solution.
*   **Dijkstra and Prim:** These often required at least a high-level hint to steer the model away from less efficient approaches like Bellman-Ford.
*   **KMP and Strassen:** These remained extremely difficult. Algorithms requiring non-obvious data structures (like the prefix function in KMP) or counterintuitive mathematical transformations (like the specific sub-matrix multiplications in Strassen) were rarely reinvented without significant external guidance.

The presence of hints dramatically improved performance. With step-by-step hints (Level 2), the RSR for the strongest model jumped to 80.9%, demonstrating that the models could effectively translate natural language logic into functional code even for algorithms they had previously "forgotten."

## The "Thought Collapse" Phenomenon and the Role of Verifiers

A critical discovery during the reinvention phase was the phenomenon of "thought collapse." In interactive settings without external feedback, models often showed a progressive decline in the length and quality of their reasoning. As the number of rounds increased, the models generated fewer and fewer "thinking" tokens, eventually stagnating or producing repetitive, low-effort solutions.

![Figure 4: Illustration of thought collapse, where the number of output tokens decreases significantly over multiple rounds of interaction.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05716v1/x4.png)

To combat this, the researchers utilized a generative verifier. This verifier acts as a self-critique mechanism, where the model analyzes why its previous code failed (e.g., "the complexity is $O(N^3)$ because of the nested loop, but the requirement is $O(N^2)$") and suggests specific improvements. The inclusion of this feedback loop was found to be essential for maintaining exploration.

![Figure 5: The impact of different verifiers on output length. The presence of a verifier (self or oracle) significantly mitigates the collapse of reasoning tokens compared to a scenario with no verifier.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05716v1/x5.png)

By providing diagnostic feedback, the verifier allowed the model to maintain a consistent "thought volume" across dozens of rounds. This sustained exploration was often the difference between success and failure for more complex tasks like Dijkstra's algorithm.

## Pushing the Frontier with Test-Time RL

For the most difficult algorithms where the initial success rate was zero, the researchers applied test-time reinforcement learning (RL). Unlike traditional training, test-time RL optimizes the model on a specific problem during the inference phase. The model is rewarded based on the correctness and efficiency of its generated code, with a reward signal defined as $1/T$ for correct solutions, where $T$ is the execution time.

This approach proved particularly effective for Strassen's matrix multiplication algorithm. While the unlearned model initially failed to produce a correct implementation even with Level 2 hints, test-time RL allowed it to refine its search until it achieved a 62.5% success rate. This suggests that even when a model cannot immediately "reason" its way to a foundational discovery, the combination of guided exploration and performance-based rewards can push it across the finish line.

![Figure 6: Reward curves during test-time reinforcement learning for difficult algorithms. The star indicates a successful reinvention of Strassen's algorithm after several steps of optimization.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05716v1/x6.png)

## Implications for AI-Driven Research

The "Unlearn-and-Reinvent" methodology provides a rigorous framework for distinguishing between an LLM's ability to recall information and its ability to innovate. The results suggest that while current LLMs possess a genuine capacity for algorithmic invention, they are bounded by the complexity of the "conceptual leap" required. 

Algorithms that require highly specific, non-intuitive invariants remain at the edge of current capabilities. However, the study also highlights that interactive environments, self-verification, and inference-time optimization are powerful tools that can extend the reach of these models. This research lays the groundwork for future AI systems that might not only reinvent known foundational algorithms but eventually discover entirely new ones that have yet to be conceived by human researchers.

## Relevant Citations

- Mathematical discoveries from program search with large language models: This paper, which introduces the FunSearch system, is cited in the introduction to establish the state-of-the-art in using LLMs for algorithmic discovery. It provides the essential context and motivation for the main paper's central question of whether LLMs can produce foundational discoveries rather than just incremental improvements.
- Towards making systems forget with machine unlearning: This is a foundational citation for the concept of "machine unlearning," which is the core technique enabling the paper's 'Unlearn-and-Reinvent' pipeline. The entire experimental methodology is predicated on the ability to make a model forget specific knowledge, a concept pioneered by this work.
- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper is cited as the source for Group Relative Policy Optimization (GRPO), the specific on-policy unlearning method adopted by the authors. This citation is crucial as the paper's methodology section is built around this GRPO-based approach, which they find to be highly effective for their experiments.
- Generative verifiers: Reward modeling as next-token prediction: This work is cited for the "generative verifier," a key component of the paper's reinvention phase. The authors dedicate a significant ablation study to demonstrate that this verifier plays a critical role in preventing "thought collapse" and sustaining the model's reasoning, making it central to their findings and conclusions.
