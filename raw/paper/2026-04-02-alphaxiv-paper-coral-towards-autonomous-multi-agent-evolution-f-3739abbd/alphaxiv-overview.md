# CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery

- alphaXiv: https://www.alphaxiv.org/abs/2604.01658
- Source paper: https://arxiv.org/abs/2604.01658

In the landscape of modern artificial intelligence, solving complex problems often involves iterative refinement. For tasks where the optimal solution is unknown—such as optimizing high-performance code or discovering new mathematical proofs—researchers typically rely on evolutionary search. Historically, these search processes have been "fixed," meaning a human designer dictates the rules for how solutions are proposed, evaluated, and updated. The CORAL framework represents a shift in this paradigm by delegating the control of the evolutionary process to autonomous Large Language Model (LLM) agents. By allowing multiple agents to coordinate asynchronously through shared knowledge, CORAL enables a form of "horizontal parallelism" that allows AI to explore and discover solutions in open-ended domains more effectively than traditional, rigid search algorithms.

![Comparison of evolutionary paradigms](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01658v1/x2.png)
*Figure 1: Evolution of search paradigms from fixed evolutionary loops to autonomous single-agent and multi-agent evolution. While fixed search relies on external rules for selection and updates, CORAL grants agents the autonomy to decide how to retrieve information, propose candidates, and store collective knowledge.*

## The Limitations of Fixed Evolutionary Search

Open-ended discovery is characterized by problems where the goal is to continuously improve a solution, guided by an evaluator $E(x, y)$ that provides a score $s$ and qualitative feedback $f$. In conventional systems like FunSearch or AlphaEvolve, an LLM acts as a "mutation operator." It receives a set of high-performing parent programs selected by a pre-defined algorithm (such as MAP-Elites) and is tasked with generating a slightly different version.

While successful, this approach has a significant drawback: the search strategy is rigid. The decision of which parent solutions to inspect, when to run intermediate tests, and what specific insights to record for future attempts are all determined by external heuristics. These heuristics are often generic and may not be optimal for a specific, complex problem like kernel engineering. CORAL addresses this by treating the evolutionary loop itself as a task for the agent. Instead of being told which parents to use, the agent is given a workspace and the autonomy to explore the history of all attempts, decide its own strategy, and manage its own internal "knowledge base."

## The CORAL Architecture: Autonomous Multi-Agent Evolution

The CORAL framework is built around the concept of a population of $N$ agents working in parallel. Unlike "vertical scaling" systems, where agents are assigned specific roles (like a "manager" and a "coder"), CORAL agents are homogeneous. They collaborate "horizontally" through an indirect coordination mechanism.

At the heart of the system is the Shared Persistent Memory, implemented as a structured file system. Each agent $i$ has its own private workspace but can read from and write to the shared repository. This repository is organized into three primary directories:

1.  **`attempts/`**: A leaderboard of historical candidate solutions, their source code, and their evaluation outcomes.
2.  **`notes/`**: A collection of markdown files where agents record observations, reflections, and analyses of what worked and what failed.
3.  **`skills/`**: A library of reusable tools, scripts, and implementation patterns that agents have developed to automate parts of their search.

![System architecture of CORAL](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01658v1/x3.png)
*Figure 2: The CORAL architecture. Multiple agents operate in private workspaces while interacting with a shared persistent memory. Heartbeat monitors periodically intervene to prompt reflection, consolidation of knowledge, or redirection if the search stagnates.*

This shared memory $M$ acts as a collective intelligence hub. When an agent $i$ writes a discovery $W_i^t$ to the memory, any other agent $j$ can retrieve that discovery as part of its context $M_j^t$ in a future iteration. This allows successful strategies to "diffuse" through the population naturally. If one agent discovers a specific loop-unrolling technique that improves performance, other agents can read the corresponding note, try the same technique on their own variations, and build upon it.

## Heartbeat Interventions and Strategic Steering

To ensure that autonomous agents remain productive over long horizons, CORAL introduces "heartbeat-based interventions." Because agents can sometimes get stuck in local minima (repeatedly trying variations of a failing strategy) or neglect to document their findings, the system manager periodically triggers structured prompts that force a modification to the agent's local context $C_i^t \to C_i^{t'}$.

There are three primary types of heartbeats:
*   **Reflection Heartbeats**: These occur at every iteration, prompting the agent to write a quick note about its current attempt. This captures immediate insights before they are lost in the next cycle.
*   **Consolidation Heartbeats**: These are triggered periodically to have the agents step back, review the collective notes, and merge overlapping findings into formal "skills."
*   **Redirection Heartbeats**: If an agent fails to improve its score after several attempts, this heartbeat activates. It prompts the agent to perform a "post-mortem" analysis of its recent failures and try a fundamentally different strategy, preventing the search from stagnating.

## Discovery in High-Stakes Domains

The researchers evaluated CORAL on two "stress-test" tasks that represent real-world discovery challenges: GPU kernel engineering and polyomino packing.

### Kernel Engineering
In kernel engineering, the goal is to optimize low-level GPU code to minimize execution cycles. This is a notoriously difficult task because performance depends on intricate hardware details like memory latency, register usage, and instruction scheduling. The primary metric is the speedup over a baseline:

$$\text{Score} = \frac{\text{Baseline Cycles}}{\text{Optimized Cycles}}$$

CORAL achieved a new state-of-the-art result on a standard benchmark, reducing the execution time from the previous best of 1,363 cycles down to 1,103 cycles. This 18.3% improvement was achieved by four agents working together to stack multiple optimization tricks—such as pipelining and data loading overlaps—that were discovered independently and then combined via the shared memory.

![Kernel engineering performance comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01658v1/x1.png)
*Figure 3: Performance of CORAL on the kernel engineering task. CORAL (4 agents) significantly outperforms both fixed evolutionary search (OpenEvolve) and its own single-agent variant, eventually surpassing the previous human-best known result.*

### Polyomino Packing
Polyomino packing is a geometric puzzle where agents must fit various shapes into a grid as tightly as possible. Unlike mathematical optimization, this requires spatial reasoning and the development of complex placement heuristics. CORAL agents successfully developed packing strategies that achieved 89.4% grid coverage, surpassing the previous best of 87%.

![Polyomino packing results](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01658v1/x4.png)
*Figure 4: Polyomino packing results. The autonomous evolution of CORAL allows it to discover dense packing arrangements that exceed the capabilities of a single-shot LLM attempt and previous optimized search results.*

## Why Does Autonomous Evolution Work?

The success of CORAL is not just a result of using more compute; it stems from how the agents use that compute. The researchers identified three key reasons for its performance:

**1. Knowledge Accumulation and Reuse**
In fixed evolutionary loops, the "knowledge" of the system is contained only in the source code of the parent solutions. In CORAL, the notes and skills provide a high-level conceptual understanding of the problem. Agents were found to refer to other agents' notes in 87% of successful rounds in the polyomino task. By creating "skills" (such as a custom benchmarking script), agents could automate the validation of their ideas, leading to a much higher "improvement rate" per evaluation.

**2. Exploration Diversity**
Because each agent maintains its own strategy and workspace, they explore different parts of the solution space. An analysis of the strategies used by the agents showed low overlap, meaning the population was effectively diversifying its search. One agent might focus on memory optimization while another focuses on arithmetic simplification. When one succeeds, the others can adopt the successful part of that strategy without losing their own unique approach.

**3. Local Verification**
Autonomous agents tend to run their own local tests before submitting a solution for formal evaluation. On the kernel engineering task, agents performed local tests 57% of the time. This "internal monologue" and self-correction loop mean that the evaluations the system does perform are of much higher quality, making more efficient use of the limited evaluation budget.

## Conclusion

CORAL demonstrates that the next step in AI-driven discovery lies in moving from rigid, human-designed algorithms to autonomous, self-organizing agent systems. By providing agents with the tools to manage their own evolution—shared memory, the ability to create skills, and mechanisms for reflection—CORAL allows for a more flexible and powerful search process. This framework not only achieves new state-of-the-art results in technical domains like code optimization but also provides a template for how collective AI intelligence can be harnessed to solve open-ended problems where the path to a solution is not yet mapped.

## Relevant Citations

- Mathematical discoveries from program search with large language models: This paper, which introduced FunSearch, is cited as the foundational work that established the paradigm of using LLMs within an evolutionary loop for open-ended discovery. CORAL's central thesis is to improve upon this 'fixed evolutionary search' model by granting agents greater autonomy, making this citation essential for context and contrast.
- Alphaevolve: A coding agent for scientific and algorithmic discovery: AlphaEvolve is presented as a significant extension of the FunSearch paradigm, applying it to full codebases. It serves as a prime example of the state-of-the-art fixed evolutionary search systems that CORAL directly compares against and aims to surpass by introducing agent autonomy.
- EvoX: Meta-evolution for automated discovery: EvoX is used as a primary experimental baseline and is explicitly identified in the paper as the 'strongest competitor' among existing fixed evolutionary search methods. This direct comparison is crucial for demonstrating the performance benefits of CORAL's autonomous, multi-agent framework over the previous state-of-the-art.
- Reflexion: Language agents with verbal reinforcement learning: This work is cited as a key inspiration from the autonomous LLM agent literature, specifically for its use of self-feedback and reflection. CORAL incorporates this concept into its design through its 'heartbeat' mechanism, which prompts agents to reflect and consolidate knowledge, thus bridging the gap between autonomous agent capabilities and evolutionary search.
