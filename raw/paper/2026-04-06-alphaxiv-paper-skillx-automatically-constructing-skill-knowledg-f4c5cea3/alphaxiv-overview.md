# SkillX: Automatically Constructing Skill Knowledge Bases for Agents

- alphaXiv: https://www.alphaxiv.org/abs/2604.04804
- Source paper: https://arxiv.org/abs/2604.04804

## Introduction to Automated Skill Acquisition for Agents

Large Language Model (LLM) agents have shown significant potential in executing complex, multi-step tasks such as web navigation, API orchestration, and interactive problem-solving. However, these agents often operate under a "blank slate" paradigm, where they approach each new task without the benefit of prior experience. This lack of a memory mechanism for reusable behaviors leads to high computational costs, as agents must rediscover strategies repeatedly, and a general fragility when faced with slightly different environments or tasks.

Prior attempts to enable "self-evolving" agents—agents that learn from their own past executions—frequently encounter scalability issues. These agents often learn in isolation, meaning they fail to extract generalizable patterns that can be shared across different tasks or models. Furthermore, the quality of what an agent learns is often capped by its own reasoning capabilities; a weaker agent might never discover the optimal way to use a tool, while a stronger agent's insights might be too complex for a weaker one to follow.

![Comparison of SkillX with existing skill-based systems](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04804v1/x1.png)
*Figure 1: A comparison between SkillX and existing skill-based paradigms like Claude Skills. SkillX emphasizes a multi-level, itemized storage approach that is lightweight and requires only one-time loading.*

To address these challenges, the SkillX framework introduces an automated method for constructing a hierarchical, plug-and-play skill knowledge base. Instead of storing raw logs of past actions, SkillX distills experience into structured "skills" at various levels of abstraction. This approach allows agents to retrieve and apply relevant, high-quality behaviors learned from a broad set of training data, effectively decoupling the learning phase from the execution phase.

## Multi-Level Skill Representation

At the heart of the framework is a hierarchical design that organizes experience into three distinct tiers. This structure ensures that the knowledge base is concise enough for efficient retrieval while being detailed enough to guide an agent through complex technical constraints.

### 1. Planning Skills ($S_{plan}$)
Planning skills capture the high-level logic of a task. They represent the organizational structure of subtasks, including the order in which they should be performed, their dependencies, and any branching logic (e.g., "if step A fails, try step B"). These are extracted by taking successful trajectories and compressing them into an ordered set of essential steps, removing unnecessary exploration or backtracking.

### 2. Functional Skills ($S_{func}$)
Functional skills abstract specific sub-goals into macro-operations. Each functional skill corresponds to completing a specific sub-query within a larger task. For example, "authenticating with a music service" might be a functional skill. These skills are defined by a clear name, documentation (describing inputs and outputs), and the specific pattern of tool invocations required to achieve the goal.

### 3. Atomic Skills ($S_{atomic}$)
Atomic skills focus on the nuances of individual tools. While base models often have access to raw API documentation, they frequently lack practical "execution-oriented" knowledge, such as common failure modes, specific parameter constraints, or undocumented prerequisites. Atomic skills extend the original tool schemas with these practical insights distilled from real execution data.

By separating knowledge into these levels, SkillX allows an agent to maintain a high-level strategic view (via $S_{plan}$) while benefiting from concrete, reusable implementation details (via $S_{func}$ and $S_{atomic}$).

## Automated Skill Construction and Refinement

The construction of the skill library is an iterative, four-stage process designed to maximize the quality and generalizability of the stored behaviors.

![Overview of the SkillX construction and refinement pipeline](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04804v1/x2.png)
*Figure 2: The SkillX pipeline, showing the iterative cycle of rollout, extraction, refinement (merging and filtering), and library updating.*

### Extraction and Merging
The process begins with a strong "backbone" agent performing rollouts on a set of training tasks. Successful trajectories are analyzed by a skill extractor to identify potential planning, functional, and atomic skills. Because different tasks might lead to functionally identical but descriptively different skills, the framework employs a merging step. This uses semantic similarity (typically via cosine similarity of embeddings) to cluster similar skills. These clusters are then merged into a single, refined skill that aggregates the best documentation and most generalizable invocation patterns from all candidates.

### Filtering and Quality Control
Not all extracted behaviors are useful or safe to reuse. SkillX implements a two-stage filter:
*   **General Filter:** This removes skills that are too specific to a single environment (e.g., those relying on local file paths or idiosyncratic Python functions) or those that are too complex to be modular.
*   **Tool-Specific Filter:** This stage validates the skill against the actual environment's API schema. If a skill suggests a parameter that doesn't exist or uses a tool in an unsupported way, it is rejected.

### Iterative Updates
The library is not static. It undergoes multiple rounds of refinement. In each round, the current skills are used to solve tasks; the resulting feedback is then used to update the skill documentation or the execution logic. This iterative loop continues until the agent's performance on the training distribution reaches a plateau.

## Exploratory Skills Expansion

A common limitation in agentic learning is that the agent only learns from what it happens to encounter in the training set. If a specific tool or edge case is never triggered during training, the agent will never develop a skill for it. SkillX addresses this through "Experience Guiding Exploration."

Instead of random exploration, the agent uses its current experience to identify "blind spots"—tools that have never been used, tools with high failure rates, or subtasks that are consistently difficult. The agent is then specifically prompted to explore these areas. Once it successfully interacts with these under-utilized environment components, it generates "synthetic tasks" ($Q_{syn}$) based on those interactions. These synthetic tasks are then fed back into the main pipeline to extract and refine new skills, effectively expanding the knowledge base beyond the initial seed data.

## Skill-Based Inference and Retrieval

Once the knowledge base is constructed, it can be "plugged into" various base agents. During the inference phase for a new task, the agent follows a specific retrieval protocol:

1.  **Pseudo-Plan Rewriting:** The agent first retrieves high-level planning skills from tasks that are semantically similar to the current query. It then uses these to "self-rewrite" a specific plan for the new task. This pseudo-plan acts as a roadmap.
2.  **Step-wise Retrieval:** For each step in the rewritten plan, the agent retrieves the most relevant functional and atomic skills. 
3.  **Self-Filtering:** To keep the input context manageable, the agent performs a final round of self-filtering, selecting only the most applicable $S_q$ (the final set of skills for query $Q$) to include in its system prompt.

This retrieval mechanism ensures that the agent is not overwhelmed by the entire skill library but instead receives targeted, high-value guidance exactly when it is needed.

## Empirical Findings and Performance Analysis

The effectiveness of SkillX was evaluated across several rigorous benchmarks: AppWorld (for complex tool use), BFCL-v3 (for function calling), and $\tau^2$-Bench (for multi-turn conversational interactions).

![Performance and efficiency analysis of SkillX](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04804v1/analysis.png)
*Figure 3: Analytical results demonstrating (a, b) the impact of different skill levels on performance and efficiency, (c) the gains from iterative refinement, and (d, e, f) the comparison of SkillX with other memory-based baselines.*

### Key Results
*   **Performance Gains:** Integrating SkillX led to substantial improvements in task success rates across all models. For example, the Qwen3-32B model saw a nearly 10% increase in success rate on tool-heavy benchmarks.
*   **Efficiency:** SkillX significantly reduced the number of execution steps and input tokens required to solve tasks. By following the "best practices" stored in the skill library, agents avoided costly trial-and-error exploration.
*   **Capability Transfer:** One of the most significant findings was that skills extracted from a strong model (like GLM-4.6) could be successfully used by a weaker model (like Qwen3-32B) to achieve performance levels far beyond the weaker model's base capabilities.
*   **Component Contribution:** Ablation studies (shown in Figure 3a and 3b) revealed that while functional skills ($S_{func}$) often provide the largest performance boost, the combination of all three levels is necessary for optimal performance and efficiency.

### Case Studies
Case studies across the benchmarks highlighted how SkillX prevents common failure modes.

![Case study from AppWorld](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04804v1/case_study_appworld.png)
*Figure 4: In AppWorld, SkillX enables correct cross-app integration and complex API patterns (like pagination) that a base model typically fails to execute correctly.*

![Case study from BFCL-v3](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04804v1/case_study_bfcl.png)
*Figure 5: In BFCL-v3, SkillX helps the agent follow safety sequences and prerequisite checks that are not explicitly detailed in the original tool documentation.*

![Case study from tau2-bench](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04804v1/case_study_tau2bench.png)
*Figure 6: In conversational tasks, the skill library provides guidance on handling topic shifts and verifying user claims according to specific policies.*

## Conclusion and Research Implications

The SkillX framework demonstrates that the automated construction of a hierarchical skill knowledge base is a viable path toward creating more generalizable and efficient LLM agents. By moving from raw trajectory memory to structured, multi-level skills, the framework enables agents to accumulate and reuse experience in a way that is both scalable and model-agnostic.

The findings suggest that the bottleneck for many current agents is not just their inherent reasoning ability, but their lack of structured, execution-oriented knowledge. SkillX provides a mechanism to bridge this gap, allowing agents to learn from their successes and failures and to transfer that knowledge across different tasks. This research lays a foundation for lifelong learning in autonomous systems, where agents become progressively more capable and efficient as they interact with their environments.

## Relevant Citations

- Expel: LLM agents are experiential learners: This paper introduces ExpeL, a framework for experience-driven agent learning, which is used as a primary baseline for comparison in the SkillX paper. ExpeL represents a competing approach where agents learn from retrieved past trajectories and distilled insights, making it highly relevant for evaluating SkillX's hierarchical skill-based method.
- Agent workflow memory: This paper proposes Agent Workflow Memory (AWM), which reuses modular workflows distilled from historical agent trajectories. AWM is a key baseline in SkillX's experiments, representing an alternative strategy for structuring and reusing agent experience, thereby providing a direct point of comparison for SkillX's multi-level skill design.
- Appworld: A controllable world of apps and people for benchmarking interactive coding agents: AppWorld is one of the main benchmarks used to evaluate SkillX. Its design, featuring a complex environment with hundreds of APIs and long-horizon tasks, motivates the need for efficient experience reuse and highlights the practical challenges that SkillX's automated skill library construction is designed to address.
- A-mem: Agentic memory for llm agents: A-Mem presents a framework for dynamically managing structured episodic memories for LLM agents. It is used as a representative baseline in the SkillX paper to compare different paradigms of experience management, making it crucial for contextualizing the performance and design of SkillX's skill knowledge base.
