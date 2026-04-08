---
id: 2026-04-01-alphaxiv-paper-test-time-scaling-makes-overtraining-compute-opt-3a3760da
kind: paper
title: Test-Time Scaling Makes Overtraining Compute-Optimal
source_url: https://www.alphaxiv.org/abs/2604.01411
source_name: alphaXiv Papers
authors:
- Nicholas Roberts
- Sungjun Cho
- Zhiqi Gao
- Tzu-Heng Huang
- Albert Wu
- Gabriel Orlanski
published_at: '2026-04-01T21:17:32Z'
ingested_at: '2026-04-07T21:43:28.200365Z'
content_hash: e8e9ce9f8e3f79076dd8e0ebf3a51726f53f36e0a85fa4510010004172bf8d26
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cl
- cs.lg
- efficient-transformers
- inference-optimization
- ml-systems
- model-deployment-systems
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
external_key: https://www.alphaxiv.org/abs/2604.01411
canonical_url: https://www.alphaxiv.org/abs/2604.01411
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-07T21:43:28.200372Z'
short_summary: null
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-08T14:16:00.474440Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: bf7289154d5ef60efddbfbf4f34186187e1a7e253e8a3279e41a2e601eec9662
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: f8c433e2098704b0548bc5675eb529c3d0558d9fea80e21f0876355f39275fd1
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 1.0
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses favorite topics like language models, evaluation, and optimization through the lens of scaling laws and inference optimization.
  evidence_quotes:
  - We present Train-to-Test ($T^2$) scaling laws that jointly optimize model size, training tokens, and number of inference samples under fixed end-to-end budgets.
  - Optimal pretraining strategies fundamentally shift towards smaller, "overtrained" models when the total compute budget includes test-time scaling via repeated s
  - 'A unified framework for optimizing both training and inference compute is essential for efficient LLM development, as these phases are interdependent in modern '
---
# Test-Time Scaling Makes Overtraining Compute-Optimal

## alphaXiv Summary

Researchers at the University of Wisconsin-Madison and Stanford University introduced Train-to-Test (T2) scaling laws, a framework that jointly optimizes language model size, training tokens, and inference samples under a unified compute budget. Their findings indicate that accounting for test-time scaling through repeated sampling makes training smaller models for longer periods (overtraining) compute-optimal, leading to superior performance compared to traditional scaling recommendations.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.01411
- Source paper: https://arxiv.org/abs/2604.01411
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.01411v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.01411v1.png
- Paper ID: 2604.01411
- Canonical ID: 2604.01411v1
- Paper group ID: 019d51de-624f-7bf5-aab4-25e1967e0ca4
- Version ID: 019d51de-62ae-71c0-a1b7-2e58006147af
- Version: v1
- Version order: 1
- Published at: 2026-04-01T21:17:32+00:00
- First published at: 2026-04-01T21:17:32+00:00
- Updated at: 2026-04-03T05:43:41.903000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Nicholas Roberts
- Sungjun Cho
- Zhiqi Gao
- Tzu-Heng Huang
- Albert Wu
- Gabriel Orlanski
- Avi Trost
- Kelly Buchanan
- Aws Albarghouthi
- Frederic Sala

## Topics

- Computer Science
- cs.CL
- cs.LG
- efficient-transformers
- inference-optimization
- ml-systems
- model-deployment-systems
- optimization-methods
- parameter-efficient-training
- Statistics
- stat.ML
- training-orchestration
- transformers

## Metrics

- Visits (all): 336
- Visits (last 7 days): 336
- Total votes: 5
- Public total votes: 33
- X likes: 0

## Abstract

Modern LLMs scale at test-time, e.g. via repeated sampling, where inference cost grows with model size and the number of samples. This creates a trade-off that pretraining scaling laws, such as Chinchilla, do not address. We present Train-to-Test ($T^2$) scaling laws that jointly optimize model size, training tokens, and number of inference samples under fixed end-to-end budgets. $T^2$ modernizes pretraining scaling laws with pass@$k$ modeling used for test-time scaling, then jointly optimizes pretraining and test-time decisions. Forecasts from $T^2$ are robust over distinct modeling approaches: measuring joint scaling effect on the task loss and modeling impact on task accuracy. Across eight downstream tasks, we find that when accounting for inference cost, optimal pretraining decisions shift radically into the overtraining regime, well-outside of the range of standard pretraining scaling suites. We validate our results by pretraining heavily overtrained models in the optimal region that $T^2$ scaling forecasts, confirming their substantially stronger performance compared to pretraining scaling alone. Finally, as frontier LLMs are post-trained, we show that our findings survive the post-training stage, making $T^2$ scaling meaningful in modern deployments.

## Problem

- Traditional pretraining scaling laws (e.g., Chinchilla) optimize pretraining loss but do not account for modern test-time scaling strategies like repeated sampling, leading to suboptimal overall resource allocation.
- Test-time scaling laws focus on optimizing inference compute but treat pretrained models as fixed, failing to connect pretraining choices to inference costs and performance gains from repeated sampling.
- There is no formal framework to guide the industry practice of "overtraining" smaller models (training on significantly more tokens than Chinchilla-optimal) to reduce per-query inference costs when repeated sampling is used.

## Method

- Introduced "Train-to-Test (T2) scaling laws" to jointly optimize model size (N), training tokens (D), and inference samples (k) under a combined training and inference compute budget.
- Developed two complementary T2 modeling approaches: one as a parametric model of task loss (extending Chinchilla loss with a k-term) and another as a parametric model of task accuracy (using a Beta distribution for pass@k).
- Incorporated an inference cost correction where the number of samples k is made dependent on model size N (k = C_inf / (2N)), allowing for joint optimization of N and D under combined compute constraints.

## Results

- T2 scaling forecasts that optimal models at high compute scales are substantially smaller and more overtrained than Chinchilla-optimal models, with significantly higher tokens per parameter ratios, confirming pretraining should change.
- Both T2 modeling approaches successfully extrapolate to the overtrained regime (with 2.8% and 8.4% relative absolute errors), and empirically, T2-predicted overtrained models consistently outperformed Chinchilla-optimal models on 8 downstream tasks.
- The benefits of T2-guided overtraining persist after post-training (fine-tuning and SFT), with overtrained models continuing to outperform Chinchilla-optimized counterparts across tasks, despite a slightly "subdued" effect.

## Takeaways

- Optimal pretraining strategies fundamentally shift towards smaller, "overtrained" models when the total compute budget includes test-time scaling via repeated sampling.
- The benefits of overtraining (relative to Chinchilla recommendations) are robust, translating to improved empirical performance in actual checkpoints and persisting even after post-training procedures like fine-tuning.
- A unified framework for optimizing both training and inference compute is essential for efficient LLM development, as these phases are interdependent in modern deployment scenarios.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d51de-624f-7bf5-aab4-25e1967e0ca4/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d51de-624f-7bf5-aab4-25e1967e0ca4/transcript.json
- Transcript lines: 17
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- Training Compute-Optimal Large Language Models (2203.15556v1): Google DeepMind research establishes new compute-optimal scaling laws for large language models, demonstrating that model size and training data should scale equally for efficient training. The resulting 70B parameter Chinchilla model, trained on 1.4 trillion tokens, achieved lower perplexity and outperformed larger models like Gopher and GPT-3 on various benchmarks, validating the new scaling approach.
- Compute Optimal Scaling of Skills: Knowledge vs Reasoning (2503.10061v3): Researchers from Meta and the University of Wisconsin investigated compute-optimal scaling for large language models, finding that the optimal trade-off between model parameters and training data tokens is skill-dependent. They demonstrated that knowledge-based tasks are "capacity-hungry" while code generation is "data-hungry," providing empirical strategies for aligning these optima through data mixture adjustments and highlighting the critical role of validation set composition.
- Kinetics: Rethinking Test-Time Scaling Laws (2506.05333v3): This work introduces the "Kinetics Scaling Law," a new cost model for Large Language Model inference that integrates both computation and memory access costs, especially Key-Value cache access. The paper demonstrates that previous FLOPs-centric scaling laws significantly overestimate the efficiency of smaller models in test-time scenarios and proposes sparse attention as an architectural solution to achieve substantial gains in problem-solving accuracy and throughput.
- Inference Scaling Laws: An Empirical Analysis of Compute-Optimal  Inference for Problem-Solving with Language Models (2408.00724v3): Researchers from Tsinghua University and Carnegie Mellon University empirically analyzed inference scaling laws for large language models (LLMs) and introduced REBASE, a novel tree search algorithm. Their work demonstrates that smaller LLMs, when combined with compute-optimal inference strategies like REBASE, can achieve problem-solving performance comparable to or better than much larger models, with significantly reduced computational overhead during deployment.
- Rethinking Fine-Tuning when Scaling Test-Time Compute: Limiting Confidence Improves Mathematical Reasoning (2502.07154v4): Researchers from Stanford University identify that standard fine-tuning with cross-entropy loss induces model overconfidence, which paradoxically degrades Large Language Model (LLM) performance when scaling test-time compute for mathematical reasoning. They propose Direct Coverage Optimization (DCO) loss, a novel training objective that limits overconfidence and significantly improves `pass@N` accuracy across various complex reasoning benchmarks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
