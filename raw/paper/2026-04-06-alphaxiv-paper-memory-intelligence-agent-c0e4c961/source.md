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
- Jingyu Gong
- Kun Shao
- Yuan Xie
published_at: '2026-04-07T16:26:16Z'
ingested_at: '2026-04-07T21:43:42.636384Z'
content_hash: f142d60fb6a30d35e79faf58c58881690c1168f7335f1c2677272059e5dcbc10
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
- Computer Science
- cs.AI
- cs.MA
- online-learning
- reasoning
- reinforcement-learning
- representation-learning
- self-supervised-learning
- tool-use
- github
- audio
- transcript
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
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04503
canonical_url: https://www.alphaxiv.org/abs/2604.04503
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:11:48.208756Z'
short_summary: The Memory Intelligence Agent (MIA) framework enhances Deep Research Agents by integrating a brain-inspired memory system within a Manager-Planner-Executor architecture. MIA improved average accuracy by 5.5 percentage points on multimodal benchmarks and 7.5 percentage points on text-only tasks compared to prior memory-based methods, also enabling unsupervised self-evolution.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Memory Intelligence Agent

## alphaXiv Summary

The Memory Intelligence Agent (MIA) framework enhances Deep Research Agents by integrating a brain-inspired memory system within a Manager-Planner-Executor architecture. MIA improved average accuracy by 5.5 percentage points on multimodal benchmarks and 7.5 percentage points on text-only tasks compared to prior memory-based methods, also enabling unsupervised self-evolution.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04503
- Source paper: https://arxiv.org/abs/2604.04503
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04503v2.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04503v2.png
- GitHub: https://github.com/ECNU-SII/MIA
- GitHub stars: 50
- Paper ID: 2604.04503
- Canonical ID: 2604.04503v2
- Paper group ID: 019d65d5-2846-740f-ac03-efc7c9c1cc17
- Version ID: 019d6b02-d1f8-77b3-9807-b54ade53e953
- Version: v2
- Version order: 2
- Published at: 2026-04-07T16:26:16+00:00
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

- Visits (all): 215
- Visits (last 7 days): 215
- Total votes: 2
- Public total votes: 14
- X likes: 0

## Abstract

Deep research agents (DRAs) integrate LLM reasoning with external tools. Memory systems enable DRAs to leverage historical experiences, which are essential for efficient reasoning and autonomous evolution. Existing methods rely on retrieving similar trajectories from memory to aid reasoning, while suffering from key limitations of ineffective memory evolution and increasing storage and retrieval costs. To address these problems, we propose a novel Memory Intelligence Agent (MIA) framework, consisting of a Manager-Planner-Executor architecture. Memory Manager is a non-parametric memory system that can store compressed historical search trajectories. Planner is a parametric memory agent that can produce search plans for questions. Executor is another agent that can search and analyze information guided by the search plan. To build the MIA framework, we first adopt an alternating reinforcement learning paradigm to enhance cooperation between the Planner and the Executor. Furthermore, we enable the Planner to continuously evolve during test-time learning, with updates performed on-the-fly alongside inference without interrupting the reasoning process. Additionally, we establish a bidirectional conversion loop between parametric and non-parametric memories to achieve efficient memory evolution. Finally, we incorporate a reflection and an unsupervised judgment mechanisms to boost reasoning and self-evolution in the open world. Extensive experiments across eleven benchmarks demonstrate the superiority of MIA.

## Problem

- Deep research agents face ineffective memory evolution, struggling to consolidate historical experiences into refined strategies.
- Existing memory systems for LLMs incur high storage and retrieval costs due to long contexts, often leading to diluted attention and noise.
- Current systems primarily capture factual knowledge, lacking process-oriented memory needed for guiding complex search path planning and strategy reuse.

## Method

- MIA introduces a Manager-Planner-Executor architecture that decouples historical memory storage, strategic planning, and dynamic execution.
- It employs a dual-memory system with a non-parametric Memory Manager storing compressed trajectories and a parametric Planner internalizing high-value experiences through training.
- The framework utilizes a two-stage alternating Reinforcement Learning paradigm and continual test-time learning for the Planner, enabling autonomous adaptation in unsupervised environments.

## Results

- MIA achieved an average accuracy of 53.6% on multimodal datasets and 53.5% on text-only datasets, surpassing previous memory-based methods by 5.5 and 7.5 percentage points, respectively.
- The framework consistently enhanced the performance of closed-source LLMs (e.g., GPT-5.4, Gemini-3-Flash) on tasks like LiveVQA and HotpotQA, with GPT-5.4 showing up to an 8.9% accuracy gain.
- An unsupervised self-evolution mechanism allowed MIA to accumulate useful experience and progressively solve previously failed problems, achieving performance comparable to or superior to supervised baselines.

## Takeaways

- Decoupling memory management and execution through a multi-agent architecture (Manager-Planner-Executor) improves reasoning efficiency and robustness, mitigating long-context limitations.
- A bidirectional conversion loop between non-parametric episodic memory and parametric strategic knowledge facilitates efficient memory evolution and reduces computational overhead.
- An alternating RL training approach combined with an unsupervised evaluation framework enables agents to continuously improve planning and execution strategies without explicit ground-truth supervision.

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
- Transcript lines: 16
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/ECNU-SII/MIA

## Similar Papers

- ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory (2509.25140v2): Researchers from Google Cloud AI Research and the University of Illinois Urbana-Champaign developed ReasoningBank, a memory framework for LLM agents that distills generalizable reasoning strategies from self-judged successful and failed experiences, combined with Memory-aware Test-Time Scaling (MaTTS). This approach improved agent success rates by up to 8.3 percentage points and reduced interaction steps by up to 2.8 across web navigation and software engineering tasks, fostering continuous self-evolution.
- A-MEM: Agentic Memory for LLM Agents (2502.12110v11): A-Mem introduces a dynamic, agentic memory system for LLM agents, inspired by the Zettelkasten method, enabling autonomous organization, evolution, and retrieval of knowledge for long-term interactions. It achieves up to a six-fold improvement in complex multi-hop reasoning tasks and reduces memory operation token usage by 85-93% compared to existing baselines.
- Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for Large Language Model Agents (2601.01885v1): AgeMem introduces a framework for Large Language Model (LLM) agents that unifies long-term and short-term memory management through a learnable policy, enabling the agent to autonomously control memory operations. This approach improved average task performance across diverse benchmarks by 4.82 to 8.57 percentage points over existing memory-augmented baselines and enhanced memory quality and context efficiency.
- Agentic Reasoning: A Streamlined Framework for Enhancing LLM Reasoning with Agentic Tools (2502.04644v2): The "Agentic Reasoning" framework enhances Large Language Model (LLM) reasoning by integrating streamlined external agents for web-search, code execution, and a novel Mind-Map memory. The approach enables open-source LLMs to achieve state-of-the-art performance, rivalling or surpassing proprietary models on complex expert-level problem-solving and deep research tasks.
- General Agentic Memory Via Deep Research (2511.18423v1): Researchers from BAAI, Peking University, Renmin University of China, and Hong Kong Polytechnic University developed General Agentic Memory (GAM), a framework for AI agents that employs a Just-in-Time Compilation principle through a dual-agent (Memorizer and Researcher) architecture. This approach, designed for dynamic context creation, consistently surpassed existing memory systems and achieved over 90% accuracy on complex multi-step reasoning benchmarks like HotpotQA.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
