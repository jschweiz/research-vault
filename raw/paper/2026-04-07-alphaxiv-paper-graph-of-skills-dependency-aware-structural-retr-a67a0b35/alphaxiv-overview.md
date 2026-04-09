# Graph of Skills: Dependency-Aware Structural Retrieval for Massive Agent Skills

- alphaXiv: https://www.alphaxiv.org/abs/2604.05333
- Source paper: https://arxiv.org/abs/2604.05333

The development of Large Language Model (LLM) agents has progressed from simple text generation to the creation of autonomous systems capable of using external tools, APIs, and "skills" to solve complex tasks. As these systems move from controlled laboratory settings into real-world production environments, they are required to navigate increasingly large libraries containing thousands of potential skills. This scale introduces a significant technical hurdle: how to efficiently identify and retrieve the exact subset of skills needed for a specific task without overwhelming the agent's memory or computational budget.

## The Challenge of Massive Skill Libraries

When an LLM agent is tasked with a problem, such as "Analyze pedestrian traffic from a raw video file," it must select appropriate tools from its library. In a small ecosystem with ten tools, providing the entire list to the agent is feasible. however, modern "skill-centric" architectures aim to maintain libraries with thousands of specialized functions.

![Graph of Skills Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05333v1/x1.png)
*Figure 1: Comparison between Vanilla full loading, standard Vector-based retrieval, and the Graph of Skills (GoS) approach.*

The "Graph of Skills" (GoS) research addresses two primary bottlenecks that emerge at this scale. The first is context window saturation. Loading every skill into the prompt (a "Vanilla" approach) is computationally expensive, increases latency, and often leads to model "hallucination," where the LLM loses track of relevant details amidst the noise. The second bottleneck is the functional dependency of tools. Many technical tasks require a sequence of operations where the primary solver depends on auxiliary tools (like data formatters or parsers) that may not be semantically similar to the original user query.

## The Limitations of Existing Retrieval Paradigms

Current solutions for skill selection generally fall into two categories, both of which have notable drawbacks:

1.  **Vanilla Skills (Full Loading):** This involves prepending the entire skill set to the context. While it ensures the agent "knows" everything available, the token cost grows linearly with the library size. Large prompts also degrade the reasoning capabilities of many LLMs, making it harder for them to select the right tool for the job.
2.  **Vector-Based Retrieval:** This method uses semantic similarity (dense embeddings) to find skills that "look like" the query. For example, a query about "counting traffic" might retrieve a high-level counter. However, it might miss a necessary "video-to-frame" extractor because the extractor's description doesn't mention "traffic" or "counting." This is known as the **prerequisite gap**.

GoS is designed to close this gap by treating the skill library not as a flat list, but as a structured, directed graph where functional relationships between tools are explicitly mapped and used during retrieval.

## Graph of Skills (GoS): A Structural Approach

GoS introduces an inference-time retrieval layer that ensures the retrieved skills are both relevant and "execution-complete." The system operates in two distinct phases: an offline construction phase and an online retrieval phase.

The framework models the library as a typed directed graph $G = (V, E, w, \phi)$. In this graph, $V$ represents individual skill records, while $E$ represents the connections between them. These connections are categorized into four types to capture the nuance of tool relationships:
- **Dependency:** Indicates that one tool's output is required as another's input.
- **Workflow:** Captures common multi-step sequences.
- **Semantic:** Connects tools that are topically related.
- **Alternative:** Links tools that provide different strategies for the same problem.

## Building the Foundation: Offline Graph Construction

Before any query is processed, GoS processes the skill corpus $C$ to build the graph. This starts with **Skill Normalization**, where raw documentation is parsed into a standardized record. This record includes executable fields like I/O requirements, capability summaries, and entry points.

![GoS Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05333v1/x2.png)
*Figure 2: The GoS pipeline consisting of Offline Indexing, Graph Construction, and Online Retrieval.*

The most critical part of this phase is **Typed Relation Induction**. The system identifies dependencies ($v_i \to v_j$) by matching the output types of one skill to the input requirements of another. For non-deterministic relations like "workflow" or "alternative," a lightweight LLM pass is used to validate potential connections within a restricted candidate pool, ensuring the graph remains precise and manageable.

## Intelligent Retrieval: The Online Phase

When a user submits a task query $q$, GoS performs structural retrieval to find a compact bundle $B(q) \subseteq V$ that fits within a context budget $\tau$.

### Hybrid Seeding
The process begins with **Hybrid Seeding**. To avoid the pitfalls of purely semantic search, GoS combines a semantic score $s_{\text{sem}_i}(q)$ with a lexical score $s_{\text{lex}_i}(q)$. Lexical search is particularly effective at catching exact keyword matches for technical terms. These scores are combined using a weighting factor $\eta$ to create an initial seed distribution $p$.

### Reverse-Aware Graph Diffusion
The core innovation of GoS is how it expands from these seeds. Using the typed graph, it performs a diffusion process similar to Personalized PageRank (PPR). The system defines a transition operator $T$ that combines forward transitions $T_{\to_r}$ (following dependencies) and reverse transitions $T_{\leftarrow_r}$ (finding prerequisites). The reverse transitions are weighted by $\gamma_r$, allowing the "relevance" to flow from a high-level tool back to the lower-level utilities it needs.

The importance of each skill is updated iteratively through the following equation:

$$
s^{(\ell+1)} = \alpha p + (1-\alpha)T^T s^{(\ell)}
$$

where $\alpha$ is a restart probability that keeps the search anchored to the original query seeds. This process ensures that if a "Traffic Counter" is highly relevant, its "Video Parser" prerequisite also receives a high score, even if the parser itself doesn't match the "traffic" query semantically.

### Reranking and Hydration
After the scores converge to $s^*_i$, a final reranking score $\rho_i(q)$ is calculated. This combines the diffusion result with direct query evidence $m_i(q)$, weighted by $\mu$:

$$
\rho_i(q) = (1-\mu)s^*_i + \mu m_i(q)
$$

The top-ranked skills are "hydrated"—meaning their full documentation and executable paths are packaged—until the context budget $\tau$ is reached.

## Quantitative Performance and Efficiency

The researchers evaluated GoS using two rigorous benchmarks: **SkillsBench** (1,000 real-world technical skills) and **ALFWorld** (sequential decision-making). They tested the system across different LLM families, including Claude, MiniMax, and GPT-5.2 Codex.

The results demonstrated that GoS significantly outperforms both full-loading and vector-only approaches:
- **Success Rate:** Compared to Vanilla full loading, GoS increased the average success reward by approximately 43.6%. It also consistently beat Vector-based retrieval, proving that the structural graph information is vital for task completion.
- **Token Efficiency:** GoS reduced input token usage by roughly 37.8% compared to the Vanilla baseline. Because it only provides the most relevant and necessary tools, it prevents the context window from being filled with irrelevant "noise."
- **Scalability:** As the number of skills in the library increased from 200 to 2,000, the performance of Vanilla loading dropped due to context saturation. In contrast, GoS maintained high accuracy and stable token usage, showing it is better suited for massive toolsets.

## Qualitative Impact and Strategic Decision-Making

Beyond the numbers, GoS changes how agents "think" about a problem. In a case study involving a traffic counting task, the Vanilla agent often got lost in the vast documentation, while the Vector-only agent failed to find the necessary video extraction tools.

GoS, by contrast, provided a "functional bundle." By retrieving the counter and its prerequisites simultaneously, the agent could immediately commit to a viable execution plan. This suggests that structural retrieval doesn't just provide better tools; it provides a better logical framework for the agent to construct its plan, leading to higher reliability in complex, multi-step engineering tasks.

## Conclusion and Broader Implications

Graph of Skills represents a shift in how we approach tool-augmented LLMs. Instead of treating retrieval as a simple search problem, it treats it as a structural assembly problem. By acknowledging that tools exist in an ecosystem of dependencies, GoS allows agents to scale to thousands of skills without the traditional penalties of cost, latency, or reduced reasoning accuracy.

The significance of this work lies in its modularity. It acts as a lightweight, inference-time layer that can be added to existing agent architectures. As we move toward more autonomous systems in specialized domains like software engineering, data science, and robotics, the ability to selectively and accurately retrieve executable tool bundles will be a cornerstone of reliable agent performance. Future work may further enhance this by learning graph structures directly from execution traces, allowing the "Graph of Skills" to evolve and improve as the agent gains experience.

## Relevant Citations

- Toolnet: Connecting large language models with massive tools via tool graph: This paper is highly relevant as it also proposes using a graph structure for tool access. The 'Graph of Skills' paper explicitly contrasts its approach of retrieving a dependency-complete local bundle with ToolNet's objective of connecting models to a broader tool ecosystem for planning.
- Toolllm: Facilitating large language models to master 16000+ real-world apis: ToolLLM establishes the challenge of scaling agent skills to massive libraries with over 16,000 APIs, which is the core problem that 'Graph of Skills' is designed to solve. The GoS paper uses work like ToolLLM to motivate the need for an efficient and dependency-aware retrieval layer.
- Skillnet: Create, evaluate, and connect ai skills: The paper positions 'Graph of Skills' as a complementary component for large-scale skill ecosystems like SkillNet. While SkillNet focuses on the creation and organization of skills at a repository level, GoS addresses the critical problem of retrieving a relevant, executable subset from such a library for a given task.
- Retrieval models aren’t tool-savvy: Benchmarking tool retrieval for large language models: This citation provides the core motivation for the 'Graph of Skills' paper, as it is cited for establishing that tool retrieval is a major bottleneck and that generic retrievers are poorly suited for real tool-use needs. This directly justifies the development of GoS's dependency-aware, structural retrieval approach.
