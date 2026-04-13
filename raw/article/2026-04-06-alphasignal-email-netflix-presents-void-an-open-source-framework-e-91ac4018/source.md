---
id: 2026-04-06-alphasignal-email-netflix-presents-void-an-open-source-framework-e-91ac4018
kind: article
title: Netflix presents VOID, an open-source framework enabling video object removal with updated motion
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=AJ8MVbbKueyzSAB&mid=53a079f7-c01a-447c-83a7-c5835d17963d
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-06T16:19:19Z'
ingested_at: '2026-04-09T22:56:54.776017Z'
content_hash: 127dcf2974f5872deae7f017d1f2bbbf7269a5108b3df15bb2a97cd61772caa2
identity_hash: b8a66fa0c5c371d9a2512e30a105b64f77a720b5f918bace1279b69e419b49b7
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- netflix
- void
- video object removal
- open-source
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d639768b8eb8bf::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=AJ8MVbbKueyzSAB&mid=53a079f7-c01a-447c-83a7-c5835d17963d
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=AJ8MVbbKueyzSAB&mid=53a079f7-c01a-447c-83a7-c5835d17963d
doc_role: derived
parent_id: 2026-04-06-alphasignal-email-anthropic-blocks-openclaw-access-requires-api-ke-b06cbb06
index_visibility: visible
fetched_at: '2026-04-09T22:56:54.776024Z'
short_summary: Netflix introduced VOID, an open-source framework that removes objects from videos while updating motion and physical interactions. VOID achieves this by simulating cause-and-effect and using a vision-language model to regenerate consistent frames.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:56.644822Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 5bb31f0f78d30d212b416cfa8b1a14b042f7be65923789de412623e3d2d2b2dc
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 3e64ca9a80b8616b54a01fa43b3d7f717e565edee8f20bd295c685f7ed32f5f7
lightweight_score:
  relevance_score: 0.4794
  source_fit_score: 0.24
  topic_fit_score: 0.426
  author_fit_score: 0.12
  evidence_fit_score: 1.0
  confidence_score: 0.6316
  bucket_hint: worth_a_skim
  reason: 'Heuristic fallback based on rubric matches: reasoning in llms, 1 favorite-topic match.'
  evidence_quotes:
  - Netflix introduced VOID, an open-source framework that removes objects from videos while updating motion and physical interactions. VOID achieves this by simula
---
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
