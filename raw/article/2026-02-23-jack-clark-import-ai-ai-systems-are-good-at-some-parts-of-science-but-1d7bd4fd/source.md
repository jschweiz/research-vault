---
id: 2026-02-23-jack-clark-import-ai-ai-systems-are-good-at-some-parts-of-science-but-1d7bd4fd
kind: article
title: AI systems are good at some parts of science, but their capabilities are very unevenly distributed
source_url: https://drive.google.com/file/d/1BV5UtmBRdpbQoz9jC1AuUF8WUTRQMqK_/view
source_name: Import AI
authors: []
published_at: '2026-02-23T13:31:18Z'
ingested_at: '2026-04-09T20:16:29.891497Z'
content_hash: 1bbc8bd47c092dd8f7484e0d4b7abc970d3189578f7eade3b7f8eabfd7522bce
identity_hash: 577fd979f60c35ce32797bbc2e086a3b9239566946c0b4dc50de8516dbf97b66
tags:
- newsletter
- ai
- analysis
- policy
- website
- article
- science
- labbench2
- biology
- retrieval
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/23/import-ai-446-nuclear-llms-chinas-big-ai-benchmark-measurement-and-ai-policy::story::4:https://drive.google.com/file/d/1BV5UtmBRdpbQoz9jC1AuUF8WUTRQMqK_/view
canonical_url: https://drive.google.com/file/d/1BV5UtmBRdpbQoz9jC1AuUF8WUTRQMqK_/view
doc_role: derived
parent_id: 2026-02-23-jack-clark-import-ai-import-ai-446-nuclear-llms-chinas-big-ai-benchma-74d04bde
index_visibility: visible
fetched_at: '2026-04-13T18:16:00.669651Z'
short_summary: AI systems show uneven capabilities in science, with notable weaknesses in tasks like cross-referencing biological databases and understanding figures, though they perform well in searching full-text papers.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:53:59.584698Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 993049cc4175c136ce5856b624ea6dd6999a69646c6f4b20584de09def455639
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: dfcc80cbc64c90bba2d84bd16753e095005d9e29e975a670b17c80f4902e119d
lightweight_score:
  relevance_score: 0.45
  source_fit_score: 0.3
  topic_fit_score: 0.75
  author_fit_score: 0.0
  evidence_fit_score: 0.9
  confidence_score: 0.95
  bucket_hint: worth_a_skim
  reason: The document is highly relevant to evaluation and reasoning in LLMs, focusing on scientific capabilities and benchmark limitations.
  evidence_quotes:
  - AI systems show uneven capabilities in science, with notable weaknesses in tasks like cross-referencing biological databases and understanding figures, though t
  - LABBench2 shows some of the holes in frontier models – no model is very good at cross-referencing multiple biological databases to come up with an answer, nor a
  - 'Areas of improvement: LABBench2 highlights a few areas where AI systems need to improve to become more useful to scientists.'
---
# AI systems are good at some parts of science, but their capabilities are very unevenly distributed

Source newsletter: Import AI 446: Nuclear LLMs; China’s big AI benchmark; measurement and AI policy
Source issue: https://jack-clark.net/2026/02/23/import-ai-446-nuclear-llms-chinas-big-ai-benchmark-measurement-and-ai-policy
Published At: 2026-02-23T13:31:18+00:00
Canonical URL: https://drive.google.com/file/d/1BV5UtmBRdpbQoz9jC1AuUF8WUTRQMqK_/view

## Newsletter Context

…LABBench2 says it’ll be a while till AI has well rounded scientific skills… Researchers with AI science startup Edison Scientific, the University of California at Berkeley, FutureHouse, and the Broad Institute have built and released LABBench2, a test to evaluate how well AI systems can support and accelerate science.

LABBench2 consists of 1,900 tasks “spanning literature understanding and retrieval, data access, protocol troubleshooting, molecular biology assistance, and experiment planning”.

AI systems aren’t well-rounded scientists: LABBench2 shows some of the holes in frontier models – no model is very good at cross-referencing multiple biological databases to come up with an answer, nor are models good at studying scientific figures and tables. By comparison, models are pretty good at searching over full-text patents and lab trial papers to answer questions. Generally speaking, you can improve performance on tasks by giving the models access to tools to help them deal with their deficiencies.

Areas of improvement: LABBench2 highlights a few areas where AI systems need to improve to become more useful to scientists. These include:

- Retrieval and localization abilities ; “the largest performance drops arise when models must (i) identify the correct source, and then (ii) localize a specific figure/table/supplemental information within a long document.”

- Faithful handling of exact inputs; “even when the required operation is conceptually straight-forward, correctness depends on exact string-level fidelity and using tools correctly. This is a well-known error source, and human experts have built many purpose-built tools to deal with things like faithful DNA sequence manipulation within complex protocols.”

- Developing better scientific ‘taste’; one component of LABBench2, SourceQuality, challenges AI systems to “surface the most epistemically salient reason a study is inappropriate for a research question”. AI systems are still not very good at this.

Why this matters – for AI to truly change the world, it needs to do stuff in the physical world: Benchmarks like LABBench2 will help us figure out when AI is able to effectively jump from manipulating bits to manipulating atoms – and once the realm of atoms becomes as intuitive for it to deal with as the digital world, we’ll likely see a vast growth in economic and scientific activity attributable to AI. Read the research paper: LABBench2: An Improved Benchmark for AI Systems Performing Biology Research (PDF) . Find out more at the website (official LABBench2 website) . Get the benchmark here (LABBench2, GitHub) .
