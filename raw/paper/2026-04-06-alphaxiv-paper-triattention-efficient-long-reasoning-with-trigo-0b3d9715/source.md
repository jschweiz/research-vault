---
id: 2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
kind: paper
title: TriAttention: Efficient Long Reasoning with Trigonometric KV Compression
source_url: https://www.alphaxiv.org/abs/2604.04921
source_name: alphaXiv Papers
authors:
  - Weian Mao
  - Xi Lin
  - Wei Huang
  - Yuxin Xie
  - Tianfu Fu
  - Bohan Zhuang
published_at: 2026-04-06T17:58:42Z
ingested_at: 2026-04-07T21:42:08.648109Z
content_hash: 2b0d3e52d6cc3190796d40bdbdbb8af462357f914a4a90c619c9ecea7303a39f
tags:
  - paper
  - alphaxiv
  - research
  - attention-mechanisms
  - computer science
  - cs.cl
  - cs.cv
  - efficient-transformers
  - hardware-aware-algorithms
  - inference-optimization
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
  - alphaxiv-transcript.json
  - alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04921
canonical_url: https://www.alphaxiv.org/abs/2604.04921
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:26:00.695898Z
short_summary: # TriAttention: Efficient Long Reasoning with Trigonometric KV Compression ## alphaXiv Summary Researchers from MIT, ZJU, and NVIDIA introduced TriAttention, a KV cache compression method leveraging a newly identified property of Q/K vector concentration in the pre-RoPE space. This approach predicts attention patterns via a trigonometric series, achieving up to 6.3x higher throughput and 10.7x KV memory reduction while matching or exceeding full attention accuracy on long reasoning tasks.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-08T10:12:15.050216Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 2b0d3e52d6cc3190796d40bdbdbb8af462357f914a4a90c619c9ecea7303a39f
lightweight_enrichment_error: null
---
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

- Visits (all): 279
- Visits (last 7 days): 279
- Total votes: 4
- Public total votes: 16
- X likes: 0

## Abstract

Extended reasoning in large language models (LLMs) creates severe KV cache memory bottlenecks. Leading KV cache compression methods estimate KV importance using attention scores from recent post-RoPE queries. However, queries rotate with position during RoPE, making representative queries very few, leading to poor top-key selection and unstable reasoning. To avoid this issue, we turn to the pre-RoPE space, where we observe that Q and K vectors are highly concentrated around fixed non-zero centers and remain stable across positions -- Q/K concentration. We show that this concentration causes queries to preferentially attend to keys at specific distances (e.g., nearest keys), with the centers determining which distances are preferred via a trigonometric series. Based on this, we propose TriAttention to estimate key importance by leveraging these centers. Via the trigonometric series, we use the distance preference characterized by these centers to score keys according to their positions, and also leverage Q/K norms as an additional signal for importance estimation. On AIME25 with 32K-token generation, TriAttention matches Full Attention reasoning accuracy while achieving 2.5x higher throughput or 10.7x KV memory reduction, whereas leading baselines achieve only about half the accuracy at the same efficiency. TriAttention enables OpenClaw deployment on a single consumer GPU, where long context would otherwise cause out-of-memory with Full Attention.

## Problem

- Large language models (LLMs) performing long chain-of-thought reasoning face a severe KV cache memory bottleneck, limiting context length and inference speed.
- Existing attention-based KV cache compression methods are unstable; the dynamic rotation of post-RoPE vectors creates a narrow observation window, leading to premature eviction of critical tokens.
- Norm-based compression methods often disregard crucial directional information, which is vital for accurate attention computation.

## Method

- The authors identified that Query (Q) and Key (K) vectors in the *pre-RoPE* space are highly concentrated around fixed, non-zero centers across most attention heads in various LLMs.
- This Q/K concentration allows attention logits to be approximated by a trigonometric series that primarily depends on the Query-Key distance, enabling prediction of long-range attention patterns.
- TriAttention combines a trigonometric series-based score (S_trig_) and an adaptively weighted norm-based score (S_norm_) to robustly estimate key importance for KV cache compression.

## Results

- TriAttention achieved up to 6.3x higher throughput and 10.7x KV memory reduction, consistently matching or slightly exceeding the reasoning accuracy of full attention on benchmarks like AIME and MATH.
- The method demonstrated superior accuracy over leading baselines (e.g., SnapKV, R-KV) across various LLMs (Qwen3-8B, DeepSeek-R1, GPT-OSS-20B) and KV cache budget levels.
- The observed Q/K concentration and attention predictability generalize across diverse LLM architectures (GQA and MLA) and domains, with calibration statistics found to be robust and transferable.

## Takeaways

- Pre-RoPE Q/K vectors exhibit a stable and model-intrinsic concentration around specific centers, consistent across different token positions and input contexts.
- This concentration allows the attention mechanism's distance preference to be accurately predicted by a trigonometric series derived from the Q/K centers.
- Leveraging stable pre-RoPE properties offers a more reliable and accurate foundation for KV cache compression compared to approaches relying on dynamically rotating post-RoPE representations.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d7-4052-705a-a296-f3c8950354a6/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d7-4052-705a-a296-f3c8950354a6/transcript.json
- Transcript lines: 16
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Human
- Headline: Mostly Human Written
- Fraction AI: 0.03147166
- Fraction AI-assisted: 0
- Fraction human: 0.96852833

## Resources

- GitHub repository: https://github.com/WeianMao/triattention

## Similar Papers

- xKV: Cross-Layer SVD for KV-Cache Compression (2503.18893v1): A compression framework enables efficient KV-Cache memory reduction in large language models through cross-layer SVD, achieving up to 6.8x higher compression rates than previous methods while improving accuracy by 2.7% on Llama-3.1-8B and maintaining performance when combined with Multi-Head Latent Attention architectures.
- Tensor Product Attention Is All You Need (2501.06425v7)
- RazorAttention: Efficient KV Cache Compression Through Retrieval Heads (2407.15891v1): RazorAttention introduces a selective compression technique for the Key-Value (KV) cache in Large Language Models by distinguishing between retrieval and non-retrieval attention heads. This approach reduces KV cache memory usage by over 70% with less than 1% performance degradation, making LLM deployment more efficient for long contexts.
- KeyDiff: Key Similarity-Based KV Cache Eviction for Long-Context LLM Inference in Resource-Constrained Environments (2504.15364v4)
- RetroInfer: A Vector-Storage Approach for Scalable Long-Context LLM Inference (2505.02922v2): A new system called RetroInfer from Microsoft Research and collaborating universities re-architects the KV cache for large language models into a vector storage system, enabling scalable and accurate inference over extremely long contexts. It delivers full-attention-level accuracy and up to 10.5x faster throughput compared to sparse attention baselines for contexts up to a million tokens.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
