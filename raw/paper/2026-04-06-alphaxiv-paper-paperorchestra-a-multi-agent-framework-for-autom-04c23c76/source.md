---
id: 2026-04-06-alphaxiv-paper-paperorchestra-a-multi-agent-framework-for-autom-04c23c76
kind: paper
title: 'PaperOrchestra: A Multi-Agent Framework for Automated AI Research Paper Writing'
source_url: https://www.alphaxiv.org/abs/2604.05018
source_name: alphaXiv Papers
authors:
- Yiwen Song
- Yale Song
- Tomas Pfister
- Jinsung Yoon
published_at: '2026-04-06T18:00:00Z'
ingested_at: '2026-04-09T08:13:05.039670Z'
content_hash: 17fec414da3b7988d3db8f9850816b40ad2b6490bb0ad23d9661a971bb1db913
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.LG
- cs.MA
- data-curation
- generative-models
- image-generation
- reasoning
- text-generation
- audio
- summary
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.05018
canonical_url: https://www.alphaxiv.org/abs/2604.05018
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:13:05.039676Z'
short_summary: Google researchers developed PaperOrchestra, a multi-agent AI framework that converts unstructured pre-writing materials into submission-ready AI research papers, including deep literature reviews and diverse visuals. The system achieved simulated acceptance rates of 84% for CVPR and 81% for ICLR papers on a new benchmark, outperforming existing autonomous writing baselines.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# PaperOrchestra: A Multi-Agent Framework for Automated AI Research Paper Writing

## alphaXiv Summary

Google researchers developed PaperOrchestra, a multi-agent AI framework that converts unstructured pre-writing materials into submission-ready AI research papers, including deep literature reviews and diverse visuals. The system achieved simulated acceptance rates of 84% for CVPR and 81% for ICLR papers on a new benchmark, outperforming existing autonomous writing baselines.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05018
- Source paper: https://arxiv.org/abs/2604.05018
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05018v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05018v1.png
- Paper ID: 2604.05018
- Canonical ID: 2604.05018v1
- Paper group ID: 019d6ad7-98d9-7cd4-b564-92d28869642d
- Version ID: 019d6ad7-9918-7af6-acd8-89d12afe6296
- Version: v1
- Version order: 1
- Published at: 2026-04-06T18:00:00+00:00
- First published at: 2026-04-06T18:00:00+00:00
- Updated at: 2026-04-08T02:06:47.513000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yiwen Song
- Yale Song
- Tomas Pfister
- Jinsung Yoon

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.LG
- cs.MA
- data-curation
- generative-models
- image-generation
- reasoning
- text-generation

## Metrics

- Visits (all): 165
- Visits (last 7 days): 165
- Total votes: 1
- Public total votes: 4
- X likes: 0

## Abstract

Synthesizing unstructured research materials into manuscripts is an essential yet under-explored challenge in AI-driven scientific discovery. Existing autonomous writers are rigidly coupled to specific experimental pipelines, and produce superficial literature reviews. We introduce PaperOrchestra, a multi-agent framework for automated AI research paper writing. It flexibly transforms unconstrained pre-writing materials into submission-ready LaTeX manuscripts, including comprehensive literature synthesis and generated visuals, such as plots and conceptual diagrams. To evaluate performance, we present PaperWritingBench, the first standardized benchmark of reverse-engineered raw materials from 200 top-tier AI conference papers, alongside a comprehensive suite of automated evaluators. In side-by-side human evaluations, PaperOrchestra significantly outperforms autonomous baselines, achieving an absolute win rate margin of 50%-68% in literature review quality, and 14%-38% in overall manuscript quality.

## Problem

- Existing autonomous research frameworks are rigidly coupled to experimental loops, limiting their ability to process arbitrary human-provided pre-writing materials into standalone manuscripts.
- Current automated writing agents often produce superficial literature reviews with insufficient citations and lack the capability to generate diverse visuals beyond data plots, such as conceptual diagrams.
- A standardized benchmark for objectively evaluating automated AI research paper writing systems independently was missing, hindering comparative analysis and progress.

## Method

- Developed PaperOrchestra, a multi-agent framework designed for autonomous LaTeX manuscript generation from unstructured inputs, featuring sequential steps for outline generation, parallel plot and literature review generation, section writing, and iterative content refinement.
- Introduced PaperWritingBench, a new benchmark dataset of 200 top-tier AI conference papers reverse-engineered into raw pre-writing materials (idea summaries, experimental logs) to isolate and evaluate the writing task.
- Integrated a Plotting Agent with VLM-guided refinement for autonomous generation of both statistical plots and conceptual diagrams, and a Literature Review Agent employing a hybrid discovery pipeline for deep, targeted literature synthesis.

## Results

- PaperOrchestra consistently outperformed autonomous baselines in automated side-by-side evaluations, achieving 88%–99% win margins for literature review quality and 39%–86% for overall paper quality against competitors.
- It achieved high simulated acceptance rates (84% for CVPR, 81% for ICLR) under the ScholarPeer framework, with notable gains of 13% and 9% over the strongest autonomous baseline, and produced comprehensive citation lists mirroring human-written papers more closely.
- Ablation studies confirmed the critical role of the iterative Content Refinement Agent, leading to 79%–81% win rates over unrefined drafts, and demonstrated the competitiveness of autonomously generated visuals against human-authored ground truth figures.

## Takeaways

- A multi-agent architecture with specialized roles (e.g., Outline, Plotting, Literature Review, Section Writing, Content Refinement Agents) is effective for transforming diverse unstructured inputs into structured, high-quality research papers.
- Iterative content refinement, simulated through peer-review feedback, significantly improves manuscript quality, elevating drafts to submission-ready standards and substantially increasing simulated acceptance rates.
- The use of a dedicated, reverse-engineered benchmark (PaperWritingBench) is crucial for rigorously evaluating the performance of automated paper writing systems, especially regarding literature synthesis and overall coherence.

## Full Overview

Saved in `alphaxiv-overview.md` and `alphaxiv-overview.json`.

## Overview Languages

- de
- en
- es
- fr
- hi
- ja
- ko
- ru
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6ad7-98d9-7cd4-b564-92d28869642d/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ad7-98d9-7cd4-b564-92d28869642d/transcript.json

## Similar Papers

- PaperBanana: Automating Academic Illustration for AI Scientists (2601.23265v2): An agentic AI system, PaperBanana, automates the generation of publication-ready scientific illustrations, including methodology diagrams and statistical plots, from research paper text. The system achieved a 17.0% improvement in overall quality for methodology diagrams on the new PaperBananaBench and a 4.1% overall improvement for statistical plots by leveraging visual language models for iterative refinement.
- Agent Laboratory: Using LLM Agents as Research Assistants (2501.04227v2): Agent Laboratory, an LLM-based framework from AMD and academic partners, automates the scientific research process, notably reducing research costs to $2.33 per paper and enabling state-of-the-art performance in automated machine learning problem-solving. Human involvement in its co-pilot mode improves the overall quality of research outputs.
- The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery (2408.06292v3): Sakana AI and collaborating institutions developed a comprehensive framework for fully automated scientific discovery, enabling AI agents to conduct an entire research endeavor from hypothesis to peer-reviewed paper. This system generated hundreds of medium-quality papers in machine learning at a cost of under $15 per paper, with its automated reviewer achieving near-human-level performance.
- WebResearcher: Unleashing unbounded reasoning capability in Long-Horizon Agents (2509.13309v2): WebResearcher, an AI agent framework from Alibaba Group's Tongyi Lab, introduces an iterative deep-research paradigm and a scalable data synthesis engine to overcome context limitations in long-horizon tasks. It demonstrated state-of-the-art performance across six challenging benchmarks, achieving a 6.9 percentage point improvement on Humanity's Last Exam and a 9.7 percentage point lead on GAIA over previous top systems.
- SurveyForge: On the Outline Heuristics, Memory-Driven Generation, and  Multi-dimensional Evaluation for Automated Survey Writing (2503.04629v1): Shanghai AI Lab researchers introduce SURVEYFORGE, a breakthrough framework for automated academic survey writing that combines outline heuristics and memory-driven content generation, demonstrating superior performance in reference quality and outline structure while establishing a new evaluation benchmark (SurveyBench) for assessing automated survey generation systems.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
