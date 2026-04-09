# Search, Do not Guess: Teaching Small Language Models to Be Effective Search Agents

- alphaXiv: https://www.alphaxiv.org/abs/2604.04651
- Source paper: https://arxiv.org/abs/2604.04651

## The Challenge of Small Language Models as Search Agents

Language models have evolved into sophisticated "agents" capable of interacting with external tools to solve complex, knowledge-intensive tasks. These agents typically follow a cycle of formulating search queries, retrieving documents, and reasoning over the findings. While Large Language Models (LLMs) like the 32B parameter versions of Qwen3 have demonstrated high proficiency in these tasks, their deployment is often hindered by high computational costs and significant inference latency. This has spurred interest in Small Language Models (SLMs)—models with fewer than 4B parameters—which offer the efficiency required for real-time applications.

However, a performance gap persists. Smaller models often struggle with "parametric hallucination," where they attempt to answer questions using their limited internal knowledge rather than seeking external verification. This research addresses this disparity by introducing the Always-Search Policy (ASP), a framework designed to teach SLMs to act as "knowledge-free" agents that prioritize external search over internal speculation.

![Performance comparison of various SLM distillation methods and the teacher model.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04651v1/x1.png)
*Figure 1: Comparison of the Always-Search Policy (ASP) against vanilla SLMs, standard distillation, and adaptive search strategies. The "Adaptive Search Trap" illustrates the performance drop when SLMs attempt to rely on their own internal confidence.*

## Understanding the Failures of Vanilla SLMs

Current research identifies two primary reasons why SLMs underperform as search agents compared to their larger counterparts: under-searching and parametric hallucination.

1.  **Under-Searching:** Counter-intuitively, models with less internal knowledge do not necessarily search more. Evaluations show that a 1.7B parameter model may only invoke search tools an average of $1.72$ times per question, whereas a 32B model invokes them $3.02$ times. This lack of curiosity prevents the SLM from gathering the necessary evidence to answer multi-hop questions correctly.
2.  **Parametric Hallucination:** SLMs frequently rely on their internal parametric weights to "guess" an answer. Because their internal knowledge base is smaller and potentially outdated, these guesses are often incorrect.

Standard distillation methods, which involve training a student SLM to mimic the trajectories of a teacher LLM, have proven insufficient. The teacher's trajectories often rely on implicit reasoning derived from its vast parametric knowledge—knowledge that the student simply does not possess. Consequently, the student fails to replicate the teacher's success because it cannot bridge the gap between the evidence it retrieves and the reasoning required.

![Impact of model scale on accuracy and search frequency.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04651v1/x2.png)
*Figure 2: Analysis showing that as model size increases, both accuracy and the average number of tool calls rise. SLMs under-utilize tools compared to larger models.*

## Formalizing Agentic Search

To improve SLM performance, the researchers formalize agentic search as a multi-step decision process. For a given question $Q$, the agent generates a sequence of thoughts, actions, and observations. A typical trajectory $\tau$ is represented as:

$$ \tau = (Q, s_1, a_1, o_1, s_2, a_2, o_2, \dots, s_n, a_n) $$

Where:
*   $Q$ is the initial user query.
*   $s_t$ is the model's internal reasoning or "thought" at time $t$.
*   $a_t$ is an action chosen from the action space $A$.
*   $o_t$ is the observation or feedback received from the environment (e.g., search results).

The action space is defined as:

$$ A = \{ \text{Search}, \text{Answer} \} $$

In this framework, the agent must decide at each step whether to continue searching for more information or to terminate the process and provide a final answer.

## The Always-Search Policy (ASP)

The core contribution of this work is the Always-Search Policy (ASP). Rather than allowing the model to decide when it "knows enough," ASP forces the SLM to ground every piece of information in external evidence. This effectively treats the SLM as a "knowledge-free" reasoning engine.

The researchers implemented ASP through several fine-tuning strategies:

### Supervised Fine-Tuning with ASP (SFT-ASP)
Standard supervised fine-tuning (SFT) uses successful trajectories from a teacher model. SFT-ASP adds a strict filter: only trajectories where the teacher model consistently used search tools to obtain information are used for training. If the teacher generated an answer without a clear search step or used phrases like "I remember," that trajectory was discarded. This ensures the student only learns behaviors grounded in retrieval.

### On-Policy Distillation (OPD-ASP)
To further reinforce this behavior, the researchers used on-policy distillation. A system prompt explicitly instructs the SLM to always use search tools. During training, the student model's output distribution is aligned with the teacher's, but the process is biased toward the "Search" action.

### Rejection Fine-Tuning (RFT)
As a final refinement, Rejection Fine-Tuning is applied. The model generates multiple candidate trajectories, and only the highest-quality ones—those that successfully reach the correct answer through thorough searching—are used for a final round of fine-tuning.

## Experimental Results and Generalization

The effectiveness of ASP was tested across several multi-hop reasoning benchmarks, including HotpotQA, 2WikiMultiHopQA, and Bamboogle. The results showed a substantial improvement in the agentic capabilities of SLMs.

For example, on the Bamboogle benchmark, a standard-distilled 1.7B model achieved an $F1$ score of 53.2. By applying ASP, this score jumped to 70.6, coming within 2.5 points of the 32B teacher model (73.1). More importantly, the search frequency of the 1.7B model increased to 2.84 calls per question, closely matching the behavior of the teacher.

Beyond performance on standard benchmarks, the ASP-trained models demonstrated:
*   **Robustness to Noise:** When 10% of retrieval results were intentionally corrupted or replaced with irrelevant information, ASP-trained models showed higher resilience, dropping only 1.7 to 2.3 points in accuracy compared to a 12.1-point drop for standard models.
*   **Zero-Shot Generalization:** Models trained on HotpotQA were able to generalize to more complex, out-of-distribution tasks like BrowseComp-Plus and LongSeAL without additional training.
*   **Efficiency:** Despite the increased number of search calls, the ASP-trained 1.7B model maintained an inference latency approximately $3 \times$ lower than the 32B model.

## The Adaptive Search Trap

A common approach in agent research is "adaptive search," where a model only invokes a search tool if its internal confidence falls below a certain threshold. While this strategy saves computational resources for LLMs, the researchers found it to be detrimental for SLMs.

By training a multi-layer perceptron (MLP) as a confidence probe on the frozen backbone of the SLM, the researchers observed that SLMs lack reliable internal knowledge. As shown in Figure 3, the confidence distribution for SLMs is heavily skewed toward low-confidence states compared to the 32B teacher.

![Confidence distribution of SLMs versus LLMs.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04651v1/x3.png)
*Figure 3: Histograms showing the internal confidence of various models. SLMs exhibit significantly lower confidence in their parametric knowledge, making them poor candidates for adaptive search.*

In simulations, even when the SLM was allowed to self-answer only $5\%$ of the time (where its internal confidence $P$ was highest), its performance dropped significantly. For the SFT-Qwen3-1.7B model, this led to a $4.8$ point decrease in accuracy. This "Adaptive Search Trap" suggests that for small models, a consistent policy of "search, do not guess" is always superior to trying to decide when to search.

## Conclusion and Future Outlook

The "Search, Do not Guess" framework provides a clear path for making Small Language Models as effective as their larger counterparts in knowledge-intensive tasks. By shifting the focus from parametric knowledge to active retrieval, the Always-Search Policy (ASP) mitigates the inherent limitations of SLMs—specifically hallucination and under-searching.

The significance of this work lies in its practical application. It demonstrates that with the right distillation strategy, high-performing search agents can be deployed on edge devices or in low-latency environments without the massive overhead of 30B+ parameter models. Future research may explore more complex versions of ASP that can handle even more diverse toolsets or integrate more sophisticated reasoning patterns into the "knowledge-free" paradigm.

## Relevant Citations

- Search-o1: Agentic search-enhanced large reasoning models: This paper is foundational as it defines the task of agentic search that the main paper addresses. The authors explicitly state they are formalizing their task in a manner similar to this work, making it a direct methodological predecessor.
- Distilling llm agent into small models with retrieval and code tools: This work is cited as the standard approach for agent distillation, which the main paper critiques and builds upon. The proposed 'Always-Search Policy' is presented as a superior alternative to the methods described in this reference.
- Hotpotqa: A dataset for diverse, explainable multi-hop question answering: This paper introduces the HotpotQA dataset, which is the primary benchmark used for both training and evaluation throughout the study. The main paper's central claims and results are validated using this specific dataset.
- On-policy distillation of language models: Learning from self-generated mistakes: This citation is directly relevant to the methodology, as the paper implements On-Policy Distillation (OPD) as one of the specific techniques to incorporate the proposed 'Always-Search Policy'. It is a key component of the experimental setup to demonstrate the effectiveness of their approach.
