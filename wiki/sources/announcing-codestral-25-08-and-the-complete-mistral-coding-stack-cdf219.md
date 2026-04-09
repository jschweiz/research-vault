---
id: page:2025-07-30-mistral-research-announcing-codestral-25-08-and-the-complete-mist-98053d11
page_type: source-note
title: Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI
aliases:
- Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI
source_refs:
- 2025-07-30-mistral-research-announcing-codestral-25-08-and-the-complete-mist-98053d11
backlinks:
- page:2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
- page:2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
- page:2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
- page:2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
- page:2025-05-07-mistral-research-medium-is-the-new-large-mistral-ai-7a9d19dc
- page:2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
- page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
- page:2025-12-09-mistral-research-introducing-devstral-2-and-mistral-vibe-cli-mist-3175b131
- page:2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
- page:2026-03-23-mistral-research-speaking-of-voxtral-mistral-ai-6a35b94f
- topic:search
updated_at: '2026-04-09T12:15:42.607092Z'
managed: true
---
# Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/codestral-25-08
- Document kind: blog-post
- Published at: 2025-07-30T12:00:00+00:00
- Tags: mistral, official, research, website, blog-post
- Topics: [Mistral](../topics/mistral.md), [Official](../topics/official.md), [Website](../topics/website.md), [Evaluations](../topics/evaluations.md), [Inference](../topics/inference.md), [Search](../topics/search.md)
- Trend score: 56.46
- Novelty score: 1.80

## Topic Map

- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Evaluations](../topics/evaluations.md)
- [Inference](../topics/inference.md)
- [Search](../topics/search.md)

## Related Research

- [Mistral Small 3.1 | Mistral AI](mistral-small-3-1-mistral-ai-5dc4fa.md) (shared topics: Evaluations, Inference, Mistral, Official, Website)
- [Mistral Small 3 | Mistral AI](mistral-small-3-mistral-ai-098c06.md) (shared topics: Evaluations, Inference, Mistral, Official, Website)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Evaluations, Mistral, Official, Website)
- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Inference, Mistral, Official, Website)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Evaluations, Mistral, Official, Website)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Evaluations, Mistral, Official, Website)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

How the world’s leading enterprises are using integrated coding solutions from Mistral AI to cut development, review, and testing time by 50%—and why the playbook now fits every company that wants AI-native software development.
AI-powered coding is taking off, but enterprise adoption still lags due to critical limitations
Over the past year, AI coding assistants have introduced powerful capabilities, such as multi-file reasoning, contextual suggestions, and natural-language agents, all directly within the IDE. Despite these improvements, however, adoption inside enterprise environments has been slow. The reasons have less to do with model performance or the interface, and more with how these tools are built, deployed, and governed.
Key limitations holding back enterprise teams include:
-
Deployment constraints: Most AI coding tools are SaaS-only, with no options for VPC, on-prem, or air-gapped environments. This is a hard blocker for organizations in finance, defense, healthcare, and other regulated industries.
-
Limited customization: Enterprises often need to adapt models to their own codebases and development conventions. Without access to model weights, pos-training workflows, or extensibility, teams are locked out of leveraging the best of their codebases.
-
Fragmented architecture: Agents, embeddings, completions, and plugins are frequently decoupled across vendors—leading to integration drift, inconsistent context handling, and operational overhead. Moreover, coding copilots are not well-integrated into full enterprise platforms, such as product development tools, CRMs, and customer issue trackers.
-
No unified observability or control: Teams lack visibility into how AI is being used across the development lifecycle. Without telemetry, audit trails, and centralized controls, it’s difficult to scale AI usage responsibly or measure real ROI.
-
Incompatibility with internal toolchains: Many assistants operate in closed environments, making it hard to connect with internal CI/CD pipelines, knowledge bases, or static analysis frameworks.
For enterprises, these limitations aren’t edge cases—they’re baseline requirements. Solving them is what separates a good developer tool from an AI-native software development platform.
A Full-Stack Approach Built for AI-Native Software Development
Our approach to enterprise coding isn’t a bundle of isolated tools. It’s an integrated system designed to support enterprise-grade software development across every stage—from code suggestion to autonomous pull requests.
It starts with fast, reliable completion—and scales up to full codebase understanding and multi-file automation.
1. Fast, High-Fidelity Code Completion
At the foundation of the stack is Codestral, Mistral’s family of code generation models built specifically for high-precision fill-in-the-middle (FIM) completion. These models are optimized for production engineering environments: latency-sensitive, context-aware, and self-deployable.
Today, we announce its latest update. Codestral 25.08 delivers measurable upgrades over prior versions:
-
+30% increase in accepted completions
-
+10% more retained code after suggestion
-
50% fewer runaway generations, improving confidence in longer edits
-
Improved performance on academic benchmarks for short and long-context FIM completion
These improvements were validated in live IDE usage across production codebases. The model supports a wide range of languages and tasks, and is deployable across cloud, VPC, or on-prem environments—with no architectural changes required.
Codestral-2508 also brings improvements to chat mode:
-
Instruction following: +5% on IF eval v8
-
Code abilities: +5% in average MultiplE
2. Codebase-Scale Search and Semantic Retrieval
Autocomplete accelerates, but only if the model understands your codebase. [Codestral Embed](https://docs.mistral.ai/capabilities/embeddings/code_embeddings/) sets a new standard in this domain. Designed specifically for code rather than general
