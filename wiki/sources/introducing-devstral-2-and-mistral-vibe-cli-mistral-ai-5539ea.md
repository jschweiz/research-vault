---
id: page:2025-12-09-mistral-research-introducing-devstral-2-and-mistral-vibe-cli-mist-3175b131
page_type: source-note
title: 'Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI'
aliases:
- 'Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI'
source_refs:
- 2025-12-09-mistral-research-introducing-devstral-2-and-mistral-vibe-cli-mist-3175b131
backlinks:
- page:2025-05-21-mistral-research-devstral-mistral-ai-f4d5cce5
- page:2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
- page:2025-07-10-mistral-research-upgrading-agentic-coding-capabilities-with-the-n-4a9a767c
- page:2025-07-15-mistral-research-voxtral-mistral-ai-d4863455
- page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
- page:2026-03-16-mistral-research-introducing-mistral-small-4-mistral-ai-b071b337
- page:2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
- page:2026-03-23-anthropic-research-long-running-claude-for-scientific-computing-20a930ae
- page:2026-03-23-mistral-research-speaking-of-voxtral-mistral-ai-6a35b94f
- topic:inference
- topic:mistral
- topic:open-weight-models
updated_at: '2026-04-09T12:15:42.030294Z'
managed: true
---
# Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/devstral-2-vibe-cli
- Document kind: blog-post
- Published at: 2025-12-09T12:00:00+00:00
- Tags: mistral, official, research, website, blog-post
- Topics: [Mistral](../topics/mistral.md), [Official](../topics/official.md), [Website](../topics/website.md), [Agents](../topics/agents.md), [Inference](../topics/inference.md), [Open-Weight Models](../topics/open-weight-models.md)
- Trend score: 249.90
- Novelty score: 4.80

## Topic Map

- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Agents](../topics/agents.md)
- [Inference](../topics/inference.md)
- [Open-Weight Models](../topics/open-weight-models.md)

## Related Research

- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Agents, Inference, Mistral, Official, Website)
- [Introducing Mistral 3 | Mistral AI](introducing-mistral-3-mistral-ai-2b540b.md) (shared topics: Inference, Mistral, Official, Open-Weight Models, Website)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Agents, Mistral, Official, Website)
- [Long-running Claude for scientific computing](long-running-claude-for-scientific-computing-b8d3ec.md) (shared topics: Agents, Inference, Official, Website)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Agents, Mistral, Official, Website)
- [Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI](announcing-codestral-25-08-and-the-complete-mistral-coding-stack-cdf219.md) (shared topics: Inference, Mistral, Official, Website)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Content
Today, we're releasing Devstral 2—our next-generation coding model family available in two sizes: Devstral 2 (123B) and Devstral Small 2 (24B). Devstral 2 ships under a modified MIT license, while Devstral Small 2 uses Apache 2.0. Both are open-source and permissively licensed to accelerate distributed intelligence.
Devstral 2 is currently free to use via [our API](https://console.mistral.ai/).
We are also introducing Mistral Vibe, a native CLI built for Devstral that enables end-to-end code automation.
Highlights.
-
Devstral 2: SOTA open model for code agents with a fraction of the parameters of its competitors and achieving 72.2% on SWE-bench Verified.
-
Up to 7x more cost-efficient than Claude Sonnet at real-world tasks.
-
Mistral Vibe CLI: Native, open-source agent in your terminal solving software engineering tasks autonomously.
-
Devstral Small 2: 24B parameter model available via API or deployable locally on consumer hardware.
-
Compatible with on-prem deployment and custom fine-tuning.
Devstral: the next generation of SOTA coding.
Devstral 2 is a 123B-parameter dense transformer supporting a 256K context window. It reaches 72.2% on SWE-bench Verified—establishing it as one of the best open-weight models while remaining highly cost efficient. Released under a modified MIT license, Devstral sets the open state-of-the-art for code agents.
Devstral Small 2 scores 68.0% on SWE-bench Verified, and places firmly among models up to five times its size while being capable of running locally on consumer hardware.
Devstral 2 (123B) and Devstral Small 2 (24B) are 5x and 28x smaller than DeepSeek V3.2, and 8x and 41x smaller than Kimi K2—proving that compact models can match or exceed the performance of much larger competitors. Their reduced size makes deployment practical on limited hardware, lowering barriers for developers, small businesses, and hobbyists.hardware.
Built for production-grade workflows.
Devstral 2 supports exploring codebases and orchestrating changes across multiple files while maintaining architecture-level context. It tracks framework dependencies, detects failures, and retries with corrections—solving challenges like bug fixing and modernizing legacy systems.
The model can be fine-tuned to prioritize specific languages or optimize for large enterprise codebases.
We evaluated Devstral 2 against DeepSeek V3.2 and Claude Sonnet 4.5 using human evaluations conducted by an independent annotation provider, with tasks scaffolded through Cline. Devstral 2 shows a clear advantage over DeepSeek V3.2, with a 42.8% win rate versus 28.6% loss rate. However, Claude Sonnet 4.5 remains significantly preferred, indicating a gap with closed-source models persists.
“Devstral 2 is at the frontier of open-source coding models. In Cline, it delivers a tool-calling success rate on par with the best closed models; it's a remarkably smooth driver. This is a massive contribution to the open-source ecosystem.” — Cline.
“Devstral 2 was one of our most successful stealth launches yet, surpassing 17B tokens in the first 24 hours. Mistral AI is moving at Kilo Speed with a cost-efficient model that truly works at scale.” — Kilo Code.
Devstral Small 2, a 24B-parameter model with the same 256K context window and released under Apache 2.0, brings these capabilities to a compact, locally deployable form. Its size enables fast inference, tight feedback loops, and easy customization—with fully private, on-device runtime. It also supports image inputs, and can power multimodal agents.
Mistral Vibe CLI.
Mistral Vibe CLI is an open-source command-line coding assistant powered by Devstral. It explores, modifies, and executes changes across your codebase using natural language—in your terminal or integrated into your preferred IDE via the Agent Communication Protocol. It is released under the Apache 2.0 license.
Vibe CLI provides an interactive chat interface with tools for file manipulation, code searching, version control, and command execut
