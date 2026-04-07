---
id: 2026-04-06-alphaxiv-paper-memory-intelligence-agent-c0e4c961
kind: paper
title: Memory Intelligence Agent
source_url: https://www.alphaxiv.org/abs/2604.04503
source_name: alphaXiv Papers
authors:
  - Jingyang Qiao
  - Weicheng Meng
  - Yu Cheng
  - Zhihang Lin
  - Zhizhong Zhang
  - Xin Tan
published_at: 2026-04-06T07:59:52Z
ingested_at: 2026-04-07T21:43:42.636384Z
content_hash: 4d65a989816263b31bf59df94d2a498a5593e24f5ff49be4b8d7f8bbd9af1ece
tags:
  - paper
  - alphaxiv
  - research
  - agentic-frameworks
  - agents
  - computer science
  - continual-learning
  - cs.ai
  - cs.ma
  - multi-agent-learning
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
external_key: https://www.alphaxiv.org/abs/2604.04503
canonical_url: https://www.alphaxiv.org/abs/2604.04503
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-07T21:43:42.636394Z
short_summary: # Memory Intelligence Agent ## alphaXiv Summary The Memory Intelligence Agent (MIA) framework enhances deep research agents by integrating brain-inspired memory mechanisms, a Manager-Planner-Executor architecture, and a novel unsupervised self-evolution capability. It achieves an average accuracy of 53.6% on multimodal datasets and 53.5% on text-only datasets, outperforming previous memory-based methods by 5.46 and 7.5 percentage points, respectively.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-07T21:46:33.316573Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 4d65a989816263b31bf59df94d2a498a5593e24f5ff49be4b8d7f8bbd9af1ece
lightweight_enrichment_error: null
---
# Memory Intelligence Agent

## alphaXiv Summary

The Memory Intelligence Agent (MIA) framework enhances deep research agents by integrating brain-inspired memory mechanisms, a Manager-Planner-Executor architecture, and a novel unsupervised self-evolution capability. It achieves an average accuracy of 53.6% on multimodal datasets and 53.5% on text-only datasets, outperforming previous memory-based methods by 5.46 and 7.5 percentage points, respectively.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04503
- Source paper: https://arxiv.org/abs/2604.04503
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04503v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04503v1.png
- GitHub: https://github.com/ECNU-SII/MIA
- GitHub stars: 50
- Paper ID: 2604.04503
- Canonical ID: 2604.04503v1
- Paper group ID: 019d65d5-2846-740f-ac03-efc7c9c1cc17
- Version ID: 019d65d5-2876-75f2-84bc-a968c3d9b335
- Version: v1
- Version order: 1
- Published at: 2026-04-06T07:59:52+00:00
- First published at: 2026-04-06T07:59:52+00:00
- Updated at: 2026-04-07T02:46:01.542000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Jingyang Qiao
- Weicheng Meng
- Yu Cheng
- Zhihang Lin
- Zhizhong Zhang
- Xin Tan
- Jingyu Gong
- Kun Shao
- Yuan Xie

## Topics

- agentic-frameworks
- agents
- Computer Science
- continual-learning
- cs.AI
- cs.MA
- multi-agent-learning
- online-learning
- reasoning
- reinforcement-learning
- representation-learning
- self-supervised-learning
- tool-use

## Metrics

- Visits (all): 54
- Visits (last 7 days): 54
- Total votes: 0
- Public total votes: 5
- X likes: 0

## Abstract

Deep research agents (DRAs) integrate LLM reasoning with external tools. Memory systems enable DRAs to leverage historical experiences, which are essential for efficient reasoning and autonomous evolution. Existing methods rely on retrieving similar trajectories from memory to aid reasoning, while suffering from key limitations of ineffective memory evolution and increasing storage and retrieval costs. To address these problems, we propose a novel Memory Intelligence Agent (MIA) framework, consisting of a Manager-Planner-Executor architecture. Memory Manager is a non-parametric memory system that can store compressed historical search trajectories. Planner is a parametric memory agent that can produce search plans for questions. Executor is another agent that can search and analyze information guided by the search plan. To build the MIA framework, we first adopt an alternating reinforcement learning paradigm to enhance cooperation between the Planner and the Executor. Furthermore, we enable the Planner to continuously evolve during test-time learning, with updates performed on-the-fly alongside inference without interrupting the reasoning process. Additionally, we establish a bidirectional conversion loop between parametric and non-parametric memories to achieve efficient memory evolution. Finally, we incorporate a reflection and an unsupervised judgment mechanisms to boost reasoning and self-evolution in the open world. Extensive experiments across eleven benchmarks demonstrate the superiority of MIA.

## Problem

- Existing deep research agents struggle with attention dilution and noise from long-context memory, leading to inefficient retrieval and storage costs.
- Traditional memory systems primarily store factual knowledge, lacking process-oriented memory crucial for guiding complex planning and exploration strategies.
- Suboptimal collaboration between untrained planning and execution agents, compounded by ineffective few-shot example selection, limits performance in multi-turn reasoning.

## Method

- MIA introduces a Manager-Planner-Executor architecture that utilizes a non-parametric Memory Manager to store compressed, high-value historical search trajectories, and a parametric Planner to generate plans, with an Executor performing actions.
- A two-stage alternating Reinforcement Learning (RL) strategy trains the Planner and Executor for synergistic cooperation, enhancing plan interpretation and execution.
- An online Test-Time Learning (TTL) mechanism enables continuous self-evolution during inference, leveraging an unsupervised evaluation framework that mimics a scientific peer-review process to update memory and parameters without ground-truth labels.

## Results

- MIA achieved an average accuracy of 53.6% on multimodal datasets, surpassing previous memory-based methods by an average of 5.46 percentage points, and maintained competitive performance against larger closed-source general models.
- On text-only datasets, MIA attained an average accuracy of 53.5%, improving upon the Memento baseline by an average of 7.5 percentage points.
- Ablation studies confirmed that each proposed module, including the Manager-Planner-Executor architecture, reflection mechanism, alternating RL training, and online TTL, individually contributes to improved reasoning accuracy, totaling an 8.94% increase on multimodal and 12.38% on text-only benchmarks.

## Takeaways

- Decoupling explicit historical memory (non-parametric) from internalized planning knowledge (parametric) effectively mitigates long-context issues and improves memory efficiency.
- Synergistic training and dynamic feedback between planning and execution agents significantly enhance multi-turn reasoning and task completion reliability.
- Continuous self-evolution in unsupervised environments is achievable through selective memory compression, parameter updates, and a robust LLM-based peer-review evaluation system.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d5-2846-740f-ac03-efc7c9c1cc17/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d5-2846-740f-ac03-efc7c9c1cc17/transcript.json

## Resources

- GitHub repository: https://github.com/ECNU-SII/MIA

## Similar Papers

- ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory (2509.25140v2): Researchers from Google Cloud AI Research and the University of Illinois Urbana-Champaign developed ReasoningBank, a memory framework for LLM agents that distills generalizable reasoning strategies from self-judged successful and failed experiences, combined with Memory-aware Test-Time Scaling (MaTTS). This approach improved agent success rates by up to 8.3 percentage points and reduced interaction steps by up to 2.8 across web navigation and software engineering tasks, fostering continuous self-evolution.
- A-MEM: Agentic Memory for LLM Agents (2502.12110v11): A-Mem introduces a dynamic, agentic memory system for LLM agents, inspired by the Zettelkasten method, enabling autonomous organization, evolution, and retrieval of knowledge for long-term interactions. It achieves up to a six-fold improvement in complex multi-hop reasoning tasks and reduces memory operation token usage by 85-93% compared to existing baselines.
- Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for Large Language Model Agents (2601.01885v1): AgeMem introduces a framework for Large Language Model (LLM) agents that unifies long-term and short-term memory management through a learnable policy, enabling the agent to autonomously control memory operations. This approach improved average task performance across diverse benchmarks by 4.82 to 8.57 percentage points over existing memory-augmented baselines and enhanced memory quality and context efficiency.
- Agentic Reasoning: A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools (2502.04644v2): The "Agentic Reasoning" framework enhances Large Language Model (LLM) reasoning by integrating streamlined external agents for web-search, code execution, and a novel Mind-Map memory. The approach enables open-source LLMs to achieve state-of-the-art performance, rivalling or surpassing proprietary models on complex expert-level problem-solving and deep research tasks.
- General Agentic Memory Via Deep Research (2511.18423v1): Researchers from BAAI, Peking University, Renmin University of China, and Hong Kong Polytechnic University developed General Agentic Memory (GAM), a framework for AI agents that employs a Just-in-Time Compilation principle through a dual-agent (Memorizer and Researcher) architecture. This approach, designed for dynamic context creation, consistently surpassed existing memory systems and achieved over 90% accuracy on complex multi-step reasoning benchmarks like HotpotQA.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
