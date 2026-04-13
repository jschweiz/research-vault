---
id: page:2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
page_type: source-note
title: Mistral OCR | Mistral AI
aliases:
- Mistral OCR | Mistral AI
source_refs:
- 2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
backlinks:
- page:2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
- page:2025-12-17-mistral-research-introducing-mistral-ocr-3-mistral-ai-2f4f54ff
- topic:api
- topic:document-understanding
- topic:ocr
updated_at: '2026-04-09T23:08:06.157697Z'
managed: true
---
# Mistral OCR | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/mistral-ocr
- Document kind: blog-post
- Published at: 2025-03-06T17:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, ocr, document understanding, multimodal, api
- Topics: [Multimodal](../topics/multimodal.md), [Api](../topics/api.md), [Document Understanding](../topics/document-understanding.md), [Mistral](../topics/mistral.md), [Ocr](../topics/ocr.md), [Official](../topics/official.md)
- Trend score: 68.20
- Novelty score: 3.40

## Summary

Mistral OCR is an Optical Character Recognition API that excels at understanding complex documents, including images, tables, and equations, with strong multilingual capabilities. It is designed to extract content from various document types and offers features like doc-as-prompt and self-hosting options.

## Topic Map

- [Multimodal](../topics/multimodal.md)
- [Api](../topics/api.md)
- [Document Understanding](../topics/document-understanding.md)
- [Mistral](../topics/mistral.md)
- [Ocr](../topics/ocr.md)
- [Official](../topics/official.md)

## Related Research

- [Introducing Mistral OCR 3 | Mistral AI](introducing-mistral-ocr-3-mistral-ai-0ff4ac.md) (shared topics: Mistral, Ocr, Official)
- [Mistral Small 3.1 | Mistral AI](mistral-small-3-1-mistral-ai-5dc4fa.md) (shared topics: Mistral, Multimodal, Official)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Mistral, Official)
- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Mistral, Multimodal)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral, Official)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Mistral, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Throughout history, advancements in information abstraction and retrieval have driven human progress. From hieroglyphs to papyri, the printing press to digitization, each leap has made human knowledge more accessible and actionable, fueling further innovation.
Today, we’re at the precipice of the next big leap—to unlock the collective intelligence of all digitized information. Approximately [90%](https://resources.data.gov/glossary/unstructured-data/) of the world’s organizational data is stored as documents, and to harness this potential, we are introducing [Mistral OCR](https://docs.mistral.ai/capabilities/document/).
Mistral OCR is an Optical Character Recognition API that sets a new standard in document understanding. Unlike other models, Mistral OCR comprehends each element of documents—media, text, tables, equations—with unprecedented accuracy and cognition. It takes images and PDFs as input and extracts content in an ordered interleaved text and images.
As a result, Mistral OCR is an ideal model to use in combination with a RAG system taking multimodal documents (such as slides or complex PDFs) as input.
We have made Mistral OCR as the default model for document understanding across millions of users on Le Chat, and are releasing the API mistral-ocr-latest at 1000 pages / $ (and approximately double the pages per dollar with batch inference). The API is available today on our developer suite [la Plateforme](http://console.mistral.ai), and coming soon to our cloud and inference partners, as well as on-premises.
Highlights
-
State of the art understanding of complex documents
-
Natively multilingual and multimodal
-
Top-tier benchmarks
-
Fastest in its category
-
Doc-as-prompt, structured output
-
Selectively available to self-host for organizations dealing with highly sensitive or classified information
Let’s dive into each.
State of the art understanding of complex documents
Mistral OCR excels in understanding complex document elements, including interleaved imagery, mathematical expressions, tables, and advanced layouts such as LaTeX formatting. The model enables deeper understanding of rich documents such as scientific papers with charts, graphs, equations and figures.
Below is an example of the model extracting text as well as imagery from a given PDF into a markdown file. You can access the notebook [here](https://colab.research.google.com/github/mistralai/cookbook/blob/main/mistral/ocr/structured_ocr.ipynb).
Below we have side-by-side comparisons of PDFs and their respective OCR's outputs. Hover the slider to switch between input and output.
Top-tier benchmarks
Mistral OCR has consistently outperformed other leading OCR models in rigorous benchmark tests. Its superior accuracy across multiple aspects of document analysis is illustrated below. We extract embedded images from documents along with text. The other LLMs compared below, do not have that capability. For a fair comparison, we evaluate them on our internal “text-only” test-set containing various publication papers, and PDFs from the web; below:
| Model | Overall | Math | Multilingual | Scanned | Tables |
|---|---|---|---|---|---|
| Google Document AI | 83.42 | 80.29 | 86.42 | 92.77 | 78.16 |
| Azure OCR | 89.52 | 85.72 | 87.52 | 94.65 | 89.52 |
| Gemini-1.5-Flash-002 | 90.23 | 89.11 | 86.76 | 94.87 | 90.48 |
| Gemini-1.5-Pro-002 | 89.92 | 88.48 | 86.33 | 96.15 | 89.71 |
| Gemini-2.0-Flash-001 | 88.69 | 84.18 | 85.80 | 95.11 | 91.46 |
| GPT-4o-2024-11-20 | 89.77 | 87.55 | 86.00 | 94.58 | 91.70 |
| Mistral OCR 2503 | 94.89 | 94.29 | 89.55 | 98.96 | 96.12 |
Natively multilingual
Since Mistral’s founding, we have aspired to serve the world with our models, and consequently strived for multilingual capabilities across our offerings. Mistral OCR takes this to a new level, being able to parse, understand, and transcribe thousands of scripts, fonts, and languages across all continents. This versatility is crucial for both global organizations that handle documents
