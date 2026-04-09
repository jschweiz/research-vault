# MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale

- alphaXiv: https://www.alphaxiv.org/abs/2604.04771
- Source paper: https://arxiv.org/abs/2604.04771

## The Data-Centric Evolution of Document Parsing

Document parsing—the process of converting unstructured PDF and image-based documents into structured, machine-readable formats like Markdown or HTML—is a critical component of modern AI data pipelines. It serves as the primary gateway for feeding high-quality information into Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG) systems. While initial efforts focused on complex multi-step pipelines and vision-language model (VLM) architectures, recent research suggests that architectural innovations alone are reaching a point of diminishing returns.

MinerU2.5-Pro represents a shift toward a data-centric methodology. The core hypothesis of this work is that common failure modes across different state-of-the-art models are not the result of architectural flaws, but rather shared deficiencies in training data quality and coverage. By maintaining the fixed $1.2\text{B}$ architecture of the previous MinerU2.5 and focusing exclusively on systematic data engineering, the researchers aimed to push the limits of what a smaller-scale model can achieve.

![MinerU2.5-Pro Performance Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04771v1/x1.png)
*Figure 1: Comprehensive benchmark ranking on OmniDocBench v1.6, demonstrating the performance of MinerU2.5-Pro across Full, Base, and Hard document subsets.*

This approach addresses the "long-tail" problem in document understanding: the difficulty of parsing complex nested tables, dense mathematical formulas, and unconventional multi-column layouts that appear infrequently in standard datasets but are essential for robust real-world performance.

## The MinerU2.5-Pro Data Engine: Strategy Over Architecture

The centerpiece of this work is the "Data Engine," a framework designed to co-optimize data coverage, informativeness, and annotation accuracy. Instead of merely increasing the volume of training data, the engine uses visual and model-based heuristics to select and refine the most valuable samples.

![Data Engine Workflow](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04771v1/x2.png)
*Figure 2: The architecture of the MinerU2.5-Pro Data Engine, illustrating the path from a raw PDF pool to high-quality training samples.*

The engine's first component is Diversity-and-Difficulty-Aware Sampling (DDAS). It begins by extracting visual features from millions of PDFs using ViT-base embeddings, which are then grouped through K-Means clustering. This ensures that the sampling process captures a wide variety of document styles rather than over-representing common layouts. From this diverse pool, the system uses a hierarchy of difficulty assessments at both the page and element levels (e.g., text blocks, tables, and formulas).

![Sampling Strategy](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04771v1/x3.png)
*Figure 3: Details of the DDAS mechanism, showing how page-level and element-level clusters are sampled based on difficulty tiers.*

By upweighting "Hard" clusters—those containing complex structural elements—the engine expands the effective training data from a few million pages to approximately 60 million, prioritizing samples that offer the highest marginal learning value.

## Cross-Model Consistency and the Judge-Refine Pipeline

To manage such a massive scale of data without introducing excessive noise, the researchers implemented Cross-Model Consistency Verification (CMCV). This technique identifies sample difficulty by comparing the outputs of multiple heterogeneous models (such as MinerU2.5, PaddleOCR-VL, and Qwen3-VL-30B).

The consistency is categorized into three tiers:
1. **Easy:** High agreement across all models; these are used for foundational training.
2. **Medium:** External models agree, but the baseline MinerU2.5 differs. Here, the consensus among other models acts as a pseudo-label to correct the baseline model.
3. **Hard:** Significant disagreement across all models, indicating a genuinely difficult case that requires further refinement or expert human intervention.

For the Hard samples, the "Judge-and-Refine" pipeline introduces a "render-then-verify" mechanism. Since complex structural formats like LaTeX or HTML are difficult for models to verify purely through text, the pipeline renders the model's prediction back into an image. A large, sophisticated "Judge" model (Qwen3-VL-235B) then compares the rendered image of the prediction against the original document image. This visual feedback allows the system to localize structural errors—such as missing table rows or misaligned formula symbols—with high precision. Samples that remain ambiguous after this process are routed to human experts, ensuring the final fine-tuning set is of the highest possible quality.

## A Three-Stage Progressive Training Strategy

MinerU2.5-Pro utilizes a multi-stage training pipeline to integrate these different data tiers effectively. Each stage has a specific objective, scaling from broad understanding to fine-grained structural alignment.

### Stage 1: Document Parsing Pre-training
This stage uses approximately 65.5 million Easy and Medium samples. The focus is on building broad foundational capabilities across all subtasks (layout detection, text, formula, and table recognition). In this stage, all parameters are trainable with relatively high learning rates: $\eta_{\text{LM}} = 10^{-3}$ for the language model component and $\eta_{\text{vision}} = 10^{-4}$ for the vision encoder.

### Stage 2: High-Quality Supervised Fine-Tuning (SFT)
The model is then refined on a set of 192,000 expert-annotated Hard samples. To prevent the model from forgetting the broad knowledge gained in Stage 1, "replay data" is mixed in at task-specific ratios. This stage is where the model learns to handle the most complex document structures that typically cause smaller models to fail.

### Stage 3: Reinforcement Learning with GRPO
The final stage employs Group Relative Policy Optimization (GRPO) to bridge the gap between standard training losses and task-specific evaluation metrics. Instead of just predicting the next token, the model is rewarded based on sequence-level metrics like $\text{TEDS}$ (for tables) and $\text{CDM}$ (for formulas). By sampling multiple outputs for each prompt and rewarding those that achieve the best structural accuracy, the model learns to align its internal weights with the actual goals of the parsing task.

## Advancing Evaluation: OmniDocBench v1.6

A significant contribution of this work is the upgrade of the evaluation framework to OmniDocBench v1.6. The researchers identified that previous benchmarks suffered from element-matching biases. For instance, if a model's segmentation of a dense text block differed from the ground truth—even if the content was 100% correct—the scoring logic might penalize it heavily due to a lack of a one-to-one match.

![Matching Bias Examples](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04771v1/x4.png)
*Figure 4: Visual examples of element-matching biases where traditional one-to-one matching leads to incorrect scoring artifacts despite correct content recognition.*

To solve this, MinerU2.5-Pro introduces Multi-Granularity Adaptive Matching (MGAM). Given the ground truth set $G = \{g_1, g_2, \dots, g_n\}$ and the prediction set $P = \{p_1, p_2, \dots, p_m\}$, MGAM follows a three-stage adaptive process:
1. **Direct Bipartite Matching:** Standard matching between $P$ and $G$.
2. **Prediction Splitting:** Splitting predicted elements $P$ into a finer-grained set $P'$ to find better matches with $G$.
3. **Partition Enumeration:** Exploring potential groupings of $P'$ elements to find the global optimum that best reflects the semantic correctness of the output.

Furthermore, a new "Hard" subset of 296 professionally annotated pages was added to the benchmark. This subset specifically targets the failure points of current top-tier models, providing a more discriminative test of a model's true robustness.

## Results and Quantitative Analysis

The data-centric approach yielded significant performance gains across all document categories. On the OmniDocBench v1.6 Full dataset, MinerU2.5-Pro achieved an overall score of 95.69, an improvement of 2.71 points over the baseline MinerU2.5, despite having no changes to the model architecture.

The model's performance on the Hard subset was particularly noteworthy, scoring 94.08 and outperforming much larger models like PaddleOCR-VL-1.5 and GLM-OCR. This validates the effectiveness of the targeted hard-sample mining and the iterative refinement pipeline.

In specific sub-metrics, the model showed high precision:
- **Formula Recognition:** Achieved a $\text{CDM}$ score of 97.29, leading across specialized benchmarks.
- **Table Recognition:** Achieved a $\text{TEDS}$ score of 93.42 and a $\text{TEDS-S}$ (structure only) score of 95.92.
- **Text Recognition:** Reduced the $\text{Edit Distance}$ to 0.019, reflecting a 30.5% reduction in errors compared to the previous version.

Ablation studies confirmed that while scaling the data (Stage 1) provided the largest foundational gain, the expert-guided SFT (Stage 2) and the RL-based alignment (Stage 3) were crucial for achieving state-of-the-art results on complex tables and formulas.

![Qualitative Table Parsing](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04771v1/x17.png)
*Figure 5: Qualitative comparison of table parsing. MinerU2.5-Pro demonstrates superior accuracy in handling long merged cells and complex multi-row structures compared to general-purpose VLMs.*

## Beyond Extraction: Extended Parsing Capabilities

The researchers also expanded the model's utility for real-world document workflows through several functional enhancements:
- **Image-Aware Parsing:** The model can classify chart or diagram regions and extract their internal structure as Mermaid code or tables, rather than treating them as opaque images.
- **Truncated Paragraph Merging:** It can identify and reassemble paragraphs that were split across pages or by layout elements like images.
- **Cross-Page Table Merging:** It detects when a single table spans multiple pages and merges the fragments into a unified structured output.
- **In-Table Image Detection:** It can preserve the identity and location of images embedded within table cells, ensuring no information is lost during the conversion to text-based formats.

These features, while not directly measured by standard benchmark scores, represent a move toward holistic document understanding that prioritizes the semantic continuity of the information over simple region-by-region extraction. By focusing on the "what" (data) rather than just the "how" (architecture), MinerU2.5-Pro establishes a new benchmark for efficiency and accuracy in the field of document parsing.

## Relevant Citations

- Mineru2.5: A decoupled vision-language model for efficient high-resolution document parsing: This paper introduces MinerU2.5, the direct predecessor and baseline model for the work presented. The core contribution of MinerU2.5-Pro is improving upon this model's performance solely through data engineering and training strategies, while keeping the MinerU2.5 architecture entirely fixed.
- Omnidocbench: Benchmarking diverse pdf document parsing with comprehensive annotations: This is the foundational evaluation benchmark that the paper uses and improves upon. A significant contribution of the main paper is the introduction of OmniDocBench v1.6, which corrects biases and adds a 'Hard' subset to this original benchmark to allow for more discriminative evaluation.
- Paddleocr-vl-1.5: Towards a multi-task 0.9 b vlm for robust in-the-wild document parsing: This paper presents a key state-of-the-art competitor model that MinerU2.5-Pro is benchmarked against. Furthermore, its data sampling method (UACS) is explicitly contrasted with the main paper's Cross-Model Consistency Verification (CMCV), highlighting the methodological differences in data-centric approaches.
- Data-centric ai: Perspectives and challenges: This citation provides the theoretical background for the paper's core philosophy. The main paper's entire premise is a practical application of the 'Data-Centric AI' paradigm—systematically improving data quality while keeping the model fixed—to the domain of document parsing.
