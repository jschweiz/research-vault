---
id: 2026-04-07-alphasignal-email-cursor-introduces-warp-decode-where-each-gpu-war-b10d073c
kind: article
title: Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=ESAhwLEof7wPMJe0&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-07T16:55:46Z'
ingested_at: '2026-04-09T22:56:38.556331Z'
content_hash: d07684495ffe74782777c7b6e524f840c41aed3ec4525ba1335cf8ee26842d3d
identity_hash: 28fcf0e759b2c19ea9b8700d57575c73888ccede25e659608f5a1df1ea1798a9
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- warp decode
- moe
- gpu
- token generation
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d68df217d42501::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=ESAhwLEof7wPMJe0&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=ESAhwLEof7wPMJe0&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
doc_role: derived
parent_id: 2026-04-07-alphasignal-email-openai-proposes-ai-tax-policy-linking-systems-to-2a605bbd
index_visibility: visible
fetched_at: '2026-04-13T18:08:07.405260Z'
short_summary: Cursor introduced warp decode to improve efficiency in mixture-of-experts models by having each GPU warp compute one output directly, reducing overhead and increasing speed.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:56.823063Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 0fd175b75c614a7f844acf96fc08666d361ed602e2b230a181bea63cf43e5186
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts

Source newsletter: 🏛️ OpenAI proposes AI tax policy linking systems to economic infrastru
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-07T16:55:46+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=ESAhwLEof7wPMJe0&mid=228b82d4-2e38-42c1-8557-e73c77f98a75

## Newsletter Context

Section: Top News

> 2,528 Stars

Most mixture-of-experts models generate tokens by grouping work around experts, which adds overhead during single-token decoding. Cursor changes this by introducing warp decode , where each GPU warp computes one output value directly.

This shift removes coordination steps and improves both speed and numerical accuracy.

The issue appears during autoregressive decoding, where models process one token at a time. Traditional pipelines spend multiple stages just moving and reshaping data, not computing results.

Cursor removes these stages by mapping computation to outputs instead of experts, so each warp works independently with minimal data movement.

The system runs through two fused GPU kernels that stream weights, accumulate results in registers, and write a single output. This avoids intermediate buffers and synchronization, which reduces latency and improves hardware usage.

**Key features and results**

- Assign each warp to one output neuron, eliminating expert-level batching overhead
- Remove padding, scatter, and combine stages from the decode pipeline
- Keep activations in BF16 and accumulate in FP32 for higher numerical precision
- Achieve 1.84× higher throughput on Blackwell GPUs during token generation
- Reach ~3.95 TB/s memory bandwidth, close to hardware limits
- Produce outputs 1.4× closer to FP32 reference than standard MoE decode
