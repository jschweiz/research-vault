---
id: 2025-06-10-mistral-research-magistral-mistral-ai-f37de11b
kind: blog-post
title: Magistral | Mistral AI
source_url: https://mistral.ai/news/magistral
source_name: Mistral Research
authors:
- Mistral AI
published_at: '2025-06-10T12:00:00Z'
ingested_at: '2026-04-07T21:28:05.039255Z'
content_hash: 846aa9b4abe56c93618d33b82a9a3d53b8fb6b618c437cb3badfb5894c547c09
tags:
- mistral
- official
- research
- website
- blog-post
- magistral
- reasoning model
- mistral ai
- open source
- multilingual
status: active
asset_paths:
- original.html
source_id: mistral-research
source_pipeline_id: mistral-research
external_key: https://mistral.ai/news/magistral
canonical_url: https://mistral.ai/news/magistral
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:08:53.808892Z'
short_summary: Mistral AI announced Magistral, the first reasoning model by Mistral AI, designed to excel in domain-specific, transparent, and multilingual reasoning. Magistral is released in two variants, Magistral Small and Magistral Medium, offering various applications from scientific simulation to enterprise decision-making.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-08T13:57:49.633188Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 14fe13c18c966cdaa7240035e3ba41aa874f3400f031f067fcaf2062d1236bae
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
Stands to reason.
Magistral
Announcing Magistral — the first reasoning model by Mistral AI — excelling in domain-specific, transparent, and multilingual reasoning.
The best human thinking isn’t linear — it weaves through logic, insight, uncertainty, and discovery. Reasoning language models have enabled us to augment and delegate complex thinking and deep understanding to AI, improving our ability to work through problems requiring precise, step-by-step deliberation and analysis.
But this space is still nascent. Lack of specialized depth needed for domain-specific problems, limited transparency, and inconsistent reasoning in the desired language — are just some of the known limitations of early thinking models.
Today, we’re excited to announce our latest contribution to AI research with Magistral — our first reasoning model. Released in both open and enterprise versions, Magistral is designed to think things through — in ways familiar to us — while bringing expertise across professional domains, transparent reasoning that you can follow and verify, along with deep multilingual flexibility.
A one-shot physics simulation showcasing gravity, friction and collisions with Magistral Medium in Preview.
Highlights.
Magistral is a dual-release model focused on real-world reasoning and feedback-driven improvement.
-
We’re releasing the model in two variants: Magistral Small — a 24B parameter open-source version and Magistral Medium — a more powerful, enterprise version.
-
Magistral Medium scored 73.6% on AIME2024, and 90% with majority voting @64. Magistral Small scored 70.7% and 83.3% respectively.
-
Reason natively — Magistral’s chain-of-thought works across global languages and alphabets.
-
Suited for a wide range of enterprise use cases — from structured calculations and programmatic logic to decision trees and rule-based systems.
-
With the new Think mode and Flash Answers in Le Chat, you can get responses at 10x the speed compared to most competitors.
-
The release is supported by our
[latest paper](https://arxiv.org/pdf/2506.10910)covering comprehensive evaluations of Magistral, our training infrastructure, reinforcement learning algorithm, and novel observations for training reasoning models.
As we’ve open-sourced Magistral Small, we welcome the community to examine, modify and build upon its architecture and reasoning processes to further accelerate the emergence of thinking language models. Our earlier open models have already been leveraged by the community for exciting projects like [ether0](https://www.futurehouse.org/research-announcements/ether0-a-scientific-reasoning-model-for-chemistry) and [DeepHermes 3](https://huggingface.co/NousResearch/DeepHermes-3-Mistral-24B-Preview).
Purpose-built for transparent reasoning.
Magistral is fine-tuned for multi-step logic, improving interpretability and providing a traceable thought process in the user’s language, unlike general-purpose models.
We aim to iterate the model quickly starting with this release. Expect the models to constantly improve.
Multilingual dexterity.
The model excels in maintaining high-fidelity reasoning across numerous languages. Magistral is especially well-suited to reason in languages including English, French, Spanish, German, Italian, Arabic, Russian, and Simplified Chinese.
Prompt and response in Arabic with Magistral Medium in Preview in Le Chat.
10x faster reasoning with Le Chat.
With Flash Answers in Le Chat, Magistral Medium achieves up to 10x faster token throughput than most competitors. This enables real-time reasoning and user feedback, at scale.
Speed comparison of Magistral Medium in Preview in Le Chat against ChatGPT.
Versatility in application.
Magistral is ideal for general purpose use requiring longer thought processing and better accuracy than with non-reasoning LLMs. From legal research and financial forecasting to software development and creative storytelling — this model solves multi-step challenges where transparency and precision are critical.
Business strategy and operations.
Building on our flagship [models](https://mistral.ai/models), Magistral is designed for research, strategic planning, operational optimization, and data-driven decision making — whether executing risk assessment and modelling with multiple factors, or calculating optimal delivery windows under constraints.
Regulated industries and sectors.
Legal, finance, healthcare, and government professionals get traceable reasoning that meets compliance requirements. Every conclusion can be traced back through its logical steps, providing auditability for high-stakes environments with domain-specialized AI.
Systems, software, and data engineering.
Magistral enhances coding and development use cases: compared to non-reasoning models, it significantly improves project planning, backend architecture, frontend design, and data engineering through sequenced, multi-step actions involving external tools or API.
Content and communication.
Our early tests indicated that Magistral is an excellent creative companion. We highly recommend it for creative writing and storytelling, with the model capable of producing coherent or — if needed — delightfully eccentric copy.
Availability
Magistral Small is an open-weight model, and is available for self-deployment under the Apache 2.0 license. You can download it from:
-
Hugging Face:
[https://huggingface.co/mistralai/Magistral-Small-2506](https://huggingface.co/mistralai/Magistral-Small-2506)
You can try out a preview version of Magistral Medium in [Le Chat](http://chat.mistral.ai) or via API on [La Plateforme](http://console.mistral.ai).
Magistral Medium is also available on Amazon SageMaker, and soon on IBM WatsonX, Azure AI and Google Cloud Marketplace.
BTW, we’re hiring!
Magistral represents a significant contribution by Mistral AI to the open source community, with input from seasoned experts and interns. And we’re keen to grow our family to further shape future AI innovation.
If you’re interested in joining us on our mission to democratize artificial intelligence, we welcome your applications to [join our team](https://mistral.ai/careers)!
