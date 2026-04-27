---
id: 2026-04-10-alphasignal-email-anthropic-introduces-an-advisor-tool-that-lets-s-6fbfbbea
kind: article
title: Anthropic introduces an advisor tool that lets smaller models call Opus only when needed during agent execution
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=gea2YtmCVsUdR10E&mid=3feb7337-64eb-4569-b52d-fc5970cc2625
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-10T15:38:59Z'
ingested_at: '2026-04-13T18:07:08.505396Z'
content_hash: c56c15d0a24f860abd864b20f9cb136b0f8516a02fd38ab9b2b000f1a61e73cb
identity_hash: 67b813faa92680599fde38750bc4c895accde0be6dc3c4e5ed17d409f5bfc366
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- anthropic
- opus
- agent execution
- cost reduction
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d780beb0977c87::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=gea2YtmCVsUdR10E&mid=3feb7337-64eb-4569-b52d-fc5970cc2625
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=gea2YtmCVsUdR10E&mid=3feb7337-64eb-4569-b52d-fc5970cc2625
doc_role: derived
parent_id: 2026-04-10-alphasignal-email-anthropic-opus-advisor-cuts-agent-costs-12-with--25ff1a0c
index_visibility: visible
fetched_at: '2026-04-13T18:07:08.505403Z'
short_summary: Anthropic introduced an advisor tool to allow smaller models to call Opus only when necessary during agent execution, which helps reduce costs.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:06.654336Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 9e5e308a95d9bab4732cf45884c37bd9ecd03b16c8e5e29a53d5a153e8d8a8bb
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 5e3dc6052d48b6d2ca464189f0797a08a3f0248e5388942d19bf76c21e08bd9a
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.95
  topic_fit_score: 1.0
  author_fit_score: 0.9
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses cost reduction and agent execution methods using Anthropic models, which aligns perfectly with the user's interest in LLM efficiency, reasoning, and agent execution.
  evidence_quotes:
  - Anthropic introduced an advisor tool to allow smaller models to call Opus only when necessary during agent execution, which helps reduce costs.
  - SWE-bench Multilingual increases by 2.7 points over Sonnet alone
  - Cost per task reduces by 11.9% compared to Sonnet-only execution
---
# Anthropic introduces an advisor tool that lets smaller models call Opus only when needed during agent execution

Source newsletter: 🔄 Anthropic Opus Advisor cuts agent costs 12% with auto-escalation
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-10T15:38:59+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=gea2YtmCVsUdR10E&mid=3feb7337-64eb-4569-b52d-fc5970cc2625

## Newsletter Context

Section: Top News

> 33,539 Likes

Anthropic adds the advisor tool to the Claude Platform to simplify a common agent pattern.

You run Claude Sonnet or Claude Haiku as the main agent, and bring in Claude Opus only for harder decisions. This setup keeps most execution at lower cost while still using a stronger model when reasoning becomes difficult.

**How it works**

The executor model runs the task end-to-end and calls the advisor when needed.

- Executor handles tools, steps through tasks, and produces final outputs directly
- Advisor reads shared context and returns a plan or correction, then exits
- Advisor does not call tools or generate user-visible responses during execution
- Entire interaction runs inside a single API request without external orchestration

**Results and performance**

Anthropic reports gains across benchmarks with lower cost per task.

- SWE-bench Multilingual increases by 2.7 points over Sonnet alone
- Cost per task reduces by 11.9% compared to Sonnet-only execution
- Haiku improves from 19.7% to 41.2% on BrowseComp with advisor enabled
- Haiku setup remains 85% cheaper than Sonnet for comparable workloads

**How to use it**

You add the advisor tool directly in your API call.

- Define advisor_20260301 with Opus as the advisor model
- Set max_uses to control how often the advisor gets invoked
- Send your task through /v1/messages and let the executor decide escalation
- Monitor separate token usage for advisor and executor in the response
