---
id: 2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
kind: blog-post
title: Introducing Mistral 3 | Mistral AI
source_url: https://mistral.ai/news/mistral-3
source_name: Mistral Research
authors:
- Mistral AI
published_at: '2025-12-02T16:00:00Z'
ingested_at: '2026-04-09T12:04:31.805863Z'
content_hash: 54a9e519379876a08dd81c337355b0b21027fa42bb65a2b5814e48029e9e44bf
identity_hash: a8974140ffe3ff657dfcf5fa2cab5d242488a4a2a1cb795f6cbd8817ecb54df5
tags:
- mistral
- official
- research
- website
- blog-post
- model release
- multimodal ai
- open source
- large 3
- ministral 3
status: active
asset_paths:
- original.html
source_id: mistral-research
source_pipeline_id: mistral-research
external_key: https://mistral.ai/news/mistral-3
canonical_url: https://mistral.ai/news/mistral-3
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:22:48.643501Z'
short_summary: Mistral 3 introduces a new family of open multimodal and multilingual AI models, including Mistral Large 3 and the Ministral 3 series, emphasizing state-of-the-art performance, efficiency, and open access.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T12:24:04.601755Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 804431b26989be87f62ba0c5a454fcb75d70074274f1d6a816b72d1981fa8dce
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 26a22a0653ec2110a8f1a7a99ac682840a8cbda762193649c5244cdab33e59de
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 1.0
  topic_fit_score: 1.0
  author_fit_score: 1.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses the release of a new family of frontier multimodal and multilingual models, focusing on efficiency, multimodal capabilities, and reasoning, which aligns perfectly with the user's favorite topics and authors.
  evidence_quotes:
  - Mistral 3 introduces a new family of open multimodal and multilingual AI models, including Mistral Large 3 and the Ministral 3 series, emphasizing state-of-the-
  - Mistral Large 3 is Mistral’s first mixture-of-experts model since the seminal Mixtral series, and represents a substantial step forward in pretraining at Mistra
  - 'Mistral Large 3 debuts at #2 in the OSS non-reasoning models category (#6 amongst OSS models overall) on the [LMArena leaderboard](https://lmarena.ai/leaderboar'
---
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
For edge and local use cases, we release the Ministral 3 series, available in three model sizes: 3B, 8B, and 14B parameters. Furthermore, for each model size, we release base, instruct, and reasoning variants to the community, each with image understanding capabilities, all under the Apache 2.0 license. When married with the models’ native multimodal and multilingual capabilities, the Ministral 3 family offers a model for all enterprise or developer needs.
Furthermore, Ministral 3 achieves the best cost-to-performance ratio of any OSS model. In real-world use cases, both the number of generated tokens and model size matter equally. The Ministral instruct models match or exceed the performance of comparable models while often producing an order of magnitude fewer tokens.
For settings where accuracy is the only concern, the Ministral reasoning variants can think longer to produce state-of-the-art accuracy amongst their weight class - for instance 85% on AIME ‘25 with our 14B variant.
Available Today
Mistral 3 is available today on [Mistral AI Studio](https://console.mistral.ai/home), [Amazon Bedrock](https://aws.amazon.com/about-aws/whats-new/2025/12/mistral-large-3-ministral-3-family-available-amazon-bedrock/), Azure Foundry, Hugging Face ([Large 3](https://huggingface.co/collections/mistralai/mistral-large-3) & [Ministral](https://huggingface.co/collections/mistralai/ministral-3)), [Modal](https://modal.com/docs/examples/ministral3_inference), IBM WatsonX, OpenRouter, Fireworks, Unsloth AI,and Together AI. In addition, coming soon on NVIDIA NIM and AWS SageMaker.
One more thing… customization with Mistral AI
For organizations seeking tailored AI solutions, Mistral AI offers [custom model training services](https://mistral.ai/solutions/custom-model-training) to fine-tune or fully adapt our models to your specific needs. Whether optimizing for domain-specific tasks, enhancing performance on proprietary datasets, or deploying models in unique environments, our team collaborates with you to build AI systems that align with your goals. For enterprise-grade deployments, custom training ensures your AI solution delivers maximum impact securely, efficiently, and at scale.
Get started with Mistral 3
The future of AI is open. Mistral 3 redefines what’s possible with a family of models built for frontier intelligence, multimodal flexibility, and unmatched customization. Whether you’re deploying edge-optimized solutions with Ministral 3 or pushing the boundaries of reasoning with Mistral Large 3, this release puts state-of-the-art AI directly into your hands.
Why Mistral 3?
-
Frontier performance, open access: Achieve closed-source-level results with the transparency and control of open-source models.
-
Multimodal and multilingual: Build applications that understand text, images, and complex logic across 40+ native languages.
-
Scalable efficiency: From 3B to 675B parameters, choose the model that fits your needs, from edge devices to enterprise workflows.
-
Agentic and adaptable: Deploy for coding, creative collaboration, document analysis, or tool-use workflows with precision.
Next Steps
-
Explore the model documentation:
-
Technical documentation for customers is available on our
[AI Governance Hub](https://legal.mistral.ai/) -
Start building:
[Ministral 3](https://huggingface.co/collections/mistralai/ministral-3)and[Large 3](https://huggingface.co/collections/mistralai/mistral-large-3)on Hugging Face, or deploy via[Mistral AI’s platform](https://console.mistral.ai/home)for instant API access and[API pricing](https://mistral.ai/pricing#api-pricing) -
Customize for your needs: Need a tailored solution?
[Contact our team](https://mistral.ai/contact)to explore fine-tuning or enterprise-grade training. -
Share your projects, questions, or breakthroughs with us:
[Twitter/X](https://x.com/MistralAI),[Discord](https://discord.com/invite/mistralai), or[GitHub](https://github.com/mistralai).
Alongside this launch, you can explore the full details of the Ministral 3 series architecture in our latest research paper [here](https://arxiv.org/abs/2601.08584).
We believe that the future of AI should be built on transparency, accessibility, and collective progress. With this release, we invite the world to explore, build, and innovate with us, unlocking new possibilities in reasoning, efficiency, and real-world applications.
Together, let’s turn understanding into action.
