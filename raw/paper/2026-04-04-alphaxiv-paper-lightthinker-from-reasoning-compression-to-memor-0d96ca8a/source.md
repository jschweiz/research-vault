---
id: 2026-04-04-alphaxiv-paper-lightthinker-from-reasoning-compression-to-memor-0d96ca8a
kind: paper
title: 'LightThinker++: From Reasoning Compression to Memory Management'
source_url: https://www.alphaxiv.org/abs/2604.03679
source_name: alphaXiv Papers
authors:
- Yuqi Zhu
- Jintian Zhang
- Zhenjie Wan
- Yujie Luo
- Shuofei Qiao
- Zhengke Gui
- Da Zheng
- Lei Liang
- Huajun Chen
- Ningyu Zhang
published_at: '2026-04-04T10:46:09Z'
ingested_at: '2026-04-07T21:43:07.714695Z'
content_hash: 3e67009d3fafc7a518bbf308fb3360abf5a5293e9f6c447de535e088f59d1a5c
identity_hash: acbfc80bf03e71ccb2cac62d3786b8a0273fc5378fcdefabe767ecb76ba1118f
tags:
- paper
- alphaxiv
- research
- agents
- computer science
- cs.ai
- cs.cl
- cs.ir
- cs.lg
- cs.mm
- Computer Science
- cs.AI
- cs.CL
- cs.IR
- cs.LG
- cs.MM
- efficient-transformers
- inference-optimization
- model-compression
- optimization-methods
- reasoning
- transformers
- github
- audio
- summary
status: active
asset_paths:
- alphaxiv-ai-detection.json
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
external_key: https://www.alphaxiv.org/abs/2604.03679
canonical_url: https://www.alphaxiv.org/abs/2604.03679
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:59:02.296145Z'
short_summary: LightThinker and LightThinker++ are proposed, enabling large language models to efficiently manage reasoning context by compressing intermediate thoughts. LightThinker reduces peak token usage by up to 70% and inference time by 26% through implicit compression, while LightThinker++ employs explicit, adaptive memory management to maintain reasoning fidelity and reduce active context by 60-70% in long-horizon agentic tasks.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# LightThinker++: From Reasoning Compression to Memory Management

## alphaXiv Summary

LightThinker and LightThinker++ are proposed, enabling large language models to efficiently manage reasoning context by compressing intermediate thoughts. LightThinker reduces peak token usage by up to 70% and inference time by 26% through implicit compression, while LightThinker++ employs explicit, adaptive memory management to maintain reasoning fidelity and reduce active context by 60-70% in long-horizon agentic tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03679
- Source paper: https://arxiv.org/abs/2604.03679
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03679v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03679v1.png
- GitHub: https://github.com/zjunlp/LightThinker
- GitHub stars: 137
- Paper ID: 2604.03679
- Canonical ID: 2604.03679v1
- Paper group ID: 019d65f9-5386-7a8f-a166-c33947abd840
- Version ID: 019d65f9-53de-716e-84d9-027f3b4487f0
- Version: v1
- Version order: 1
- Published at: 2026-04-04T10:46:09+00:00
- First published at: 2026-04-04T10:46:09+00:00
- Updated at: 2026-04-07T03:25:31.910000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Yuqi Zhu
- Jintian Zhang
- Zhenjie Wan
- Yujie Luo
- Shuofei Qiao
- Zhengke Gui
- Da Zheng
- Lei Liang
- Huajun Chen
- Ningyu Zhang

## Topics

- agents
- Computer Science
- cs.AI
- cs.CL
- cs.IR
- cs.LG
- cs.MM
- efficient-transformers
- inference-optimization
- model-compression
- optimization-methods
- reasoning
- transformers

## Metrics

- Visits (all): 147
- Visits (last 7 days): 147
- Total votes: 3
- Public total votes: 18
- X likes: 0

## Abstract

Large language models (LLMs) excel at complex reasoning, yet their efficiency is limited by the surging cognitive overhead of long thought traces. In this paper, we propose LightThinker, a method that enables LLMs to dynamically compress intermediate thoughts into compact semantic representations. However, static compression often struggles with complex reasoning where the irreversible loss of intermediate details can lead to logical bottlenecks. To address this, we evolve the framework into LightThinker++, introducing Explicit Adaptive Memory Management. This paradigm shifts to behavioral-level management by incorporating explicit memory primitives, supported by a specialized trajectory synthesis pipeline to train purposeful memory scheduling. Extensive experiments demonstrate the framework's versatility across three dimensions. (1) LightThinker reduces peak token usage by 70% and inference time by 26% with minimal accuracy loss. (2) In standard reasoning, LightThinker++ slashes peak token usage by 69.9% while yielding a +2.42% accuracy gain under the same context budget for maximum performance. (3) Most notably, in long-horizon agentic tasks, it maintains a stable footprint beyond 80 rounds (a 60%-70% reduction), achieving an average performance gain of 14.8% across different complex scenarios. Overall, our work provides a scalable direction for sustaining deep LLM reasoning over extended horizons with minimal overhead.

## Problem

- Large Language Models (LLMs) incur substantial computational and memory overhead in complex reasoning due to generating numerous tokens and the quadratic complexity of attention and linear growth of KV Cache.
- Existing context management techniques, such as prompt engineering or real-time token pruning, often require extensive data construction or introduce significant inference latency.
- Implicit compression methods, while efficient, risk irreversible information loss that can create "logical bottlenecks" in complex reasoning tasks requiring detailed intermediate steps.

## Method

- LightThinker, an initial framework, trains LLMs to implicitly compress lengthy thought steps into compact semantic representations using special "gist tokens" and a segmented attention mask.
- LightThinker++ evolves this by introducing explicit, behavioral-level memory management through primitives like "commit," "expand," and "fold," allowing dynamic archiving of semantic summaries or restoration of raw reasoning details.
- A specialized environment-aware trajectory synthesis pipeline is used to train LLMs in purposeful memory scheduling, generating expert demonstrations that interleave reasoning with explicit memory operations.

## Results

- LightThinker reduced peak token usage by up to 70% and inference time by 26% on Qwen2.5-7B, achieving a 4.5x compression ratio with a minimal 1% accuracy drop compared to vanilla models.
- LightThinker++ reduced average peak tokens and Dependency by 69.9% while maintaining accuracy comparable to baselines, and in a quality-focused setting, yielded a +2.42% average accuracy gain with a 45.0% peak memory reduction.
- For long-horizon agentic tasks, LightThinker++ improved Pass@1 scores by 5.7% (on xbench), maintained a lean and stable active context footprint (60-70% reduction), and demonstrated up to 2.5x action efficiency compared to standard agentic baselines.

## Takeaways

- LLM-generated tokens serve both linguistic fluency and reasoning, indicating that the essential semantic content can be distilled from verbose sequences for efficiency.
- Drawing inspiration from human cognitive economy, LLMs can benefit from retaining key conclusions or summaries in active memory, only revisiting detailed information when necessary.
- Explicit memory management with reversible actions ("expand" and "fold") is crucial for "hard-logic," dense reasoning steps to prevent irreversible information loss, unlike fixed-capacity implicit compression which is better suited for "soft," redundant natural language reasoning.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65f9-5386-7a8f-a166-c33947abd840/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65f9-5386-7a8f-a166-c33947abd840/transcript.json

## AI Detection

- State: done
- Prediction: Mixed
- Headline: Mostly Human, AI Detected
- Fraction AI: 0.14989927
- Fraction AI-assisted: 0
- Fraction human: 0.85010076

## Resources

- GitHub repository: https://github.com/zjunlp/LightThinker

## Similar Papers

- Learning to Think: Information-Theoretic Reinforcement Fine-Tuning for LLMs (2505.10425v3): The Learning to Think (L2T) framework fine-unes large language models to achieve higher reasoning accuracy with significantly fewer tokens. It introduces a universal, information-theoretic dense process reward that guides models to adaptively optimize reasoning depth.
- Chain of Draft: Thinking Faster by Writing Less (2502.18600v2): Researchers at Zoom Communications developed Chain of Draft, a prompting strategy for large language models that significantly reduces token usage and inference latency during multi-step reasoning. The method achieved up to a 92.4% token reduction and substantial latency improvements across various reasoning tasks while largely preserving or enhancing accuracy on models like GPT-4o and Claude 3.5 Sonnet.
- Agentic Memory: Learning Unified Long-Term and Short-Term Memory Management for Large Language Model Agents (2601.01885v1): AgeMem introduces a framework for Large Language Model (LLM) agents that unifies long-term and short-term memory management through a learnable policy, enabling the agent to autonomously control memory operations. This approach improved average task performance across diverse benchmarks by 4.82 to 8.57 percentage points over existing memory-augmented baselines and enhanced memory quality and context efficiency.
- LightMem: Lightweight and Efficient Memory-Augmented Generation (2510.18866v4): LightMem, developed by Zhejiang University, presents a cognition-inspired, multi-stage memory system for large language models to efficiently manage long-term conversational history. It reduces online token consumption by up to 117.1x and API calls by up to 309.9x, while improving task accuracy by up to 29.29% on interactive memory benchmarks.
- Z1: Efficient Test-time Scaling with Code (2504.00810v1): Researchers from Tsinghua and Yale Universities introduce Z1, a test-time scaling framework that reduces token consumption in language model reasoning by 70% while maintaining performance through code-based training and a novel "Shifted Thinking Window" mechanism that adapts reasoning depth based on problem complexity.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
