# SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization

- alphaXiv: https://www.alphaxiv.org/abs/2604.02268
- Source paper: https://arxiv.org/abs/2604.02268

In the rapidly evolving field of Large Language Model (LLM) agents, a key goal is to develop systems that can perform complex, multi-step tasks autonomously. Currently, the most successful approach involves "skill augmentation," where an agent is given a library of procedural knowledge—such as how to use a specific tool or how to solve a logic puzzle—and retrieves relevant skills to include in its prompt at each step. While effective, this creates a perpetual dependency: the agent never actually "learns" the skill; it simply follows the instructions provided in its context window.

SKILL0 proposes a shift from this "retrieve-and-prompt" paradigm toward **skill internalization**. Drawing an analogy to human learning, where we move from following a manual to performing a task from memory, SKILL0 introduces a framework that allows agents to consolidate external skills into their own model parameters. The core philosophy is "Skills at training, zero at inference," meaning that while the agent uses skills as scaffolding during its learning phase, it eventually operates entirely without them.

![Comparison of Skill Augmentation vs. Skill Internalization](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02268v1/x1.png)
*Figure 1: Traditional skill augmentation (top) relies on continuous retrieval from a skill bank, increasing token costs and noise. SKILL0 (bottom) uses a training-time curriculum to internalize these skills, enabling zero-shot inference without external prompts.*

## The Challenges of Skill Augmentation

Current LLM agents primarily rely on inference-time augmentation, where a skill bank is searched for relevant textual descriptions that are then injected into the model's prompt. While this allows models to handle tasks they weren't originally trained for, it introduces several fundamental bottlenecks:

1.  **Retrieval Noise:** Semantic search (finding skills based on text similarity) is imperfect. Irrelevant or misleading skill descriptions can confuse the agent, leading to "context corruption" where the model fails because it follows the wrong advice.
2.  **Token Overhead:** Injecting long skill descriptions significantly increases the number of tokens the model must process. In multi-turn interactions, these costs compound, making the system slower and more expensive to run.
3.  **Lack of True Agency:** If an agent can only perform a task when a manual is provided in its context, it hasn't truly acquired the capability. The intelligence resides in the prompt, not the model parameters. This makes the agent fragile—if the retrieval system fails, the agent's performance collapses.

SKILL0 addresses these issues by treating skills as a curriculum for Reinforcement Learning (RL). By providing skills during training but systematically withdrawing them, the model is forced to internalize the logic of those skills into its weights.

## The SKILL0 Technical Framework

The SKILL0 architecture is designed to handle the transition from guided execution to autonomous mastery. It consists of three primary layers: a visual-aware agent loop, an in-context reinforcement learning objective, and an adaptive curriculum.

![SKILL0 Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02268v1/x2.png)
*Figure 2: The SKILL0 framework, showing the interaction between the skill bank, the visual agent loop, and the curriculum-driven reinforcement learning process.*

### 1. The Agent Loop and Visual Rendering
The agent operates in a sequential environment, generating actions $a_t$ based on a task instruction $I$ and the history of interactions $h_t$. To solve the token overhead problem, SKILL0 uses a vision-based approach. Rather than feeding long text histories back into the model, the system renders the textual context into a compact RGB image $V_t$ using a vision encoder $Enc$. This visual representation preserves the structure of the task history while using far fewer tokens than raw text.

Furthermore, the model learns to output a dynamic compression ratio $c_t$. This allows the agent to decide how much detail it needs from its history at any given time, further optimizing efficiency.

### 2. Hierarchical SkillBank
Instead of flat retrieval, SKILL0 organizes knowledge into a `SkillBank` containing General skills (logic, general tool-use) and Task-specific skills. During training, the agent doesn't just retrieve based on similarity; it selects a subset $S$ of skill files based on their "on-policy helpfulness"—a measure of how much a specific skill actually improves the current model's performance on a task.

## In-Context Reinforcement Learning (ICRL)

The internalization process is driven by a specialized reinforcement learning objective. Standard RL often struggles with "sparse rewards," where an agent gets no feedback until the very end of a long task. By providing skills in the context during training, SKILL0 gives the agent "scaffolding" that makes early exploration more successful.

To encourage both task success and efficiency, SKILL0 utilizes a composite reward function $\tilde{r}_t$:

$$\tilde{r}_t = r_t + \lambda (I_{succ}(\tau) - \log(c_t))$$

In this equation, $r_t$ is the standard task reward, $I_{succ}(\tau)$ is a binary indicator of whether the task was ultimately successful, and $\log(c_t)$ is a penalty for high context usage. The hyperparameter $\lambda$ balances the trade-off between succeeding at the task and being efficient with memory.

The policy is updated using a PPO-like objective function $L_{SKILL0}(\theta)$. This objective uses importance-sampled advantage values $A_i$ to update the model weights. To ensure the model doesn't deviate too drastically from its original reasoning capabilities, a KL divergence regularization term is included, which penalizes the difference between the current policy and a stable reference model $\pi_{ref}$.

## Adaptive Curriculum Learning

The most critical component of SKILL0 is the **Helpfulness-Driven Dynamic Curriculum**. This is what ensures that skills are actually internalized rather than just followed. The curriculum operates in two phases:

### Phase 1: Relevance-Driven Grouping (Offline)
Before training begins, the system partitions the training data into $N$ sub-tasks $T_k$. Each sub-task is associated with specific skill files $S_k$ from the SkillBank. This creates a structured environment where the system knows which skills are theoretically relevant to which tasks.

### Phase 2: Dynamic Decay (Online)
Training is divided into $N_S$ stages. In each stage $s$, the agent has a "skill budget" $M^{(s)}$—the maximum number of skill files it can look at. Critically, this budget $M^{(s)}$ decays linearly over time, eventually reaching zero.

To decide which skills to keep as the budget shrinks, the system evaluates the **helpfulness** $\Delta_k$ of each skill. Every $d$ steps, the model is tested on a validation sub-task $T_k$ both with and without the skill $S_k$. If the model performs just as well without the skill, $\Delta_k$ is low, and the skill is a candidate for removal. If the model still struggles without it, the skill is kept in the prompt to provide continued guidance.

This "rise-then-fall" pattern of helpfulness is a hallmark of internalization:
*   **Early Training:** The agent hasn't learned the skill, so providing it in the prompt helps significantly (high $\Delta_k$).
*   **Late Training:** The agent has "memorized" the skill logic into its parameters, so the prompt becomes redundant (low $\Delta_k$).

## Experimental Results and Performance

SKILL0 was evaluated on two challenging benchmarks: **ALFWorld** (a synthetic environment for multi-step household tasks) and **Search-QA** (complex question answering requiring multi-hop search).

### Performance and Efficiency
The results demonstrate that SKILL0 significantly outperforms existing RL-based agents. On ALFWorld, a 3B-parameter model using SKILL0 achieved an 87.9% success rate, outperforming the baseline AgentOCR (78.2%). More importantly, it achieved this while using significantly fewer tokens.

| Method | Success Rate (ALFWorld) | Tokens per Step |
| :--- | :--- | :--- |
| SkillRL (Augmentation) | 82.4% | 2.21k |
| AgentOCR (Baseline) | 78.2% | 0.81k |
| **SKILL0 (Ours)** | **87.9%** | **0.38k** |

As shown in the table, SKILL0 is not only more effective but also over 5 times more token-efficient than standard skill-augmented methods. This efficiency stems from the fact that at inference time, SKILL0 does not need to retrieve or process any skill descriptions.

### Training Dynamics
The training curves provide evidence of the internalization process. Initially, models evaluated with skill prompts perform better. however, as training progresses, the "skill-free" performance of SKILL0 catches up to and eventually matches the "skill-guided" performance.

![Reward Curves during RL Training](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02268v1/x3.png)
*Figure 3: Reward curves for 3B models showing SKILL0 (red) maintaining higher and more stable rewards than the baseline (blue).*

![Internalization Accuracy](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02268v1/x5.png)
*Figure 4: Accuracy tracked during training. Note how the "without skill" accuracy (purple) eventually converges with the "with skill" accuracy (green), signifying successful internalization.*

## Ablation: Why the Curriculum Matters

The researchers conducted ablation studies to determine if the decaying budget was truly necessary. They compared the decaying budget $[6, 3, 0]$ with a fixed high budget $[6, 6, 6]$.

![Ablation Study of Skill Budgets](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02268v1/ablations.png)
*Figure 5: Comparison of different budget strategies. The decaying budget (left) is the only one that achieves a performance gain when skills are removed, indicating successful internalization.*

If the model is always given skills during training (fixed high budget), it becomes "lazy" and over-reliant on the prompt. When those skills are removed at inference time, performance drops by over 13%. In contrast, SKILL0's decaying curriculum forces the model to take over the reasoning process, leading to a slight performance *increase* when the "distracting" prompts are finally removed at the end of training.

## Conclusion

SKILL0 represents a significant step toward creating truly autonomous AI agents. By moving beyond the "retrieve-then-prompt" model, it demonstrates that complex procedural knowledge can be consolidated directly into the parameters of a large language model. This not only makes agents more efficient and less expensive to operate but also makes them more robust.

The success of the helpfulness-driven curriculum suggests that "scaffolding" is a powerful tool for agentic reinforcement learning. By providing the right information at the right time—and then taking it away—we can train agents that don't just follow instructions but truly "understand" the skills required to navigate complex environments. While the framework currently depends on a high-quality initial skill bank, it sets the stage for future research into agents that can autonomously discover, refine, and internalize their own libraries of expertise.

## Relevant Citations

- Skillrl: Evolving agents via recursive skill-augmented reinforcement learning: This paper introduces SkillRL, a key baseline representing the 'skill augmentation' paradigm where skills are provided in-context during inference. SKILL0 directly contrasts its 'skill internalization' approach with SkillRL's, uses it as a primary performance benchmark, and even initializes its skill library from SkillRL's resources, making it a fundamental point of comparison.
- Agentocr: Reimagining agent history via optical self-compression: This work is the direct inspiration for SKILL0's context rendering mechanism, which compresses textual history and skills into an image to reduce token overhead. AgentOCR also serves as a critical reinforcement learning baseline in the experiments, allowing for a direct comparison of SKILL0's internalization approach against another method that uses a compressed visual context.
- Agent skills for large language models: Architecture, acquisition, security, and the path forward: This paper is cited as a foundational work that defines and surveys the concept of 'agent skills' as reusable, structured knowledge. SKILL0 builds directly upon this concept by proposing a novel method for skill acquisition (internalization), positioning its contribution within the broader research area framed by this work.
- Reflexion: Language agents with verbal reinforcement learning: Reflexion is a seminal work in enhancing agent capabilities through self-reflection and experience, a form of verbal reinforcement learning. It is included as a key prompt-based agentic baseline in the extended comparisons, representing an alternative approach to improving agent performance without direct skill injection, thereby providing a valuable reference point for SKILL0's learning-based internalization method.
