# Memory Intelligence Agent

- alphaXiv: https://www.alphaxiv.org/abs/2604.04503
- Source paper: https://arxiv.org/abs/2604.04503

## Introduction to Memory Intelligence Agents

The rapid advancement of Large Language Models (LLMs) has enabled the creation of Deep Research Agents (DRAs) that can autonomously handle complex, open-ended tasks by searching the web and reasoning through information. However, these agents often face a significant hurdle: they do not effectively learn from their own history. When tasked with a research query, many agents treat it as a brand-new problem, even if they have encountered similar challenges before. This lack of persistent memory leads to redundant searches, high computational costs, and a plateau in reasoning capabilities.

Existing attempts to provide agents with memory typically rely on long-context retrieval, where past experiences are simply fed back into the model as text. While this can help, it often introduces noise and dilutes the model's focus, as irrelevant historical details clutter the current reasoning path. To address these limitations, researchers have developed the Memory Intelligence Agent (MIA). MIA is designed to move beyond simple data retrieval toward a more brain-like system that consolidates experiences into actionable knowledge. It uses a structured "Manager-Planner-Executor" architecture to separate high-level strategy from low-level execution, allowing the agent to evolve its internal parameters over time.

![MIA Architecture Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v2/x3.png)
**Figure 1: The architecture of the Memory Intelligence Agent (MIA), illustrating the interaction between the Memory Manager, the Planner, and the Executor within the research process.**

## The Manager-Planner-Executor Architecture

The core of MIA is its tripartite architecture, which distributes cognitive labor across three specialized components: the Memory Manager, the Planner, and the Executor. This division of labor is intended to mirror human cognition, where we separate our memories of "how to do things" from the "actual doing."

1.  **Memory Manager (Non-parametric Memory):** This component acts as the agent's long-term storage. It maintains a buffer of historical trajectories—step-by-step records of how previous questions were answered. To keep this storage efficient, it uses a large LLM to compress verbose logs into "workflow summaries" and converts images into text captions. This ensures that only the most critical strategic information is preserved.
2.  **Planner (Parametric Memory):** The Planner is the cognitive hub of the system. Its role is to take the current user question, look at relevant memories provided by the Manager, and generate a structured search plan. Unlike a simple text-retrieval system, the Planner is "trainable." It internalizes successful strategies into its own neural weights (parametric memory), allowing it to become more intuitive and efficient the more it is used.
3.  **Executor:** This is the operational terminal. It receives the plan from the Planner and interacts with external tools, such as web search engines or image analysis tools. It follows a ReAct (Reason + Act) loop, where it thinks about the results it gets and decides on the next specific tool call. If the Executor hits a dead end, it sends feedback back to the Planner for a revised strategy.

## A Dual-Memory System: Parametric and Non-Parametric

One of the most distinct features of MIA is its bidirectional memory conversion loop. Most agents use either non-parametric memory (like a database or vector store) or parametric memory (the model's pre-trained knowledge). MIA combines both.

When the agent solves a new problem, the "episodic memory" of that event (the search trajectory) is first stored in the non-parametric Memory Manager. However, MIA doesn't stop there. Through a process called Test-Time Learning (TTL), the agent uses these high-value historical cases to retrain the Planner model. This converts the external, text-based experience into internal, parametric knowledge.

To prevent memory bloat, the system uses a hybrid retrieval strategy. When a new question $Q$ arrives, the Manager calculates a score based on three factors:
*   **Semantic Similarity:** How much the current question resembles the memory.
*   **Value Reward:** How successful the past trajectory was (prioritizing winning strategies).
*   **Frequency Reward:** A reward for low-frequency memories to encourage the agent to explore diverse reasoning paths.

## The Reasoning Loop and Experience Consolidation

The reasoning process in MIA follows a rigorous multi-stage loop. It begins with **Memory Retrieval**, where the agent identifies both positive paradigms (what worked) and negative constraints (what failed) from its history.

Next is **Collaborative Reasoning**. The Planner generates an initial plan using a few-shot Chain-of-Thought (CoT) strategy. This plan is handed to the Executor, which performs the actual search. A critical feature here is the **Reflect-Replan mechanism**. If the Executor provides feedback that the information found is insufficient or the plan has failed, the Planner is invoked again to adjust the search path based on the new context.

Finally, the process concludes with **Experience Consolidation**. Once an answer is found, an LLM-based Judger evaluates its correctness. The trajectory is then compressed. For example, a multi-round search for a specific chemical compound might be summarized into a workflow like: "1. Search for chemical name -> 2. Verify molecular structure -> 3. Synthesize factual answer." This summary is then stored back in the Manager, and the Planner is updated to reinforce this successful strategy.

![The Detailed Agent Interaction Loop](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v2/x2.png)
**Figure 2: A detailed trace of the interaction between the Planner and Executor, showcasing how the agent handles complex visual and textual queries through planning and reflection.**

## Two-Stage Alternating Reinforcement Learning

To optimize the collaboration between the Planner and the Executor, MIA employs a training strategy called Group Relative Policy Optimization (GRPO). Because the Planner and Executor have different roles, training them simultaneously can be unstable. Instead, MIA uses an alternating approach.

In the **Executor RL Training** stage, the Planner is kept frozen. The Executor is trained to follow instructions precisely and use tools effectively. The reward function for the Executor, $R_{exec}$, is defined as:

$$R_{exec} = 0.7 \cdot \mathbb{I}_{correct} + 0.2 \cdot R_{tool} + 0.1 \cdot R_{format}$$

Here, correctness is the primary goal, but the agent is also rewarded for correct tool usage and following the required output format.

In the **Planner RL Training** stage, the Executor is frozen. The Planner is trained to absorb historical memories and generate better strategic plans. Its reward function, $R_{plan}$, is slightly more complex to account for its role in the reflection process:

$$R_{plan} = 0.7 \cdot \mathbb{I}_{final} + 0.2 \cdot \mathbb{I}_{mid} + 0.05 \cdot R_{reflect} + 0.05 \cdot R_{format}$$

This setup ensures that the Planner is rewarded not just for the final answer, but for its ability to provide helpful intermediate guidance and effective reflection when errors occur.

## Unsupervised Self-Evolution

In real-world scenarios, agents often lack "ground truth" answers to learn from. MIA addresses this through a novel **unsupervised evaluation framework** that mimics a scientific peer-review process. Instead of a single model guessing if it is right, MIA uses three specialized reviewer models and an "Area Chair" model:

*   **Reviewer 1:** Focuses on reasoning and logical consistency.
*   **Reviewer 2:** Focuses on information sourcing and the credibility of retrieved data.
*   **Reviewer 3:** Focuses on result validity and completeness.
*   **Area Chair Agent:** Collects the scores and reasons from the reviewers to make a final meta-decision on whether to accept or reject the trajectory for memory storage.

This system allows MIA to identify high-quality experiences even in environments where the correct answer is unknown. It creates a self-sustaining loop where the agent can continuously refine its own knowledge base and planning capabilities without human intervention.

![Unsupervised Self-Evolution Mechanism](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v2/x6.png)
**Figure 3: The unsupervised self-evolution loop, showing how three specialized reviewers and an Area Chair agent judge trajectories to provide training signals.**

## Evaluation and Performance

MIA was evaluated against eleven different benchmarks, covering both multimodal (images + text) and text-only tasks. The results indicated that the framework significantly outperforms standard long-context memory methods.

In multimodal benchmarks, MIA achieved an average accuracy of 53.6%, which was 5.5 percentage points higher than the previous best memory-based method. Notably, traditional methods like RAG (Retrieval-Augmented Generation) actually performed worse than having no memory at all in some cases, likely due to the noise introduced by long, unstructured contexts. MIA avoided this pitfall through its structured workflow compression.

Furthermore, the research demonstrated that MIA generalizes well to closed-source models. When used as a planning layer for models like GPT-4o or Gemini-2.5-Pro, MIA consistently improved their performance on complex reasoning tasks. This suggests that the "Manager-Planner" strategy is a valuable wrapper for any sufficiently capable LLM.

## Significance and Future Impact

The development of the Memory Intelligence Agent highlights a shift in how researchers view agentic memory. It moves away from the idea of memory as a "passive database" and toward a view of memory as an "active cognitive process." By decoupling the storage of history from the execution of tasks and allowing the agent to internalize its experiences through reinforcement learning, MIA achieves a more robust and scalable architecture.

The significance of this work lies in several areas:
*   **Efficiency:** By compressing trajectories and internalizing them into model weights, MIA reduces the computational and token costs associated with long-context reasoning.
*   **Self-Evolution:** The unsupervised peer-review system provides a path for agents to learn in the "wild," where labeled datasets are not available.
*   **Collaborative Planning:** The alternating RL training demonstrates a method for optimizing the relationship between high-level logic and low-level action.

As agents continue to take on more significant research roles in science, medicine, and engineering, frameworks like MIA will be essential for ensuring they can handle the increasing complexity of human knowledge without becoming bogged down by the very data they are designed to process.

## Relevant Citations

- Memento: Fine-tuning llm agents without fine-tuning llms: This paper is a key state-of-the-art memory baseline that MIA is directly compared against in the experimental results. It represents a different approach by exploring performance gains through memory fine-tuning while freezing the LLMs, providing a crucial point of contrast for MIA's architectural and learning paradigm.
- Expel: Llm agents are experiential learners: This work is cited as an important baseline method for agent memory systems. Its framework for optimizing decision-making by learning from both successful and failed experiences is highly relevant to MIA's use of both positive and negative trajectories to construct a rich contextual prior for planning.
- MMSearch-R1: Incentivizing lmms to search: This paper is a significant baseline in the domain of multimodal deep research agents. MIA is compared against it and its methodology for integrating multimodal search tools is foundational to the problem space MIA addresses. The main paper also mentions using the MMSearch-R1 codebase and dataset splits, indicating its direct influence.
- Search-r1: Training llms to reason and leverage search engines with reinforcement learning: This citation is foundational to the main paper's methodology. It introduces the use of reinforcement learning to enhance multi-turn search and retrieval, a core concept that MIA builds upon with its more complex two-stage alternating RL training paradigm for the Planner and Executor agents.
