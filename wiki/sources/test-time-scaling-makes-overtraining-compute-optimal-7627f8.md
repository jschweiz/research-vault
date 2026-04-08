---
id: page:2026-04-01-alphaxiv-paper-test-time-scaling-makes-overtraining-compute-opt-3a3760da
page_type: source-note
title: Test-Time Scaling Makes Overtraining Compute-Optimal
aliases:
  - Test-Time Scaling Makes Overtraining Compute-Optimal
source_refs:
  - 2026-04-01-alphaxiv-paper-test-time-scaling-makes-overtraining-compute-opt-3a3760da
backlinks:
  - page:2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
  - page:2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
  - topic:efficient-transformers
  - topic:inference-optimization
  - topic:language-modeling
  - topic:machine-learning
  - topic:ml-systems
updated_at: 2026-04-08T07:14:52.277680Z
managed: true
---
# Test-Time Scaling Makes Overtraining Compute-Optimal

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.01411
- Document kind: paper
- Published at: 2026-04-01T21:17:32+00:00
- Authors: Nicholas Roberts, Sungjun Cho, Zhiqi Gao, Tzu-Heng Huang, Albert Wu, Gabriel Orlanski
- Tags: paper, alphaxiv, research, computer science, cs.cl, cs.lg, efficient-transformers, inference-optimization, ml-systems, model-deployment-systems
- Topics: [Computer Science](../topics/computer-science.md), [Efficient Transformers](../topics/efficient-transformers.md), [Inference Optimization](../topics/inference-optimization.md), [Language Modeling](../topics/language-modeling.md), [Machine Learning](../topics/machine-learning.md), [Ml Systems](../topics/ml-systems.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# Test-Time Scaling Makes Overtraining Compute-Optimal ## alphaXiv Summary Researchers at the University of Wisconsin-Madison and Stanford University introduced Train-to-Test (T2) scaling laws, a framework that jointly optimizes language model size, training tokens, and inference samples under a unified compute budget. Their findings indicate that accounting for test-time scaling through repeated sampling makes training smaller models for longer periods (overtraining) compute-optimal, leading to

## Topic Map

- [Computer Science](../topics/computer-science.md)
- [Efficient Transformers](../topics/efficient-transformers.md)
- [Inference Optimization](../topics/inference-optimization.md)
- [Language Modeling](../topics/language-modeling.md)
- [Machine Learning](../topics/machine-learning.md)
- [Ml Systems](../topics/ml-systems.md)

## Related Research

- [Meta-Harness: End-to-End Optimization of Model Harnesses](meta-harness-end-to-end-optimization-of-model-harnesses-1e9809.md) (shared topics: Computer Science, Efficient Transformers, Ml Systems)
- [Meta-Harness: End-to-End Optimization of Model Harnesses](meta-harness-end-to-end-optimization-of-model-harnesses-ebb80b.md) (shared topics: Computer Science, Efficient Transformers, Ml Systems)
- [A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens](a-frame-is-worth-one-token-efficient-generative-world-modeling-w-98472f.md) (shared topics: Computer Science, Inference Optimization)
- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Computer Science, Language Modeling)
- [MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale](mineru2-5-pro-pushing-the-limits-of-data-centric-document-parsin-394662.md) (shared topics: Computer Science, Language Modeling)
- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Computer Science, Language Modeling)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
- Developed two complementary T2 modeling approaches: one as a parametric model of task loss (
