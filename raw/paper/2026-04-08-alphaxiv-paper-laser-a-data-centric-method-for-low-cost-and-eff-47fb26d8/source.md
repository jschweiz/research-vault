---
id: 2026-04-08-alphaxiv-paper-laser-a-data-centric-method-for-low-cost-and-eff-47fb26d8
kind: paper
title: 'LASER: A Data-Centric Method for Low-Cost and Efficient SQL Rewriting based on SQL-GRPO'
source_url: https://www.alphaxiv.org/abs/2604.06804
source_name: alphaXiv Papers
authors:
- Jiahui Li
- Tongwang Wu
- Yuren Mao
- Rong Kang
- Tieying Zhang
- Yunjun Gao
published_at: '2026-04-08T08:17:25Z'
ingested_at: '2026-04-09T09:59:44.047239Z'
content_hash: 3642764d5c3979d0dcf3a39c75b67c4bc4d76548db0f97d7d0666ab60b9d2d21
identity_hash: cf159413b9282da9f4ac55083d98b0c47e6d43a760780e8725828307f72dab0c
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.DB
- audio
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06804
canonical_url: https://www.alphaxiv.org/abs/2604.06804
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:59:44.047244Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# LASER: A Data-Centric Method for Low-Cost and Efficient SQL Rewriting based on SQL-GRPO

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06804
- Source paper: https://arxiv.org/abs/2604.06804
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06804v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06804v1.png
- Paper ID: 2604.06804
- Canonical ID: 2604.06804v1
- Paper group ID: 019d6ff6-d613-7171-ac88-054610d876fe
- Version ID: 019d6ff6-d649-78bf-bc1d-022dfaac5895
- Version: v1
- Version order: 1
- Published at: 2026-04-08T08:17:25+00:00
- First published at: 2026-04-08T08:17:25+00:00
- Updated at: 2026-04-09T01:59:00.883000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Jiahui Li
- Tongwang Wu
- Yuren Mao
- Rong Kang
- Tieying Zhang
- Yunjun Gao

## Topics

- Computer Science
- cs.DB

## Metrics

- Visits (all): 19
- Visits (last 7 days): 19
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Query rewriting, the process of transforming queries into semantically equivalent yet more efficient variants, is crucial for database optimization. Existing solutions predominantly rely on either rule-based heuristics or Large Language Models (LLMs). However, traditional rule-based methods lack adaptability, while LLM-based approaches incur prohibitive inference costs and privacy risks. In contrast, Small Language Models (SLMs) present a compelling middle ground, potentially offering both flexibility and efficiency. However, the development of such compact models is severely bottlenecked by the scarcity of high-quality, domain-specific training data. To bridge this gap, we introduce LASER, a data-centric framework designed to empower small models for robust SQL optimization. First, to address the scarcity of existing benchmarks and the limited optimization headroom of generic synthetic queries, we construct SQL-MCTS, a large-scale corpus of complex slow queries. We employ an MCTS-based hybrid expansion strategy that combines rule-guided anti-patterns with LLM mutations to evolve structurally expressive seeds into execution-verified slow variants. Second, to enable the model to autonomously discover latency-aware rewriting patterns, we propose SQL-GRPO, a specialized alignment strategy adapted from Group Relative Policy Optimization. By integrating Anchored Group Advantage to refine advantage estimation and Complexity-Adaptive Dynamic Rollout to efficiently allocate exploration budgets, this approach effectively empowers compact models to master execution-based optimization logic. Implemented on Qwen3 models, LASER significantly outperforms rule-based systems and LLMs in execution efficiency, while exhibiting robust zero-shot transferability with minimal overhead.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6ff6-d613-7171-ac88-054610d876fe/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ff6-d613-7171-ac88-054610d876fe/transcript.json

## Similar Papers

- A Query Optimization Method Utilizing Large Language Models (2503.06902v1): Researchers from Renmin University introduce LLMOpt, a query optimization framework that leverages large language models to generate query plans and select optimal execution strategies, demonstrating reduced execution latency compared to traditional optimizers while maintaining practical end-to-end performance through a novel list-wise plan selection approach.
- Distill-C: Enhanced NL2SQL via Distilled Customization with LLMs (2504.00048v1)
- MCTS-SQL: Light-Weight LLMs can Master the Text-to-SQL through Monte Carlo Tree Search (2501.16607v3)
- Alpha-SQL: Zero-Shot Text-to-SQL using Monte Carlo Tree Search (2502.17248v2): A zero-shot Text-to-SQL framework, Alpha-SQL, combines Large Language Models with Monte Carlo Tree Search and a self-supervised reward function. This approach enables smaller, open-source LLMs to reach state-of-the-art execution accuracy, exceeding prior zero-shot methods and rivaling larger, proprietary models such as GPT-4o on benchmarks like BIRD and Spider.
- SEFRQO: A Self-Evolving Fine-Tuned RAG-Based Query Optimizer (2508.17556v1)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
