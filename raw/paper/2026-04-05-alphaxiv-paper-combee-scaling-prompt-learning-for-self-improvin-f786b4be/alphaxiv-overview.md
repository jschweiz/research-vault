# Combee: Scaling Prompt Learning for Self-Improving Language Model Agents

- alphaXiv: https://www.alphaxiv.org/abs/2604.04247
- Source paper: https://arxiv.org/abs/2604.04247

## Scaling Prompt Learning for Language Model Agents

Large Language Models (LLMs) are increasingly deployed as autonomous agents to solve complex, multi-step tasks in domains like software engineering, financial analysis, and legal research. While these models are pre-trained on vast datasets, they often encounter specific scenarios at inference time that require immediate adaptation. Traditionally, this was addressed through "prompt engineering"—manually crafting instructions to guide the model. More recently, the field has moved toward "prompt learning," where agents automatically refine their own instructions or "playbooks" based on their experiences.

A common approach involves a generate-reflect-update cycle: an agent performs a task, reflects on its performance, and then updates a shared context or playbook. However, as agentic systems scale to handle thousands of tasks in parallel, current prompt learning methods face a significant bottleneck. Naive parallelization—simply feeding many reflections at once to an "aggregator" LLM—leads to a phenomenon called "context overload." In this state, the aggregator model struggles to process dense information, often discarding specific, high-value insights in favor of generic patterns, which degrades the agent's accuracy.

![Combee Framework Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04247v1/x3.png)
*Figure 1: The Combee framework architecture, illustrating the Map-Shuffle-Reduce paradigm for scaling prompt learning.*

To address this, researchers from UC Berkeley, Stanford, and other institutions developed Combee. This framework scales prompt learning by adopting a distributed "Map-Shuffle-Reduce" paradigm. It introduces a hierarchical parallel scan algorithm, augmented shuffling, and a dynamic batch size controller to ensure that agents can learn from massive volumes of data efficiently without sacrificing the quality of the learned knowledge.

## The Challenge of Context Overload

When prompt learning is performed sequentially, an agent learns from one experience at a time. This is high-quality but extremely slow for large datasets. To speed this up, researchers tried increasing the batch size, allowing the model to reflect on multiple trajectories simultaneously.

The problem, however, is that LLMs have a "cognitive" limit when distilling information. Even if the text of 100 reflections fits within the model's token limit (context window), the model's ability to extract and synthesize unique insights from each reflection diminishes. This is known as context overload. As shown in Figure 2, as the batch size increases in naive setups, the number of useful context updates drops sharply, dragging down the agent's task accuracy.

![Context Overload Impact](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04247v1/x2.png)
*Figure 2: Evidence of context overload. As the batch size increases (x-axis), the number of meaningful context updates and the resulting accuracy decrease.*

Instead of learning a detailed, 5,000-token playbook of specific rules, a model under context overload might produce a 500-token summary of generic advice. This loss of information is fatal for agents performing complex tasks that require precise, domain-specific instructions.

## The Combee Framework: Map-Shuffle-Reduce for Prompts

Combee restructures the prompt learning process into three distinct phases inspired by distributed computing: Map, Shuffle, and Reduce.

### The Map Phase: Parallel Execution and Reflection
In the Map phase, $n$ parallel agents are deployed to handle $n$ different queries. Each agent executes its task and generates a trajectory—a log of its actions and the environment's responses. Following execution, the agent reflects on its own trajectory to identify what went well and what failed. This results in $n$ individual reflections.

### The Shuffle Phase: Augmented Shuffling
Before these reflections are aggregated, Combee applies "augmented shuffling." Each reflection is duplicated $p$ times (typically $p = 2$) and then randomly shuffled. This duplication ensures that high-importance insights have multiple chances to be noticed by the aggregator models. This approach is conceptually similar to "self-consistency" techniques in LLM reasoning, where multiple paths are taken to find a robust answer.

### The Reduce Phase: Parallel Scan Aggregation
This is the core of Combee's efficiency. Instead of one LLM trying to read all $n$ reflections, Combee uses a hierarchical "parallel scan." The reflections are split into $k$ subgroups. An LLM aggregates reflections within each subgroup into intermediate context updates. Then, another LLM combines these intermediate updates into a final global context update. 

The researchers found that setting the number of subgroups $k = \lfloor\sqrt{n}\rfloor$ creates a balanced tree where each LLM processes a manageable amount of information at each level. This prevents any single model from being overwhelmed, effectively bypassing the context overload problem.

## Dynamic Batch Size Control

Selecting the right batch size $bs$ is a balancing act. A small batch size is high-quality but slow; a very large batch size might be fast but risks quality degradation if the hierarchy isn't deep enough. Combee includes a controller that profiles the system during the first few iterations.

The controller measures the time taken for an epoch at different candidate batch sizes and fits a power-law curve:
$$
T_{epoch}(bs) = A \cdot bs^{-\alpha}
$$
where $T_{epoch}$ is the estimated time and $bs$ is the batch size. The controller identifies the "plateau batch size"—the point where further increasing $bs$ provides diminishing returns in speedup. It sets a threshold $\tau_1$ to choose the largest possible batch size that still offers meaningful efficiency gains.

## Evaluation and Performance

Combee was evaluated on several demanding benchmarks, including **AppWorld** (multi-step API tasks), **Terminal-Bench** (command-line operations), and finance-specific tasks like **FiNER** and **Formula**. It was integrated into two existing prompt learning frameworks: **ACE** (Agentic Context Engineering) and **GEPA** (Generative Prompt Evolution Agent).

### Speed and Efficiency
On the Terminal-Bench 2.0 dataset, Combee achieved a 17.2x speedup compared to sequential learning. In AppWorld, it achieved a 12x speedup. Crucially, these speedups were achieved without increasing the total computational cost (the number of tokens processed), as the hierarchical structure simply redistributes the work rather than multiplying it exponentially.

![Performance Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04247v1/x1.png)
*Figure 3: Quality-delay tradeoff and context size comparison. Combee (star) maintains high accuracy while significantly reducing training time and retaining larger, more detailed playbooks.*

### Quality Retention
While naive parallelization saw accuracy drop as batch sizes grew, Combee maintained high quality. For example, in the Formula benchmark, naive parallelization with a batch size of 100 saw accuracy drop to 72.5%. Combee, with the same degree of parallelism, maintained accuracy comparable to the high-quality sequential baseline (around 85%).

The secret to this quality lies in the richness of the learned context. In AppWorld, the playbook learned by Combee was approximately 13 times larger in token count than the one produced by naive parallelization. This indicates that Combee successfully captured the fine-grained details necessary for the agent to navigate complex API calls.

## Significance of the Work

The primary contribution of Combee is demonstrating that prompt learning—an inherently "cognitive" task for LLMs—can be scaled using principles from distributed systems. By recognizing that context overload is a functional limitation of how LLMs process information rather than a raw token-limit issue, the authors developed a framework that allows agents to learn from vast amounts of parallel experience.

This has several implications for the future of AI agents:
1.  **Continuous Adaptation:** Large-scale agent deployments can now update their "knowledge bases" or playbooks in near real-time, learning from thousands of users simultaneously.
2.  **Resource Efficiency:** Because Combee is framework-agnostic and does not require model fine-tuning, it provides a cost-effective way to improve agent performance without the massive GPU requirements of training new weights.
3.  **Robustness:** The use of augmented shuffling and hierarchical aggregation makes the learning process more robust to "noise" in individual reflections, ensuring that only reliable patterns are consolidated into the agent's long-term memory.

In conclusion, Combee provides a scalable path for creating self-improving agents. By moving from simple batching to a structured Map-Shuffle-Reduce approach, it enables language models to effectively "digest" large-scale interactions, turning raw traces into actionable, high-quality expertise.

## Relevant Citations

- Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models: This paper introduces ACE, one of the two primary prompt learning frameworks that Combee is built directly upon. Combee's main contribution is to scale the 'generate-reflect-update' loop exemplified by ACE to handle high parallelism, making this citation foundational to the paper's problem definition and evaluation.
- GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning: This work introduces GEPA, the second core prompt learning method that Combee is prototyped and evaluated on. Alongside ACE, GEPA serves as a key example of the sequential prompt learning systems that suffer from 'context overload', a problem Combee is designed to solve.
- Prefix sums and their applications: This classic computer science paper is the origin of the parallel scan algorithm, which is the core technical mechanism Combee uses for its 'parallel scan aggregation' component. This algorithm is Combee's main solution to the 'context overload' problem, making this a direct and crucial methodological inspiration for the work.
- Reflexion: Language Agents with Verbal Reinforcement Learning: This paper is frequently cited as a key example of the 'generate-reflect-update' paradigm that the Combee framework aims to scale. The concept of agents reflecting on past trajectories to extract insights for future improvement is central to the problem Combee addresses, and Reflexion is an influential work that helps establish this approach.
