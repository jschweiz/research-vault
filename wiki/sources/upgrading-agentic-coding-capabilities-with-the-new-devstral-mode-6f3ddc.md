---
id: page:2025-07-10-mistral-research-upgrading-agentic-coding-capabilities-with-the-n-4a9a767c
page_type: source-note
title: Upgrading agentic coding capabilities with the new Devstral models | Mistral AI
aliases:
- Upgrading agentic coding capabilities with the new Devstral models | Mistral AI
source_refs:
- 2025-07-10-mistral-research-upgrading-agentic-coding-capabilities-with-the-n-4a9a767c
backlinks:
- topic:agentic-coding-capabilities
- topic:models-mistral-ai
updated_at: '2026-04-09T12:15:42.407066Z'
managed: true
---
# Upgrading agentic coding capabilities with the new Devstral models | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/devstral-2507
- Document kind: blog-post
- Published at: 2025-07-10T16:00:00+00:00
- Tags: mistral, official, research, website, blog-post
- Topics: [Agents](../topics/agents.md), [Mistral](../topics/mistral.md), [Official](../topics/official.md), [Website](../topics/website.md), [Agentic Coding Capabilities](../topics/agentic-coding-capabilities.md), [Models Mistral Ai](../topics/models-mistral-ai.md)
- Trend score: 249.90
- Novelty score: 4.80

## Topic Map

- [Agents](../topics/agents.md)
- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Agentic Coding Capabilities](../topics/agentic-coding-capabilities.md)
- [Models Mistral Ai](../topics/models-mistral-ai.md)

## Related Research

- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Agents, Mistral, Official, Website)
- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Agents, Mistral, Official, Website)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Agents, Mistral, Official, Website)
- [Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI](introducing-devstral-2-and-mistral-vibe-cli-mistral-ai-5539ea.md) (shared topics: Agents, Mistral, Official, Website)
- [Codestral Embed | Mistral AI](codestral-embed-mistral-ai-1a4c58.md) (shared topics: Agents, Mistral, Official, Website)
- [Devstral | Mistral AI](devstral-mistral-ai-f64958.md) (shared topics: Agents, Mistral, Official, Website)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Today, we introduce Devstral Medium, as well as an upgrade to Devstral Small. These models are released under the collaboration between Mistral AI and [All Hands AI](https://www.all-hands.dev/) 🙌, with a strong emphasis on generalization to different prompts and agentic scaffolds.
The new Devstral Small 1.1 is released under the Apache 2.0 license, and is state-of-the-art amongst open models for code agents. Devstral Medium is available through our API, and sets a new point on the cost/performance pareto frontier, surpassing Gemini 2.5 Pro and GPT 4.1 for a quarter of the price.
Devstral Small 1.1
As with the previous version of Devstral Small, we release Devstral Small 1.1 under the Apache 2.0 license. While the architecture remains the same, with only 24B parameters, Devstral Small 1.1 comes with significant improvements over its predecessor:
Enhanced Performance
Devstral Small 1.1 achieves a score of 53.6% on SWE-Bench Verified, and sets a new state-of-the-art for open models without test-time scaling.
Versatility and Generalization
Devstral Small 1.1 excels when paired with OpenHands, and also demonstrates better generalization to different prompts and coding environments. Its versatility is further enhanced by supporting both Mistral function calling and XML formats, making it adaptable to a wide range of applications and agentic scaffolds.
Devstral Medium
Devstral Medium builds upon the strengths of Devstral Small and takes performance to the next level with a score of 61.6% on SWE-Bench Verified. Devstral Medium is available through our public API, and offers exceptional performance at a competitive price point, making it an ideal choice for businesses and developers looking for a high-quality, cost-effective model.
For those who prefer on-premise solutions, Devstral Medium can be directly deployed on private infrastructure, offering enhanced data privacy and control. We also support custom finetuning for Devstral Medium, allowing enterprises to customize the model for specific use cases, and achieve optimal performance tailored to their specific requirements.
Availability
Both models are available through our API under the the following names:
-
devstral-small-2507 at the same price as Mistral Small 3.1: $0.1/M input tokens and $0.3/M output tokens.
-
devstral-medium-2507 at the same price as Mistral Medium 3: $0.4/M input tokens and $2/M output tokens.
We release Devstral Small 1.1 under the Apache 2.0 license for the community to build on, customize, and accelerate autonomous software development. To try it for yourself, head over to our [model card](https://huggingface.co/mistralai/Devstral-Small-2507).
Devstral Medium will also be available on [Mistral Code](https://mistral.ai/news/mistral-code) for enterprise customers and on our [finetuning API](https://docs.mistral.ai/guides/finetuning/). To deploy and customize the model in your environment, please [contact us](https://mistral.ai/contact).
We are dedicated to open-sourcing our most accessible and impactful models, ensuring the open-source community can easily utilize and benefit from our advanced technology. While Devstral Small is easily usable for local deployment and available under the Apache 2.0 license for everyone to use and build upon, Devstral Medium is available on our API and offers high performance for developers and enterprises.
