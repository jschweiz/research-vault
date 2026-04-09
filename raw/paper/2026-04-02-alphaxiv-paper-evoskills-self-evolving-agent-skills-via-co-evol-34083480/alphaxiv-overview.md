# EvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification

- alphaXiv: https://www.alphaxiv.org/abs/2604.01687
- Source paper: https://arxiv.org/abs/2604.01687

## Evolution from Tools to Agent Skills

The development of Large Language Model (LLM) agents has traditionally focused on "tool-use"—the ability of a model to call external APIs or execute single functions to solve a problem. While effective for simple queries, many real-world professional tasks, such as scientific analysis, complex software debugging, or financial modeling, require more than isolated function calls. These tasks demand structured workflows that include goal decomposition, multi-step execution logic, error recovery, and intermediate validation. 

To bridge this gap, researchers have introduced the concept of "agent skills." Unlike a tool, which is typically a single, self-contained function, a skill is a structured package comprising workflow instructions, executable scripts, and domain-specific reference materials. These skills often span multiple files and offer a comprehensive template for solving specific classes of problems.

![Comparison between a single tool and a multi-file agent skill.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/tool_skill_diff.png)
*Figure 1: While tools are single-purpose functions, skills are structured collections of resources and logic designed for complex, multi-step tasks.*

Despite their potential, creating high-quality skills currently relies on manual human authoring. This process is not only labor-intensive but also suffers from "human-machine cognitive misalignment"—where human-designed workflows do not align with how LLMs naturally reason or process information. This misalignment can lead to sub-optimal performance, where adding a human-curated skill sometimes performs worse than no skill at all. EvoSkills addresses these challenges by introducing a framework for agents to autonomously generate and refine their own multi-file skills through a process of co-evolutionary verification.

## The Human-Machine Alignment Problem

The primary motivation for EvoSkills stems from the observation that human-authored guidance is not always optimal for AI agents. Evaluation benchmarks like SkillsBench have shown that human-curated skills yield inconsistent results. In certain domains, like natural science, these skills can actually degrade performance compared to a "no-skill" baseline. 

This happens because humans design workflows based on their own cognitive abstractions, which may involve steps or data structures that are intuitive for people but computationally inefficient or confusing for an LLM. Furthermore, existing self-evolving methods—where agents try to improve themselves—have mostly focused on simple, atomic functions (tools). These methods are not designed to handle the multi-file, inter-dependent nature of skills, nor do they function well without high-quality, ground-truth feedback, which is often unavailable in real-world scenarios.

## Formalizing the EvoSkills Framework

EvoSkills treats the task environment as a Partially Observable Markov Decision Process (POMDP). In this setting, the agent lacks full knowledge of the "ground-truth" tests used to evaluate success. Let the state space be $X$, actions (terminal commands and file edits) be $A$, and observations (command results) be $O$. A skill $S$ conditions the agent's policy $\pi_\theta$. The goal is to find an optimal skill $S$ that maximizes the expected terminal reward:

$$J(S) = \mathbb{E}_{\tau \sim P(\tau|\pi_\theta, S, M)} [R(x_T)]$$

where $R(x_T)$ is a binary success/failure signal from a hidden ground-truth test. Because direct optimization of this reward is difficult (the oracle is opaque), EvoSkills introduces a surrogate verifier reward $\tilde{R}(x, V)$. This reward is calculated based on a suite of deterministic test assertions $V = \{e_1, \dots, e_{|V|}\}$ created by an independent verifier.

![The EvoSkills framework architecture featuring the Skill Generator and Surrogate Verifier.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/x1.png)
*Figure 2: The framework utilizes an alternating optimization loop where a Skill Generator refines the skill and a Surrogate Verifier refines the testing logic.*

## Co-Evolutionary Verification Mechanics

The framework operates through two coupled feedback pathways, involving two distinct LLM instances: the Skill Generator and the Surrogate Verifier.

### The Skill Generator
The Skill Generator is responsible for creating and iteratively refining the multi-file skill bundles. It maintains a persistent conversation context $C$, initialized with task instructions $I$ and a domain-agnostic meta-skill $S_{\text{meta}}$. Each new skill revision $S^{(i+1)}$ is produced by considering the previous version $S^{(i)}$ and the feedback received:

$$C^{(i+1)} = C^{(i)} \oplus F^{(i,j)}$$

where $F^{(i,j)}$ is a structured diagnostic from the verifier.

### The Surrogate Verifier
The Surrogate Verifier acts as a proxy for the ground-truth reward. To avoid inheriting biases from the generator, it operates in a completely isolated LLM session $\pi^V_\theta$, seeing only the task instructions and the agent's current outputs $x^{(i)}$. It performs two main roles:
1.  **Diagnostic Feedback:** If the agent fails its tests ($\tilde{R} < 1$), it provides root-cause analysis and actionable suggestions.
2.  **Test Escalation:** If the agent's current output passes all surrogate tests ($\tilde{R} = 1$) but fails a ground-truth check (the "oracle"), the verifier is forced to strengthen its tests.

This "Test Escalation" is a critical feature. When a failure occurs that the current tests didn't catch, the verifier independently evolves its test suite to be more diverse and challenging:

$$V^{(j+1)} \sim \pi^V_\theta(\cdot | I, x^{(i)}, V^{(j)})$$

Crucially, the verifier never sees the ground-truth test content; it only receives an opaque signal $1[R(\hat{x}^{(i)}) < 1]$ indicating its current tests were insufficient.

## Benchmarking Skill Quality

The EvoSkills framework was evaluated on the SkillsBench dataset using models like Claude Opus 4.6. The results demonstrated that self-evolved skills significantly outperform both baseline agents and human-curated procedures.

![Pass rate growth across evolution iterations.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/x2.png)
*Figure 3: Performance improves steadily through iteration, surpassing human-curated benchmarks by the third round.*

In these tests, the EvoSkills framework achieved a 71.1% pass rate, which is a 40.5 percentage point (pp) increase over the "no-skill" baseline (30.6%) and a 17.6 pp improvement over human-curated skills (53.5%). Other automated methods, such as simple one-shot generation, showed almost no improvement over the baseline, suggesting that the iterative co-evolution process is the primary driver of skill quality.

![Performance comparison of EvoSkills against various baselines.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/x3.png)
*Figure 4: EvoSkills significantly outperforms standard self-generation and human-curated skills on professional tasks.*

## Cross-Model Transferability

A key finding of the research is that skills evolved by a high-performing model (like Claude Opus) are highly transferable to other LLM families. When these Opus-evolved skills were applied to models from GPT, Qwen, DeepSeek, and Mistral, they consistently improved performance by 36 to 44 percentage points over each model's baseline.

![Cross-model transferability of evolved skills.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/x4.png)
*Figure 5: Skills evolved by one model family provide substantial performance gains when deployed on different, unrelated models.*

This transferability suggests that EvoSkills does not just produce model-specific "hacks" but discovers fundamental task structures and procedural logic that are universally beneficial for LLM agents.

## Domain-Specific Success and Misalignment

The paper provides strong evidence for the "human-machine cognitive misalignment" theory through domain-level analysis. Self-evolved skills outperformed human-curated ones in 9 out of 11 professional domains tested. 

In fields like Finance and Cybersecurity, the gains were massive (+56.9 pp and +23.2 pp respectively). Most tellingly, in the Natural Science domain, human-curated skills actually performed worse than the no-skill baseline, whereas self-evolved skills provided a significant boost. This confirms that procedures designed by human experts can sometimes hinder an agent if they don't align with the agent's internal logic.

![Domain-level performance analysis showing human skill degradation.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/x5.png)
*Figure 6: In several domains, human-curated skills perform worse than having no skills at all, while self-evolved skills consistently excel.*

## Evolution Dynamics and Efficiency

Evolution is not an instantaneous process. The framework typically requires several cycles to converge on a high-quality skill. On average, a task requires 4.1 verification cycles (with the Surrogate Verifier) and 2.4 evolution rounds (triggered by the ground-truth oracle).

![Histograms of verification cycles and evolution rounds.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01687v1/x6.png)
*Figure 7: Most tasks converge within a few rounds, with the surrogate verifier handling the bulk of the iterative refinement cost.*

The use of a surrogate verifier is highly efficient. It absorbs much of the diagnostic burden, allowing the more expensive ground-truth oracle to be used sparingly. A case study on exoplanet detection illustrated this: the verifier caught initial coding bugs, while the ground-truth oracle eventually exposed a fundamental algorithmic limitation. This forced the agent to switch its entire strategy—from tuning a specific algorithm to replacing it entirely—resulting in a final skill that was much more robust than the human-designed alternative.

## Summary of Impact

EvoSkills demonstrates that LLM agents are capable of autonomously developing complex, multi-file skills that surpass the quality of human-authored procedures. By using a co-evolutionary approach that isolates the generator from the verifier, the framework provides a scalable way to equip agents with professional-grade capabilities without needing explicit human supervision or access to ground-truth test data.

The findings suggest a future where AI agents continuously refine their own operational libraries, discovering workflows that are optimized for their unique reasoning patterns. This not only reduces the manual labor of AI development but also unlocks higher performance in technical and scientific domains where human intuition may not be the best guide for machine execution.

## Relevant Citations

- Skillsbench: Benchmarking how well agent skills work across diverse tasks: This paper introduces the SkillsBench benchmark, which is the sole evaluation platform used in the EvoSkills paper. All experimental results, baseline comparisons, and performance claims for EvoSkills are validated using this benchmark, making it fundamental to the paper's contributions.
- Agent skills overview: This citation from Anthropic introduces the core concept of 'agent skills' which is the central subject of the EvoSkills paper. The paper's primary motivation is to automate the generation of these skills, moving beyond the labor-intensive human authoring process described by Anthropic.
- Sok: Agentic skills–beyond tool use in llm agents: This work provides a systematic definition of agent skills, distinguishing them from simpler tools. The EvoSkills paper builds upon this formalization to justify its focus on generating complex, structured, multi-file skill packages, which it argues existing tool-evolution methods cannot handle.
- Voyager: An open-ended embodied agent with large language models: This paper is cited as a prominent example of prior work on self-evolving agents. EvoSkills contrasts its approach with methods like Voyager to highlight the 'tool-skill gap,' arguing that existing frameworks for self-improvement are designed for simple functions or prompts, not the complex, multi-file skills EvoSkills generates.
