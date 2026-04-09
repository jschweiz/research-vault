# Meta-Harness: End-to-End Optimization of Model Harnesses

- alphaXiv: https://www.alphaxiv.org/abs/2603.28052
- Source paper: https://arxiv.org/abs/2603.28052

The performance of large language model (LLM) systems is defined not only by the parameters of the underlying model but also by the "harness"—the external software environment that manages how information is retrieved, stored, and presented to the model. While significant research effort is dedicated to optimizing model weights, the development of these harnesses remains largely a manual, trial-and-error process. Manual harness engineering involves human practitioners inspecting failure cases, adjusting prompts, and refining context-management heuristics.

Recent studies suggest that for the same underlying model, the design of the harness can result in up to a six-fold difference in performance on standard benchmarks. This gap highlights the criticality of harness design and the potential for automated optimization. However, current automated text and prompt optimization methods often struggle with the complexity of harnesses. These systems are typically "stateful" programs where decisions made early in an interaction (such as what to store in memory) have long-horizon consequences for later steps. Traditional optimizers, which rely on compressed feedback like scalar scores or short summaries, often lose the diagnostic granularity needed to identify and fix these complex, multi-step failures.

## The Meta-Harness Framework: Agentic Search in Code-Space

Meta-Harness is an end-to-end optimization system that automates the discovery of high-performing harnesses. It treats the harness as a stateful program that encapsulates an LLM and manages the context the model perceives at each step. 

![Meta-Harness System Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.28052v1/x3.png)
*Figure 1: The Meta-Harness optimization loop. An agentic proposer (1) generates harness code by inspecting a filesystem of prior experience. The candidate is evaluated on tasks (2), and its full execution logs, including reasoning traces and scores, are stored back into the filesystem (3) for future iterations.*

Formally, given a fixed language model $M$ and a task distribution $X$, a harness $H$ produces a rollout trajectory $\tau$. The system aims to find an optimal harness $H^*$ that maximizes the expected reward $r(\tau, x)$ across the task distribution:

$$
H^* = \arg \max_H \mathbb{E}_{x \sim X, \tau \sim p_M(H,x)} [r(\tau, x)]
$$

Unlike previous methods that optimize over prompt strings or limited templates, Meta-Harness searches directly in the space of executable code. The core innovation lies in its feedback mechanism: instead of providing the optimizer with a "compressed" summary of past performance, Meta-Harness gives a coding agent (the proposer) selective access to a full, uncompressed filesystem $D$ containing all prior candidate code, evaluation scores, and detailed execution traces.

The optimization process follows an iterative loop:
1.  **Search History Access:** The proposer, an LLM-based coding agent, uses standard terminal tools (e.g., `grep`, `cat`) to browse the filesystem $D$. This allows the agent to inspect the raw prompts, model outputs, and tool-call sequences that led to specific failures in previous versions.
2.  **Harness Proposal:** Based on its reasoning, the agent proposes $k$ new harness candidates. Because the search happens in code-space, the agent can introduce entirely new logic for retrieval, state updates, or prompt construction.
3.  **Evaluation and Logging:** Each new harness is evaluated on a subset of task instances. Critically, every bit of diagnostic data—up to millions of tokens per evaluation—is logged to the filesystem.
4.  **Refinement:** This cycle repeats for $N$ iterations, building a comprehensive database of "what worked and what didn't," allowing the proposer to form and test causal hypotheses about harness design.

## The Role of Uncompressed History

A central finding of this research is the importance of providing the proposer with "uncompressed" historical data. Most existing optimizers operate under strict context constraints, often providing the proposer with only the most recent results or a brief summary of failures. In contrast, Meta-Harness treats the entire history of the search as a browsable knowledge base. 

The necessity of this approach is evident when dealing with harnesses that manage memory. A failure at step 50 of a task might be caused by a suboptimal storage decision at step 2. A scalar score ("0/1") or a high-level summary ("model failed to find information") is insufficient to diagnose that the specific data point was never stored in the harness's state. By allowing the proposer to inspect the raw execution trace $\tau_x$ for a specific instance $x \sim X$, Meta-Harness enables the agent to identify the exact line of code responsible for the upstream failure.

![Harness Optimizer Search Progress](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.28052v1/x5.png)
*Figure 2: Search progress comparison in the online text classification domain. Meta-Harness reaches superior performance significantly faster than existing text optimizers like OpenEvolve or TTT-Discover, which use more restricted feedback channels.*

Ablation studies conducted by the authors confirmed this: providing only scores or human-written summaries of failures resulted in significantly lower final performance compared to providing the agent with raw execution logs. The agent's ability to selectively "deep-dive" into specific traces is what allows it to navigate the vast search space of executable code effectively.

## Evaluating Meta-Harness Across Diverse Domains

To test the generality of the approach, the authors evaluated Meta-Harness across three distinct domains: online text classification, math reasoning, and agentic coding.

### Online Text Classification
In the classification domain, the harness must decide which previous examples to keep in the model's context to help classify new incoming data. The search was performed using a 120B parameter open-source model. Meta-Harness discovered strategies that outperformed existing hand-engineered methods like Agentic Context Engineering (ACE). 

![Accuracy vs Context Trade-off](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.28052v1/x4.png)
*Figure 3: The Pareto frontier discovered by Meta-Harness in text classification. The system successfully identifies multiple harnesses that balance high accuracy with low context cost (measured in characters), outperforming human-designed baselines.*

Notably, the discovered harnesses generalized to nine unseen datasets. One discovered strategy, termed "Label-Primed Query," used a two-step process: first, the model identifies the most likely label, and then it specifically retrieves examples corresponding to that label to confirm the decision. This algorithmic refinement was discovered entirely through automated search and achieved 48.6% accuracy, surpassing ACE's 40.9% while using four times fewer context tokens.

### Retrieval-Augmented Math Reasoning
For IMO-level (International Mathematical Olympiad) math problems, the harness manages a retrieval system to find relevant solved problems from a corpus of 500,000 examples. Meta-Harness discovered a retrieval policy that improved accuracy across five different held-out base models by an average of 4.7 points. The discovered harness was a compact program that routed queries to subject-specific retrieval policies based on the problem's text, incorporating deduplication and difficulty-based reranking.

### Agentic Coding on TerminalBench-2
The most complex domain tested was agentic coding, where an LLM must interact with a terminal to solve software engineering tasks. Starting from a strong human-written baseline, Meta-Harness optimized the harness's environment-handling and prompt-construction logic.

![TerminalBench-2 Performance](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.28052v1/x2.png)
*Figure 4: Pass rates on TerminalBench-2. Meta-Harness discovered harnesses that allowed Claude models to achieve state-of-the-art performance on the leaderboard, surpassing specialized human-engineered agents.*

On TerminalBench-2, the discovered harness for Claude Haiku 4.5 achieved a 37.6% pass rate, ranking #1 among Haiku-based agents. For the more powerful Claude Opus 4.6, it achieved 76.4%, ranking #2 on the overall leaderboard. The proposer identified that the agent often wasted initial turns exploring the environment. To fix this, the proposer added an "environment bootstrapping" step that automatically snapshots the sandbox environment and injects it into the initial prompt, saving exploratory turns and improving success rates.

## Analysis: Why Meta-Harness Succeeds

The success of Meta-Harness can be attributed to several factors that distinguish it from prior work in meta-learning and text optimization:

1.  **Code-Space Search as Regularization:** Optimizing in the space of Python programs provides a natural bias toward coherent, algorithmic solutions. Unlike weight-space optimization, which can be opaque, the resulting harnesses are human-readable and modular.
2.  **Causal Reasoning via Logs:** By providing the proposer with the ability to "debug" previous attempts using raw logs, the system moves from random or heuristic search to informed, causal reasoning. The agent doesn't just know *that* a harness failed; it can see *how* it failed.
3.  **End-to-End Credit Assignment:** Meta-Harness assigns credit at the level of the harness logic. It can recognize when a prompt change is insufficient and a structural change to the retrieval or state-management code is required.
4.  **Multi-Objective Discovery:** Because the system evaluates many candidates, it naturally identifies a Pareto frontier of solutions, allowing developers to choose harnesses that optimize for different constraints, such as maximizing accuracy versus minimizing inference cost.

## Conclusion and Implications

Meta-Harness demonstrates that the labor-intensive process of harness engineering can be effectively automated through agentic search over executable code. By shifting the focus from manual heuristic tuning to automated search over full execution histories, the framework consistently finds strategies that outperform human-designed counterparts across varied domains.

The implications of this work extend beyond LLM benchmarks. The ability of an agent to autonomously refine its own external "scaffolding" by reasoning over its past experience suggests a path toward more self-improving AI systems. Furthermore, because the output of Meta-Harness is transparent Python code, these discovered strategies can be easily inspected, audited, and deployed in production environments, providing a bridge between automated optimization and reliable software engineering. The transition from "prompt engineering" to "automated harness engineering" represents a significant shift in how complex LLM systems are developed and scaled.

## Relevant Citations

- Agentic context engineering: Evolving contexts for self-improving language models: This paper introduces Agentic Context Engineering (ACE), a state-of-the-art, hand-designed harness for online text classification. ACE serves as a crucial baseline in the main paper's experiments, where Meta-Harness is shown to significantly improve accuracy by 7.7 points while using 4x fewer context tokens.
- Alphaevolve: A coding agent for scientific and algorithmic discovery: This paper represents a key class of prior work on program search, where an LLM acts as a mutation operator. Meta-Harness contrasts its approach of providing full, unstructured access to prior experience against methods like AlphaEvolve, which use more structured and limited feedback, and shows superior performance in direct comparisons.
- Learning to discover at test time: This work introduces TTT-Discover, a text-optimization method used as a direct experimental baseline. The comparison highlights the core contribution of Meta-Harness, which outperforms TTT-Discover by providing the proposer with full filesystem access to raw execution traces rather than more compressed or structured feedback.
- Terminalbench: Benchmarking agents on hard, realistic tasks in command line interfaces: This paper introduces the TerminalBench-2 benchmark, which is used for one of the three main experimental evaluations of Meta-Harness. The ability of Meta-Harness to automatically discover a harness that achieves state-of-the-art performance on this difficult and actively contested benchmark is a key result demonstrating its practical value for complex agentic tasks.
