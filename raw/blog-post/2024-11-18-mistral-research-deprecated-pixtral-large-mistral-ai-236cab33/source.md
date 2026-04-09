---
id: 2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
kind: blog-post
title: '[Deprecated] Pixtral Large | Mistral AI'
source_url: https://mistral.ai/news/pixtral-large
source_name: Mistral Research
authors:
- Mistral AI
published_at: '2024-11-18T08:00:00Z'
ingested_at: '2026-04-09T12:04:55.754253Z'
content_hash: 536827f17a27f664251f7cced96df9575ce6e3956b7fd5d3950ef50da30534f4
identity_hash: 266d8ab0d79d8f0c5a78d34c32ecd8bb5197afb4d14f723902193799427381ed
tags:
- mistral
- official
- research
- website
- blog-post
- multimodal model
- pixtral large
- mistral large 2
- multimodal benchmarks
- vision encoder
status: active
asset_paths:
- original.html
source_id: mistral-research
source_pipeline_id: mistral-research
external_key: https://mistral.ai/news/pixtral-large
canonical_url: https://mistral.ai/news/pixtral-large
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:04:55.754257Z'
short_summary: Pixtral Large is a 124B open-weights multimodal model built on Mistral Large 2, demonstrating frontier-class performance in multimodal tasks like document understanding and mathematical reasoning.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T12:18:45.735393Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: a8f23526eb7fd1e8a618258796181dfbec6bd6e964d85d1251d5344aa1e4d2da
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 7e083791d1d7e68573012e0c40d8c2de4b9fd895d90ddcecd3ed69b51b1028b2
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 1.0
  topic_fit_score: 1.0
  author_fit_score: 1.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly discusses a new multimodal model (Pixtral Large) and its performance in reasoning and multimodal tasks, aligning perfectly with the user's favorite topics of LLM architecture, evaluation, and reasoning.
  evidence_quotes:
  - Pixtral Large is a 124B open-weights multimodal model built on top of Mistral Large 2, demonstrating frontier-class performance in multimodal tasks like documen
  - On MathVista, which evaluates complex mathematical reasoning over visual data, our model achieves 69.4%, outperforming all other models.
  - To assess reasoning capabilities over complex charts and documents, we evaluate performance using ChartQA and DocVQA, where Pixtral Large surpasses GPT-4o and G
---
Pixtral Large in short:
- Frontier-class multimodal performance
- State-of-the-art on MathVista, DocVQA, VQAv2
- Extends Mistral Large 2 without compromising text performance
- 123B multimodal decoder, 1B parameter vision encoder
- 128K context window: fits minimum of 30 high-resolution images
- Use:
Today we announce Pixtral Large, a 124B open-weights multimodal model built on top of Mistral Large 2. Pixtral Large is the second model in our multimodal family and demonstrates frontier-level image understanding. Particularly, the model is able to understand documents, charts and natural images, while maintaining the leading text-only understanding of Mistral Large 2.
The model is available under the Mistral Research License (MRL) for research and educational use; and the [Mistral Commercial License](https://mistral.ai/contact/) for experimentation, testing, and production for commercial purposes.
Performance
We evaluate Pixtral Large against frontier models on a set of standard multimodal benchmarks, through a common testing harness. On MathVista, which evaluates complex mathematical reasoning over visual data, our model achieves 69.4%, outperforming all other models. To assess reasoning capabilities over complex charts and documents, we evaluate performance using ChartQA and DocVQA, where Pixtral Large surpasses GPT-4o and Gemini-1.5 Pro.
Pixtral Large also demonstrates competitive capabilities on MM-MT-Bench, outperforming all of Claude-3.5 Sonnet (new), Gemini-1.5 Pro and GPT-4o (latest). MM-MT-Bench is an [open-source](https://github.com/mistralai/mistral-evals), judge-based evaluation intended to reflect real-world use cases of multimodal LLMs (see the [Pixtral 12B technical report](https://arxiv.org/abs/2410.07073) for details).
Finally, on the [LMSys Vision Leaderboard](https://lmarena.ai/), Pixtral Large is the best open-weights model by a substantial margin, surpassing the nearest competitor by nearly 50 ELO points. Pixtral Large also outperforms a number of proprietary models, such as GPT-4o (August '24).
Qualitative Samples
Multilingual OCR and reasoning...
Prompt:
I bought the coffee and the sausage. How much do I owe? Add a 18% tip.
Response:
To calculate the total amount you owe, including the 18% tip, follow these steps:
-
Calculate the cost of the coffee and the sausage:
- 2x Latte Macchiato: 2 * 4.50 CHF = 9.00 CHF
- 1x Schweinschnitzel: 22.00 CHF
- Total cost for coffee and sausage: 9.00 CHF + 22.00 CHF = 31.00 CHF
-
Calculate the 18% tip:
- Tip: 31.00 CHF * 0.18 = 5.58 CHF
-
Add the tip to the total cost:
- Total amount owed: 31.00 CHF + 5.58 CHF = 36.58 CHF
So, you owe a total of 36.58 CHF.
Chart understanding...
Prompt:
When did things start to go wrong for dark dragon?
Response:
The training loss for the "dark-dragon-50" model starts to exhibit significant instability around the 10,000 steps mark. There is a noticeable spike in the loss value at this point, and the instability continues with another major spike around the 20,000 steps mark. These spikes indicate that the training process for the "dark-dragon-50" model began to encounter issues starting around the 10,000 steps mark.
And more...
Prompt:
Which companies use models made by Mistral AI?
Response:
The companies that use models made by Mistral AI, as shown in the image, are:
- BNP Paribas
- Brave
- Cloudflare
- CMA CGM
- Front
One more thing...
Along with Pixtral Large, Mistral Large, our state-of-the-art text model, also gets an update. The model is available as pixtral-large-latest
on our [API](https://docs.mistral.ai/api/), as well as for self-deployment as Mistral Large 24.11 on HuggingFace under the Mistral Research License (MRL) for research, or with a [commercial license](https://mistral.ai/contact/) from Mistral AI for commercial use.
This newest model provides a significant upgrade on the previous Mistral Large 24.07, with notable improvements in long context understanding, a new system prompt, and more accurate function calling. The model is highly capable for RAG and agentic workflows, making it a suitable choice for enterprise use cases such as knowledge exploration and sharing, semantic understanding of documents, task automation, and improved customer experiences.
Mistral Large 24.11 will be available from our cloud provider partners soon, starting with Google Cloud and Microsoft Azure within a week.
