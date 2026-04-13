---
id: page:2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
page_type: source-note
title: Codestral Embed | Mistral AI
aliases:
- Codestral Embed | Mistral AI
source_refs:
- 2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
backlinks:
- page:2025-01-13-mistral-research-codestral-25-01-mistral-ai-b8c278ab
- page:2025-06-10-mistral-research-magistral-mistral-ai-f37de11b
- page:2025-07-10-mistral-research-upgrading-agentic-coding-capabilities-with-the-n-4a9a767c
- topic:code-embedding
- topic:codestral-embed
- topic:mistral-ai
- topic:search
updated_at: '2026-04-09T23:08:06.133764Z'
managed: true
---
# Codestral Embed | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/codestral-embed
- Document kind: blog-post
- Published at: 2025-05-28T12:00:00+00:00
- Tags: mistral, official, research, website, blog-post, codestral embed, mistral ai, code embedding, retrieval, semantic search
- Topics: [Search](../topics/search.md), [Mistral Ai](../topics/mistral-ai.md), [Code Embedding](../topics/code-embedding.md), [Codestral Embed](../topics/codestral-embed.md), [Mistral](../topics/mistral.md), [Official](../topics/official.md)
- Trend score: 68.20
- Novelty score: 4.80

## Summary

Codestral Embed is a new embedding model specialized for code, designed to outperform leading code embedders in retrieval tasks. It supports various use cases like retrieval-augmented generation, semantic code search, and duplicate detection.

## Topic Map

- [Search](../topics/search.md)
- [Mistral Ai](../topics/mistral-ai.md)
- [Code Embedding](../topics/code-embedding.md)
- [Codestral Embed](../topics/codestral-embed.md)
- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)

## Related Research

- [Magistral | Mistral AI](magistral-mistral-ai-df7660.md) (shared topics: Mistral, Mistral Ai, Official)
- [Codestral 25.01 | Mistral AI](codestral-25-01-mistral-ai-caf9e8.md) (shared topics: Mistral, Mistral Ai, Official)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Mistral, Official)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral, Official)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Mistral, Official)
- [Introducing Mistral OCR 3 | Mistral AI](introducing-mistral-ocr-3-mistral-ai-0ff4ac.md) (shared topics: Mistral, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

We are excited to release Codestral Embed, our first embedding model specialized for code. It performs especially well for retrieval use cases on real-world code data.
Codestral Embed significantly outperforms leading code embedders in the market today: Voyage Code 3, Cohere Embed v4.0 and OpenAI’s large embedding model.
Codestral Embed can output embeddings with different dimensions and precisions, and the figure below illustrates the trade-offs between retrieval quality and storage costs. Codestral Embed with dimension 256 and int8 precision still performs better than any model from our competitors. The dimensions of our embeddings are ordered by relevance. For any integer target dimension n, you can choose to keep the first n dimensions for a smooth trade-off between quality and cost.
Results
Below we show the performance of Codestral Embed for several categories. The details of the benchmarks corresponding to each category can be found in the table in the “Benchmarks details” section.
SWE-Bench is based on a dataset of real-world GitHub issues and corresponding fixes, and is especially relevant for retrieval-augmented generation for coding agents. Text2Code (GitHub) contains benchmarks relevant for giving context for code completion or edition. We believe that these two categories are especially relevant to code assistants.
Use cases
Codestral Embed is optimized for high-performance code retrieval and semantic understanding. It enables a range of practical applications across development workflows, especially when working with large-scale code corpora.
1. Retrieval-augmented generation
Codestral Embed facilitates rapid and efficient context retrieval for code completion, editing, or explanation tasks. It is ideal for AI-powered software engineering in copilots or coding agent frameworks.
2. Semantic code search
Embed enables accurate search of relevant code snippets from natural language or code queries. It is suitable for use within developer tools, documentation systems, and copilots.
3. Similarity search and duplicate detection
The model’s embeddings can be used to identify near-duplicate or functionally similar code segments, even with significant lexical variation. This supports use cases such as identifying reusable code to avoid duplicates, or detecting copy-paste reuse to enforce licensing policies.
4. Semantic clustering and code analytics
Codestral Embed supports unsupervised grouping of code based on functionality or structure. This is useful for analyzing repository composition, identifying emergent architecture patterns, or feeding into automated documentation and categorization systems.
Availability
Codestral Embed is available on our API under the name `codestral-embed-2505` at a price of $0.15 per million tokens. It is also available on our [batch API](https://docs.mistral.ai/capabilities/batch/) at a 50% discount. For on-prem deployments, please [contact us](https://mistral.ai/contact) to connect with our applied AI team.
Please check our [docs](https://docs.mistral.ai/capabilities/embeddings/code_embeddings/) to get started and our [cookbook ](https://colab.research.google.com/github/mistralai/cookbook/blob/main/mistral/embeddings/code_embedding.ipynb)for examples of how to use Codestral Embed for code agent retrieval.
Chunking parameters
For retrieval use cases, while you can use the full context size of 8192 tokens, it is often more efficient to chunk your dataset. We recommend using chunks of 3000 characters with 1000 characters overlap. Larger chunks tend to adversely affect the performance of the retrieval system. Refer to [our ](https://docs.mistral.ai/guides/rag/#split-document-into-chunks)[cookbook](https://colab.research.google.com/github/mistralai/cookbook/blob/main/mistral/embeddings/code_embedding.ipynb) for more information about chunking.
Benchmark details
You can find the details of the benchmarks that we used to evaluate our model in the table below. We report the average score per categor
