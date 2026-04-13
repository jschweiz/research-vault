---
id: page:2026-03-16-mistral-research-introducing-mistral-small-4-mistral-ai-b071b337
page_type: source-note
title: Introducing Mistral Small 4 | Mistral AI
aliases:
- Introducing Mistral Small 4 | Mistral AI
source_refs:
- 2026-03-16-mistral-research-introducing-mistral-small-4-mistral-ai-b071b337
backlinks:
- page:2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
- page:2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
- page:2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
- page:2025-06-10-mistral-research-magistral-mistral-ai-f37de11b
- page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
- page:2026-04-02-manual-import-gemma-4-byte-for-byte-the-most-capable-open-mode-20e9cbbb
- topic:architecture
- topic:efficiency
- topic:inference
- topic:mistral
- topic:reasoning
updated_at: '2026-04-09T23:10:03.467783Z'
managed: true
---
# Introducing Mistral Small 4 | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/mistral-small-4
- Document kind: blog-post
- Published at: 2026-03-16T21:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, model, multimodal, reasoning, open-source, architecture
- Topics: [Multimodal](../topics/multimodal.md), [Reasoning](../topics/reasoning.md), [Inference](../topics/inference.md), [Efficiency](../topics/efficiency.md), [Architecture](../topics/architecture.md), [Mistral](../topics/mistral.md)
- Trend score: 31.16
- Novelty score: 5.40

## Summary

Mistral Small 4 is a new model that unifies reasoning, multimodal, and coding capabilities into a single, versatile model. It features configurable reasoning effort and is optimized for efficiency and performance.

## Topic Map

- [Multimodal](../topics/multimodal.md)
- [Reasoning](../topics/reasoning.md)
- [Inference](../topics/inference.md)
- [Efficiency](../topics/efficiency.md)
- [Architecture](../topics/architecture.md)
- [Mistral](../topics/mistral.md)

## Related Research

- [Mistral Small 3.1 | Mistral AI](mistral-small-3-1-mistral-ai-5dc4fa.md) (shared topics: Inference, Mistral, Multimodal)
- [A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model](a1-a-fully-transparent-open-source-adaptive-and-efficient-trunca-ac0efe.md) (shared topics: Inference, Multimodal)
- [Gemma 4: Byte for byte, the most capable open models](gemma-4-byte-for-byte-the-most-capable-open-models-24dd40.md) (shared topics: Multimodal, Reasoning)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Inference, Mistral)
- [Introducing Mistral 3 | Mistral AI](introducing-mistral-3-mistral-ai-2b540b.md) (shared topics: Efficiency, Mistral)
- [Magistral | Mistral AI](magistral-mistral-ai-df7660.md) (shared topics: Mistral, Reasoning)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Introducing
Mistral Small 4
Today, we are announcing Mistral Small 4. This model is the next major release in the Mistral Small family. Mistral Small 4 is the first Mistral model to unify the capabilities of our flagship models, Magistral for reasoning, Pixtral for multimodal, and Devstral for agentic coding, into a single, versatile model. With Small 4, users no longer need to choose between a fast instruct model, a powerful reasoning engine, or a multimodal assistant: one model now delivers all three, with configurable reasoning effort and best-in-class efficiency.
Mistral Small 4 is released under the Apache 2.0 license, continuing our commitment to open, accessible, and customizable AI.
A new standard for multimodal, reasoning-optimized models
Mistral Small 4 is a hybrid model optimized for general chat, coding, agentic tasks, and complex reasoning. Its architecture supports both text and image inputs, making it versatile for a wide range of applications. With Mistral Small 4, we reaffirm our commitment to open-source models and are proud to join the [NVIDIA Nemotron Coalition](/news/mistral-ai-and-nvidia-partner-to-accelerate-open-frontier-models) as a founding member, advancing collaboration and innovation in AI development.
Key architectural details
-
Mixture of Experts (MoE): 128 experts, with 4 active per token, enabling efficient scaling and specialization.
-
119B total parameters, with 6B active parameters per token (8B including embedding and output layers).
-
256k context window, supporting long-form interactions and document analysis.
-
Configurable reasoning effort: Toggle between fast, low-latency responses and deep, reasoning-intensive outputs.
-
Native multimodality: Accepts both text and image inputs, unlocking use cases from document parsing to visual analysis.
Performance highlights
-
40% reduction in end-to-end completion time (latency-optimized setup).
-
3x more requests per second (throughput-optimized setup) compared to Mistral Small 3.
Why Mistral Small 4?
Unified capabilities
Mistral Small 4 consolidates the strengths of Magistral (reasoning), Devstral (coding agents), and Mistral Small (instruct) into a single model. Whether you need a chat assistant, a research partner, or a coding agent, Small 4 adapts to your task, no need to switch between specialized models.
Reasoning on demand
With the new reasoning_effort
parameter, users can dynamically adjust the model’s behavior:
reasoning_effort="none"
: Fast, lightweight responses for everyday tasks, equivalent to the same chat style of Mistral Small 3.2.reasoning_effort="high"
: Deep, step-by-step reasoning for complex problems, with equivalent verbosity to previous Magistral models.
Enterprise-grade efficiency
-
Minimum infrastructure: 4x
[NVIDIA HGX H100](https://www.nvidia.com/en-us/data-center/h100/), 2x[NVIDIA HGX H200](https://www.nvidia.com/en-us/data-center/h200/), or 1x[NVIDIA DGX B200](https://www.nvidia.com/en-us/data-center/technologies/blackwell-architecture/). -
Recommended setup: 4x NVIDIA HGX H100, 4x NVIDIA HGX H200, or 2x NVIDIA DGX B200 for optimal performance.
-
Mistral Small 4 is fully open source. Fine-tune it for specialized tasks or deploy it out of the box for general-purpose use. Thanks to collaboration with the community, it’s now available on vLLM, llama.cpp, SGLang, Transformers, and more.
-
Delivering advanced open-source AI models requires broad optimization. Through close collaboration with NVIDIA, inference has been optimized for both open source vLLM and SGLang, ensuring efficient, high-throughput serving across deployment scenarios.
Figure: Score vs. Output Length across three benchmarks. Top: accuracy scores (higher is better). Bottom: average output length in thousands of characters (shorter is better).
Mistral Small 4 with reasoning achieves competitive scores, matching or surpassing GPT-OSS 120B on all three benchmarks, while generating significantly shorter outputs. On AA LCR, Mistral Small 4 scores 0.72 with just
