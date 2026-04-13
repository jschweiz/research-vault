---
id: 2026-04-07-alphasignal-email-mempalace-stores-full-ai-conversations-locally-a-646922e3
kind: article
title: MemPalace stores full AI conversations locally and retrieves them with a structured memory system instead of summaries
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=Ha6pF1r0OeKLOwDg&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-07T16:55:46Z'
ingested_at: '2026-04-09T22:56:39.205253Z'
content_hash: 82df8675b554566e2244485e69570bb15297c7fd556f1017d09a0ec0b0159197
identity_hash: 87211cee23e3990731294b617592a8542755003a4a97dc734a26b7a083934f4a
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- mempalace
- llm
- memory
- local stack
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d68df217d42501::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=Ha6pF1r0OeKLOwDg&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=Ha6pF1r0OeKLOwDg&mid=228b82d4-2e38-42c1-8557-e73c77f98a75
doc_role: derived
parent_id: 2026-04-07-alphasignal-email-openai-proposes-ai-tax-policy-linking-systems-to-2a605bbd
index_visibility: visible
fetched_at: '2026-04-13T18:08:08.158666Z'
short_summary: MemPalace is an open-source memory layer for LLM workflows that stores full AI conversations locally using a structured memory system instead of summaries. It enables fast retrieval of context by organizing information into a 'palace' structure.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:56.846838Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 6f30434df91e5e3b536902f626067b53e086ba0ac9cf0638fe50abd04aca6208
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# MemPalace stores full AI conversations locally and retrieves them with a structured memory system instead of summaries

Source newsletter: 🏛️ OpenAI proposes AI tax policy linking systems to economic infrastru
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-07T16:55:46+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=a05d3c75312d80ef&lid=Ha6pF1r0OeKLOwDg&mid=228b82d4-2e38-42c1-8557-e73c77f98a75

## Newsletter Context

Section: Top Repo

> 9,528 Stars

MemPalace is an open-source memory layer for LLM workflows. It fixes a common issue: your past chats, decisions, and debugging steps disappear after each session.

It keeps everything and organizes it into a “palace” structure so your model can find the right context fast. It reports a 100% LongMemEval score (500/500) and 96.6% without API calls using local retrieval.

**What it does**

- Stores full conversations, not summaries, so reasoning and decisions stay intact
- Uses wings (projects), rooms (topics), halls (types) to guide search
- Runs semantic search only after narrowing scope with structure

Key features

- AAAK compression: ~30× smaller context, still readable by any LLM
- Local stack: SQLite + ChromaDB, no API key required
- Knowledge graph tracks facts and flags contradictions

**How to use it**

- Install: pip install mempalace, then run mempalace init
- Ingest chats or code: mempalace mine <dir>
- Query memory: mempalace search "your question"
- Connect to agents via MCP or inject results into prompts manually
