---
id: page:2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
page_type: source-note
title: TriAttention: Efficient Long Reasoning with Trigonometric KV Compression
aliases:
  - TriAttention: Efficient Long Reasoning with Trigonometric KV Compression
source_refs:
  - 2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
backlinks:
  - page:2026-04-02-alphaxiv-paper-the-latent-space-foundation-evolution-mechanism--4559cf35
  - page:2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
  - page:2026-04-03-alphaxiv-paper-joyai-llm-flash-advancing-mid-scale-llms-with-to-7299ba1c
  - page:2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
  - page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
  - page:2026-04-06-alphaxiv-paper-openworldlib-a-unified-codebase-and-definition-o-349dac12
  - page:2026-04-06-alphaxiv-paper-vero-an-open-rl-recipe-for-general-visual-reason-80650390
  - topic:attention-mechanisms
  - topic:computer-science
  - topic:computer-vision
  - topic:efficiency
  - topic:inference
  - topic:reasoning
updated_at: 2026-04-08T07:14:52.254571Z
managed: true
---
# TriAttention: Efficient Long Reasoning with Trigonometric KV Compression

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04921
- Document kind: paper
- Published at: 2026-04-06T17:58:42+00:00
- Authors: Weian Mao, Xi Lin, Wei Huang, Yuxin Xie, Tianfu Fu, Bohan Zhuang
- Tags: paper, alphaxiv, research, attention-mechanisms, computer science, cs.cl, cs.cv, efficient-transformers, hardware-aware-algorithms, inference-optimization
- Topics: [Efficiency](../topics/efficiency.md), [Reasoning](../topics/reasoning.md), [Inference](../topics/inference.md), [Attention Mechanisms](../topics/attention-mechanisms.md), [Computer Science](../topics/computer-science.md), [Computer Vision](../topics/computer-vision.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# TriAttention: Efficient Long Reasoning with Trigonometric KV Compression ## alphaXiv Summary Researchers from MIT, ZJU, and NVIDIA introduced TriAttention, a KV cache compression method leveraging a newly identified property of Q/K vector concentration in the pre-RoPE space. This approach predicts attention patterns via a trigonometric series, achieving up to 6.3x higher throughput and 10.7x KV memory reduction while matching or exceeding full attention accuracy on long reasoning tasks.

## Topic Map

- [Efficiency](../topics/efficiency.md)
- [Reasoning](../topics/reasoning.md)
- [Inference](../topics/inference.md)
- [Attention Mechanisms](../topics/attention-mechanisms.md)
- [Computer Science](../topics/computer-science.md)
- [Computer Vision](../topics/computer-vision.md)

## Related Research

- [Vero: An Open RL Recipe for General Visual Reasoning](vero-an-open-rl-recipe-for-general-visual-reasoning-a332b2.md) (shared topics: Computer Vision, Reasoning)
- [A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens](a-frame-is-worth-one-token-efficient-generative-world-modeling-w-98472f.md) (shared topics: Computer Science, Computer Vision)
- [MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale](mineru2-5-pro-pushing-the-limits-of-data-centric-document-parsin-394662.md) (shared topics: Computer Science, Computer Vision)
- [OpenWorldLib: A Unified Codebase and Definition of Advanced World Models](openworldlib-a-unified-codebase-and-definition-of-advanced-world-187d2a.md) (shared topics: Computer Science, Computer Vision)
- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Computer Science, Efficiency)
- [JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency](joyai-llm-flash-advancing-mid-scale-llms-with-token-efficiency-ea0c5b.md) (shared topics: Computer Science, Efficiency)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# TriAttention: Efficient Long Reasoning with Trigonometric KV Compression

## alphaXiv Summary

Researchers from MIT, ZJU, and NVIDIA introduced TriAttention, a KV cache compression method leveraging a newly identified property of Q/K vector concentration in the pre-RoPE space. This approach predicts attention patterns via a trigonometric series, achieving up to 6.3x higher throughput and 10.7x KV memory reduction while matching or exceeding full attention accuracy on long reasoning tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04921
- Source paper: https://arxiv.org/abs/2604.04921
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04921v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04921v1.png
- GitHub: https://github.com/WeianMao/triattention
- GitHub stars: 2
- Paper ID: 2604.04921
- Canonical ID: 2604.04921v1
- Paper group ID: 019d65d7-4052-705a-a296-f3c8950354a6
- Version ID: 019d65d7-4083-75ac-aced-3f0d57e425d5
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:58:42+00:00
- First published at: 2026-04-06T17:58:42+00:00
- Updated at: 2026-04-07T02:48:18.770000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Weian Mao
- Xi Lin
- Wei Huang
- Yuxin Xie
- Tianfu Fu
- Bohan Zhuang
- Song Han
- Yukang Chen

## Topics

- attention-mechanisms
- Computer Science
- cs.CL
- cs.CV
- efficient-transformers
- hardware-aware-algorithms
- inference-optimization
- lightweight-models
- model-compression
- reasoning
- transformers

## Metrics

- Visits (all): 164
- Visits (last 7 days): 164
- Total votes: 1
- Public total votes: 13
- X likes: 0

## Abstract

Extended reasoning in large language models (LLMs) creates severe KV cache memory bottlenecks. Leading KV cache compression methods estimate KV importance using attention scores from recent post-RoPE queries. However, queries rotate with position during RoPE, making representative queries very few, leading to poor top-key selection and unstable reasoning. To avoid this issue, we turn to the pre-RoPE space, where we observe that Q and K vectors are highly concentrated around fixed non-zero centers and remain stable across positions -- Q/K concentration. We show that this concentration causes queries to preferentially attend to keys at specific distances (e.g., nearest keys), with the centers determining which distances are preferred via a trigonometric series. Based on this, we propose TriAttention to estimate key importance by leveraging these centers. Via the trigonometric series, we use the distance preference characterized by these centers to score keys according to their positions, and also leverage Q/K norms as an additional signal for importance estimation. On AIME25 with 32K-token generation, TriAttention matches Full Attention reasoning accuracy while achieving 2.5x higher throughput or 10.7x KV memory reduction, whereas leading baselines achieve only about half the accuracy at the same efficiency. TriAttention enables OpenClaw deployment on a single consumer GPU, where long context would otherwise cause out-of-memory with Full Attention.

## Problem

- Large language models (LLMs) performing long chain-of-thought reasoning face a severe KV cache memory bottleneck, limiting context length and inference speed.
- Existing attention-based KV cache compression methods are unstable; the dynamic rotation of post-RoPE vectors creates a narrow observation window, leading to premature eviction of critical tokens.
- Norm-based compression methods often disregard crucial directional information, which is vital for accurate attention computation.

## Method

- The authors identified that Query (Q) and Key (K) vectors in the *pre-RoPE* space are highly concentrated around fixed, non-zero centers across most attention heads in various LLMs.
- This Q/K concentration allows attention logits to be approximated by a trigonometric series that primarily depends on the Query-Key distance, enabling predi
