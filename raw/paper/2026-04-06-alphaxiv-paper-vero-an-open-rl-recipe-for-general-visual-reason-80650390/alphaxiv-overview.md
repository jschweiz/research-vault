# Vero: An Open RL Recipe for General Visual Reasoning

- alphaXiv: https://www.alphaxiv.org/abs/2604.04917
- Source paper: https://arxiv.org/abs/2604.04917

The field of Vision-Language Models (VLMs) has seen substantial progress, with models like Qwen-VL and GPT-4V demonstrating advanced reasoning capabilities across a wide range of visual tasks. While earlier models primarily relied on supervised fine-tuning (SFT) on massive datasets of paired images and text, the most performant recent models have increasingly adopted reinforcement learning (RL) to refine their reasoning processes. These models use techniques such as chain-of-thought (CoT) to "think" through a problem before arriving at an answer, using RL to optimize for correctness and reasoning quality.

However, the state-of-the-art in VLM reasoning is often obscured by proprietary development pipelines. Many frontier models are trained using non-public datasets and undisclosed reward mechanisms, making it difficult for the research community to understand which design choices truly drive performance. Conversely, many existing open-source RL efforts focus on narrow domains like mathematical reasoning, which often fails to generalize to broader visual tasks such as spatial understanding or chart interpretation.

Vero, an initiative from researchers at Princeton University, addresses this gap by providing a fully open RL recipe for general visual reasoning. By releasing the training data, reward code, and model weights, the project aims to establish a transparent framework for building versatile visual reasoners.

![Vero Performance Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v1/x1.png)
*Figure 1: Vero demonstrates improvements across a broad spectrum of visual reasoning tasks, outperforming existing open-weight models and matching proprietary training recipes through its multi-task RL pipeline.*

## Vero-600K: A Diverse Foundation for Visual RL

A primary finding of the Vero project is that training on a single domain—such as visual mathematics—does not reliably improve a model's performance on other visual tasks. In fact, narrow specialization often results in "negative transfer," where the model's performance on general tasks degrades as it over-optimizes for a specific reasoning style.

To solve this, the researchers constructed Vero-600K, a diverse dataset containing 600,000 samples across six core categories:
1.  **STEM:** Reasoning over scientific diagrams, mathematical figures, and medical images.
2.  **Spatial & Action:** Understanding 3D configurations, UI navigation, and planning sequences of actions.
3.  **Knowledge & Recognition:** Combining visual recognition with external knowledge to answer complex queries.
4.  **Chart & OCR:** Extracting and analyzing structured information from charts, tables, and documents.
5.  **Grounding, Counting & Search:** Localizing specific objects, performing visual search, and accurately counting items.
6.  **Captioning & Instruction Following:** Describing images in detail and adhering to specific stylistic or structural instructions.

The dataset was curated from over 250 candidate sources through a rigorous pipeline. Heuristic filtering removed low-resolution images and binary questions (where a model might guess the answer with 50% accuracy). Manual inspection ensured that the remaining samples were unambiguous and verifiable. Finally, large language models (LLMs) were used to normalize ground-truth answers and filter out questions that were irrelevant to the image or poorly phrased.

![Vero-600K Data Distribution](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v1/x2.png)
*Figure 2: The Vero-600K dataset is balanced across six major task categories, ensuring that the model develops a broad repertoire of visual reasoning skills rather than specializing in a single domain.*

## The Reinforcement Learning Recipe

Vero utilizes a single-stage RL pipeline based on Group Relative Policy Optimization (GRPO), which is particularly effective for training models to reason because it allows for comparing multiple outputs for the same prompt. The researchers further refined this into Group Sequence Policy Optimization (GSPO), which stabilizes training by using sequence-level ratios rather than per-token ratios.

The core of the Vero recipe is its "task-routed" reward system. Because visual reasoning tasks are highly heterogeneous, a single reward function (like simple string matching) is insufficient. Vero employs ten distinct reward functions tailored to specific task requirements:
- **String Match and Multiple Choice:** For standard discrete answers.
- **Numeric Verification:** For math and STEM tasks, accounting for precision and formatting.
- **Grounding & Pointing:** Using Intersection over Union (IoU) or distance-based metrics to reward accurate spatial localization.
- **Web Action:** Rewarding the correct sequence of clicks and interactions for UI tasks.
- **LLM-as-Judge:** For open-ended tasks like captioning, a separate judge model (Qwen3-32B) scores responses on a scale from 1 to 10 based on detail, accuracy, and helpfulness.

The total reward $R(y, y^*)$ for a generated response $y$ given the ground truth $y^*$ is calculated as:
$$
R(y, y^*) = R_{\text{acc}}(y, y^*) + R_{\text{fmt}}(y) + R_{\text{overlong}}(y)
$$
where $R_{\text{acc}}$ is the accuracy reward from the task-routed functions, $R_{\text{fmt}}$ penalizes format errors (such as missing the `<think>` or `<answer>` tags), and $R_{\text{overlong}}$ prevents the model from generating unnecessarily long responses.

![Vero Reward Types](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v1/x5.png)
*Figure 3: Overview of the different reward types used in Vero, ranging from programmatic checks for grounding and numbers to LLM-based evaluation for open-ended chat.*

## Performance Across the Visual Reasoning Spectrum

The Vero recipe was applied to several base models, including Qwen3-VL and MiMo-VL. The resulting models, Vero-Qwen3T-8B and Vero-Qwen3I-8B, set a new standard for open 8B-parameter visual reasoners. They achieved consistent improvements across all 30 benchmarks in the VeroEval suite, with notable gains in spatial reasoning and chart analysis.

One significant finding is that Vero training outperformed proprietary RL recipes. For instance, when the Vero recipe was applied to the MiMo-VL base model, it outperformed the official "RL" version of MiMo-VL (trained by the original developers using proprietary data) on several categories, including STEM and Knowledge & Recognition. This demonstrates that a carefully curated open dataset and a multi-route reward system can match or exceed the performance of closed-source pipelines.

![Training Curves](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v1/x6.png)
*Figure 4: RL training curves showing consistent performance gains across all six task categories compared to prior open RL efforts.*

A key challenge in multi-task RL is maintaining "visual chat" ability. Models trained solely on structured tasks (like math or counting) often become unhelpful in open-ended conversation, providing short, robotic answers. By including the "Captioning & Instruction Following" category and using an LLM-as-judge with strict anti-hacking guidelines, Vero models maintain high-quality conversational abilities while simultaneously improving their structured reasoning performance.

## Cognitive Profiles and the Mechanics of Thought

Because Vero models use a thinking-based approach, researchers could analyze the "thinking traces" generated before the final answer. This analysis revealed that the models adapt their cognitive strategies based on the task.

For example, when solving STEM problems, the models exhibit a high degree of "backtracking" and "reflective verification"—checking their work as they proceed through a multi-step calculation. In contrast, for grounding and search tasks, the thinking traces show a pattern of "directed visual search" and "spatial organization," where the model systematically scans regions of the image to find the target object.

The researchers also extracted specific skills from these traces, such as "apply triangle angle sum" or "identify nutrient sources." A classification model could accurately predict the task category simply by looking at the thinking trace, confirming that the RL process cultivates a diverse and domain-specific skill repertoire.

![Reasoning Lengths](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04917v1/x8.png)
*Figure 5: Different task categories elicit different reasoning behaviors. Spatial and chart tasks typically require significantly longer thinking processes than simple recognition tasks.*

## Ablations and Design Choices

The Vero paper provides several critical insights through ablation studies:
- **RL vs. SFT:** While SFT on the Vero-600K dataset improves performance, RL provides much more substantial and uniform gains across all tasks. RL allows the model to explore different reasoning paths and learn which ones lead to the correct answer, which is more effective than simply mimicking a single demonstration.
- **Task-Routed Rewards:** Using task-specific rewards is essential. A model trained with a unified "one-size-fits-all" reward function (like standard math verification) performed significantly worse, particularly on open-ended tasks and grounding.
- **Data Mixture:** A uniform mixture of all task categories was found to be the most robust. Over-weighting "difficult" tasks (where the base model has low accuracy) often led to instability, as the model struggled to find high-reward samples to learn from.

## Conclusion

Vero demonstrates that general visual reasoning can be effectively improved through a single-stage reinforcement learning pipeline using entirely open resources. By moving beyond narrow specialization and embracing a diverse, multi-task approach with task-specific rewards, the researchers have created a recipe that empowers the broader AI community to build and study advanced multimodal reasoners. The project highlights that performance in modern VLMs is driven as much by the structure of the training distribution and the precision of the reward signals as it is by the underlying architecture. By open-sourcing these components, Vero provides a foundation for more transparent and collaborative research in the next generation of visual-language understanding.

## Relevant Citations

- Group sequence policy optimization: This paper introduces Group Sequence Policy Optimization (GSPO), the core reinforcement learning algorithm used to train Vero. The main paper explicitly states its method integrates advances from GSPO and includes an ablation study showing that GSPO outperforms other RL algorithms like GRPO, making it a foundational component of the Vero recipe.
- Qwen3-vl technical report: This report details the Qwen3-VL models, which serve as the primary base models for training Vero. The main performance claims of the Vero paper are centered on significantly improving over the Qwen3-VL-Instruct and outperforming the Qwen3-VL-Thinking variants, making this a crucial reference for understanding the starting point and key comparison.
- Openmmreasoner: Pushing the frontiers for multimodal reasoning with an open and general recipe: This work is a key example of a prior fully open RL recipe for VLMs, but with a narrow focus on visual math. The Vero paper repeatedly contrasts its own broad, multi-domain approach with the specialized scope of OpenMMReasoner to highlight its main contribution of achieving general visual reasoning across diverse tasks.
- VL-Rethinker: Incentivizing self-reflection of vision-language models with reinforcement learning: This paper is cited as a significant prior work on fully open RL for VLMs and is used as a direct baseline in performance comparisons. The Vero paper argues that its broad data coverage allows it to generalize better than narrowly-trained models like VL-Rethinker, making this a key point of comparison to establish state-of-the-art performance.
