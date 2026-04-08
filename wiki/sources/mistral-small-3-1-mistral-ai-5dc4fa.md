---
id: page:2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
page_type: source-note
title: Mistral Small 3.1 | Mistral AI
aliases:
  - Mistral Small 3.1 | Mistral AI
source_refs:
  - 2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
backlinks:
  - page:2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
  - page:2025-07-15-mistral-research-voxtral-mistral-ai-d4863455
  - page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
  - page:2026-03-16-mistral-research-introducing-mistral-small-4-mistral-ai-b071b337
  - page:2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
  - page:2026-03-17-openai-website-introducing-gpt-5-4-mini-and-nano-8afdb503
  - topic:ai-applications
  - topic:model-release
  - topic:multimodal
  - topic:open-source
updated_at: 2026-04-08T07:14:52.176942Z
managed: true
---
# Mistral Small 3.1 | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/mistral-small-3-1
- Document kind: blog-post
- Published at: 2025-03-17T12:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, model release, multimodal, open source, ai applications, performance
- Topics: [Multimodal](../topics/multimodal.md), [Ai Applications](../topics/ai-applications.md), [Mistral](../topics/mistral.md), [Model Release](../topics/model-release.md), [Official](../topics/official.md), [Open Source](../topics/open-source.md)
- Trend score: 58.29
- Novelty score: 1.20

## Summary

Today we announce Mistral Small 3.1: the best model in its weight class. Building on [Mistral Small 3](https://mistral.ai/news/mistral-small-3), this new model comes with improved text performance, multimodal understanding, and an expanded context window of up to 128k tokens.

## Topic Map

- [Multimodal](../topics/multimodal.md)
- [Ai Applications](../topics/ai-applications.md)
- [Mistral](../topics/mistral.md)
- [Model Release](../topics/model-release.md)
- [Official](../topics/official.md)
- [Open Source](../topics/open-source.md)

## Related Research

- [Introducing Mistral 3 | Mistral AI](introducing-mistral-3-mistral-ai-2b540b.md) (shared topics: Mistral, Model Release, Official, Open Source)
- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Mistral, Multimodal, Official)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral, Official, Open Source)
- [Voxtral | Mistral AI](voxtral-mistral-ai-ae07c3.md) (shared topics: Mistral, Official, Open Source)
- [Mistral Small 3 | Mistral AI](mistral-small-3-mistral-ai-098c06.md) (shared topics: Mistral, Official, Open Source)
- [[Deprecated] Pixtral Large | Mistral AI](deprecated-pixtral-large-mistral-ai-0d8433.md) (shared topics: Mistral, Multimodal, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Today we announce Mistral Small 3.1: the best model in its weight class.
Building on [Mistral Small 3](https://mistral.ai/news/mistral-small-3), this new model comes with improved text performance, multimodal understanding, and an expanded context window of up to 128k tokens. The model outperforms comparable models like Gemma 3 and GPT-4o Mini, while delivering inference speeds of 150 tokens per second.
Mistral Small 3.1 is released under an Apache 2.0 license.
Modern AI applications demand a blend of capabilities—handling text, understanding multimodal inputs, supporting multiple languages, and managing long contexts—with low latency and cost efficiency. As shown below, Mistral Small 3.1 is the first open source model that not only meets, but in fact surpasses, the performance of leading small proprietary models across all these dimensions.
Below you will find more details on model performance. Whenever possible, we show numbers reported previously by other providers, otherwise we evaluate models through our common evaluation harness.
Instruct Performance
Text instruct benchmarks
Multimodal Instruct Benchmarks
MM-MT-Bench scaled to between 0 and 100.
Multilingual
Long Context
Pretrained Performance
We also release the pretrained base model for Mistral Small 3.1.
All pretrain
Use cases
Mistral Small 3.1 is a versatile model designed to handle a wide range of generative AI tasks, including instruction following, conversational assistance, image understanding, and function calling. It provides a solid foundation for both enterprise and consumer-grade AI applications.
Key Features and Capabilities
-
Lightweight: Mistral Small 3.1 can run on a single RTX 4090 or a Mac with 32GB RAM. This makes it a great fit for on-device use cases.
-
Fast-response conversational assistance: Ideal for virtual assistants and other applications where quick, accurate responses are essential.
-
Low-latency function calling: Capable of rapid function execution within automated or agentic workflows
-
Fine-tuning for specialized domains: Mistral Small 3.1 can be fine-tuned to specialize in specific domains, creating accurate subject matter experts. This is particularly useful in fields like legal advice, medical diagnostics, and technical support.
-
Foundation for advanced reasoning: We continue to be impressed by how the community builds on top of open Mistral models. Just in the last few weeks, we have seen several excellent reasoning models built on Mistral Small 3, such as the
[DeepHermes 24B](https://huggingface.co/NousResearch/DeepHermes-3-Mistral-24B-Preview)by Nous Research. To that end, we are releasing both base and instruct checkpoints for Mistral Small 3.1 to enable further downstream customization of the model.
Mistral Small 3.1 can be used across various enterprise and consumer applications that require multimodal understanding, such as document verification, diagnostics, on-device image processing, visual inspection for quality checks, object detection in security systems, image-based customer support, and general purpose assistance.
Availability
Mistral Small 3.1 is available to download on the huggingface website [Mistral Small 3.1 Base](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Base-2503) and [Mistral Small 3.1 Instruct](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Instruct-2503). For enterprise deployments with private and optimized inference infrastructure, please [contact us](https://mistral.ai/contact).
You can also try the model via API on Mistral AI’s developer playground [La Plateforme](https://mistral.ai/news/la-plateforme) starting today. The model is also available on [Google Cloud Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/partner-models/mistral). Mistral Small 3.1 will be available on [NVIDIA NIM](https://developer.nvidia.com/nim) and [Microsoft Azure AI Foundry](https://ai.azure.com/explore/models?&selectedCollection=mistral) in the coming weeks.
Happy building!
