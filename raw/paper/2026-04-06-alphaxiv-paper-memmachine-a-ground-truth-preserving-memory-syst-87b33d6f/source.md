---
id: 2026-04-06-alphaxiv-paper-memmachine-a-ground-truth-preserving-memory-syst-87b33d6f
kind: paper
title: 'MemMachine: A Ground-Truth-Preserving Memory System for Personalized AI Agents'
source_url: https://www.alphaxiv.org/abs/2604.04853
source_name: alphaXiv Papers
authors:
- Shu Wang
- Edwin Yu
- Oscar Love
- Tom Zhang
- Tom Wong
- Steve Scargall
- Charles Fan
published_at: '2026-04-06T16:57:06Z'
ingested_at: '2026-04-09T10:01:48.259351Z'
content_hash: 7074ff9cc4a396a849b6816a230fa1b714fae918f83c1126a236ca743fb902d9
identity_hash: 9c8ea50caad414d007cff577f847876035fa9d3f4f0857e4ed881c25022e443e
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- human-ai-interaction
- information-extraction
- ml-systems
- optimization-methods
- reasoning
- tool-use
- transformers
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
external_key: https://www.alphaxiv.org/abs/2604.04853
canonical_url: https://www.alphaxiv.org/abs/2604.04853
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:01:48.259355Z'
short_summary: MemMachine introduces a ground-truth-preserving memory system for personalized AI agents, utilizing a two-tier architecture that minimizes reliance on LLMs for routine operations. It achieved state-of-the-art performance on the LoCoMo benchmark with an LLM Judge Score of 0.8747 and reduced input token usage by approximately 80% compared to Mem0.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# MemMachine: A Ground-Truth-Preserving Memory System for Personalized AI Agents

## alphaXiv Summary

MemMachine introduces a ground-truth-preserving memory system for personalized AI agents, utilizing a two-tier architecture that minimizes reliance on LLMs for routine operations. It achieved state-of-the-art performance on the LoCoMo benchmark with an LLM Judge Score of 0.8747 and reduced input token usage by approximately 80% compared to Mem0.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04853
- Source paper: https://arxiv.org/abs/2604.04853
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04853v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04853v1.png
- Paper ID: 2604.04853
- Canonical ID: 2604.04853v1
- Paper group ID: 019d6656-a93c-706a-af4d-0c4af32690b5
- Version ID: 019d6656-a95a-72ee-b625-2f5526c00c7d
- Version: v1
- Version order: 1
- Published at: 2026-04-06T16:57:06+00:00
- First published at: 2026-04-06T16:57:06+00:00
- Updated at: 2026-04-07T05:07:28.700000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Shu Wang
- Edwin Yu
- Oscar Love
- Tom Zhang
- Tom Wong
- Steve Scargall
- Charles Fan

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- human-ai-interaction
- information-extraction
- ml-systems
- optimization-methods
- reasoning
- tool-use
- transformers

## Metrics

- Visits (all): 51
- Visits (last 7 days): 51
- Total votes: 0
- Public total votes: 7
- X likes: 0

## Abstract

Large Language Model (LLM) agents require persistent memory to maintain personalization, factual continuity, and long-horizon reasoning, yet standard context-window and retrieval-augmented generation (RAG) pipelines degrade over multi-session interactions. We present MemMachine, an open-source memory system that integrates short-term, long-term episodic, and profile memory within a ground-truth-preserving architecture that stores entire conversational episodes and reduces lossy LLM-based extraction. MemMachine uses contextualized retrieval that expands nucleus matches with surrounding context, improving recall when relevant evidence spans multiple dialogue turns. Across benchmarks, MemMachine achieves strong accuracy-efficiency tradeoffs: on LoCoMo it reaches 0.9169 using gpt4.1-mini; on LongMemEvalS (ICLR 2025), a six-dimension ablation yields 93.0 percent accuracy, with retrieval-stage optimizations -- retrieval depth tuning (+4.2 percent), context formatting (+2.0 percent), search prompt design (+1.8 percent), and query bias correction (+1.4 percent) -- outperforming ingestion-stage gains such as sentence chunking (+0.8 percent). GPT-5-mini exceeds GPT-5 by 2.6 percent when paired with optimized prompts, making it the most cost-efficient setup. Compared to Mem0, MemMachine uses roughly 80 percent fewer input tokens under matched conditions. A companion Retrieval Agent adaptively routes queries among direct retrieval, parallel decomposition, or iterative chain-of-query strategies, achieving 93.2 percent on HotpotQA-hard and 92.6 percent on WikiMultiHop under randomized-noise conditions. These results show that preserving episodic ground truth while layering adaptive retrieval yields robust, efficient long-term memory for personalized LLM agents.

## Problem

- Large Language Models (LLMs) have static parameters and restricted context windows, hindering their ability to learn dynamically and maintain long-term context.
- Traditional Retrieval-Augmented Generation (RAG) is insufficient for dynamic, bidirectional interactions required by persistent, personalized AI agents.
- Existing LLM-centric memory systems for agents suffer from high operational costs, potential accuracy degradation due to probabilistic extraction, and accumulating 'factual drift'.

## Method

- MemMachine implements a client-server architecture with a two-tier memory system: episodic memory (short-term and long-term) and profile (semantic) memory, prioritizing ground-truth preservation by storing raw conversational episodes.
- It minimizes LLM dependence for routine memory operations, using LLMs strategically for higher-level functions like summarization and profile extraction.
- The system introduces novel retrieval mechanisms, including contextualized retrieval (expanding matched sentences with neighboring conversational turns) and an LLM-orchestrated Retrieval Agent for multi-hop queries.

## Results

- Achieved an LLM Judge Score of 0.8747 on the LoCoMo benchmark using `gpt-4o-mini`, outperforming Memobase, Zep, Mem0, LangMem, and OpenAI baseline.
- Demonstrated approximately 80% fewer input tokens compared to Mem0 on LoCoMo, translating to significant cost reductions and improved inference latency.
- The Retrieval Agent improved accuracy on HotpotQA hard by +2.0 percentage points and WikiMultiHop (randomized-noise) by +5.2 percentage points, showcasing enhanced performance on complex multi-hop reasoning tasks.

## Takeaways

- Ground-truth preservation via fine-grained, sentence-level indexing is critical for minimizing factual drift and errors in long-term AI agent interactions.
- Retrieval-stage optimizations, such as increased retrieval depth and improved context formatting, contribute more significantly to overall accuracy than ingestion-stage changes.
- Smaller, instruction-following LLMs can outperform larger models when co-optimized with tailored prompts, indicating the importance of model-prompt co-design for efficiency and performance.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6656-a93c-706a-af4d-0c4af32690b5/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6656-a93c-706a-af4d-0c4af32690b5/transcript.json

## Similar Papers

- Mem0: Building Production-Ready AI Agents with Scalable Long-Term Memory (2504.19413v1): Mem0 and Mem0g offer scalable long-term memory architectures for AI agents, enabling them to overcome LLM context window limitations by dynamically extracting, consolidating, and retrieving salient information. These solutions significantly enhance conversational coherence and reasoning capabilities while achieving substantial reductions in latency and token consumption compared to existing methods.
- Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for Large Language Model Agents (2601.01885v1): AgeMem introduces a framework for Large Language Model (LLM) agents that unifies long-term and short-term memory management through a learnable policy, enabling the agent to autonomously control memory operations. This approach improved average task performance across diverse benchmarks by 4.82 to 8.57 percentage points over existing memory-augmented baselines and enhanced memory quality and context efficiency.
- MemInsight: Autonomous Memory Augmentation for LLM Agents (2503.21760v2): MemInsight, developed by AWS AI, introduces an autonomous framework to enhance Large Language Model (LLM) agents' long-term memory by automatically extracting and utilizing semantically meaningful attributes from historical interactions. This approach improves information retrieval and agent performance across question answering, conversational recommendation, and event summarization tasks.
- LightMem: Lightweight and Efficient Memory-Augmented Generation (2510.18866v4): LightMem, developed by Zhejiang University, presents a cognition-inspired, multi-stage memory system for large language models to efficiently manage long-term conversational history. It reduces online token consumption by up to 117.1x and API calls by up to 309.9x, while improving task accuracy by up to 29.29% on interactive memory benchmarks.
- SimpleMem: Efficient Lifelong Memory for LLM Agents (2601.02553v3): SimpleMem presents an efficient lifelong memory framework for LLM agents, utilizing semantic structured compression and adaptive retrieval to filter redundancy and consolidate experiences. The system achieves an average F1 score improvement of 26.4% while reducing inference-time token consumption by up to 30x and speeding up memory construction 14x compared to existing methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
