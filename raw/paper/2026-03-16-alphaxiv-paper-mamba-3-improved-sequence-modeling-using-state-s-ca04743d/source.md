---
id: 2026-03-16-alphaxiv-paper-mamba-3-improved-sequence-modeling-using-state-s-ca04743d
kind: paper
title: 'Mamba-3: Improved Sequence Modeling using State Space Principles'
source_url: https://www.alphaxiv.org/abs/2603.15569
source_name: alphaXiv Papers
authors:
- Aakash Lahoti
- Kevin Y. Li
- Berlin Chen
- Caitlin Wang
- Aviv Bick
- J. Zico Kolter
- Tri Dao
- Albert Gu
published_at: '2026-03-16T17:30:08Z'
ingested_at: '2026-04-09T23:37:21.986909Z'
content_hash: 0b8fb6a10327670066783adc88af638e4e03f5780b5ecd93bd15688223aefe4e
identity_hash: 6d589537882a2cc9f7766374183ed5189a689c146f31b5a1e0137c97edf15606
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.LG
- hardware-aware-algorithms
- inference-optimization
- lightweight-models
- sequence-modeling
- transformers
status: active
asset_paths:
- alphaxiv-citation.bib
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-podcast.mp3
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2603.15569
canonical_url: https://www.alphaxiv.org/abs/2603.15569
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T23:37:21.986915Z'
short_summary: Mamba-3 introduces a State Space Model architecture featuring exponential-trapezoidal discretization, complex-valued states, and a multi-input, multi-output formulation to improve sequence modeling. It demonstrates superior language modeling quality and enhanced inference efficiency compared to prior linear models like Mamba-2 and GDN, achieving a 1.8 percentage point accuracy gain over GDN at the 1.5B scale and lower decode latency.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:42:59.412441Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 61b06231527509631bdaae70639dd5fba1d9de3f0ded57fa9c1e9210634c1f35
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b+alphaxiv-metrics-v1
lightweight_scoring_input_hash: c1100502d131670c00c1471d2e51a1c1663407f5632fd45db9b68f7eb15bf716
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 1.0
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: 'This paper directly addresses core topics like LLM architecture, efficiency, and sequence modeling, making it highly relevant for a frontier LLM researcher. alphaXiv engagement signals: 179 public votes, 60 total votes, 190 visits in the last 7 days.'
  evidence_quotes:
  - Mamba-3 introduces a State Space Model architecture featuring exponential-trapezoidal discretization, complex-valued states, and a multi-input, multi-output for
  - Mamba-3 models consistently surpass Mamba-2 and GDN in language modeling quality, with the MIMO variant (R=4) achieving a 1.8 percentage point accuracy gain ove
  - The model demonstrated robust performance on synthetic state-tracking tasks, achieving 100% accuracy on Parity and 98.51% on Modular Arithmetic, a capability en
---
# Mamba-3: Improved Sequence Modeling using State Space Principles

## alphaXiv Summary

Mamba-3 introduces a State Space Model architecture featuring exponential-trapezoidal discretization, complex-valued states, and a multi-input, multi-output formulation to improve sequence modeling. It demonstrates superior language modeling quality and enhanced inference efficiency compared to prior linear models like Mamba-2 and GDN, achieving a 1.8 percentage point accuracy gain over GDN at the 1.5B scale and lower decode latency.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.15569
- Source paper: https://arxiv.org/abs/2603.15569
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.15569v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.15569v1.png
- Paper ID: 2603.15569
- Canonical ID: 2603.15569v1
- Paper group ID: 019cf9f2-aa5c-71ce-994a-d0e61e0e6ced
- Version ID: 019cf9f2-aa94-7f1d-b3ad-5cc013b83abf
- Version: v1
- Version order: 1
- Published at: 2026-03-16T17:30:08+00:00
- First published at: 2026-03-16T17:30:08+00:00
- Updated at: 2026-03-17T03:59:16.060000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0
- BibTeX saved in `alphaxiv-citation.bib`

## Authors

- Aakash Lahoti
- Kevin Y. Li
- Berlin Chen
- Caitlin Wang
- Aviv Bick
- J. Zico Kolter
- Tri Dao
- Albert Gu

## Topics

- Computer Science
- cs.LG
- hardware-aware-algorithms
- inference-optimization
- lightweight-models
- sequence-modeling
- transformers

## Metrics

- Visits (all): 2323
- Visits (last 7 days): 190
- Total votes: 60
- Public total votes: 179
- X likes: 0

## Abstract

Scaling inference-time compute has emerged as an important driver of LLM performance, making inference efficiency a central focus of model design alongside model quality. While the current Transformer-based models deliver strong model quality, their quadratic compute and linear memory make inference expensive. This has spurred the development of sub-quadratic models with reduced linear compute and constant memory requirements. However, many recent linear models trade off model quality and capability for algorithmic efficiency, failing on tasks such as state tracking. Moreover, their theoretically linear inference remains hardware-inefficient in practice. Guided by an inference-first perspective, we introduce three core methodological improvements inspired by the state space model (SSM) viewpoint of linear models. We combine: (1) a more expressive recurrence derived from SSM discretization, (2) a complex-valued state update rule that enables richer state tracking, and (3) a multi-input, multi-output (MIMO) formulation for better model performance without increasing decode latency. Together with architectural refinements, our Mamba-3 model achieves significant gains across retrieval, state-tracking, and downstream language modeling tasks. At the 1.5B scale, Mamba-3 improves average downstream accuracy by 0.6 percentage points compared to the next best model (Gated DeltaNet), with Mamba-3's MIMO variant further improving accuracy by another 1.2 points for a total 1.8 point gain. Across state-size experiments, Mamba-3 achieves comparable perplexity to Mamba-2 despite using half of its predecessor's state size. Our evaluations demonstrate Mamba-3's ability to advance the performance-efficiency Pareto frontier.

## Problem

- Transformer-based LLMs incur quadratic computational complexity and linear memory usage during inference, leading to high costs and slow response times at scale and long context lengths.
- Prior sub-quadratic models often compromise model quality or specific capabilities like robust state tracking for algorithmic efficiency.
- Existing linear model inference algorithms frequently exhibit low hardware efficiency due to memory-bound decoding phases and low arithmetic intensity.

## Method

- Introduces an "exponential-trapezoidal" discretization method for LTV SSMs, providing a more expressive three-term recurrence with O(Δ³) truncation error.
- Reintegrates complex-valued states via data-dependent Rotary Position Embeddings (RoPE) to enhance the model's capacity for complex state-tracking tasks.
- Develops a Multi-Input, Multi-Output (MIMO) SSM formulation to improve hardware utilization and arithmetic intensity during decoding, moving from memory-bound to compute-bound operations.

## Results

- Mamba-3 models consistently surpass Mamba-2 and GDN in language modeling quality, with the MIMO variant (R=4) achieving a 1.8 percentage point accuracy gain over GDN at the 1.5B scale.
- The model demonstrated robust performance on synthetic state-tracking tasks, achieving 100% accuracy on Parity and 98.51% on Modular Arithmetic, a capability enabled by its complex-valued state mechanism.
- Optimized Mamba-3 kernels recorded the lowest per-token decode latency among recurrent models (0.156 ms for SISO at 128 state size) and exhibited superior scaling with context length compared to Transformer baselines.

## Takeaways

- Rigorous discretization of LTV SSMs, specifically the exponential-trapezoidal method, yields more expressive recurrences that can implicitly handle convolutional aspects, potentially removing the need for explicit short causal convolutions.
- Reintroducing complex-valued states, realized through data-dependent Rotary Position Embeddings (RoPE), is key for linear models to robustly solve state-tracking tasks that require rotational hidden state dynamics.
- Adopting a Multi-Input, Multi-Output (MIMO) formulation in SSMs effectively increases arithmetic intensity during inference, leading to higher hardware utilization and improved practical efficiency without significant latency overhead.

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

- MP3: https://paper-podcasts.alphaxiv.org/019cf9f2-aa5c-71ce-994a-d0e61e0e6ced/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019cf9f2-aa5c-71ce-994a-d0e61e0e6ced/transcript.json
- Transcript lines: 25
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- Mamba: Linear-Time Sequence Modeling with Selective State Spaces (2312.00752v2): Mamba introduces Selective State Space Models (SSMs) to create a linear-time sequence model that matches Transformer performance while scaling linearly with sequence length. It demonstrates competitive quality on language, genomics, and audio tasks, achieving up to 5x higher inference throughput and significantly better long-context generalization than prior models.
- Nemotron-H: A Family of Accurate and Efficient Hybrid Mamba-Transformer Models (2504.03624v4)
- Log-Linear Attention (2506.04761v3): Log-linear attention is presented as a novel mechanism combining O(T log T) computational complexity and O(log T) memory through a logarithmically growing set of hidden states. It improved performance on long-context tasks like Multi-Query Associative Recall and Needle-In-A-Haystack, and showed competitive or better throughput than FlashAttention-2 for sequences over 8K.
- M1: Towards Scalable Test-Time Compute with Mamba Reasoning Models (2504.10449v3): M1 introduces a hybrid linear RNN reasoning model based on the Mamba architecture, addressing the scalability limitations of Transformers for complex reasoning tasks. It achieves competitive reasoning performance, demonstrates over 3x faster inference throughput than similarly sized Transformers, and effectively translates this speed into higher accuracy on mathematical benchmarks when leveraging test-time compute strategies like self-consistency.
- TransMamba: A Sequence-Level Hybrid Transformer-Mamba Language Model (2503.24067v2): A sequence-level hybrid Transformer-Mamba language model, TransMamba, unifies these architectures through shared parameters and dynamic switching, achieving improved performance on various NLP and long-text tasks while reducing training time by up to 25%.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
