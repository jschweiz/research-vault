---
id: 2026-04-06-tldr-email-how-claude-code-builds-a-system-prompt-a4d9c7c0
kind: article
title: How Claude Code Builds a System Prompt
source_url: https://www.dbreunig.com/2026/04/04/how-claude-code-builds-a-system-prompt.html
source_name: TLDR Email
authors:
- TLDR <dan@tldrnewsletter.com>
- TLDR
published_at: '2026-04-06T11:04:43Z'
ingested_at: '2026-04-09T12:05:04.773094Z'
content_hash: 07135b458307272d5e0084489c9426625293978be038f6b8dfcb6c216d2043a2
identity_hash: e88c11732dd03e22b3419dcbe24102da13b8e219178aa848d0428e6613b51802
tags:
- newsletter
- tldr
- email
- ai
- article
- system prompts
- claude code
- context engineering
- programming
status: active
asset_paths: []
source_id: tldr-email
source_pipeline_id: tldr-email
external_key: 19d627761e563067::link::https://www.dbreunig.com/2026/04/04/how-claude-code-builds-a-system-prompt.html
canonical_url: https://www.dbreunig.com/2026/04/04/how-claude-code-builds-a-system-prompt.html
doc_role: derived
parent_id: 2026-04-06-tldr-email-apple-egpu-support-inside-ai-lab-finances-claude-f865879a
index_visibility: visible
fetched_at: '2026-04-09T12:15:31.744953Z'
short_summary: This article explores how Claude Code builds system prompts, highlighting the complexity of context engineering and the importance of harnesses. It includes a table demonstrating the components of a system prompt.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T12:14:22.921123Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: fa8f03ba4862d513caf7c6f07c8aad27105f2d4661683182c08a434255170310
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# How Claude Code Builds a System Prompt

Source newsletter: Apple eGPU support ⚡, inside AI lab finances 💰, Claude Code system prompts 🤖
Sender: TLDR <dan@tldrnewsletter.com>
Published At: 2026-04-06T11:04:43+00:00
Canonical URL: https://www.dbreunig.com/2026/04/04/how-claude-code-builds-a-system-prompt.html

## Newsletter Context

Section: Programming, Design & Data Science

System prompts are often the best manual for how an app is intended to work. The accidental leak of Claude Code's source code reveals how Claude Code assembles a context and shows how complex context engineering can be, and the importance of harnesses. This post contains a table that shows how Claude Code assembles a system prompt. Some components are always included, while others are conditional, and components may have variations.
