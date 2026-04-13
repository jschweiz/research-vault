---
id: page:undated-the-batch-research-recursive-language-models-offer-path-to-aramatic-5b60cd95
page_type: source-note
title: Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window
aliases:
- Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window
source_refs:
- undated-the-batch-research-recursive-language-models-offer-path-to-aramatic-5b60cd95
backlinks:
- page:2026-02-27-the-batch-research-stanford-and-together-ai-researchers-chart-edge--37b43f41
- page:2026-03-06-the-batch-research-nano-banana-2-aka-gemini-3-1-flash-image-makes-e-edbe5d36
- page:2026-03-20-the-batch-research-deepseek-made-upcoming-4-0-model-available-for-p-8f8c21d6
- page:2026-03-27-the-batch-research-nvidias-open-nemotron-3-super-120b-a12b-model-se-7cf0f41a
- page:2026-04-03-the-batch-research-test-time-training-end-to-end-ttt-e2e-retrains-m-87b314e7
- page:undated-the-batch-research-alibabas-latest-flagship-models-are-open-weights-2ff46fcf
- page:undated-the-batch-research-claude-codes-source-code-leaked-exposing-potenti-0c9adaf3
- page:undated-the-batch-research-inside-feature-auto-encoder-a-diffusion-image-ge-ac0c194f
- topic:deep-learning
- topic:deeplearning-ai
- topic:language-models
- topic:long-context
- topic:recursive-language-models
updated_at: '2026-04-09T23:10:03.782341Z'
managed: true
---
# Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/recursive-language-models-offer-path-to-aramatically-expand-beyond-the-context-window
- Document kind: blog-post
- Published at: 2026-03-27T07:07:03-07:00
- Authors: Alex L. Zhang, Tim Kraska, Omar Khattab
- Tags: deeplearning-ai, official, research, website, blog-post, language models, context window, recursive models, deep learning, recursive language models
- Topics: [Long Context](../topics/long-context.md), [Deep Learning](../topics/deep-learning.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Language Models](../topics/language-models.md), [Official](../topics/official.md), [Recursive Language Models](../topics/recursive-language-models.md)
- Trend score: 68.20
- Novelty score: 3.60

## Summary

Researchers developed Recursive Language Models (RLMs) that process long prompts by offloading context to an external environment and managing it programmatically. This method allows models to maintain high precision when reasoning over extremely long documents.

## Topic Map

- [Long Context](../topics/long-context.md)
- [Deep Learning](../topics/deep-learning.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Language Models](../topics/language-models.md)
- [Official](../topics/official.md)
- [Recursive Language Models](../topics/recursive-language-models.md)

## Related Research

- [Nvidia’s Open Nemotron 3 Super 120B-A12B Model Sets New Paces In Its Class](nvidias-open-nemotron-3-super-120b-a12b-model-sets-new-paces-in--503103.md) (shared topics: Deep Learning, Deeplearning Ai, Official)
- [Alibaba’s Latest Flagship Qwen3.5 Models Are Open-Weights MoE Performers In Sizes from Less than 1B Parameters](alibabas-latest-flagship-qwen3-5-models-are-open-weights-moe-per-be882e.md) (shared topics: Deep Learning, Deeplearning Ai, Official)
- [Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs](test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to--b1f1bd.md) (shared topics: Deeplearning Ai, Official)
- [Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs](google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30--7835fb.md) (shared topics: Deeplearning Ai, Official)
- [Claude Code’s Source Code Leaked, Exposing Potential Future Features Kairos and autoDream](claude-codes-source-code-leaked-exposing-potential-future-featur-2d1053.md) (shared topics: Deeplearning Ai, Official)
- [Grok Imagine 1.0 Sharply Cuts Costs for High-Quality Video Generation](grok-imagine-1-0-sharply-cuts-costs-for-high-quality-video-gener-bc473a.md) (shared topics: Deeplearning Ai, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

When processing long contexts, large language models often lose track of details or devolve into nonsense. Researchers reduced these effects by managing context externally.
What’s new: MIT’s Alex L. Zhang, Tim Kraska, and Omar Khattab developed [Recursive Language Models](https://arxiv.org/abs/2512.24601?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz) (RLMs) that process long prompts encountered in books, web searches, and codebases by offloading prompts to an external environment and managing them programmatically.
Key insight: A language model can process long inputs, including inputs larger than its context window, by treating input text as a persistent variable in an external programming environment. The model can write code to fetch only the necessary chunks of text. For example, it can look for keywords and retrieve the paragraphs that surround them. Writing code Iteratively enables the model to break down long-context tasks into sub-tasks before approaching the tasks as a whole.
How it works: RLMs read and manipulate tasks (a user’s prompt and associated documents) using Python code execution in a simple read-evaluate-print loop (REPL) environment. The tasks involved analyzing, understanding, or retrieving details from long documents. The model generated a program that invoked new instances of itself, or submodels, to handle each subtask and fed each instance’s output back into the root model.
- The authors built RLM systems based on Qwen3-8B (which has a 32,768-token context window), GPT-5 (400,000-token context window), and Qwen3-Coder-480B (256,000-token context window). Each system comprised a model and a custom agentic framework that read and wrote to a Python environment and called submodels.
- The RLM systems loaded task data into a Python interpreter as a variable rather than feeding it directly into the model.
- A system prompt instructed the root model to generate Python code to interact with the REPL environment and address stored tasks. For example, the model inspected the length of a prompt, found keywords, split it into logical chunks (like chapters or sections), and called a different submodel to answer questions about each chunk.
- Each submodel processed its chunk according to the root model’s instructions or questions and passed its results back to the root model.
- The system stored the submodels’ outputs as variables. The root model used these intermediate results to construct its final output.
Results: The authors compared RLMs based on Qwen3-8B, GPT-5 with medium reasoning, and Qwen3-Coder-480B to the original models using using benchmarks that involve retrieval and reasoning over documents up to 1 million tokens long. They also compared the RLMs to CodeAct agents with retrieval tools and custom agents that compacted or summarized context. The RLMs significantly outperformed both the stock models and other agentic strategies on tasks that require understanding of multiple documents, up to 11 million tokens total.
- On
[BrowseComp+](https://arxiv.org/abs/2508.06600?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz), a question-answering benchmark that requires reasoning over multiple documents, the RLM-GPT-5 (91.3 percent accuracy) outperformed GPT-5, which ran into context length limitations and was unable to produce an answer. It also outperformed the summary agent that used GPT-5 (70.5 percent accuracy). Similarly, RLM-Qwen3-Coder-480B (44.7 percent accuracy) outperformed Qwen3-Coder-480B with a summary agent (38.0 percent accuracy). RLM-Qwen3-8B (14 percent accuracy) outperformed Qwen3-8B (0 percent accuracy.) - The authors tested the models on OOLONG-PAIRS, a version of the
[OOLONG](https://arxiv.org/abs/2511.02817?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq6
