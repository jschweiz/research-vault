---
id: 2025-05-21-mistral-research-devstral-mistral-ai-f4d5cce5
kind: blog-post
title: Devstral | Mistral AI
source_url: https://mistral.ai/news/devstral
source_name: Mistral Research
authors:
- Mistral AI
published_at: '2025-05-21T12:00:00Z'
ingested_at: '2026-04-07T21:28:08.275631Z'
content_hash: aac3f266e10af082d62ca22935563776336dd2824f5428ee46fe42266a49eeb5
tags:
- mistral
- official
- research
- website
- blog-post
- agentic llm
- software engineering
- llm
- github issues
- performance
status: active
asset_paths:
- original.html
source_id: mistral-research
source_pipeline_id: mistral-research
external_key: https://mistral.ai/news/devstral
canonical_url: https://mistral.ai/news/devstral
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:09:00.117398Z'
short_summary: Devstral is an agentic LLM designed for software engineering tasks, trained to solve real GitHub issues and outperforming open-source models on SWE-Bench. It is lightweight enough for local deployment and suitable for agentic coding in enterprise settings.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:16:24.654329Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 40a964b5b755b6523460d8dd0f92263897f491d5dfa77f4e87caec89ced1e033
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: af55e7594ba4da02f958987693dad0935e53df276e98b55069d13057215d71b8
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 1.0
  topic_fit_score: 1.0
  author_fit_score: 1.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses agentic LLMs and software engineering, which aligns perfectly with the user's favorite topics and authors.
  evidence_quotes:
  - Devstral is an agentic LLM designed for software engineering tasks, trained to solve real GitHub issues and outperforming open-source models on SWE-Bench.
  - 'Devstral is trained to solve real GitHub issues; it runs over code agent scaffolds such as OpenHands or SWE-Agent, which define the interface between the model '
  - When evaluated under the same test scaffold (OpenHands, provided by [All Hands AI](https://www.all-hands.dev/) 🙌), Devstral exceeds far larger models such as De
---
Today we introduce Devstral, our agentic LLM for software engineering tasks. Devstral is built under a collaboration between Mistral AI and [All Hands AI](https://www.all-hands.dev/) 🙌, and outperforms all open-source models on SWE-Bench Verified by a large margin. We release Devstral under the Apache 2.0 license.
Agentic LLMs for software development
While typical LLMs are excellent at atomic coding tasks such as writing standalone functions or code completion, they currently struggle to solve real-world software engineering problems. Real-world development requires contextualising code within a large codebase, identifying relationships between disparate components, and identifying subtle bugs in intricate functions.
Devstral is designed to tackle this problem. Devstral is trained to solve real GitHub issues; it runs over code agent scaffolds such as OpenHands or SWE-Agent, which define the interface between the model and the test cases. Here, we show Devstral’s performance on the popular SWE-Bench Verified benchmark, a dataset of 500 real-world GitHub issues which have been manually screened for correctness.
Devstral achieves a score of 46.8% on SWE-Bench Verified, outperforming prior open-source SoTA models by more than 6% points. When evaluated under the same test scaffold (OpenHands, provided by [All Hands AI](https://www.all-hands.dev/) 🙌), Devstral exceeds far larger models such as Deepseek-V3-0324 (671B) and Qwen3 232B-A22B.
In the table below, we also compare Devstral to closed and open models evaluated under any scaffold (including ones custom for the model). Here, we find that Devstral achieves substantially better performance than a number of closed-source alternatives. For example, Devstral surpasses the recent GPT-4.1-mini by over 20%.
Versatile: local deployment ↔️ enterprise use ↔️ copilots
Devstral is light enough to run on a single RTX 4090 or a Mac with 32GB RAM, making it an ideal choice for local deployment and on-device use. Coding platforms such as [OpenHands](https://github.com/All-Hands-AI/OpenHands) can allow the model to interact with local codebases and provide fast resolution to issues. To try it yourself, view the [documentation](https://docs.all-hands.dev/modules/usage/llms/local-llms) or [tutorial video](https://www.youtube.com/watch?v=oV9tAkS2Xic).
The performance of the model also makes it a suitable choice for agentic coding on privacy-sensitive repositories in enterprises, especially ones subject to stringent security and compliance requirements.
Finally, if you’re building or using an agentic coding IDE, plugin, or environment, Devstral is a great choice to add to your model selector.
Availability
We release this model for free under an Apache 2.0 license for the community to build on, customize, and accelerate autonomous software development. To try it for yourself, head over to our [model card](https://huggingface.co/mistralai/Devstral-Small-2505).
The model is also available on our API under the name devstral-small-2505 at the same price as Mistral Small 3.1: $0.1/M input tokens and $0.3/M output tokens.
Should you choose to self-deploy, you can download the model on [HuggingFace](https://huggingface.co/mistralai/Devstral-Small-2505), [Ollama](https://ollama.com/library/devstral), [Kaggle](https://www.kaggle.com/models/mistral-ai/devstral-small-2505), [Unsloth](https://docs.unsloth.ai/basics/devstral), [LM Studio](https://lmstudio.ai/model/devstral-small-2505-MLX) starting today.
For enterprise deployments that require fine-tuning on private codebases, or higher-fidelity customization such as continued pre-training or distilling Devstral’s capabilities into other models, please [contact us](https://mistral.ai/contact) to connect with our applied AI team.
What’s next
Devstral is a research preview and we welcome feedback! We’re hard at work building a larger agentic coding model that will be available in the coming weeks.
Interested in discussing how we can help your team put Devstral to use, and about our portfolio of models, products and solutions? [Contact us](https://mistral.ai/contact) and we’ll be happy to help.
