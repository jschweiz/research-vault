---
id: page:2026-04-06-alphasignal-email-netflix-presents-void-an-open-source-framework-e-91ac4018
page_type: source-note
title: Netflix presents VOID, an open-source framework enabling video object removal with updated motion
aliases:
- Netflix presents VOID, an open-source framework enabling video object removal with updated motion
source_refs:
- 2026-04-06-alphasignal-email-netflix-presents-void-an-open-source-framework-e-91ac4018
backlinks:
- page:2026-04-05-alphasignal-email-follow-on-x-8009c6bd
- page:2026-04-07-alphasignal-email-cursor-introduces-warp-decode-where-each-gpu-war-b10d073c
- page:2026-04-08-alphasignal-email-ai2-presents-open-source-wilddet3d-enabling-3d-o-15880951
- page:2026-04-08-alphasignal-email-cognition-releases-swe-1-6-with-parallel-tool-ca-9b67cb6d
- page:2026-04-08-alphasignal-email-world-labs-refines-marble-models-for-better-visu-c73a06fb
- page:2026-04-08-alphasignal-email-z-ai-announces-open-source-glm-5-1-coding-model--bcddf463
- page:2026-04-08-tldr-email-the-building-block-economy-2eb76b35
- topic:netflix
- topic:open-source
updated_at: '2026-04-09T23:10:03.641772Z'
managed: true
---
# Netflix presents VOID, an open-source framework enabling video object removal with updated motion

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: AlphaSignal Email
- Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=AJ8MVbbKueyzSAB&mid=53a079f7-c01a-447c-83a7-c5835d17963d
- Document kind: article
- Published at: 2026-04-06T16:19:19+00:00
- Authors: AlphaSignal <news@alphasignal.ai>, AlphaSignal
- Tags: newsletter, alphasignal, email, ai, article, sub-document, netflix, void, video object removal, open-source
- Topics: [Alphasignal](../topics/alphasignal.md), [Email](../topics/email.md), [Netflix](../topics/netflix.md), [Newsletter](../topics/newsletter.md), [Open Source](../topics/open-source.md), [Sub Document](../topics/sub-document.md)
- Trend score: 721.95
- Novelty score: 6.80

## Summary

Netflix introduced VOID, an open-source framework that removes objects from videos while updating motion and physical interactions. VOID achieves this by simulating cause-and-effect and using a vision-language model to regenerate consistent frames.

## Topic Map

- [Alphasignal](../topics/alphasignal.md)
- [Email](../topics/email.md)
- [Netflix](../topics/netflix.md)
- [Newsletter](../topics/newsletter.md)
- [Open Source](../topics/open-source.md)
- [Sub Document](../topics/sub-document.md)

## Related Research

- [Ai2 presents open-source WildDet3D enabling 3D object detection from a single image](ai2-presents-open-source-wilddet3d-enabling-3d-object-detection--79899d.md) (shared topics: Alphasignal, Email, Newsletter, Open Source, Sub Document)
- [Z.ai announces open-source GLM-5.1 coding model topping SWE-Bench Pro and beating GPT-5.4 and Opus 4.6](z-ai-announces-open-source-glm-5-1-coding-model-topping-swe-benc-b77584.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [World Labs refines Marble models for better visuals and introduces scalable environment generation model](world-labs-refines-marble-models-for-better-visuals-and-introduc-3d3001.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Cognition releases SWE-1.6 with parallel tool calls and fewer reasoning loops](cognition-releases-swe-1-6-with-parallel-tool-calls-and-fewer-re-bf6883.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts](cursor-introduces-warp-decode-where-each-gpu-warp-computes-one-o-46e94c.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)
- [Work With Us](work-with-us-b67b8e.md) (shared topics: Alphasignal, Email, Newsletter, Sub Document)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Netflix presents VOID, an open-source framework enabling video object removal with updated motion

Source newsletter: 🚨 Anthropic blocks OpenClaw access, requires API keys starting April 4
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-06T16:19:19+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=AJ8MVbbKueyzSAB&mid=53a079f7-c01a-447c-83a7-c5835d17963d

## Newsletter Context

Section: Top Paper

> 4,528 Stars

Netflix introduces VOID, an open-source framework that removes objects from videos and updates the physical interactions they cause.

Most tools only fill in pixels behind removed objects, which breaks motion and collisions in the scene. VOID instead generates a new version of the video where objects move and react as if the removed object never existed.

**What it does**

VOID edits videos by simulating cause-and-effect, not just appearance.

- Removes selected objects while updating motion, collisions, and trajectories across frames
- Uses a vision-language model (image + text reasoning system) to find affected regions
- Builds a quadmask that separates removed, affected, and preserved areas
- Runs a video diffusion model to regenerate consistent frames over time

**How it works**

VOID trains on examples where object removal changes interactions.

- Uses Kubric for physics-based synthetic scenes and HUMOTO for human motion data
- Learns from paired inputs: original video, mask, and correct counterfactual outcome
- Runs a second pass with flow-guided noise to stabilize object shapes if needed

**Results**

VOID improves consistency compared to standard inpainting methods.

- Handles gravity, collisions, and chain reactions after object removal
- Avoids artifacts like floating objects or broken motion paths
- Evaluators prefer VOID outputs in ~66% of comparisons vs baseline models
