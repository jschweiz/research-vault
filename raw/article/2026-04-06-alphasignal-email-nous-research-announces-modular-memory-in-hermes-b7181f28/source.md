---
id: 2026-04-06-alphasignal-email-nous-research-announces-modular-memory-in-hermes-b7181f28
kind: article
title: Nous Research announces modular memory in Hermes Agent update with support for custom backend providers
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- Nous Research
published_at: '2026-04-06T16:19:19Z'
ingested_at: '2026-04-09T22:56:54.002873Z'
content_hash: 5e47b27920ff4a1bedb3005028e03fe1d7e9e7977381a1665057e9791d5f0a62
identity_hash: 3c3398e6026ba913b7fe94d3a541508124a391bef3cede749de4f349fbc886bd
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- hermes agent
- modular memory
- plugin system
- agent execution
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d639768b8eb8bf::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d
doc_role: derived
parent_id: 2026-04-06-alphasignal-email-anthropic-blocks-openclaw-access-requires-api-ke-b06cbb06
index_visibility: visible
fetched_at: '2026-04-09T22:56:54.002878Z'
short_summary: Nous Research released Hermes Agent v0.7.0, introducing modular memory and a plugin system that allows for custom memory backends.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:56.687716Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: f88508e6ccfe22f0287bea9dd8c7238352af9d47935b78625166e22cb7643a2a
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 36759f1fc2aed87ac3c0ca7198f3c3bacd7d6e00893f86209c268753db84ee34
lightweight_score:
  relevance_score: 0.6909
  source_fit_score: 0.24
  topic_fit_score: 0.755
  author_fit_score: 0.12
  evidence_fit_score: 1.0
  confidence_score: 0.735
  bucket_hint: worth_a_skim
  reason: 'Heuristic fallback based on rubric matches: post-training techniques, rl for llms, 1 favorite-topic match.'
  evidence_quotes:
  - Nous Research released Hermes Agent v0.7.0, introducing modular memory and a plugin system that allows for custom memory backends.
---
# Nous Research announces modular memory in Hermes Agent update with support for custom backend providers

Source newsletter: 🚨 Anthropic blocks OpenClaw access, requires API keys starting April 4
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-06T16:19:19+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d

## Newsletter Context

Section: Top News

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
