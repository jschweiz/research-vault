---
id: 2026-04-06-alphasignal-email-anthropic-blocks-openclaw-access-requires-api-ke-b06cbb06
kind: newsletter
title: 🚨 Anthropic blocks OpenClaw access, requires API keys starting April 4
source_url: https://mail.google.com/mail/u/0/#inbox/19d639768b8eb8bf
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-06T16:19:19Z'
ingested_at: '2026-04-09T22:56:48.148696Z'
content_hash: 0bc71851604ae672e77a4e86bc4c6800c5fec23a0e898043ff75f8482af9c471
identity_hash: a3ae4e07001b0893a6171fca1fa70f3514a0087b80784ff274973d0c05a92124
tags:
- newsletter
- alphasignal
- email
- ai
- anthropic
- claude
- agent
- openclaw
- nous research
- hermes agent
status: active
asset_paths:
- original.html
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d639768b8eb8bf
canonical_url: https://mail.google.com/mail/u/0/#inbox/19d639768b8eb8bf
doc_role: primary
parent_id: null
index_visibility: hidden
fetched_at: '2026-04-09T22:56:48.148705Z'
short_summary: Anthropic is changing its Claude subscription policy to exclude third-party agent tools like OpenClaw, requiring users to use credits or API keys starting April 4. Additionally, Nous Research released an update for Hermes Agent featuring modular memory and enhanced execution stability.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:57.499971Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 24e7347feaa59b0003e4cd38cfeb2b0de88b09c4eb0feb238aa54f7fa51456a7
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: aa3c34696476c5f19f2126acd4850376260e65620e2f68777181da825cf44b58
lightweight_score:
  relevance_score: 0.75
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 0.95
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses agent memory and execution stability, which aligns perfectly with the user's favorite topics of memory, reasoning, and LLM architecture.
  evidence_quotes:
  - Nous Research releases Hermes Agent v0.7.0 with a shift toward modular memory and more stable agent execution.
  - The update replaces fixed memory with a plugin system, so the agent no longer depends on a single storage design.
  - Pluggable memory system supports custom backends like vector stores or databases
---
# 🚨 Anthropic blocks OpenClaw access, requires API keys starting April 4

## Top News

### [Anthropic ends third-party agent like OpenClaw access under Claude plans, requires credits or API keys](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=RMewuCBe66p1OsRZ&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 16,539 Likes

Anthropic updates Claude subscriptions to exclude third-party tools like OpenClaw. Starting April 4, these tools no longer use Pro or Max plan quotas.

**Policy change**

Claude plans stop covering third-party agent workloads.

- Third-party tools now consume paid usage credits instead of subscription limits
- Applies to integrations using Claude login inside external agent platforms
- System prompt checks identify and restrict non-first-party usage attempts
- Requests return errors when attempting to use plan-based quota through agents

**Reason for change**

Anthropic adjusts for demand from continuous agent execution.

- Agent tools send persistent, high-frequency requests beyond plan assumptions
- Flat-rate pricing fails under sustained autonomous task execution patterns
- Capacity management prioritizes direct product usage and API customers
- Company states change supports long-term service stability and allocation control

**Pricing updates**

Anthropic introduces credits and revised access paths.

- One-time credit equals the user’s current monthly subscription payment
- Discounted usage bundles replace subscription coverage for external tools
- Refund option provided through email link for users choosing cancellation
- API key access continues with standard pay-as-you-go billing structure

### [Nous Research announces modular memory in Hermes Agent update with support for custom backend providers](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 2,592 Likes

Nous Research releases Hermes Agent v0.7.0 with a shift toward modular memory and more stable agent execution.

The update replaces fixed memory with a plugin system, so the agent no longer depends on a single storage design. The key change lets you choose or build memory backends, which changes how agents store and retrieve context across tasks.

**What it does**

Hermes Agent runs autonomous tasks using tools, APIs, and stored context.

- Executes multi-step workflows using models, tools, and external services
- Stores context (“memory”) so agents reuse past information across tasks
- Integrates with editors, APIs, and browsers through tool plugins
- Supports long-running sessions with persistent state and tool access

**Key features**

This release adds modular systems and execution visibility.

- Pluggable memory system supports custom backends like vector stores or databases
- Credential pools rotate API keys automatically to handle failures and limits
- Camofox browser enables local browsing with session persistence and debugging access
- Inline diff previews show file changes before the agent continues execution
- Security checks block secret leaks from prompts, URLs, and tool outputs

## Top Paper

### [Netflix presents VOID, an open-source framework enabling video object removal with updated motion](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=AJ8MVbbKueyzSAB&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

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

## Signals

### [Anthropic enables Claude to use email, documents, and files from Microsoft 365 in conversations](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=TFAbLm4ANuZeD4Rx&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 16,401 Likes

### [Pika introduces video chat skill allowing agents to interact and perform tasks during calls](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=qxN4FoIfi6F1LmB1&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 5,422 Likes

### [OpenClaw adds video generation with automatic provider selection and runtime modes](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=1AjKuQWULNqvAELjK&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 4,819 Likes

### [Anthropic proposes model diffing to focus safety analysis on features unique to each model](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=ZLUldD4P7qE2qu1C&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 2,632 Likes

### [Nous Research integrates Manim into Hermes Agent for visualizing algorithms, equations, and technical concepts](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=1wxmOv8ipRrHf9t42&mid=53a079f7-c01a-447c-83a7-c5835d17963d)

> 4,103 Likes
