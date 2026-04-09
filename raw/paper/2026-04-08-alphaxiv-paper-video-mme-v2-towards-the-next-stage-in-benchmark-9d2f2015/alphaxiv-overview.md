# Video-MME-v2: Towards the Next Stage in Benchmarks for Comprehensive Video Understanding

- alphaXiv: https://www.alphaxiv.org/abs/2604.05015
- Source paper: https://arxiv.org/abs/2604.05015

## Redefining the Standard for Video Understanding

The rapid evolution of multimodal large language models (MLLMs) has pushed the boundaries of video comprehension, moving from simple object recognition to complex, long-horizon reasoning. However, as models improve, existing benchmarks often become "saturated," showing high leaderboard scores that do not always translate to robust real-world performance. This discrepancy suggests that current evaluation methods may overstate model capabilities by relying on isolated, per-question accuracy that can be inflated through lucky guesses or language-based shortcuts.

![Video-MME-v2 Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05015v1/x1.png)
*Figure 1: The Video-MME-v2 framework features a tri-level capability hierarchy and a group-based non-linear evaluation strategy to assess robustness and faithfulness in video understanding.*

Video-MME-v2 is a comprehensive benchmark designed to address these limitations. It moves away from fragmented testing by introducing a structured taxonomy of video understanding and a rigorous evaluation strategy that rewards consistency and logical coherence. By shifting the focus from whether a model can answer a single question to whether it truly understands the underlying dynamics of a video across related queries, the benchmark provides a more faithful measure of genuine multimodal proficiency.

## A Progressive Hierarchy of Video Capabilities

To systematically evaluate the depth of video understanding, Video-MME-v2 establishes a tri-level hierarchy that categorizes capabilities based on increasing cognitive complexity. This structure ensures that models are tested not just on what they see, but on how they integrate temporal information and apply high-level reasoning.

**Level 1: Visual Information Aggregation**
At the foundational level, the benchmark assesses the model's ability to perceive and integrate information at specific moments. This includes Visual Recognition (identifying objects, scenes, and text), Cross-Modal Consistency (aligning visual and audio cues), and Basic Counting and Calculation. These tasks form the "perceptual base" upon which more complex reasoning is built.

**Level 2: Temporal Dynamics**
The second level focuses on the evolution of events over time. It requires models to understand Action and Motion Analysis (fine-grained trajectories and properties), Sequential Ordering (the chronological flow of events), and Causal Reasoning (predicting future outcomes or identifying the cause of an observed event). This level tests the model’s ability to treat video as a continuous temporal stream rather than a collection of static frames.

**Level 3: Complex Reasoning**
The final level simulates advanced cognitive tasks. It includes Narrative Understanding (deconstructing plots and metaphors), Social Behavior Analysis (understanding individual and collective interactions), and Physical World Reasoning (tracking entity persistence and performing counterfactual analysis). These tasks often require professional-grade knowledge and multi-hop inference, reflecting the most challenging aspects of human-like video comprehension.

## Group-Based Evaluation for Consistency and Coherence

A core contribution of Video-MME-v2 is its move beyond traditional accuracy metrics. In standard benchmarks, a model might answer a question correctly by chance or by exploiting textual biases. Video-MME-v2 mitigates this by organizing questions into "Groups" of four related queries per video, using two distinct strategies:

**Consistency-Based Groups**
These groups evaluate the breadth and stability of a specific skill. For instance, a model might be asked four different questions about spatial relationships in a scene. To reward consistent performance and penalize fragmented success, the benchmark uses a quadratic scoring function:

$$S = \left(\frac{N}{4}\right)^2$$

In this formula, $N$ represents the number of correct answers within the group of four. Under this scoring system, answering only one or two questions correctly yields a disproportionately low score, while answering all four correctly is required to achieve the full credit. This encourages models to demonstrate a robust grasp of the underlying capability rather than a surface-level association.

**Coherence-Based Groups**
These groups model a logical reasoning chain. Questions are structured to follow a human-like progression, starting from localized clues (e.g., "What object is out of place?") and leading to high-level conclusions (e.g., "Why did the character react that way?"). To ensure faithfulness, these groups use a first-error truncation mechanism. If a model fails at a foundational reasoning step, such as $Q_1$ or $Q_2$, it receives no credit for subsequent correct answers in that group. This ensures that a correct conclusion ($Q_4$) is only rewarded if it is supported by a valid and coherent reasoning process.

## Rigorous Data Construction and Quality Control

The reliability of any benchmark depends on its data quality and its resistance to "data contamination"—where models might have seen the test data during their pre-training phase. Video-MME-v2 implements several rigorous measures to ensure the integrity of its evaluation.

![Video Categories](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05015v1/video_category.png)
*Figure 2: The benchmark spans a diverse taxonomy of 31 subcategories across sports, lifestyle, art, and knowledge domains.*

To prevent memorization, the team utilized a recency-oriented collection strategy. More than $80\%$ of the videos in the dataset were published in $2025$ or later, with nearly $40\%$ published after October $2025$. This ensures the content is novel even to the most recently trained models. Furthermore, the team manually excluded famous films, TV shows, and viral influencer content that might be present in large-scale web-crawled training sets.

![Publish Date Stats](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05015v1/video_publish_month.png)
*Figure 3: Distribution of video publication dates, highlighting the emphasis on recent content to mitigate data leakage.*

The annotation process involved over $3,300$ human-hours, with $12$ primary annotators and $50$ independent reviewers. Each question was refined through five rounds of quality assurance. To increase the difficulty and reduce random success, each question is presented in an 8-option multiple-choice format, reducing the random guessing probability to just $12.5\%$. Annotators also meticulously crafted adversarial distractors—options that appear plausible but are contradicted by fine-grained details in the video—to test the models' discriminative capabilities.

## Benchmarking the State-of-the-Art

The evaluation of prominent models, including Gemini-3-Pro, GPT-5, and open-source models like Qwen3.5, reveals a significant gap between current AI performance and human experts. While human experts achieved a non-linear score of $90.7\%$ and an average accuracy of $94.9\%$, the highest-performing commercial model, Gemini-3-Pro, reached only $49.4$ in its non-linear score.

![Model Accuracy Q1-Q4](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05015v1/q1-q4_models_acc_0406.png)
*Figure 4: Performance trends across question groups. Coherence groups (middle) show a monotonic decline, reflecting the increasing logical depth required for later questions.*

A key finding is the presence of "hierarchical bottlenecks." Across all models, performance steadily declines from Level 1 to Level 3. This suggests that errors in basic perception (Level 1) or temporal tracking (Level 2) propagate upward, preventing the model from succeeding in complex reasoning tasks. Proprietary models generally demonstrated more robustness than open-source counterparts, particularly when textual subtitles were removed, indicating a more sophisticated native visual understanding.

![Effect of Thinking Mode](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05015v1/scientific_think_effect_v2.png)
*Figure 5: The impact of enabling "Thinking Mode" across different levels. While often beneficial, it can lead to regressions in certain models when visual cues are absent.*

The study also analyzed the "Thinking Mode" (where models generate a chain of thought before answering). While this mode generally improves performance—especially when textual subtitles provide a semantic anchor—it can sometimes lead to regressions. For some models, explicit reasoning resulted in an over-reliance on linguistic priors, causing them to hallucinate or misinterpret purely visual information when textual cues were missing. This highlights that "more thinking" is not always better if the underlying visual-linguistic alignment is weak.

## Significance for Future Research

Video-MME-v2 establishes a more demanding and diagnostic testbed for the next generation of video MLLMs. By quantifying consistency and coherence, it exposes the stochastic nature of current models, where a "correct" answer is often not backed by a robust understanding of the video's context.

![Capability Radar](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05015v1/radar_second_head.png)
*Figure 6: A radar chart comparing model capabilities. Significant gaps remain in Action & Motion and Physical World Reasoning across all tested models.*

The benchmark's findings suggest several paths for future development. First, the integration of native audio processing (omni-modal architectures) provides a clear performance boost, as seen in models like Gemini-3-Pro and MiMo-v2-Omni. Second, increasing the frame sampling rate (long-context processing) remains a reliable way to improve temporal modeling. Finally, the $41.3$ point gap between the best AI and human performance in the non-linear metric indicates that achieving truly faithful, human-like video reasoning remains a major challenge. Video-MME-v2 provides the necessary granularity to track progress toward this goal, ensuring that future advancements are measured not just by accuracy, but by the reliability of the model's understanding.

## Relevant Citations

- Video-mme: The first-ever comprehensive evaluation benchmark of multi-modal llms in video analysis: This paper introduces the original Video-MME benchmark, which is the direct predecessor to Video-MME-v2. The current work is explicitly framed as the next stage in the comprehensive evaluation of video MLLMs, building directly upon the foundation and goals established by this citation.
- Mme: A comprehensive evaluation benchmark for multimodal large language models: This citation is fundamentally important as it introduced the group-based question answering and non-linear scoring approach in the image domain. The Video-MME-v2 paper explicitly states it extends this core methodological concept to the video domain to assess consistency and coherence, making it a foundational reference for its novel evaluation strategy.
- Mvbench: A comprehensive multi-modal video understanding benchmark: MVBench is frequently cited as a prominent existing benchmark for video understanding. The authors of Video-MME-v2 position their work as a necessary advancement designed to address the gaps and limitations of prior benchmarks like MVBench, particularly in providing a more holistic hierarchy and robust evaluation metric.
- Video-mmmu: Evaluating knowledge acquisition from multi-discipline professional videos: This paper is referenced as part of an emerging trend in benchmarks that focus on complex video reasoning. Video-MME-v2's design, especially its Level 3 tasks, directly engages with and aims to advance the evaluation of such sophisticated reasoning capabilities, making Video-MMMU a relevant contemporary work that the new benchmark is contextualized against.
