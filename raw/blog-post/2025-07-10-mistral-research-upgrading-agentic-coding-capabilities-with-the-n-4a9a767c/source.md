---
id: 2025-07-10-mistral-research-upgrading-agentic-coding-capabilities-with-the-n-4a9a767c
kind: blog-post
title: Upgrading agentic coding capabilities with the new Devstral models | Mistral AI
source_url: https://mistral.ai/news/devstral-2507
source_name: Mistral Research
authors:
- Mistral AI
- All Hands AI
published_at: '2025-07-10T16:00:00Z'
ingested_at: '2026-04-09T12:04:37.421685Z'
content_hash: 1a4863c5d8fb04e806f36f11b565c72690bcb88a20366ccac5c257bdcdaed5b1
identity_hash: d29104b8f4845c5548efc2cefad43a47b0bf2555e89b3cc2c075ebe1a2945c68
tags:
- mistral
- official
- research
- website
- blog-post
- devstral
- coding
- models
- mistral ai
- agentic
status: active
asset_paths:
- original.html
source_id: mistral-research
source_pipeline_id: mistral-research
external_key: https://mistral.ai/news/devstral-2507
canonical_url: https://mistral.ai/news/devstral-2507
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:04:37.421689Z'
short_summary: Mistral AI and All Hands AI released the Devstral models, including Devstral Small 1.1 and Medium, focusing on agentic coding capabilities. These models offer state-of-the-art performance for code agents and are available via API.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T12:22:52.567760Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 758558b12060147ccaaeb075f041318735e66742b01945a1a7ea15609725c24b
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: d84499ffe47a280bfb94accc5285120c66ce2ed80eee9031ccd62d5c3fb65266
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.9
  topic_fit_score: 1.0
  author_fit_score: 0.9
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses favorite topics like LLM models, evaluation, and agentic capabilities, and features authors from the user's preferred list.
  evidence_quotes:
  - Mistral AI and All Hands AI released the Devstral models, including Devstral Small 1.1 and Medium, focusing on agentic coding capabilities.
  - Devstral Small 1.1 achieves a score of 53.6% on SWE-Bench Verified, and sets a new state-of-the-art for open models without test-time scaling.
  - Devstral Medium is available through our public API, and offers exceptional performance at a competitive price point, making it an ideal choice for businesses a
---
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
