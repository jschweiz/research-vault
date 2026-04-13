---
id: page:2026-04-07-alphasignal-email-cursor-introduces-warp-decode-where-each-gpu-war-b10d073c
page_type: source-note
title: Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts
aliases:
- Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts
source_refs:
- 2026-04-07-alphasignal-email-cursor-introduces-warp-decode-where-each-gpu-war-b10d073c
backlinks:
- page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
- page:2026-03-16-jack-clark-import-ai-if-ai-writes-all-the-worlds-software-we-should-i-e3751112
- page:2026-04-05-alphasignal-email-follow-on-x-8009c6bd
- page:2026-04-05-alphasignal-email-kv-cache-transform-coding-a0f74007
- page:2026-04-06-alphasignal-email-netflix-presents-void-an-open-source-framework-e-91ac4018
- page:2026-04-07-alphasignal-email-anthropic-signs-deal-with-google-and-broadcom-fo-965138a0
- page:2026-04-08-alphasignal-email-ai2-presents-open-source-wilddet3d-enabling-3d-o-15880951
- page:2026-04-08-alphasignal-email-anthropic-launches-glasswing-using-claude-mythos-9a955e8d
- page:2026-04-08-alphasignal-email-cognition-releases-swe-1-6-with-parallel-tool-ca-9b67cb6d
- page:2026-04-08-alphasignal-email-world-labs-refines-marble-models-for-better-visu-c73a06fb
- page:2026-04-08-alphasignal-email-z-ai-announces-open-source-glm-5-1-coding-model--bcddf463
- topic:efficiency
- topic:infrastructure
updated_at: '2026-04-09T23:10:03.049052Z'
managed: true
---
# Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: AlphaSignal Email
- Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=ESAhwLEof7wPMJe0&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
- Document kind: article
- Published at: 2026-04-07T16:55:46+00:00
- Authors: AlphaSignal <news@alphasignal.ai>, AlphaSignal
- Tags: newsletter, alphasignal, email, ai, article, sub-document, warp decode, moe, gpu, token generation
- Topics: [Efficiency](../topics/efficiency.md), [Infrastructure](../topics/infrastructure.md), [Alphasignal](../topics/alphasignal.md), [Email](../topics/email.md), [Newsletter](../topics/newsletter.md), [Sub Document](../topics/sub-document.md)
- Trend score: 721.95
- Novelty score: 6.80

## Summary

Cursor introduced warp decode to improve efficiency in mixture-of-experts models by having each GPU warp compute one output directly, reducing overhead and increasing speed.

## Topic Map

- [Efficiency](../topics/efficiency.md)
- [Infrastructure](../topics/infrastructure.md)
- [Alphasignal](../topics/alphasignal.md)
- [Email](../topics/email.md)
- [Newsletter](../topics/newsletter.md)
- [Sub Document](../topics/sub-document.md)

## Related Research

- [Z.ai announces open-source GLM-5.1 coding model topping SWE-Bench Pro and beating GPT-5.4 and Opus 4.6](z-ai-announces-open-source-glm-5-1-coding-model-topping-swe-benc-b77584.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [World Labs refines Marble models for better visuals and introduces scalable environment generation model](world-labs-refines-marble-models-for-better-visuals-and-introduc-3d3001.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Cognition releases SWE-1.6 with parallel tool calls and fewer reasoning loops](cognition-releases-swe-1-6-with-parallel-tool-calls-and-fewer-re-bf6883.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Ai2 presents open-source WildDet3D enabling 3D object detection from a single image](ai2-presents-open-source-wilddet3d-enabling-3d-object-detection--79899d.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Netflix presents VOID, an open-source framework enabling video object removal with updated motion](netflix-presents-void-an-open-source-framework-enabling-video-ob-75ef95.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Work With Us](work-with-us-b67b8e.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
