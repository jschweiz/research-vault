---
id: 2026-04-07-alphaxiv-paper-autosota-an-end-to-end-automated-research-system-3756ab92
kind: paper
title: 'AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery'
source_url: https://www.alphaxiv.org/abs/2604.05550
source_name: alphaXiv Papers
authors:
- Yu Li
- Chenyang Shao
- Xinyang Liu
- Ruotong Zhao
- Peijie Liu
- Hongyuan Su
- Zhibin Chen
- Qinglong Yang
- Anjie Xu
- Yi Fang
- Qingbin Zeng
- Tianxing Li
- Jingbo Xu
- Fengli Xu
- Yong Li
- Tie-Yan Liu
published_at: '2026-04-07T07:52:01Z'
ingested_at: '2026-04-09T12:08:47.189118Z'
content_hash: 76d58d13ced6281d9d0f6b95d1eae7d82fda514f5e4a0eb3290c8e5dee04cebc
identity_hash: c3092a52b50e4e67908f375db43f4f869f25814aba5024da2c675e9d783ede1e
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- computer science
- cs.ce
- cs.cl
- ml-systems
- neural-architecture-search
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
external_key: https://www.alphaxiv.org/abs/2604.05550
canonical_url: https://www.alphaxiv.org/abs/2604.05550
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:08:47.189123Z'
short_summary: An end-to-end automated research system named AutoSOTA, developed by Tsinghua University and Zhongguancun Academy, discovers new State-of-the-Art AI models from unstructured research papers. The system autonomously reproduces and optimizes original methods, achieving an average performance improvement of approximately 10% across 105 diverse AI papers within about five hours of execution per paper.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T16:19:42.710631Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 2a443184b97be635237240020191af560c333d1b481272d1b8fd50c4ee5e03be
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback+alphaxiv-metrics-v1
lightweight_scoring_input_hash: dcad590433546a8def57e3461936e8e8d189b63f2b4317bbd048f28d1013be82
lightweight_score:
  relevance_score: 0.5465
  source_fit_score: 0.5593
  topic_fit_score: 0.4
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.5593
  bucket_hint: worth_a_skim
  reason: 'Heuristic fallback based on 1 favorite-topic match. alphaXiv engagement signals: 3 public votes, 0 total votes, 48 visits in the last 7 days.'
  evidence_quotes:
  - An end-to-end automated research system named AutoSOTA, developed by Tsinghua University and Zhongguancun Academy, discovers new State-of-the-Art AI models from
---
# AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery

## alphaXiv Summary

An end-to-end automated research system named AutoSOTA, developed by Tsinghua University and Zhongguancun Academy, discovers new State-of-the-Art AI models from unstructured research papers. The system autonomously reproduces and optimizes original methods, achieving an average performance improvement of approximately 10% across 105 diverse AI papers within about five hours of execution per paper.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05550
- Source paper: https://arxiv.org/abs/2604.05550
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05550v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05550v1.png
- Paper ID: 2604.05550
- Canonical ID: 2604.05550v1
- Paper group ID: 019d6b00-2ced-78a3-bc60-c75fc74c1cea
- Version ID: 019d6b00-2d31-7587-a344-63dabc43735e
- Version: v1
- Version order: 1
- Published at: 2026-04-07T07:52:01+00:00
- First published at: 2026-04-07T07:52:01+00:00
- Updated at: 2026-04-08T02:51:06.861000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yu Li
- Chenyang Shao
- Xinyang Liu
- Ruotong Zhao
- Peijie Liu
- Hongyuan Su
- Zhibin Chen
- Qinglong Yang
- Anjie Xu
- Yi Fang
- Qingbin Zeng
- Tianxing Li
- Jingbo Xu
- Fengli Xu
- Yong Li
- Tie-Yan Liu

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.CE
- cs.CL
- ml-systems
- neural-architecture-search
- optimization-methods
- training-orchestration

## Metrics

- Visits (all): 48
- Visits (last 7 days): 48
- Total votes: 0
- Public total votes: 3
- X likes: 0

## Abstract

Artificial intelligence research increasingly depends on prolonged cycles of reproduction, debugging, and iterative refinement to achieve State-Of-The-Art (SOTA) performance, creating a growing need for systems that can accelerate the full pipeline of empirical model optimization. In this work, we introduce AutoSOTA, an end-to-end automated research system that advances the latest SOTA models published in top-tier AI papers to reproducible and empirically improved new SOTA models. We formulate this problem through three tightly coupled stages: resource preparation and goal setting; experiment evaluation; and reflection and ideation. To tackle this problem, AutoSOTA adopts a multi-agent architecture with eight specialized agents that collaboratively ground papers to code and dependencies, initialize and repair execution environments, track long-horizon experiments, generate and schedule optimization ideas, and supervise validity to avoid spurious gains. We evaluate AutoSOTA on recent research papers collected from eight top-tier AI conferences under filters for code availability and execution cost. Across these papers, AutoSOTA achieves strong end-to-end performance in both automated replication and subsequent optimization. Specifically, it successfully discovers 105 new SOTA models that surpass the original reported methods, averaging approximately five hours per paper. Case studies spanning LLM, NLP, computer vision, time series, and optimization further show that the system can move beyond routine hyperparameter tuning to identify architectural innovation, algorithmic redesigns, and workflow-level improvements. These results suggest that end-to-end research automation can serve not only as a performance optimizer, but also as a new form of research infrastructure that reduces repetitive experimental burden and helps redirect human attention toward higher-level scientific creativity.

## Problem

- Achieving State-of-the-Art (SOTA) performance in AI research requires extensive, repetitive cycles of implementation, reproduction, debugging, and refinement, consuming significant human effort.
- Existing Automated Machine Learning (AutoML) systems are limited to predefined search spaces and lack the ability to invent novel algorithms, synthesize external knowledge, or perform complex debugging.
- Current LLM-driven algorithm discovery and autonomous AI scientist systems often operate in sandboxed environments, struggle with long-horizon debugging, environment initialization, and lack robust supervisory mechanisms to ensure methodological comparability for SOTA advancement.

## Method

- AutoSOTA is an end-to-end multi-agent system composed of eight specialized agents, structured into three macro-modules: Resource Preparation and Goal Setting, Experiment Evaluation, and Reflection & Ideation.
- The system converts unstructured research papers into executable environments, reproduces reported baselines, and then performs open-ended, methodologically valid reflection to discover empirically improved SOTA models.
- It integrates agents for resource acquisition, objective definition, execution initialization, real-time monitoring, fault repair, hypothesis generation, and experiment orchestration, all supervised by a methodological validity agent.

## Results

- AutoSOTA successfully discovered new SOTA models, achieving an average performance improvement of approximately 10% over the original main methods reported in 105 diverse AI papers.
- The system exhibited consistent robustness across multidisciplinary tasks (e.g., LLM, NLP, CV, Time Series, Optimization), completing optimizations within an average of five hours of execution time per paper.
- Case studies demonstrated AutoSOTA's ability to identify deep architectural innovations, algorithmic redesigns, and bug fixes, such as a 13.44% throughput improvement in LLM decoding and a 51.4% relative improvement in CVRP optimality gap.

## Takeaways

- Automating the entire empirical AI model optimization pipeline, from unstructured literature to SOTA-surpassing code, can significantly accelerate research and free human researchers for higher-level conceptual work.
- A multi-agent architecture with specialized roles for resource preparation, experiment evaluation, and iterative reflection, combined with external memory and a skill library, enables robust, long-horizon autonomous research.
- Enforcing methodological validity through a 'Red Line System' is crucial to ensure that discovered improvements are scientifically sound, comparable, and not based on spurious gains or unfair experimental settings.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b00-2ced-78a3-bc60-c75fc74c1cea/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b00-2ced-78a3-bc60-c75fc74c1cea/transcript.json

## Similar Papers

- Paper2Code: Automating Code Generation from Scientific Papers in Machine Learning (2504.17192v5): PaperCoder introduces a multi-agent LLM framework that automatically generates executable, repository-level code directly from scientific machine learning papers. The framework significantly enhances research reproducibility by achieving superior performance on both newly established and existing benchmarks for code generation from text.
- The AI Scientist-v2: Workshop-Level Automated Scientific Discovery via  Agentic Tree Search (2504.08066v1): An autonomous AI system conducts end-to-end scientific research through agentic tree search, successfully generating a peer-reviewed workshop paper without relying on human-authored code templates, marking the first instance of a fully AI-generated paper passing peer review with a 6.33/10 reviewer score.
- Agent Laboratory: Using LLM Agents as Research Assistants (2501.04227v2): Agent Laboratory, an LLM-based framework from AMD and academic partners, automates the scientific research process, notably reducing research costs to $2.33 per paper and enabling state-of-the-art performance in automated machine learning problem-solving. Human involvement in its co-pilot mode improves the overall quality of research outputs.
- The AI Scientist: Towards Fully Automated Open-Ended Scientific Discovery (2408.06292v3): Sakana AI and collaborating institutions developed a comprehensive framework for fully automated scientific discovery, enabling AI agents to conduct an entire research endeavor from hypothesis to peer-reviewed paper. This system generated hundreds of medium-quality papers in machine learning at a cost of under $15 per paper, with its automated reviewer achieving near-human-level performance.
- AlphaGo Moment for Model Architecture Discovery (2507.18074v1): ASI-ARCH, developed by Shanghai Jiao Tong University and collaborators, is an autonomous system that discovers novel neural architectures by leveraging large language models for design, implementation, and analysis. It successfully identified 106 state-of-the-art linear attention architectures that outperform human-designed baselines and demonstrated the first empirical scaling law for scientific discovery, showing that architectural breakthroughs can be scaled computationally.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
