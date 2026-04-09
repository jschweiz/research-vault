# DIRECT: Video Mashup Creation via Hierarchical Multi-Agent Planning and Intent-Guided Editing

- alphaXiv: https://www.alphaxiv.org/abs/2604.04875
- Source paper: https://arxiv.org/abs/2604.04875

## The Complexity of Video Mashup Creation

Video mashup creation, which includes genres like movie montages and anime music videos (AMVs), is a highly demanding creative process. It involves more than just selecting video clips that match a script; it requires the meticulous orchestration of visual flow, musical synchronization, and narrative structure. Professional editors must align motion dynamics between shots, ensure consistent framing, and precisely time cuts to musical beats to create a seamless viewing experience.

Despite the rapid progress in AI-driven video generation and editing, most existing automated frameworks operate under a semantic-centric paradigm. These systems typically focus on finding shots that match text descriptions but often ignore the low-level visual and auditory nuances that define professional-grade editing. This leads to sequences that may be semantically accurate but feel disjointed, featuring abrupt transitions and rhythmic misalignments.

![Framework Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04875v1/x1.png)
*Figure 1: The DIRECT framework addresses video mashup creation across three levels: global structural alignment, local segment cohesion, and low-level multimodal coherency.*

To address these challenges, researchers have introduced **DIRECT** (Dynamic Intent for Retrieval & Editing for Cinematic Transitions), a hierarchical multi-agent framework. DIRECT models video mashup creation as a specialized optimization problem, simulating a professional production pipeline to achieve fluid visual transitions and precise musical alignment.

## Formulating Mashup as a Multimodal Coherency Problem

A core contribution of this work is the formulation of video mashup creation as a **Multimodal Coherency Satisfaction Problem (MMCSP)**. Instead of treating editing as a simple retrieval task, the authors define it as the recomposition of a sequence of visual shots $V = \{v_i\}$ from a source library $S$, aligned with a music track $M$ and user instruction $I$.

The goal is to maximize a unified optimization objective that combines high-level goals and low-level metrics:

$$V^* = \arg\max_V \left( G_{global}(V) + G_{local}(V) + \sum_i w_i \cdot M_i(V) \right)$$

This objective considers three primary layers:
1.  **Global Structural Alignment ($G_{global}$):** Ensures the overall narrative and visual themes match the progression of the music (e.g., an "Intro" vs. a "Climax").
2.  **Local Segment Cohesion ($G_{local}$):** Captures the aesthetic intent of a specific segment, such as maintaining a certain pace or visual style.
3.  **Low-Level Coherency ($M_i$):** Quantifiable metrics across three dimensions:
    *   **Semantic:** Prompt relevance ($m_1$) and segment consistency ($m_2$).
    *   **Visual:** Motion continuity ($m_3$, using optical flow) and framing consistency ($m_4$, using saliency maps).
    *   **Auditory:** Beat-cut synchronization ($m_5$) and energy correspondence between audio and visual intensity ($m_6$).

## The DIRECT Framework Architecture

To solve the MMCSP, DIRECT employs a hierarchical multi-agent system composed of three specialized modules: the Screenwriter, the Director, and the Editor. This structure mimics the collaborative workflow of a professional film crew.

![System Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04875v1/x2.png)
*Figure 2: The hierarchical architecture of DIRECT, showing the flow from high-level planning to low-level shot execution.*

### The Screenwriter: Global Alignment

The process begins with the **Screenwriter**, which is responsible for source-aware global planning. Before planning begins, the system performs a multimodal source analysis. Because long videos can overwhelm Large Language Models (LLMs) with data, DIRECT clusters the source footage based on semantic embeddings and captions the "centroids" of these clusters.

The Screenwriter then synthesizes three inputs: the footage summary, a profile of the music (sections, intensity, and timestamps), and the user's instructions. It produces a **Global Structural Plan**, which defines keywords and stylistic anchors for each section of the music. This ensures that the generated mashup has a macro-level narrative that matches the musical intensity.

### The Director: Local Intent Instantiation

The **Director** translates the Screenwriter's broad plan into concrete editing instructions for shorter segments. For each segment, the Director generates a guidance tuple:

$$G_{i,j} = \langle q_{sem}, w_{heu}, \tau_{pace} \rangle$$

*   **Semantic Query ($q_{sem}$):** A specific visual subject to look for.
*   **Editing Heuristic ($w_{heu}$):** A weight distribution that tells the system which metrics to prioritize (e.g., "Motion-Continuity-First").
*   **Rhythmic Pacing ($\tau_{pace}$):** The specific timing of shots in beats.

![Hierarchical Planning](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04875v1/x3.png)
*Figure 3: The Screenwriter anchors the global structure while the Director expands it into segment-level guidance.*

Crucially, the Director operates in a **closed-loop validation** mode. If the Editor returns a sequence that the Director (acting as a validator) deems suboptimal, the Director provides feedback to relax or alter the constraints and tries again. This prevents the system from getting stuck with poor-quality shots when better alternatives exist under slightly different search terms.

### The Editor: Intent-Guided Sequence Editing

The **Editor** is the execution engine. It treats the problem as a constrained path search within a footage graph. Using a beam search algorithm, it identifies the sequence of shots that best satisfies the Director's guidance and the low-level coherency metrics.

One of the Editor's unique features is **Dynamic Sliding-Window Trimming**. When the Editor selects a raw shot, it doesn't just cut the shot at an arbitrary point. Instead, it slides a temporal window across the raw footage to find the exact sub-clip that maximizes visual continuity with the previous shot. By analyzing optical flow and saliency maps at the boundaries, the Editor ensures that motion and framing flow naturally from one shot to the next.

![Editor Search Process](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04875v1/x4.png)
*Figure 4: The Editor uses beam search and dynamic trimming to optimize transitions between shots.*

## Evaluating Mashup Quality: Mashup-Bench

A significant obstacle in this field is the lack of standardized evaluation tools for video mashups. To address this, the researchers developed **Mashup-Bench**. This benchmark consists of:
*   **Footage Library:** 38 videos from 15 iconic movie series (e.g., *Mission Impossible*, *The Matrix*) across five genres.
*   **Music & Instructions:** 10 diverse music tracks and human-curated prompts.
*   **Quantifiable Metrics:** Tailored measures for motion continuity and beat-cut synchronization.

### Performance Results

In evaluations against state-of-the-art baselines like VideoAgent, DIRECT demonstrated significant improvements in low-level coherency. While baseline methods were often capable of finding semantically relevant clips, they struggled with the physical "flow" of the video.

As shown in the table below (derived from the paper's findings), DIRECT achieved substantially higher scores in visual and auditory metrics:

| Metric | VideoAgent | **DIRECT (Ours)** |
| :--- | :---: | :---: |
| Motion Continuity ($m_3$) | 62.24 | **77.26** |
| Framing Consistency ($m_4$) | 78.85 | **83.37** |
| Beat-Cut Sync ($m_5$) | 88.43 | **98.69** |
| Energy Correspondence ($m_6$) | 51.88 | **82.40** |

Subjective human evaluations mirrored these objective results. Participants rated DIRECT significantly higher than baselines in overall quality, specifically noting its superior global narrative flow and local segment cohesion. The 40% improvement in local cohesion scores over the best baseline highlights the effectiveness of the Director agent's adaptive heuristics.

![Visual Continuity Examples](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04875v1/x8.png)
*Figure 5: Examples of high-scoring transitions in DIRECT, showing consistent motion flow and framing.*

## Significance and Practical Implications

The DIRECT framework represents a shift toward more holistic automated video editing. By integrating high-level MLLM planning with low-level motion and energy analysis, it moves closer to the quality of professional human editors.

The practical implications for content creators are substantial. The labor-intensive process of sifting through hours of footage to find clips that align perfectly with music can be significantly streamlined. Furthermore, the hierarchical multi-agent approach provides a template for solving other complex creative tasks that require coordination across different levels of abstraction.

While the system is effective, the authors note some current limitations. For instance, LLM-based agents can occasionally "hallucinate" the existence of footage that isn't in the library, and the system's perception can struggle in extreme lighting or very chaotic scenes. Despite these challenges, DIRECT establishes a new standard for automated video mashup creation, emphasizing that professional quality comes from the synergy of semantic meaning and multimodal "flow."

## Relevant Citations

- VideoAgent: All-in-One Agentic Framework for Video Understanding, Editing, and Remaking: This is a primary state-of-the-art baseline against which the DIRECT framework is directly compared in the experiments. As a competing agentic framework using LLM-based planning for video editing, it serves as a crucial benchmark for demonstrating DIRECT's superior performance in multimodal orchestration.
- Weakly-supervised movie trailer generation driven by multi-modal semantic consistency: This paper, referred to as MMSC, is another key baseline used for quantitative comparison. It represents a state-of-the-art end-to-end framework for movie montage generation that optimizes for semantic consistency, which is a core problem that DIRECT's more comprehensive multi-level coherency approach aims to improve upon.
- Learning transferable visual models from natural language supervision: This paper introduces CLIP, a foundational vision-language model that is critical to the DIRECT framework's methodology. The authors explicitly state that they use CLIP to compute key low-level metrics such as semantic prompt relevance and segment consistency, making it an essential underlying technology for their system.
- Lave: Llm-powered agent assistance and language augmentation for video editing: This paper is cited in the related works section as a key example of an agentic video editing framework that leverages LLMs for high-level planning. It represents a similar research direction to DIRECT, helping to contextualize the paper's contribution within the emerging field of LLM-powered video editing systems.
