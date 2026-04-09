# Synthetic Sandbox for Training Machine Learning Engineering Agents

- alphaXiv: https://www.alphaxiv.org/abs/2604.04872
- Source paper: https://arxiv.org/abs/2604.04872

## The Execution Bottleneck in Machine Learning Engineering

In the pursuit of creating autonomous agents capable of performing complex, open-ended tasks, Large Language Models (LLMs) have emerged as the primary foundation. These models have shown remarkable aptitude in areas such as software engineering (SWE) and web navigation. A key driver of this success has been the use of Reinforcement Learning with Verifiable Rewards (RLVR). By interacting with a sandbox environment and receiving immediate feedback—often through unit tests—models can improve their reasoning through exploration and long-horizon decision-making.

However, the field of Machine Learning Engineering (MLE) faces a unique and significant challenge that has hindered the application of these same reinforcement learning (RL) techniques. Unlike SWE tasks, where verifying a solution often takes seconds, verifying an MLE task requires executing a full pipeline: data preprocessing, model training, and performance evaluation on potentially massive datasets. This "Execution Bottleneck" is severe. On standard benchmarks like MLE-bench, a single code execution takes approximately $196.17 \text{ seconds}$ on average.

![SandMLE Teaser](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04872v1/teaser_updated.png)
*Figure 1: Comparison between standard on-policy RL for MLE, which is prohibitively slow due to massive datasets, and the SandMLE approach, which utilizes synthetic micro-scale data to achieve a 13.7x speedup.*

This latency makes on-policy trajectory-wise RL—where a model generates thousands of potential solutions and learns from their outcomes—practically impossible for MLE tasks. To date, training MLE agents has relied on Supervised Fine-Tuning (SFT) using expert trajectories or step-wise RL using offline proxy rewards. While these methods are faster, they do not allow the model to learn through genuine exploration and environment interaction. SandMLE addresses this by introducing a "Synthetic Sandbox" that drastically reduces execution time, enabling large-scale, on-policy training for MLE agents.

## The SandMLE Framework: A Multi-Agent Pipeline

The core innovation of SandMLE is the automated generation of synthetic, micro-scale machine learning environments. Instead of training agents on massive, real-world datasets that take minutes to process, SandMLE creates simplified versions that retain the same technical and mathematical complexity but can be executed in under 15 seconds.

To achieve this, the authors developed a multi-agent framework that transforms real-world "seed" tasks into diverse, verifiable synthetic tasks. This pipeline consists of four specialized roles:

1.  **Data Strategist:** This agent abstracts a seed task into its "Task DNA." For example, it might identify that a task involves image classification with 10 classes and specific resolution requirements. It then "mutates" this DNA into a new domain (e.g., changing animal detection into road damage detection) and defines "hidden rules"—mathematical functions that link features to labels. Crucially, it restricts the dataset size to between $50-200$ samples.
2.  **MLE Developer:** This agent writes the Python scripts necessary to synthesize the data based on the Strategist's rules. It implements the mapping $l = f(z) + \epsilon$ to connect features $z$ to labels $l$ with controlled noise $\epsilon$. It also trains baseline models to establish performance milestones.
3.  **MLOps Engineer:** This agent builds the evaluation infrastructure. It standardizes the metrics (e.g., F1-score, MSE) and ensures the evaluator can deterministically score submissions by comparing them to the hidden ground-truth.
4.  **Technical Writer:** Finally, this agent compiles all the metadata into a clear markdown task description, adapting the narrative to the new synthetic domain while omitting any "cheating" information.

![SandMLE Pipeline](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04872v1/diagram_syntho.png)
*Figure 2: The multi-agent workflow for generating synthetic MLE tasks, showing the transition from a seed task to a verifiable micro-task.*

This automated pipeline ensures that the generated environments are not just simpler versions of the original tasks, but logically consistent, diverse, and technically challenging problems that demand real engineering reasoning.

## Synthetic Environment Diversity and Reliability

To be effective, the synthetic sandbox must cover a wide range of real-world scenarios. The authors generated a training corpus from 60 seed tasks, resulting in over 1,100 unique synthetic environments. These tasks span various application domains including healthcare, retail, and manufacturing, and utilize diverse data modalities like images, tabular data, text, audio, and graphs.

![Data Diversity](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04872v1/data_analysis_large.png)
*Figure 3: Sankey diagram illustrating the broad distribution of application domains, data modalities, and task formulations within the SandMLE training set.*

The reliability of these synthetic environments was verified using state-of-the-art models like Claude-4.5-Sonnet and GPT-4o-mini. The benchmarking showed that these micro-tasks successfully differentiate between models of different capabilities, with more advanced models achieving higher win rates. This confirms that the synthetic tasks are not "trivial" despite their small dataset size; they still require the agent to correctly implement data loading, model selection, and hyperparameter tuning.

Importantly, the average execution time $c_{\text{exec}}$ dropped from nearly 200 seconds to just $14.31 \text{ seconds}$. This $13.7\times$ speedup is what makes trajectory-level reinforcement learning feasible for the first time in this domain.

## Training with Trajectory-Level GRPO

With a fast execution environment, the authors applied Group Relative Policy Optimization (GRPO), an efficient variant of Proximal Policy Optimization (PPO). In this setup, the LLM agent interacts with the environment using the ReAct framework—a cycle of "Thought," "Action," and "Observation."

A major challenge in training agents for long-horizon tasks like MLE is reward sparsity. If an agent only receives a reward at the very end of a 30-turn interaction, it is difficult for the model to understand which specific actions led to success. SandMLE addresses this by using a dense, milestone-based reward function:

$$r = w_{\text{format}} r_{\text{format}} + w_{\text{execute}} I_{\text{execute}} + \sum_{i=1}^{k} w_{s_i} I_{s_i}$$

Where:
- $r_{\text{format}}$ rewards the model for using the correct reasoning tags.
- $I_{\text{execute}}$ is a binary indicator of whether the model successfully produced a valid output file.
- $I_{s_i}$ represents progressive performance milestones. If the agent's model achieves a score higher than a certain baseline (e.g., a simple linear regression), it receives a partial reward. Higher rewards are granted for surpassing more complex baselines.

This hierarchical reward structure guides the agent from basic formatting and execution towards high-performance engineering. Training was conducted across several model scales, including Qwen3 models with 8B, 14B, and 30B parameters.

## Experimental Results and Scaling

The results demonstrate that training on the synthetic sandbox leads to significant improvements in real-world MLE tasks. The models were evaluated on MLE-Bench-Lite and MLE-Dojo, which consist of authentic machine learning challenges.

### Performance Gains
The SandMLE-trained models showed substantial improvements over their base versions. For instance, the Qwen3-8B model saw a 66.9% relative improvement in its "Any Medal" rate (the frequency of achieving a performance score comparable to human competitors). Remarkably, the 8B model trained with SandMLE matched the performance of much larger closed-source models like DeepSeek-V3.1 and Gemini-2.5-Flash on these benchmarks.

### Comparison with Supervised Fine-Tuning (SFT)
A key finding was that on-policy RL outperformed SFT. While SFT (behavioral cloning from expert trajectories) improved the model's ability to follow formats, it did not significantly improve its engineering reasoning. In contrast, SandMLE models demonstrated a 20% to 67% improvement over the SFT baselines, suggesting that the "trial-and-error" nature of RL is superior for teaching agents how to debug and iterate on machine learning pipelines.

![Execution Latency](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04872v1/x5.png)
*Figure 4: Visualization of the 13.7x reduction in average execution time achieved by SandMLE compared to real-world MLE benchmarks.*

### Model Scaling
The benefits of SandMLE scaled with model size. Larger models (14B and 30B) not only achieved higher performance but also learned to produce "Valid Submissions" (code that runs to completion and outputs the correct format) much faster and more consistently than smaller models. At the 30B scale, the agent achieved a 100% valid submission rate on the test set, indicating that it had fully internalized the requirements of the engineering environment.

## Generalization and Test-Time Scaling

One of the most important aspects of the research is the "framework-agnostic" nature of the improvements. Often, agent performance is tied to a specific "scaffold"—the code that manages the agent's prompts and tools. However, models trained with SandMLE showed consistent improvements across various third-party scaffolds, such as AIDE and MLE-Agent. This indicates that the RL process improved the model's *intrinsic* reasoning, rather than just teaching it to follow a specific set of instructions.

The researchers also explored "test-time scaling," which refers to giving the model more time or "turns" to solve a problem at inference time. The Qwen3-30B-SandMLE model showed a positive scaling trend, with performance peaking at around 30 interaction turns ($T_{\text{max}} = 30$).

![Test-time Scaling](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04872v1/x7.png)
*Figure 5: Performance scaling of the 30B SandMLE model as the maximum allowed interaction turns increase, highlighting the benefits of extended reasoning.*

However, the authors noted a decline in performance beyond 30 turns. This was attributed to the context window limit of the model; as the history of thoughts and observations becomes too long, the model begins to "forget" earlier context, leading to errors. This highlights context length as a remaining bottleneck for long-horizon engineering agents.

## Conclusion and Significance

SandMLE provides a scalable solution to the execution bottleneck that has long plagued the training of machine learning engineering agents. By proving that micro-scale synthetic environments can serve as effective proxies for large-scale real-world tasks, the research opens a new path for developing autonomous engineering systems.

The significance of this work lies in its shift from imitation (SFT) to interaction (RL). By allowing agents to explore, fail, and succeed within a high-speed sandbox, we can instill robust reasoning and debugging capabilities that are transferable to any framework or domain. As LLM context windows expand and synthetic data generation becomes even more sophisticated, the paradigms established by SandMLE will likely play a central role in the evolution of AI agents from simple assistants to capable autonomous engineers.

## Relevant Citations

- Mle-bench: Evaluating machine learning agents on machine learning engineering: This paper introduces MLE-bench, the primary benchmark used to evaluate the SandMLE framework. It defines the real-world Kaggle-style tasks and medal-based evaluation metrics that the current paper's agent is optimized to solve, making it fundamental to the experimental validation.
- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper introduces Group Relative Policy Optimization (GRPO), the specific reinforcement learning algorithm that is core to the SandMLE training pipeline. The main paper's entire methodology is a direct application and adaptation of GRPO for the trajectory-level optimization of MLE agents.
- Deepswe: Training a state-of-the-art coding agent from scratch by scaling rl: This work is cited as a key example of successfully applying trajectory-wise reinforcement learning to a complex, long-horizon domain (software engineering). It serves as a major inspiration and point of comparison, motivating the current paper's effort to overcome the execution bottleneck that prevented a similar approach from being feasible in MLE.
- Acegrpo: Adaptive curriculum enhanced group relative policy optimization for autonomous machine learning engineering: This paper is cited as a key related work that also attempts to solve the prohibitive cost of RL for MLE agents. By proposing an alternative off-policy approach (asynchronous GRPO), it highlights the specific challenge SandMLE addresses and frames the novelty of enabling strictly on-policy RL through synthetic environments.
