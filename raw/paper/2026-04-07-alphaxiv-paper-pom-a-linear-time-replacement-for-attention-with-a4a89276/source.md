---
id: 2026-04-07-alphaxiv-paper-pom-a-linear-time-replacement-for-attention-with-a4a89276
kind: paper
title: 'PoM: A Linear-Time Replacement for Attention with the Polynomial Mixer'
source_url: https://www.alphaxiv.org/abs/2604.06129
source_name: alphaXiv Papers
authors:
- David Picard
- Nicolas Dufour
- Lucas Degeorge
- Arijit Ghosh
- Davide Allegro
- Tom Ravaud
- Yohann Perron
- Corentin Sautier
- Zeynep Sonat Baltaci
- Fei Meng
- Syrine Kalleli
- Marta López-Rauhut
- Thibaut Loiseau
- Ségolène Albouy
- Raphael Baena
- Elliot Vincent
- Loic Landrieu
published_at: '2026-04-07T17:40:37Z'
ingested_at: '2026-04-09T09:59:53.391650Z'
content_hash: 3ef0b0f9b326565b11429a7e02254a8b8aa361e64cd820af7478e2b2abc92009
identity_hash: d291fb689cfb3f910367f9fe9efe6013f7726c99b54c41ddb9c7ab641bc24ba6
tags:
- paper
- alphaxiv
- research
- attention-mechanisms
- Computer Science
- cs.AI
- cs.CV
- efficient-transformers
- image-generation
- lightweight-models
- representation-learning
- sequence-modeling
- text-generation
- transformers
- github
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
external_key: https://www.alphaxiv.org/abs/2604.06129
canonical_url: https://www.alphaxiv.org/abs/2604.06129
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:59:53.391655Z'
short_summary: The Polynomial Mixer (PoM) introduces a linear-time token mixing mechanism as a direct replacement for the quadratically scaling Multi-Head Attention in Transformer architectures. PoM-based models achieve comparable or superior performance across five diverse domains, demonstrating up to 2x faster throughput and significant scalability improvements for long sequence lengths.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# PoM: A Linear-Time Replacement for Attention with the Polynomial Mixer

## alphaXiv Summary

The Polynomial Mixer (PoM) introduces a linear-time token mixing mechanism as a direct replacement for the quadratically scaling Multi-Head Attention in Transformer architectures. PoM-based models achieve comparable or superior performance across five diverse domains, demonstrating up to 2x faster throughput and significant scalability improvements for long sequence lengths.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06129
- Source paper: https://arxiv.org/abs/2604.06129
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06129v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06129v1.png
- GitHub: https://github.com/davidpicard/pom
- GitHub stars: 23
- Paper ID: 2604.06129
- Canonical ID: 2604.06129v1
- Paper group ID: 019d6b78-ecf4-74d8-b09a-4c8c6cc8b776
- Version ID: 019d6b78-ed3d-75fe-aebe-e6cf7b629578
- Version: v1
- Version order: 1
- Published at: 2026-04-07T17:40:37+00:00
- First published at: 2026-04-07T17:40:37+00:00
- Updated at: 2026-04-08T05:03:00.340000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- David Picard
- Nicolas Dufour
- Lucas Degeorge
- Arijit Ghosh
- Davide Allegro
- Tom Ravaud
- Yohann Perron
- Corentin Sautier
- Zeynep Sonat Baltaci
- Fei Meng
- Syrine Kalleli
- Marta López-Rauhut
- Thibaut Loiseau
- Ségolène Albouy
- Raphael Baena
- Elliot Vincent
- Loic Landrieu

## Topics

- attention-mechanisms
- Computer Science
- cs.AI
- cs.CV
- efficient-transformers
- image-generation
- lightweight-models
- representation-learning
- sequence-modeling
- text-generation
- transformers

## Metrics

- Visits (all): 31
- Visits (last 7 days): 31
- Total votes: 1
- Public total votes: 4
- X likes: 0

## Abstract

This paper introduces the Polynomial Mixer (PoM), a novel token mixing mechanism with linear complexity that serves as a drop-in replacement for self-attention. PoM aggregates input tokens into a compact representation through a learned polynomial function, from which each token retrieves contextual information. We prove that PoM satisfies the contextual mapping property, ensuring that transformers equipped with PoM remain universal sequence-to-sequence approximators. We replace standard self-attention with PoM across five diverse domains: text generation, handwritten text recognition, image generation, 3D modeling, and Earth observation. PoM matches the performance of attention-based models while drastically reducing computational cost when working with long sequences. The code is available at this https URL.

## Problem

- Multi-Head Attention (MHA) in Transformers incurs quadratic computational and memory complexity with respect to the input sequence length.
- This quadratic scaling limits the application of Transformers to tasks involving very long sequences, such as high-resolution images, videos, or extensive text.
- Existing linear-time alternatives often compromise performance, impose fixed sequence lengths, or are limited by causal ordering, restricting their general applicability.

## Method

- PoM aggregates input tokens into a compact, shared representation using a learned polynomial function, allowing each token to query this context in a linear-time manner.
- The PolyMorpher block integrates PoM as a drop-in replacement for MHA, preserving the Transformer's residual structure, and can be adapted for causal sequences with O(1) autoregressive inference.
- The architecture ensures all internal operations scale linearly with sequence length, addressing the efficiency bottleneck of MHA.

## Results

- PoM-based models achieved performance on par with or slightly better than MHA across diverse tasks including NLP, OCR, Earth observation, 3D point cloud segmentation, and image generation.
- Models incorporating PoM demonstrated significant speedups, such as 2x faster throughput for image generation and over 300% faster inference for Earth observation compared to MHA baselines.
- PoM's linear scaling enabled efficient processing of entire point clouds without chunking and provided substantial throughput advantages over highly optimized attention (e.g., FlashAttention) for long sequence lengths.

## Takeaways

- PoM is theoretically proven to be permutation equivariant and, when combined with positional encoding, forms a universal sequence-to-sequence approximator.
- PoM satisfies the 'contextual mapping property,' allowing each token to derive a unique value from the entire sequence while retaining its identity, crucial for Transformer expressivity.
- The linear computational complexity of PoM ($O(n)$) offers substantial efficiency and scalability advantages over MHA's quadratic complexity ($O(n^2)$) for processing long sequences without sacrificing performance.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b78-ecf4-74d8-b09a-4c8c6cc8b776/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b78-ecf4-74d8-b09a-4c8c6cc8b776/transcript.json

## Resources

- GitHub repository: https://github.com/davidpicard/pom

## Similar Papers

- MoM: Linear Sequence Modeling with Mixture-of-Memories (2502.13685v4): The Mixture-of-Memories (MoM) architecture replaces a single recurrent state with multiple, independent memory states and a routing mechanism, enhancing linear sequence models' ability to retain information over long sequences. This design enables performance on recall-intensive tasks comparable to Transformer models while maintaining linear time complexity during training and constant time inference.
- RWKV-X: A Linear Complexity Hybrid Language Model (2504.21463v2): RWKV-X, a hybrid language model, integrates RWKV-7 with a "Top-k Chunk Sparse Attention" mechanism to process ultra-long contexts efficiently. The model achieves near-perfect accuracy on 64K passkey retrieval, exhibits near-linear prefill latency and constant decoding latency up to 1 million tokens, and maintains competitive performance on short-context tasks.
- MHLA: Restoring Expressivity of Linear Attention via Token-Level Multi-Head (2601.07832v2): MHLA (Multi-Head Linear Attention) from Peking University and NVIDIA addresses the expressivity limitations of linear attention by introducing token-level multi-head mixing. This method restores query-dependent diversity and representational capacity, achieving state-of-the-art performance across image classification, generation, video generation, and NLP tasks, while maintaining linear computational complexity. For instance, MHLA achieves 59.80 FID for DiT-S/2 compared to 68.40 for Self-Attention, and provides a 2.1x inference speedup for video generation.
- Rethinking Attention with Performers (2009.14794v4): Performers introduce a novel Transformer architecture that achieves linear space and time complexity for the self-attention mechanism, accurately estimating the original softmax attention without relying on sparsity or low-rank assumptions. This enables efficient processing of sequences up to 32,768 tokens, opening new applications in areas like bioinformatics.
- Paramixer: Parameterizing Mixing Links in Sparse Factors Works Better  than Dot-Product Self-Attention (2204.10670v1)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
