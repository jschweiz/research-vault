# Vero: An Open RL Recipe for General Visual Reasoning

- alphaXiv: https://www.alphaxiv.org/abs/2604.04917
- Source paper: https://arxiv.org/abs/2604.04917

## Transparency in Visual Reasoning

The advancement of Vision-Language Models (VLMs) has shifted from simple image tagging to complex reasoning. Modern models are increasingly expected to interpret scientific diagrams, solve spatial puzzles, and navigate user interfaces. Reinforcement Learning (RL) has become a primary driver for these capabilities, allowing models to refine their logic by learning from the rewards associated with their own generated responses. However, as the performance of these models improves, the transparency regarding their training often decreases.

Many state-of-the-art visual reasoners rely on proprietary RL pipelines. These pipelines utilize non-public datasets, undisclosed reward structures, and complex multi-stage training procedures that are difficult for the broader research community to replicate or study systematically. This lack of openness makes it challenging to understand why a model succeeds or fails, or how specific training data affects its reasoning behavior.

![Vero Performance Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v2/x1.png)
*Figure 1: An overview of the Vero project, showcasing the Vero-600K dataset, the VeroEval suite, and the significant performance improvements achieved by the RL recipe across various model families.*

Vero addresses this gap by providing a fully open RL recipe for general visual reasoning. By releasing the model weights, the training code, and a massive curated dataset (Vero-600K), this work establishes a transparent foundation for developing and evaluating multimodal reasoners. The central finding is that broad visual understanding can be achieved through a single-stage RL process that emphasizes data diversity and flexible, task-specific reward functions.

## Curating a Diverse Knowledge Base: Vero-600K

A significant challenge in training generalist visual reasoners is the heterogeneity of visual tasks. A model needs to excel at numeric calculations in STEM images while simultaneously maintaining the ability to describe scenes or follow complex spatial instructions. To facilitate this, the researchers developed Vero-600K, a dataset of 600,000 samples derived from 59 distinct sources.

![Vero-600K Dataset Composition](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v2/x2.png)
*Figure 2: The distribution of the Vero-600K dataset across six core task categories, highlighting the diversity of the 59 datasets included.*

The dataset is organized into six broad categories:
1.  **STEM**: Covers mathematical diagrams, scientific figures, and medical imagery where answers are often numeric or symbolic.
2.  **Spatial & Action**: Focuses on 3D spatial understanding, robotic action sequences, and UI navigation.
3.  **Knowledge & Recognition**: Combines visual recognition with external commonsense or factual knowledge.
4.  **Chart & OCR**: Involves extracting and reasoning over data in documents, tables, and infographics.
5.  **Grounding, Counting & Search**: Requires the model to localize objects using bounding boxes or provide precise counts.
6.  **Captioning & Instruction Following**: Evaluates the model's ability to provide open-ended descriptions and adhere to formatting constraints.

The curation process was meticulous. Starting with over 250 candidate datasets, the authors applied a multi-stage filtering pipeline. First, heuristic selection removed small or low-resolution datasets. Second, manual quality control ensured that at least 95% of the samples were correct and unambiguous. Finally, an automated filtering stage used high-capacity models to remove questions that were irrelevant to the image or unverifiable. This rigorous process ensures that the model learns from high-quality signal rather than noise or ambiguous labels.

![Task Category Samples](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v2/x4.png)
*Figure 3: Examples of the diverse visual reasoning tasks contained within the Vero-600K dataset, spanning from chart analysis to spatial robotics.*

## The Reinforcement Learning Recipe

The Vero models are trained using a structured response format designed to encourage chain-of-thought (CoT) reasoning. Each response consists of a reasoning trace enclosed in `<think>...</think>` tags, followed by a final answer in `<answer>...</answer>` tags. For objective questions, the answer is further structured using `\boxed{}` notation.

The RL training aims to maximize the expected reward $R(a, y^*)$ for a generated answer $a$ given a ground-truth $y^*$, a visual input $v$, and a text query $q$. The model learns a policy $\pi_{\theta}$ to generate a response $y = (z, a)$, where $z$ represents the thinking process and $a$ is the final answer.

The core algorithm used is Group Relative Policy Optimization (GRPO), with a specific enhancement called GSPO (Group Sequence Policy Optimization). Unlike standard RL methods that calculate rewards at every single step, GSPO uses sequence-level ratios to stabilize training across diverse tasks. This helps prevent the model from becoming overly sensitive to the high variance of rewards in a multi-task environment.

The total reward is calculated using a weighted combination of accuracy, formatting, and length penalties:

$$R(y, y^*) = (1 - \alpha) R_{\text{acc}}(y, y^*) + \alpha R_{\text{fmt}}(y) + R_{\text{overlong}}(y)$$

In this equation, $\alpha = 0.2$ balances formatting and accuracy. The $R_{\text{overlong}}(y)$ term acts as a soft penalty to prevent the model from generating unnecessarily long reasoning traces that consume excessive computation without improving accuracy. The formatting reward $R_{\text{fmt}}(y)$ ensures the model adheres to the structured tags, which is critical for parsing the results during automated evaluation.

## Task-Routed Reward Functions

One of the most innovative aspects of Vero is its approach to rewards. In traditional RL for LLMs (like mathematical reasoning), a single reward function (e.g., a math verifier) is often sufficient. However, for a generalist VLM, a "one-size-fits-all" reward is inadequate. How do you score a bounding box using the same logic as a scientific calculation or a creative image caption?

Vero solves this through **task-routed rewards**. The system automatically identifies the type of task and routes the model's response to one of ten specialized reward functions:

*   **Binary Rewards**: Used for string matching and multiple-choice questions.
*   **Numeric Rewards**: Employs a math verifier with a tolerance for different decimal or symbolic formats.
*   **Grounding Rewards**: Uses Hungarian matching to compare predicted bounding boxes with ground truth, scoring based on Intersection over Union (IoU).
*   **Web Action Rewards**: Checks for matches in structured JSON fields for UI navigation tasks.
*   **Instruction Following**: Scores the response based on whether it satisfied specific constraints (e.g., word count, forbidden words).
*   **LLM-as-judge**: For open-ended captioning, a high-capacity model scores the response on a $1 \to 10$ scale against a reference, following strict guidelines to prevent "reward hacking" (where the model learns to please the judge without actually being correct).

![Overview of Reward Types](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v2/x5.png)
*Figure 4: The task-routed reward system, demonstrating how different evaluation logic is applied to different task types, such as grounding, ordering, or open-ended descriptions.*

## Performance and Generalization

To evaluate the effectiveness of this recipe, the authors created **VeroEval**, a suite of 30 benchmarks. The results show that the Vero training recipe consistently improves performance across different base models, including Qwen2.5 and Qwen3.

A key finding was the impact of **data mixtures**. The researchers tested whether it is better to weight tasks by their difficulty, the length of their reasoning, or their image resolution. Surprisingly, a simple **uniform mixture**—where all task categories are sampled equally—performed the best. This suggests that for general visual reasoning, balanced exposure to different skill sets is more important than specialized weighting.

![Data Mixture and Transfer Matrix](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v2/x10.png)
*Figure 5: The transfer matrix shows that training on only one category (e.g., Chart & OCR) often leads to performance drops in others (e.g., Grounding). The "Mix Full" strategy at the far right eliminates this negative transfer, achieving gains across all categories.*

The ablation studies also highlighted a phenomenon of "negative transfer." When models were trained exclusively on one domain, such as captioning, their performance on other domains like spatial reasoning often collapsed. By mixing all tasks together during a single RL stage, Vero avoids this collapse and allows the model to develop a more robust, versatile reasoning capability.

## Analyzing the "Thinking" Process

By looking inside the `<think>` tags, the researchers discovered that different visual tasks elicit distinct "cognitive styles." Visual reasoning is not a monolithic process; rather, the model adapts its internal logic to the requirements of the task.

For instance, STEM and Chart tasks typically generate much longer reasoning traces than Knowledge or Recognition tasks. In STEM problems, the model frequently engages in "backtracking"—re-evaluating its previous steps when a contradiction is found. In contrast, Grounding tasks (finding objects) lead to reasoning traces focused on "visual search" and spatial coordinate mapping, with very little backtracking.

![Reasoning Word Lengths](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v2/x11.png)
*Figure 6: The average number of reasoning words generated by the model varies significantly by category, with Spatial and STEM tasks requiring much more internal "thought" than simple recognition.*

These findings suggest that "visual thinking" is highly contextual. A generalist model doesn't just learn more facts; it learns how to change its thinking strategy based on the image it sees. By providing an open recipe, Vero allows researchers to study these emergent behaviors in detail, moving beyond simple accuracy scores to a deeper understanding of how AI "perceives" and "reasons."

## Conclusion

Vero represents a significant step toward making advanced multimodal RL more accessible and scientifically rigorous. By combining a massive, high-quality dataset (Vero-600K) with a flexible, task-routed reward system, the authors demonstrate that it is possible to train general-purpose visual reasoners without relying on proprietary secrets.

The work underscores that the "recipe" for high-performance VLMs depends heavily on data diversity and the ability to reward a wide variety of behaviors—from the precision of a bounding box to the logical coherence of a scientific proof. As the field moves toward more autonomous and capable agents, open efforts like Vero provide the transparency needed to ensure these models are not just powerful, but also understood.

## Relevant Citations

- Group sequence policy optimization: Vero's reinforcement learning (RL) algorithm is directly built upon Group Sequence Policy Optimization (GSPO), which is central to the paper's methodology. The authors state they integrate advances from GSPO and their ablations confirm its effectiveness over other RL algorithms for their multi-task setting.
- Openmmreasoner: Pushing the frontiers for multimodal reasoning with an open and general recipe: This paper is cited as a key example of prior fully open reinforcement learning efforts for VLMs. The Vero authors contrast their work with OpenMMReasoner's narrow focus on visual math to motivate their own contribution of a broad, multi-domain RL recipe for general visual reasoning.
- VL-Rethinker: Incentivizing self-reflection of vision-language models with reinforcement learning: VL-Rethinker is another important, fully open RL-trained VLM that the paper compares against, both in performance tables and training curves. It helps establish the landscape of existing open recipes and serves as a benchmark to demonstrate the superior generalization of Vero's multi-task approach.
- Qwen3-vl technical report: The Qwen3-VL models are the primary base models that Vero is built upon and evaluated against. This citation is crucial for understanding the starting point of the Vero models and for contextualizing the significant performance gains achieved through the paper's open RL recipe.
