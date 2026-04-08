---
id: 2026-04-07-alphaxiv-paper-in-place-test-time-training-0a14ccc3
kind: paper
title: In-Place Test-Time Training
source_url: https://www.alphaxiv.org/abs/2604.06169
source_name: alphaXiv Papers
authors:
  - Guhao Feng
  - Shengjie Luo
  - Kai Hua
  - Ge Zhang
  - Di He
  - Wenhao Huang
published_at: 2026-04-07T17:59:44Z
ingested_at: 2026-04-08T09:26:55.783108Z
content_hash: a1914694e73f7fcb0f8d52d465677a642b1b3b9aba9c00cf137395e7c5aed83c
tags:
  - paper
  - alphaxiv
  - research
  - computer science
  - continual-learning
  - cs.ai
  - cs.cl
  - cs.lg
  - efficient-transformers
  - fine-tuning
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
external_key: https://www.alphaxiv.org/abs/2604.06169
canonical_url: https://www.alphaxiv.org/abs/2604.06169
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:26:55.783115Z
short_summary: # In-Place Test-Time Training ## alphaXiv Summary In-Place Test-Time Training (In-Place TTT) enables dynamic adaptation in large language models by repurposing existing MLP blocks for efficient, chunk-wise updates with a next-token prediction aligned objective. This framework demonstrates consistent performance improvements on long-context benchmarks, such as RULER, and achieves lower perplexity compared to baselines, while introducing negligible computational overhead.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-08T10:12:40.866188Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: a1914694e73f7fcb0f8d52d465677a642b1b3b9aba9c00cf137395e7c5aed83c
lightweight_enrichment_error: null
---
# In-Place Test-Time Training

## alphaXiv Summary

In-Place Test-Time Training (In-Place TTT) enables dynamic adaptation in large language models by repurposing existing MLP blocks for efficient, chunk-wise updates with a next-token prediction aligned objective. This framework demonstrates consistent performance improvements on long-context benchmarks, such as RULER, and achieves lower perplexity compared to baselines, while introducing negligible computational overhead.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06169
- Source paper: https://arxiv.org/abs/2604.06169
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06169v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06169v1.png
- GitHub: https://github.com/ByteDance-Seed/In-Place-TTT
- GitHub stars: 7
- Paper ID: 2604.06169
- Canonical ID: 2604.06169v1
- Paper group ID: 019d6b04-0a6f-7458-8574-e0d84a7b168e
- Version ID: 019d6b04-0aaf-770a-b058-6e9744eb97ca
- Version: v1
- Version order: 1
- Published at: 2026-04-07T17:59:44+00:00
- First published at: 2026-04-07T17:59:44+00:00
- Updated at: 2026-04-08T02:55:20.175000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Guhao Feng
- Shengjie Luo
- Kai Hua
- Ge Zhang
- Di He
- Wenhao Huang
- Tianle Cai

## Topics

- Computer Science
- continual-learning
- cs.AI
- cs.CL
- cs.LG
- efficient-transformers
- fine-tuning
- inference-optimization
- online-learning
- parameter-efficient-training
- Statistics
- stat.ML
- test-time-inference
- transformers

## Metrics

- Visits (all): 111
- Visits (last 7 days): 111
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

The static ``train then deploy" paradigm fundamentally limits Large Language Models (LLMs) from dynamically adapting their weights in response to continuous streams of new information inherent in real-world tasks. Test-Time Training (TTT) offers a compelling alternative by updating a subset of model parameters (fast weights) at inference time, yet its potential in the current LLM ecosystem is hindered by critical barriers including architectural incompatibility, computational inefficiency and misaligned fast weight objectives for language modeling. In this work, we introduce In-Place Test-Time Training (In-Place TTT), a framework that seamlessly endows LLMs with Test-Time Training ability. In-Place TTT treats the final projection matrix of the ubiquitous MLP blocks as its adaptable fast weights, enabling a ``drop-in" enhancement for LLMs without costly retraining from scratch. Furthermore, we replace TTT's generic reconstruction objective with a tailored, theoretically-grounded objective explicitly aligned with the Next-Token-Prediction task governing autoregressive language modeling. This principled objective, combined with an efficient chunk-wise update mechanism, results in a highly scalable algorithm compatible with context parallelism. Extensive experiments validate our framework's effectiveness: as an in-place enhancement, it enables a 4B-parameter model to achieve superior performance on tasks with contexts up to 128k, and when pretrained from scratch, it consistently outperforms competitive TTT-related approaches. Ablation study results further provide deeper insights on our design choices. Collectively, our results establish In-Place TTT as a promising step towards a paradigm of continual learning in LLMs.

## Problem

- Large Language Models operate under a static 'train then deploy' paradigm, preventing dynamic adaptation to new information or evolving contexts during inference.
- Existing Test-Time Training (TTT) methods for dynamic adaptation often introduce specialized layers incompatible with standard LLM architectures, requiring prohibitive pretraining.
- Canonical TTT update rules are computationally inefficient due to sequential per-token updates and misaligned generic self-supervised objectives for autoregressive language modeling.

## Method

- In-Place TTT repurposes existing Multi-Layer Perceptron (MLP) blocks within Transformer architectures, specifically designating the final projection matrix (W_down) as adaptable 'fast weights' for in-place updates, enabling a 'drop-in' enhancement.
- An efficient chunk-wise update strategy is implemented, decoupling TTT from attention to allow for larger chunk sizes and leverage modern parallel hardware without compromising performance.
- A novel, theoretically-grounded learning objective is introduced, explicitly tailored for the Next-Token Prediction (NTP) task of language modeling, encouraging fast weights to store predictively useful information.

## Results

- In-Place TTT consistently improved RULER benchmark scores for pre-trained LLMs (Qwen3-4B/14B, LLaMA-3.1-8B), showing up to +2.7% gain at 64k context lengths and maintaining advantage during extrapolation to 256k context.
- Models pre-trained from scratch with In-Place TTT achieved lower validation perplexity than all competitive baselines across varying context lengths (2k to 32k) on Pile and Proof-Pile-2 datasets.
- The framework introduced negligible overhead in prefill throughput and peak memory consumption, demonstrating its practicality and scalability for integration into LLMs.

## Takeaways

- Existing MLP blocks in Transformer architectures can be effectively repurposed as 'fast weights' for dynamic adaptation, avoiding architectural modifications and costly pretraining from scratch.
- Decoupling Test-Time Training updates from the attention mechanism allows for significantly more efficient chunk-wise processing, leveraging hardware parallelism while maintaining performance.
- An objective specifically aligned with Next-Token Prediction significantly enhances the effectiveness of fast weights for autoregressive language models, as theoretically shown to increase logits for correct future tokens.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b04-0a6f-7458-8574-e0d84a7b168e/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b04-0a6f-7458-8574-e0d84a7b168e/transcript.json

## Resources

- GitHub repository: https://github.com/ByteDance-Seed/In-Place-TTT

## Similar Papers

- End-to-End Test-Time Training for Long Context (2512.23675v2): End-to-End Test-Time Training (TTT-E2E) enables language models to process extremely long contexts with performance comparable to full attention Transformers, while maintaining the constant inference latency of recurrent models. This approach achieves a 2.7x speedup over full attention at 128K context on H100 GPUs, effectively transforming the efficient but limited Sliding-Window Attention baseline into the best-performing method for extended sequences.
- Test-Time Training with KV Binding Is Secretly Linear Attention (2602.21204v2): The paper re-interprets Test-Time Training with Key-Value binding (TTT-KVB), showing it is mathematically equivalent to a learned linear attention mechanism, which allows for substantial efficiency improvements and simplified model architectures. Researchers provided analytical proofs demonstrating this equivalence, even for complex TTT variants, resolving empirical paradoxes.
- End-to-End Test-Time Training for Long Context (2512.23675/sso-callbackv1): Researchers from Astera Institute, NVIDIA, Stanford, UC Berkeley, and UC San Diego developed TTT-E2E, a method that combines a standard Transformer with sliding-window attention and test-time learning to achieve constant inference cost while scaling performance (perplexity) with context length similarly to full attention.
- Test-Time Training with KV Binding Is Secretly Linear Attention (2602.21204/cpu-crshpwul.jsv1)
- Test-Time Training with KV Binding Is Secretly Linear Attention (2602.21204/route-bz8jjb93.jsv1)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
