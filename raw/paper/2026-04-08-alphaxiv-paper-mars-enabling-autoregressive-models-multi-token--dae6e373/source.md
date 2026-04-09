---
id: 2026-04-08-alphaxiv-paper-mars-enabling-autoregressive-models-multi-token--dae6e373
kind: paper
title: 'MARS: Enabling Autoregressive Models Multi-Token Generation'
source_url: https://www.alphaxiv.org/abs/2604.07023
source_name: alphaXiv Papers
authors:
- Ziqi Jin
- Lei Wang
- Ziwei Luo
- Aixin Sun
published_at: '2026-04-08T12:41:37Z'
ingested_at: '2026-04-09T09:57:58.661400Z'
content_hash: 392afb8e6bfa3d1437bfabe7ed158102147f19a6f5b855af1d86ab2f6cb26b08
identity_hash: e5bd0d6d9b7ec884759ee4da4a4e31e038993966527284a8cd1e45598d45d734
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CL
- efficient-transformers
- fine-tuning
- inference-optimization
- model-serving-infrastructure
- text-generation
- transformers
- github
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
external_key: https://www.alphaxiv.org/abs/2604.07023
canonical_url: https://www.alphaxiv.org/abs/2604.07023
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:57:58.661435Z'
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
# MARS: Enabling Autoregressive Models Multi-Token Generation

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.07023
- Source paper: https://arxiv.org/abs/2604.07023
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.07023v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.07023v1.png
- GitHub: https://github.com/Xalp/MARS
- GitHub stars: 2
- Paper ID: 2604.07023
- Canonical ID: 2604.07023v1
- Paper group ID: 019d6ffd-ac90-78a6-b252-019bed84e429
- Version ID: 019d6ffd-acd2-7293-a2db-4cbde33702eb
- Version: v1
- Version order: 1
- Published at: 2026-04-08T12:41:37+00:00
- First published at: 2026-04-08T12:41:37+00:00
- Updated at: 2026-04-09T02:06:29.008000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Ziqi Jin
- Lei Wang
- Ziwei Luo
- Aixin Sun

## Topics

- Computer Science
- cs.CL
- efficient-transformers
- fine-tuning
- inference-optimization
- model-serving-infrastructure
- text-generation
- transformers

## Metrics

- Visits (all): 25
- Visits (last 7 days): 25
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Autoregressive (AR) language models generate text one token at a time, even when consecutive tokens are highly predictable given earlier context. We introduce MARS (Mask AutoRegreSsion), a lightweight fine-tuning method that teaches an instruction-tuned AR model to predict multiple tokens per forward pass. MARS adds no architectural modifications, no extra parameters, and produces a single model that can still be called exactly like the original AR model with no performance degradation. Unlike speculative decoding, which maintains a separate draft model alongside the target, or multi-head approaches such as Medusa, which attach additional prediction heads, MARS requires only continued training on existing instruction data. When generating one token per forward pass, MARS matches or exceeds the AR baseline on six standard benchmarks. When allowed to accept multiple tokens per step, it maintains baseline-level accuracy while achieving 1.5-1.7x throughput. We further develop a block-level KV caching strategy for batch inference, achieving up to 1.71x wall-clock speedup over AR with KV cache on Qwen2.5-7B. Finally, MARS supports real-time speed adjustment via confidence thresholding: under high request load, the serving system can increase throughput on the fly without swapping models or restarting, providing a practical latency-quality knob for deployment.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6ffd-ac90-78a6-b252-019bed84e429/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ffd-ac90-78a6-b252-019bed84e429/transcript.json

## Resources

- GitHub repository: https://github.com/Xalp/MARS

## Similar Papers

- Diffusion LLMs Can Do Faster-Than-AR Inference via Discrete Diffusion Forcing (2508.09192v1): Discrete Diffusion Forcing (D2F) accelerates open-source Diffusion Large Language Models (dLLMs) beyond the inference speeds of similarly-sized autoregressive (AR) LLMs by combining block-wise autoregressive generation with inter-block parallel decoding. This approach enables a 2.5× speedup over LLaMA3-Instruct-8B on the GSM8K benchmark while preserving output quality.
- Fast-dLLM: Training-free Acceleration of Diffusion LLM by Enabling KV Cache and Parallel Decoding (2505.22618v3): Fast-dLLM introduces training-free methods to accelerate Diffusion-based Large Language Models by enabling KV cache and confidence-aware parallel decoding. The approach achieves up to 27.6x throughput improvement on benchmarks like GSM8K and MBPP, while maintaining generation quality, making Diffusion LLMs more competitive for practical deployment.
- Better & Faster Large Language Models via Multi-token Prediction (2404.19737v1): Researchers at FAIR at Meta and affiliated institutions introduced a method to train large language models by predicting multiple future tokens simultaneously, rather than just the immediate next one. This approach improves model performance, especially in code generation tasks with gains up to +7.5 percentage points on HumanEval, enhances reasoning capabilities, and accelerates inference speed by up to 3 times without requiring core architectural changes.
- Your LLM Knows the Future: Uncovering Its Multi-Token Prediction Potential (2507.11851v1): A framework developed by researchers at Apple enables pretrained autoregressive large language models to perform multi-token prediction, yielding inference speedups of up to 5.35x for code and math tasks and approximately 2.5x for general tasks while preserving generation quality.
- Fast Inference from Transformers via Speculative Decoding (2211.17192v2): Google Research developed Speculative Decoding to accelerate large Transformer model inference without altering the output distribution or requiring model retraining. The method uses a smaller model to speculatively guess future tokens, which are then verified in parallel by the larger model, achieving 2X-3X walltime speedups on tasks like translation and summarization.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
