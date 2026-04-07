# Memory Intelligence Agent

- alphaXiv: https://www.alphaxiv.org/abs/2604.04503
- Source paper: https://arxiv.org/abs/2604.04503

## Bridging Memory and Reasoning in Deep Research Agents

The advancement of Deep Research Agents (DRAs) has significantly enhanced the ability of artificial intelligence to perform complex, multi-turn reasoning tasks by integrating Large Language Models (LLMs) with external search tools. However, as these tasks grow in complexity and duration, traditional memory systems often struggle to maintain efficiency and relevance. Many existing agents store historical data as long-context search traces, which can lead to "attention dilution" where the model loses focus on the primary task, or the introduction of noise from irrelevant information. 

The Memory Intelligence Agent (MIA) framework addresses these limitations by introducing a structured, brain-inspired memory mechanism. Unlike systems that focus primarily on factual or knowledge-oriented memory (storing *what* was found), MIA emphasizes "process-oriented" memory—the strategies, search trajectories, and reasoning paths (the *how*) used to reach a result. By decoupling memory management, planning, and execution, MIA enables agents to learn from both successes and failures, evolving continuously even in environments where ground-truth answers are unavailable.

![MIA Agent Loop and Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v1/x2.png)
*Figure 1: The overarching MIA architecture featuring the planning-execution-memory loop across three stages: Memory Retrieval, Collaborative Reasoning, and Experience Consolidation.*

## A Manager-Planner-Executor Architecture

The MIA framework is built upon a tripartite architecture designed to separate high-level strategy from low-level execution, while maintaining a dedicated system for memory organization.

1.  **The Planner (Parametric Memory):** Serving as the cognitive hub, the Planner is an LLM trained to decompose complex multimodal queries into actionable search plans. It does not just act on the current query but utilizes retrieved historical experiences to generate a Chain-of-Thought (CoT) plan.
2.  **The Executor (Operational Terminal):** This component, often a Large Multimodal Model (LMM), is responsible for interpreting the Planner’s instructions. It interacts directly with the environment—performing web searches, analyzing images, and synthesizing results—using a ReAct (Reason + Act) paradigm.
3.  **The Memory Manager (Non-Parametric Memory):** The Manager acts as a non-parametric buffer that stores and organizes high-value search trajectories. It uses a frozen LLM to compress verbose, raw search traces into structured "workflow summaries," ensuring the memory remains efficient and easy to retrieve.

This division of labor ensures that the Planner can focus on "what to do next" based on past experience, while the Executor focuses on "how to perform the action" in the current environment.

## The MIA Agent Loop: From Retrieval to Consolidation

The operation of a MIA agent follows a continuous loop consisting of three distinct stages that facilitate lifelong learning.

### Stage 1: Memory Retrieval
When a new query arrives, the Memory Manager converts visual inputs into textual captions and performs a hybrid retrieval search. It looks for similar historical questions and their corresponding trajectories. The retrieval process is guided by three criteria:
- **Semantic Similarity:** How close the current question is to historical records.
- **Value Reward:** Favoring trajectories that previously led to successful outcomes.
- **Frequency Reward:** Encouraging the exploration of diverse knowledge by rewarding lower-frequency memory units.

Crucially, the system retrieves both "positive paradigms" (successful paths) and "negative constraints" (failed attempts), allowing the agent to avoid repeating past mistakes.

### Stage 2: Collaborative Reasoning
The Planner receives the retrieved trajectories and the current query to generate an initial search plan. The Executor then attempts to carry out this plan. A unique feature of MIA is the "Reflect-Replan" mechanism. If the Executor hits a dead end or receives unexpected feedback from a tool, it reports back to the Planner. The Planner then reflects on the failure and generates a revised, supplementary plan to steer the agent back on track.

### Stage 3: Experience Consolidation
Once a task is complete, an LLM-based Judger evaluates the output. Successful trajectories are compressed into structured workflows. Verbose interactions are abstracted into concise step-by-step summaries, such as: "1. Use visual search to identify the document $\to$ 2. Perform text search for specific keywords $\to$ 3. Cross-verify results." This prevents the memory buffer from becoming saturated with redundant or low-value data.

## Synergy through Two-Stage Reinforcement Learning

A common failure point in research agents is the disconnect between the planner and the executor; often, the planner generates plans the executor cannot follow, or the executor fails to provide useful feedback. MIA addresses this through a two-stage alternating Reinforcement Learning (RL) strategy using Group Relative Policy Optimization (GRPO).

In the first stage, the Executor is trained to follow plans and execute tool calls accurately while the Planner remains frozen. The reward function for the Executor, $R_{\text{Executor}}$, balances multiple objectives:

$$R_{\text{Executor}} = 0.7 \cdot r_{\text{correct}} + 0.2 \cdot r_{\text{tool}} + 0.1 \cdot r_{\text{format}}$$

Where $r_{\text{correct}}$ represents the accuracy of the final answer, $r_{\text{tool}}$ tracks successful tool usage, and $r_{\text{format}}$ ensures the output adheres to the required structure.

In the second stage, the Executor is frozen, and the Planner is trained to generate more effective plans and reflect on feedback. Its reward function, $R_{\text{Planner}}$, is slightly more complex:

$$R_{\text{Planner}} = 0.7 \cdot r_{\text{correct}} + 0.2 \cdot r_{\text{inter}} + 0.05 \cdot r_{\text{reflect}} + 0.05 \cdot r_{\text{format}}$$

Here, $r_{\text{inter}}$ rewards the quality of intermediate reasoning, and $r_{\text{reflect}}$ specifically incentivizes effective replanning after a failure. This alternating training ensures that both components are aligned and capable of sophisticated collaboration.

## Continuous Test-Time Learning (TTL)

One of the most innovative aspects of MIA is its ability to evolve during the inference phase without needing to stop for a separate training session. This is achieved through Test-Time Learning (TTL). 

![Test-Time Learning Framework](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v1/x3.png)
*Figure 2: The Test-Time Learning (TTL) mechanism, showing how successful trajectories are internalized into parametric memory while also updating the non-parametric memory bank.*

During inference, the Planner generates multiple candidate plans (rollouts). The Executor runs these plans, and the results are evaluated. Successful strategies are then used to update the Planner's parameters via an online GRPO update. This allows the agent to "internalize" successful workflows into its own weights (parametric memory) while simultaneously storing them in the external buffer (non-parametric memory).

## Self-Evolution in Unsupervised Environments

In real-world scenarios, agents often lack a "gold standard" or ground-truth answer to verify their findings. To enable self-evolution in these unsupervised settings, MIA introduces a framework modeled after a scientific peer-review process.

![Unsupervised Evaluation Framework](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v1/x4.png)
*Figure 3: The unsupervised self-evolution loop, where three specialized LLM reviewers provide structured feedback to an "Area Chair" agent to determine the validity of a reasoning trajectory.*

Three independent LLM reviewers assess different aspects of the reasoning process:
1.  **Reasoning & Logical Consistency:** Does the logic flow correctly from one step to the next?
2.  **Information Sourcing & Credibility:** Is the retrieved information understood correctly, or is the model hallucinating?
3.  **Result Validity:** Is the final answer complete and substantive?

An "Area Chair Agent" then synthesizes these reviews to make a final decision (Accept/Reject). If a trajectory is accepted, it is used as a high-quality supervision signal to update the agent's memory and parameters, allowing it to improve its performance autonomously.

## Performance and Tool Usage Analysis

MIA has been evaluated across eleven benchmarks, including multimodal datasets like LiveVQA and text-only benchmarks like GAIA and HotpotQA. It consistently outperformed traditional memory-based methods such as RAG and Mem0. On multimodal tasks, MIA achieved an average accuracy of 53.6, representing a significant gain over baseline "No Memory" models.

A key observation from the research is the relationship between memory and tool usage. Analysis of tool calls shows that models without structured memory tend to give up earlier or perform fewer search steps, resulting in lower accuracy. 

![Tool Call Analysis](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04503v1/x9.png)
*Figure 4: Distribution of tool calls across different memory methods. MIA shows a higher concentration of effective multi-turn tool interactions compared to simpler RAG or non-memory approaches.*

MIA's higher tool usage indicates a more persistent and thorough search strategy, enabled by its ability to plan and reflect. Furthermore, MIA's performance with a 7B-parameter Executor was found to be competitive with much larger closed-source models like GPT-4o and Gemini-2.5-Pro, highlighting the efficiency of its memory-driven approach.

## Significance and Future Impact

The MIA framework represents a shift in how AI agents manage experience. By moving from simple document-based memory to a dual-system process-oriented memory, MIA addresses the core challenges of long-term agent operation: noise, context limits, and the need for continuous adaptation.

The ability to evolve without human-provided labels through the peer-review evaluation mechanism opens the door for autonomous agents that can operate in niche research fields where data is scarce. Moreover, the synergy between the Planner and Executor, refined through alternating reinforcement learning, provides a template for building more reliable and communicative multi-agent systems. As agents move toward more complex, open-ended research tasks, the integration of structured memory and continuous learning will likely be a foundational requirement for truly autonomous intelligence.

## Relevant Citations

- Memento: Fine-tuning llm agents without fine-tuning llms: This paper is frequently cited as a state-of-the-art memory-based agent and is used as a primary baseline in the experiments. MIA's performance is directly compared against Memento, highlighting its relevance in demonstrating the proposed framework's superiority in abstracting memory into high-level guidance.
- Expel: Llm agents are experiential learners: The ExpeL framework is cited for its approach of learning from both successful and failed experiences. This is a core concept that MIA adopts and expands upon by retrieving both positive (successful trajectories) and negative (failed trajectories) paradigms to construct a rich contextual prior for planning.
- Mmsearch-r1: Incentivizing lmms to search: This paper is cited as a foundational work that integrates multimodal search tools into agents, a key capability of the MIA's Executor. The main paper explicitly states that one of its baselines is built upon the MMSearch-R1 codebase, making it a direct technical foundation for the research.
- React: Synergizing reasoning and acting in language models: This paper introduces the ReAct paradigm, which is fundamental to the operation of MIA's Executor. The paper repeatedly mentions that the Executor interacts with its environment via a ReAct loop, demonstrating that this citation provides the core architectural principle for the agent's action and reasoning cycle.
- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper is the source of the Group Relative Policy Optimization (GRPO) algorithm, which is the specific reinforcement learning method used in MIA's two-stage alternating training strategy. This makes it a critical methodological citation as it provides the core optimization algorithm for training both the Planner and the Executor.
