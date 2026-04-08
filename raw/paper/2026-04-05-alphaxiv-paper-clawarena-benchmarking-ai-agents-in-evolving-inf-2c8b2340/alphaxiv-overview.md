# ClawArena: Benchmarking AI Agents in Evolving Information Environments

- alphaXiv: https://www.alphaxiv.org/abs/2604.04202
- Source paper: https://arxiv.org/abs/2604.04202

## Introduction: The Challenge of Persistent AI Agents

The rapid advancement of Large Language Models (LLMs) has transitioned AI from simple chatbots to sophisticated agents capable of managing workflows, executing code, and retrieving information. In many real-world applications, these agents are deployed as persistent assistants—systems that interact with users over extended periods, managing multiple information channels like Slack, email, and internal workspaces. However, most current evaluation benchmarks operate under the assumption of a static environment with a single, authoritative source of truth.

In practice, information is rarely static or consistent. A project’s direction might change during a morning meeting, only to be updated again in a private Slack message or a revised spreadsheet. Current benchmarks often fail to capture this complexity, focusing instead on tool use or single-hop retrieval from fixed evidence. ClawArena is a benchmark designed to address this gap by evaluating AI agents in evolving information environments. It tests whether agents can resolve multi-source conflicts, revise their beliefs as new data arrives, and adapt to implicit user preferences without explicit instruction.

![ClawArena Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/overview.png)
*Figure 1: Overview of ClawArena, illustrating the complex, multi-channel environment where agents must reconcile conflicting and evolving information.*

## The Three Pillars of Evolving Information

The core of ClawArena is built around three structural challenges that arise in sustained human-in-the-loop deployments:

1.  **Multi-source Conflict Reasoning (MS):** In a professional environment, information is scattered across heterogeneous sources such as chat logs, workspace files, and monitoring data. These sources often contradict each other. An agent must determine which source is more reliable—for example, prioritizing a final audit report over an initial informal chat.
2.  **Dynamic Belief Revision (DU):** Real-world environments are not static snapshots. New evidence emerges that can invalidate previous conclusions. An agent must be able to explicitly revise its internal model of the world, rather than simply appending new facts to a growing list of contradictory information.
3.  **Implicit Personalization (P):** Users rarely give a complete list of their preferences at the start of a project. Instead, preferences regarding formatting, tone, and analytical style surface through interactions, feedback, and corrections. Persistent agents must learn these patterns and apply them consistently without being reminded in every prompt.

By integrating these three dimensions, ClawArena provides a holistic evaluation of an agent's ability to maintain a reliable "ground truth" amidst noise and change.

## Methodology: The Six-Layer Scenario Design

To ensure a rigorous evaluation, ClawArena uses a unique multi-layer scenario design. Each scenario is built around a hidden ground truth, referred to as the Narrative Bible or Layer 0 ($L_0$). This layer defines the objective timeline and the definitive answers for all questions. The agent never sees $L_0$; instead, it is exposed only to noisy, partial, and potentially contradictory traces of this truth through subsequent layers.

The layers available to the agent include:
*   **Layer 1 ($L_1$):** Workspace files, such as spreadsheets, code repositories, and logs.
*   **Layer 2 ($L_2$):** Session histories, including multi-channel communications like Slack, email, and IMs.
*   **Layer 3 ($L_3$):** Evaluation questions.
*   **Layer 4 ($L_4$):** Staged update packages that arrive at specific intervals to simulate the passage of time.

This separation ensures that answer correctness is verified against an objective reality ($L_0$), not just against whatever the latest message happens to be. The benchmark includes 64 scenarios across 8 professional domains, such as Hospital Administration, Nonprofit Management, and Tech Startups.

![Pipeline of Construction](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/pipeline_v2.png)
*Figure 2: The construction pipeline for ClawArena, which leverages real-world statistical distributions to generate authentic, multi-layered scenarios.*

## Designing for Realistic Conflict and Updates

To test an agent's reasoning depth, ClawArena embeds four canonical evidence relations within its scenarios:
*   **Factual Conflict ($C_1$):** Direct contradictions between two sources (e.g., File A says "Blue," Message B says "Red").
*   **Authority Conflict ($C_2$):** Contradictions where one source clearly has more weight (e.g., an official log vs. a rumor).
*   **Non-conflict Slots ($C_3$):** Situations that might appear contradictory but are actually consistent, testing whether agents "over-flag" errors.
*   **Temporal/Process Conflict ($C_4$):** Information that was true at time $t$ but is no longer true at time $t+1$.

The benchmark also utilizes a staged update mechanism. Information is released in phases, introducing incomplete narratives followed by confirmations or contradictions. This allows researchers to track how an agent's performance changes as the environment evolves, specifically measuring the rate at which they successfully "self-correct."

## Evaluation Metrics and Question Taxonomy

ClawArena employs a 14-category question taxonomy that covers recall and reasoning for each of the three main pillars (MS, DU, P) and their intersections. For example, a question might require reasoning about a multi-source conflict ($MS$) that was further complicated by a recent update ($DU$).

![Question Taxonomy](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/sunburst_v7_notext.png)
*Figure 3: The taxonomy of evaluation rounds in ClawArena, showing the distribution of questions across static, dynamic, and execution-based categories.*

The benchmark uses two primary formats:
1.  **Multi-choice Set-selection:** Agents must select the correct subset from 7–9 candidate statements. Scoring is calculated using a per-option accuracy formula:
    $$1 - \frac{fp + fn}{n}$$
    where $fp$ is false positives, $fn$ is false negatives, and $n$ is the total number of options.
2.  **Executable Checks:** These verify if an agent's claims about workspace data can be grounded in actual files. For instance, if an agent claims to have fixed a bug, a sandboxed shell environment runs a test suite to verify the fix.

## Experimental Findings: Frameworks vs. Models

The benchmark was used to evaluate several state-of-the-art language models and agent frameworks. One of the most significant findings was the capability gradient between models. When the framework was kept constant, the model-induced performance range was $0.154$, whereas the framework-induced range (when the model was kept constant) was only $0.092$. This suggests that the intrinsic reasoning and memory capabilities of the base LLM are currently more influential than the specific architecture of the agent framework.

![Case Analysis 1-2](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/12.png)
*Figure 4: Analysis of Multi-Source Conflict Reasoning and Dynamic Belief Revision, showing how different frameworks can either mitigate or exacerbate model biases.*

### Key Model Results:
*   **Claude Opus 4.6** achieved the highest overall score of $0.735$.
*   **Claude Sonnet 4.6** followed closely with $0.708$ and performed best on executable checks ($0.489$).
*   **GPT-5.2** scored $0.581$, though it showed a distinct advantage in Chinese-language scenarios, likely due to its training data distribution.

### Framework Performance:
The MetaClaw framework, which features a skill-driven self-evolution mechanism, achieved an overall score of $0.603$, outperforming its base version, OpenClaw ($0.579$), by $4.1\%$. This improvement was particularly notable in execution-based tasks, suggesting that self-evolution helps agents better navigate workspace files and tools.

![Case Analysis 3-4](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/34.png)
*Figure 5: Case studies on self-diagnostic accuracy and implicit preference compliance.*

## Error Analysis and Persistent Biases

ClawArena’s fine-grained diagnostic capabilities revealed several recurring failure modes in modern AI agents:

**Narrative Anchoring Bias:** Agents often "lock in" on the first narrative they encounter. Even when subsequent updates provided explicit evidence to the contrary, many agents continued to rely on the initial, now-outdated information. This was particularly evident in "belief revision" questions where concentrated, targeted updates led to performance drops of $0.28$ to $0.36$.

**Tool-Chain Bottlenecks:** There was a significant gap between an agent's ability to reason about a problem and its ability to execute a solution. For example, in one hospital administration scenario, a model achieved $95.2\%$ on multi-choice reasoning but $0.0\%$ on the associated executable checks. This discrepancy indicates that grounding reasoning in practical workspace actions remains a major hurdle.

**Temporal Policy Scoping:** Agents struggled with "Norm Retroactivity." If a user introduced a new formatting rule ($P$) in the middle of a project, agents often mistakenly applied that rule to documents created *before* the rule was established, failing to understand the temporal scope of user preferences.

![Case Analysis 5-6](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/56.png)
*Figure 6: Case studies illustrating the "Declaration-Reality Gap" in executable checks and statistical methodology conflicts.*

## Implications for the Future of AI Development

ClawArena highlights that building a truly persistent AI assistant requires more than just scaling context windows or improving retrieval. It requires agents that can:
*   **Model Source Reliability:** Not all information is equal. Agents must learn to weigh evidence based on its provenance and authority.
*   **Actively Prune Beliefs:** Instead of just accumulating data, agents must proactively discard or "mark" information that has been superseded by new updates.
*   **Integrate Long-term Implicit Memory:** Personalization must be handled as a continuous learning process rather than a one-time instruction.

![Case Analysis 7-8](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04202v1/78.png)
*Figure 7: Final case studies showing the difficulty of full-dimension integration where MS, DU, and P all interact simultaneously.*

By providing a benchmark that mirrors the messiness and evolution of real-world information, ClawArena offers a path forward for developing more reliable, adaptable, and personalized AI agents. As models continue to improve, this framework will serve as a rigorous testing ground for the next generation of autonomous digital assistants.

## Relevant Citations

- Swe-bench: Can language models resolve real-world github issues?: This paper introduces a key task-oriented benchmark that ClawArena contrasts itself with. The authors cite SWE-bench as an example of an existing evaluation that uses a single-authority environment, highlighting the gap ClawArena fills by introducing multi-source conflicts and dynamic updates.
- Agentbench: Evaluating llms as agents: AgentBench is a foundational benchmark for LLM agents that helps contextualize the contribution of ClawArena. The paper positions ClawArena as a necessary next step, moving beyond the static, single-source tasks common in benchmarks like AgentBench to evaluate performance in more realistic, evolving information environments.
- Adaptive chameleon or stubborn sloth: Revealing the behavior of large language models in knowledge conflicts: This work, also known as ConflictQA, is highly relevant as it directly investigates how LLMs handle conflicting claims, a core theme of ClawArena. The paper cites this work to demonstrate that while static conflicts have been studied, ClawArena's key innovation is adding dynamic belief revision, where agents must update conclusions as new evidence arrives.
- Gaia: A benchmark for general ai assistants: GAIA represents the state-of-the-art for evaluating general-purpose AI assistants, which is the target agent type for ClawArena. The paper cites GAIA to differentiate its own specific focus on belief maintenance amid conflicting and evolving evidence from other benchmarks that test a broader, but less dynamic, set of agent capabilities.
