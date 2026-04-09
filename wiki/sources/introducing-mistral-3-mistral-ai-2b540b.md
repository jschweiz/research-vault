---
id: page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
page_type: source-note
title: Introducing Mistral 3 | Mistral AI
aliases:
- Introducing Mistral 3 | Mistral AI
source_refs:
- 2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
backlinks:
- page:2026-03-16-mistral-research-introducing-mistral-small-4-mistral-ai-b071b337
- topic:efficiency
- topic:large-3
- topic:ministral-3
- topic:model-release
- topic:multimodal-ai
updated_at: '2026-04-09T16:35:04.475506Z'
managed: true
---
# Introducing Mistral 3 | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/mistral-3
- Document kind: blog-post
- Published at: 2025-12-02T16:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, model release, multimodal ai, open source, large 3, ministral 3
- Topics: [Efficiency](../topics/efficiency.md), [Large 3](../topics/large-3.md), [Ministral 3](../topics/ministral-3.md), [Mistral](../topics/mistral.md), [Model Release](../topics/model-release.md), [Multimodal Ai](../topics/multimodal-ai.md)
- Trend score: 4.72
- Novelty score: 0.00

## Summary

Mistral 3 introduces a new family of open multimodal and multilingual AI models, including Mistral Large 3 and the Ministral 3 series, emphasizing state-of-the-art performance, efficiency, and open access.

## Topic Map

- [Efficiency](../topics/efficiency.md)
- [Large 3](../topics/large-3.md)
- [Ministral 3](../topics/ministral-3.md)
- [Mistral](../topics/mistral.md)
- [Model Release](../topics/model-release.md)
- [Multimodal Ai](../topics/multimodal-ai.md)

## Related Research

- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Efficiency, Mistral)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Mistral)
- [Introducing our Science Blog](introducing-our-science-blog-828ea5.md) (shared topics: Efficiency)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Mistral)
- [Introducing Mistral OCR 3 | Mistral AI](introducing-mistral-ocr-3-mistral-ai-0ff4ac.md) (shared topics: Mistral)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Introducing Mistral 3
The next generation of
open multimodal and multilingual AI
Today, we announce Mistral 3, the next generation of Mistral models. Mistral 3 includes three state-of-the-art small, dense models (14B, 8B, and 3B) and Mistral Large 3 – our most capable model to date – a sparse mixture-of-experts trained with 41B active and 675B total parameters. All models are released under the Apache 2.0 license. Open-sourcing our models in a variety of compressed formats empowers the developer community and puts AI in people’s hands through distributed intelligence.
The Ministral models represent the best performance-to-cost ratio in their category. At the same time, Mistral Large 3 joins the ranks of frontier instruction-fine-tuned open-source models.
Mistral Large 3: A state-of-the-art open model
Mistral Large 3 is one of the best permissive open weight models in the world, trained from scratch on 3000 of NVIDIA’s H200 GPUs. Mistral Large 3 is Mistral’s first mixture-of-experts model since the seminal Mixtral series, and represents a substantial step forward in pretraining at Mistral. After post-training, the model achieves parity with the best instruction-tuned open-weight models on the market on general prompts, while also demonstrating image understanding and best-in-class performance on multilingual conversations (i.e., non-English/Chinese).
Mistral Large 3 debuts at #2 in the OSS non-reasoning models category (#6 amongst OSS models overall) on the [LMArena leaderboard](https://lmarena.ai/leaderboard/text).
We release both the base and instruction fine-tuned versions of Mistral Large 3 under the Apache 2.0 license, providing a strong foundation for further customization across the enterprise and developer communities. A reasoning version is coming soon!
Mistral, NVIDIA, vLLM & Red Hat join forces to deliver faster, more accessible Mistral 3
Working in conjunction with vLLM and Red Hat, Mistral Large 3 is very accessible to the open-source community. We’re releasing a checkpoint in NVFP4 format, built with [llm-compressor](https://github.com/vllm-project/llm-compressor). This optimized checkpoint lets you run Mistral Large 3 efficiently on Blackwell NVL72 systems and on a single 8×A100 or 8×H100 node using [vLLM](https://github.com/vllm-project/vllm).
Delivering advanced open-source AI models requires broad optimization, achieved through a [partnership with NVIDIA](https://blogs.nvidia.com/blog/mistral-frontier-open-models/). All our new Mistral 3 models, from Large 3 to Ministral 3, were trained on NVIDIA Hopper GPUs to tap high-bandwidth HBM3e memory for frontier-scale workloads. NVIDIA’s extreme co-design approach brings hardware, software, and models together. NVIDIA engineers enabled efficient inference support for [TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) and [SGLang](https://github.com/sgl-project/sglang) for the complete Mistral 3 family, for efficient low-precision execution.
For Large 3’s sparse MoE architecture, NVIDIA integrated state-of-the-art Blackwell attention and MoE kernels, added support for prefill/decode disaggregated serving, and collaborated with Mistral on speculative decoding, enabling developers to efficiently serve long-context, high-throughput workloads on GB200 NVL72 and beyond. On the edge, delivers optimized deployments of the Ministral models on [DGX Spark](http://nvidia.com/en-us/products/workstations/dgx-spark/), [RTX PCs and laptops](https://www.nvidia.com/en-us/ai-on-rtx/), and [Jetson devices](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/), giving developers a consistent, high-performance path to run these open models from data center to robot.
We are very thankful for the collaboration and want to thank vLLM, Red Hat, and NVIDIA in particular.
Ministral 3: State-of-the-art intelligence at the edge
For edge and local use cases, we release the Ministral 3 series, available in three model sizes: 3B, 8B, and 14B parameters. Furthermore, for
