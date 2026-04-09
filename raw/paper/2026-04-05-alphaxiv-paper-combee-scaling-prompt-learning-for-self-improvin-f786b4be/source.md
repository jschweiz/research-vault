---
id: 2026-04-05-alphaxiv-paper-combee-scaling-prompt-learning-for-self-improvin-f786b4be
kind: paper
title: 'Combee: Scaling Prompt Learning for Self-Improving Language Model Agents'
source_url: https://www.alphaxiv.org/abs/2604.04247
source_name: alphaXiv Papers
authors:
- Hanchen Li
- Runyuan He
- Qizheng Zhang
- Changxiu Ji
- Qiuyang Mang
- Xiaokun Chen
- Lakshya A Agrawal
- Wei-Liang Liao
- Eric Yang
- Alvin Cheung
- James Zou
- Kunle Olukotun
- Ion Stoica
- Joseph E. Gonzalez
published_at: '2026-04-05T20:07:48Z'
ingested_at: '2026-04-09T12:08:19.071014Z'
content_hash: ef26203f1303b60b6932e574936a8fc011ab77ddf1eb9ca01fa46a9a027cdd2d
identity_hash: 69403063f105986c5eee9886ddba07507aab1a5647043d97fdfe02dc2845f476
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- computer science
- cs.ai
- cs.cl
- cs.lg
- distributed-learning
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
external_key: https://www.alphaxiv.org/abs/2604.04247
canonical_url: https://www.alphaxiv.org/abs/2604.04247
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:08:19.071021Z'
short_summary: Combee presents a distributed framework for scaling prompt learning in self-improving language model agents. It effectively tackles the "context overload" challenge in parallel aggregation, yielding up to a 17x speedup compared to sequential methods while preserving or enhancing accuracy on benchmarks such as AppWorld and Terminal-Bench 2.0.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T16:19:42.578451Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 153b098927b87d91f75571a61f501cafad685fca59394c1d11acebab42334cf1
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b+alphaxiv-metrics-v1
lightweight_scoring_input_hash: e802b73b4013bc67b6e83f0daf7901199edadf5de70db9cdd82b0ca99cc99725
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.5899
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: 'The document directly addresses the user''s favorite topics of LLM agents, scaling, and evaluation, making it a high-priority read. alphaXiv engagement signals: 12 public votes, 2 total votes, 114 visits in the last 7 days.'
  evidence_quotes:
  - Combee presents a distributed framework for scaling prompt learning in self-improving language model agents.
  - Combee speeds up learning and enables running many agents in parallel while learning from their aggregate traces without quality degradation.
  - Combee achieved up to a 17x speedup in training time over sequential prompt learning baselines across various agentic and domain-specific benchmarks.
---
# Combee: Scaling Prompt Learning for Self-Improving Language Model Agents

## alphaXiv Summary

Combee presents a distributed framework for scaling prompt learning in self-improving language model agents. It effectively tackles the "context overload" challenge in parallel aggregation, yielding up to a 17x speedup compared to sequential methods while preserving or enhancing accuracy on benchmarks such as AppWorld and Terminal-Bench 2.0.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04247
- Source paper: https://arxiv.org/abs/2604.04247
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04247v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04247v1.png
- Paper ID: 2604.04247
- Canonical ID: 2604.04247v1
- Paper group ID: 019d65ff-90bb-7060-907e-fa43c4f93a58
- Version ID: 019d65ff-9120-778a-8fe3-1bc7ac1bd9c1
- Version: v1
- Version order: 1
- Published at: 2026-04-05T20:07:48+00:00
- First published at: 2026-04-05T20:07:48+00:00
- Updated at: 2026-04-07T03:32:20.795000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Hanchen Li
- Runyuan He
- Qizheng Zhang
- Changxiu Ji
- Qiuyang Mang
- Xiaokun Chen
- Lakshya A Agrawal
- Wei-Liang Liao
- Eric Yang
- Alvin Cheung
- James Zou
- Kunle Olukotun
- Ion Stoica
- Joseph E. Gonzalez

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.CL
- cs.LG
- distributed-learning
- meta-learning
- ml-systems
- optimization-methods

## Metrics

- Visits (all): 114
- Visits (last 7 days): 114
- Total votes: 2
- Public total votes: 12
- X likes: 0

## Abstract

Recent advances in prompt learning allow large language model agents to acquire task-relevant knowledge from inference-time context without parameter changes. For example, existing methods (like ACE or GEPA) can learn system prompts to improve accuracy based on previous agent runs. However, these methods primarily focus on single-agent or low-parallelism settings. This fundamentally limits their ability to efficiently learn from a large set of collected agentic traces. It would be efficient and beneficial to run prompt learning in parallel to accommodate the growing trend of learning from many agentic traces or parallel agent executions. Yet without a principled strategy for scaling, current methods suffer from quality degradation with high parallelism. To improve both the efficiency and quality of prompt learning, we propose Combee, a novel framework to scale parallel prompt learning for self-improving agents. Combee speeds up learning and enables running many agents in parallel while learning from their aggregate traces without quality degradation. To achieve this, Combee leverages parallel scans and employs an augmented shuffle mechanism; Combee also introduces a dynamic batch size controller to balance quality and delay. Evaluations on AppWorld, Terminal-Bench, Formula, and FiNER demonstrate that Combee achieves up to 17x speedup over previous methods with comparable or better accuracy and equivalent cost.

## Problem

- Existing prompt learning methods for LLM agents are inefficient and not designed for high-parallelism scenarios, hindering rapid adaptation.
- Naive parallelization of prompt learning leads to "context overload," where aggregator LLMs fail to distill high-quality insights from numerous reflections, causing information loss and performance degradation.
- This limitation restricts the ability of self-improving LLM agents to learn efficiently from vast interaction traces in real-world, large-scale deployments.

## Method

- Combee introduces a distributed Map-Shuffle-Reduce paradigm for prompt learning, integrating parallel scan aggregation, augmented shuffling, and a dynamic batch size controller.
- Parallel scan aggregation employs a hierarchical, multi-level approach to combine reflections, preventing context overload for individual aggregator LLMs.
- Augmented shuffling duplicates and shuffles reflections to ensure critical information is robustly integrated, particularly when processing large batch sizes, and a dynamic batch size controller optimizes learning efficiency by adapting to workload.

## Results

- Combee achieved up to a 17x speedup in training time over sequential prompt learning baselines across various agentic and domain-specific benchmarks.
- It mitigated context overload, producing significantly richer and larger context artifacts (e.g., 6,887 tokens vs. 526 tokens for naive methods) while maintaining or improving accuracy with equivalent training costs.
- On AppWorld, Combee achieved the highest average score (65.8%) at batch size 40 with a 12x speedup; on Terminal-Bench 2.0, it recovered most sequential quality (35.6% vs. 37.9%) with over a 17x reduction in training time.

## Takeaways

- The primary bottleneck in scaling prompt learning is "context overload," not just context window limits, as aggregator LLMs struggle to distill quality insights from too many simultaneous inputs.
- Hierarchical aggregation via a parallel scan effectively manages LLM context processing, enabling high parallelism without overwhelming the LLM's distillation capabilities.
- Introducing redundancy through augmented shuffling is crucial for robust parallel learning, providing multiple opportunities for high-value insights to be incorporated into the learned context.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65ff-90bb-7060-907e-fa43c4f93a58/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65ff-90bb-7060-907e-fa43c4f93a58/transcript.json

## Similar Papers

- Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models (2510.04618v3): Agentic Context Engineering (ACE) is a framework that enables large language models to self-improve by dynamically evolving comprehensive, 'playbook'-style contexts instead of static prompts. It consistently achieved average performance gains of over 8% across agentic and domain-specific tasks while reducing adaptation costs by more than 80% compared to baselines.
- ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory (2509.25140v2): Researchers from Google Cloud AI Research and the University of Illinois Urbana-Champaign developed ReasoningBank, a memory framework for LLM agents that distills generalizable reasoning strategies from self-judged successful and failed experiences, combined with Memory-aware Test-Time Scaling (MaTTS). This approach improved agent success rates by up to 8.3 percentage points and reduced interaction steps by up to 2.8 across web navigation and software engineering tasks, fostering continuous self-evolution.
- Learning Adaptive Parallel Reasoning with Language Models (2504.15466v2): Researchers from UC Berkeley developed Adaptive Parallel Reasoning (APR), a framework that teaches language models to dynamically orchestrate parallel and serial computations during inference using `spawn()` and `join()` operations. On the Countdown task, this approach achieved 83.4% accuracy, outperforming serialized reasoning methods with better computational efficiency and a superior accuracy-latency profile.
- Native Parallel Reasoner: Reasoning in Parallelism via Self-Distilled Reinforcement Learning (2512.07461v2): The Native Parallel Reasoner (NPR) framework, developed by NLCo Lab at BIGAI, enables large language models (LLMs) to intrinsically develop parallel reasoning abilities through a self-distilled reinforcement learning process. It achieves significant accuracy improvements and up to 4.6x inference speedups on diverse reasoning benchmarks, demonstrating 100% genuine parallel execution without reliance on external teacher models.
- Reinforcement Learning for Self-Improving Agent with Skill Library (2512.17102v2): The SAGE reinforcement learning framework, developed by a team from the University of Wisconsin–Madison and AWS Agentic AI, systematically integrates skill learning into LLM agent training. This framework enhances agent self-improvement by enabling dynamic skill generation and utilization, leading to an 8.9% higher scenario goal completion, 26% fewer interaction steps, and 59% fewer generated tokens on the AppWorld dataset compared to baseline methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
