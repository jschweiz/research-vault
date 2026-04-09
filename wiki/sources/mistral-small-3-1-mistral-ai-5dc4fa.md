---
id: page:2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
page_type: source-note
title: Mistral Small 3.1 | Mistral AI
aliases:
- Mistral Small 3.1 | Mistral AI
source_refs:
- 2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
backlinks:
- page:2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
- page:2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
- page:2026-03-16-mistral-research-introducing-mistral-small-4-mistral-ai-b071b337
- page:2026-03-23-mistral-research-speaking-of-voxtral-mistral-ai-6a35b94f
- topic:inference
- topic:long-context
- topic:model
- topic:multimodal
updated_at: '2026-04-09T16:35:04.632224Z'
managed: true
---
# Mistral Small 3.1 | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/mistral-small-3-1
- Document kind: blog-post
- Published at: 2025-03-17T12:00:00+00:00
- Tags: mistral, official, research, website, blog-post, model, open source, multimodal, context window, inference
- Topics: [Inference](../topics/inference.md), [Multimodal](../topics/multimodal.md), [Long Context](../topics/long-context.md), [Mistral](../topics/mistral.md), [Model](../topics/model.md), [Official](../topics/official.md)
- Trend score: 45.05
- Novelty score: 2.40

## Summary

Mistral Small 3.1 is a new open-source model that improves text performance, multimodal understanding, and context window, outperforming comparable proprietary models. It is designed for versatile generative AI tasks, offering lightweight and fast performance for various applications.

## Topic Map

- [Inference](../topics/inference.md)
- [Multimodal](../topics/multimodal.md)
- [Long Context](../topics/long-context.md)
- [Mistral](../topics/mistral.md)
- [Model](../topics/model.md)
- [Official](../topics/official.md)

## Related Research

- [Mistral Small 3 | Mistral AI](mistral-small-3-mistral-ai-098c06.md) (shared topics: Inference, Mistral, Model, Official)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Inference, Mistral, Official)
- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Inference, Mistral, Multimodal)
- [Mistral OCR | Mistral AI](mistral-ocr-mistral-ai-eb1d8c.md) (shared topics: Mistral, Multimodal, Official)
- [A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model](a1-a-fully-transparent-open-source-adaptive-and-efficient-trunca-ac0efe.md) (shared topics: Inference, Multimodal)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral, Official)

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
