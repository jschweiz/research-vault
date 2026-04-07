# Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?

- alphaXiv: https://www.alphaxiv.org/abs/2604.03016
- Source paper: https://arxiv.org/abs/2604.03016

## Understanding Agentic Multimodal Intelligence

The evolution of Multimodal Large Language Models (MLLMs) has moved beyond static interpretation of text and images. Modern AI systems are increasingly expected to act as "agents"—active problem-solvers that do not just process the information given but actively seek out what is missing. This shift involves two primary dimensions: Visual Expansion, where a model manipulates an image (cropping, enhancing, or rotating) to uncover hidden details, and Knowledge Expansion, where it performs open-web searches to verify facts or acquire new information.

![Figure 1: Comparison of task difficulty levels in Agentic-MME, from single visual operations to complex, intertwined reasoning involving both vision and knowledge expansion.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03016v1/x1.png)

However, as MLLMs become more agentic, evaluating them becomes significantly more difficult. Traditional benchmarks often focus solely on whether a model reaches the correct final answer. This "outcome-based" assessment is limited because it cannot distinguish between a model that reasoned correctly and one that simply made a lucky guess. Furthermore, it fails to diagnose why a model failed: was it a failure in planning, a mistake in using a tool, or an inability to perceive the evidence?

To address these challenges, the Agentic-MME benchmark introduces a process-verified framework. It evaluates the synergistic application of visual and knowledge expansion in agentic MLLMs across 418 real-world tasks. By implementing detailed, step-wise checkpoints, the benchmark provides a diagnostic look into the underlying reasoning process of multimodal agents.

## Limitations of Current Evaluation Frameworks

Prior to this work, evaluating the agentic capabilities of multimodal models suffered from three major shortcomings. First, there was a lack of unified tool integration. Benchmarks typically treated visual tools (like image cropping) and knowledge tools (like web search) as separate entities. In real-world scenarios, however, these tools must be used in coordination. An agent might need to crop an obscure logo in an image before searching the web to identify the brand it represents.

Second, the synergy between visual and knowledge expansion remained largely unexplored. Most existing tests do not require the deep coupling of these two capabilities. The "intertwined" tasks that define high-level multimodal intelligence—where neither vision nor search alone is sufficient—were missing from the evaluation landscape.

Finally, the absence of process verification made it nearly impossible to audit the model's behavior. If a model fails to answer a question about a small, blurry object in a high-resolution image, current benchmarks cannot tell if the model failed to recognize it needed to zoom in, if it zoomed into the wrong area, or if it correctly zoomed in but still couldn't identify the object. Agentic-MME solves this by recording and auditing every intermediate state an agent produces.

## The Agentic-MME Methodology

The benchmark is built on a unified tool-augmented interface that provides agents with two main types of resources:

1.  **Visual Operations (13 tools):** These include `crop`, `rotate`, `enhance`, `grayscale`, `blur`, and `edge_detect`. These allow the model to actively manipulate the visual input to extract localized or processed cues.
2.  **Open-Web Retrieval (4 tools):** These include `google_search`, `google_lens_search`, `fetch_webpage`, and `download_image`. These enable the model to access the vast repository of human knowledge on the internet.

### Task Stratification by Difficulty
Agentic-MME categorizes tasks into three levels based on the complexity of interaction required:

*   **Level 1 (Visual Expansion Focus):** These tasks require a single, decisive visual operation. For example, a model might need to crop a price tag on a grocery shelf to read the value correctly.
*   **Level 2 (Visual + Knowledge):** These involve multi-step workflows, typically combining visual manipulation with a search. A model might crop a sign to read a restaurant name and then search the web to find its operating hours.
*   **Level 3 (Synergistic Coupling):** These are the most challenging scenarios. They require iterative, interleaved execution of both visual and search tools. Solving these tasks often involves resolving severe visual ambiguity through hypothesis-testing loops, where visual hints and multi-hop web searches are used for cross-validation.

### Process-Level Metrics
To move beyond final-answer accuracy ($Acc$), Agentic-MME introduces several process-aware metrics:

*   **$V\text{-axis}$ (Visual Verification):** This measures how well the agent uses visual tools. It is split into $V_{\text{tool}}$ (did the agent call the right tool at the right time?) and $V_{\text{true}}$ (did the resulting image actually contain the evidence needed?).
*   **$S\text{-axis}$ (Search Verification):** This assesses the agent's search strategy, including the relevance of its keywords and the correctness of intermediate facts it retrieved.
*   **Overthink:** This metric quantifies efficiency by comparing the agent's trajectory to a human's minimal path. It is defined as:
$$\text{Overthink} = \frac{\max(0, C_{\text{agent}} - C_{\text{human}})}{C_{\text{human}} + 1}$$
where $C_{\text{agent}}$ and $C_{\text{human}}$ represent the number of interactions for the agent and the human, respectively.

## Data Collection and Quality Assurance

The creation of Agentic-MME involved a rigorous "Model-in-the-Loop Backward Drafting" protocol. Researchers started with high-resolution, complex images and used advanced MLLMs (like Gemini 1.5 Pro) to identify details that were difficult to perceive without active manipulation. Once a candidate task was identified, human annotators meticulously documented a full reference trajectory.

![Figure 2: The data collection pipeline, emphasizing human-model co-verification and granular step-wise annotation.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03016v1/x2.png)

For every step in the trajectory, the annotators recorded the intent, the specific tool used, the intermediate visual or textual evidence, and the expected answer at that checkpoint. Quality control was maintained through consensus auditing and "Step-wise Oracle Testing," where models were guided through human paths to ensure that the evidence was indeed perceptible and the failure modes were strictly related to planning or execution.

## Key Findings and Model Analysis

The evaluation of state-of-the-art models on Agentic-MME revealed a significant performance gap between AI and humans. While humans achieved an overall accuracy of 93.8%, even the most capable model, Gemini 1.5 Pro, scored only 56.3%. On the most difficult Level 3 tasks, the gap widened further (82.3% for humans vs. 33.3% for the best model).

### Structured APIs vs. Code Generation
The benchmark tested models in two interaction modes: **Atomic (Atm)** mode, where models use structured function-calling APIs, and **Code Generation (Gen)** mode, where models write Python code to perform operations. The results showed that structured APIs are currently more reliable. In Gen mode, models often struggled with syntax and program composition, leading to lower visual tool utilization. For example, GPT-4o in Gen mode showed a visual tool invocation rate ($V_{\text{tool}}$) of only 7.6%, but this jumped to over 70% when switched to the simpler Atm mode.

### Open-Source vs. Closed-Source
Closed-source models consistently outperformed open-source ones, particularly in their ability to plan and execute searches. Analysis of the $S\text{-axis}$ scores showed that many open-source models failed to formulate useful search queries or extract relevant information from search results, leading to $S\text{-axis}$ scores below 5%.

### The "Overthinking" Problem
A unique finding of this research is the tendency for models to "overthink." While a human might find an answer in two or three steps, models often enter redundant loops, calling tools repeatedly without making progress. Gemini 1.5 Pro was found to be the most successful because it balanced exploration with reliable execution, whereas other models either failed to act ("reluctance to act") or explored aimlessly without achieving high accuracy.

## Diagnostic Failure Modes

Agentic-MME identifies seven distinct failure modes that hinder multimodal agents:

1.  **Reluctance to Act:** The model guesses an answer based on passive observation rather than using a tool to find the required evidence.
2.  **Overthinking Collapse:** The agent becomes trapped in redundant, circular tool-invocation loops.
3.  **Unfaithful Visual Tool Use:** The agent uses a tool (like `crop`) but targets the wrong region of the image.
4.  **Tool-Misexecution:** Failures in syntax or API parameterization, common in code-generation modes.
5.  **Bad Search Query:** Formulating queries that are too vague or irrelevant to the task.
6.  **Missing Search/Visual Tools:** The agent fails to recognize that it needs to search or manipulate the image to find the answer.
7.  **Post-Visual Perception Deficit:** The model correctly uses a tool to isolate evidence but fails to correctly interpret the newly processed image.

![Figure 3: Heatmap of failure modes across different models and task difficulty levels, showing that missing visual tool use is a primary bottleneck.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03016v1/x7.png)

## Significance of the Work

The Agentic-MME benchmark serves as a critical diagnostic tool for the AI research community. By pinpointing exactly where multimodal agents fail—be it in the planning stage, the execution of a tool, or the final perception of processed data—it provides a roadmap for future development.

The work highlights that true multimodal intelligence is not just about having more parameters or better vision encoders; it is about the coordination of disparate skills. The benchmark pushes the field toward "active" intelligence, where models are trained not just to describe what they see, but to strategically manipulate their environment and retrieve external knowledge to solve complex, real-world problems. By providing a process-verified evaluation, Agentic-MME ensures that progress in the field is measured by robust reasoning rather than sophisticated pattern matching.

## Relevant Citations

- Codev: Code with images for faithful visual reasoning via tool-aware policy optimization: This paper is cited as a direct inspiration for Agentic-MME's core methodology of process verification. Agentic-MME adopts and extends CodeV's approach to evaluate the faithfulness of intermediate visual artifacts, moving beyond simple final-answer scoring to ensure tools are used correctly.
- Beyond seeing: Evaluating multimodal llms on tool-enabled image perception, transformation, and reasoning: VisToolBench is a representative benchmark that focuses specifically on 'Visual Expansion'—the use of image manipulation tools. Agentic-MME is positioned as an advancement over such works by integrating visual tool use with a core open-web search component to evaluate their synergistic combination.
- Mm-browsecomp: A comprehensive benchmark for multimodal browsing agents: This benchmark is relevant as it addresses the 'Knowledge Expansion' aspect by evaluating multimodal web browsing. Agentic-MME is designed to fill a gap identified in such works by introducing a rich suite of active visual manipulation tools and verifying their intermediate outputs, thus unifying deep visual interaction with web retrieval.
- Gaia2: Benchmarking llm agents on dynamic and asynchronous environments: GAIA2 is a significant generalist agent benchmark that also highlights the necessity of process-aware evaluation. This citation is important because it contextualizes Agentic-MME within the broader research trend of creating more rigorous agent evaluations, showing how Agentic-MME contributes by applying this principle specifically to the multimodal visual and search domain.
