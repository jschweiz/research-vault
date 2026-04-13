---
id: page:2026-02-23-jack-clark-import-ai-ai-systems-are-good-at-some-parts-of-science-but-1d7bd4fd
page_type: source-note
title: AI systems are good at some parts of science, but their capabilities are very unevenly distributed
aliases:
- AI systems are good at some parts of science, but their capabilities are very unevenly distributed
source_refs:
- 2026-02-23-jack-clark-import-ai-ai-systems-are-good-at-some-parts-of-science-but-1d7bd4fd
backlinks:
- topic:biology
- topic:labbench2
- topic:science
- topic:search
updated_at: '2026-04-09T23:10:02.843587Z'
managed: true
---
# AI systems are good at some parts of science, but their capabilities are very unevenly distributed

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://drive.google.com/file/d/1BV5UtmBRdpbQoz9jC1AuUF8WUTRQMqK_/view
- Document kind: article
- Published at: 2026-02-23T13:31:18+00:00
- Tags: newsletter, ai, analysis, policy, website, article, science, labbench2, biology, retrieval, sub-document
- Topics: [Search](../topics/search.md), [Biology](../topics/biology.md), [Labbench2](../topics/labbench2.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Science](../topics/science.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

AI systems have uneven scientific capabilities, showing weaknesses in areas like cross-referencing biological data and understanding scientific figures. Improvements are needed in retrieval, handling exact inputs, and developing scientific 'taste' for AI to be more useful to scientists.

## Topic Map

- [Search](../topics/search.md)
- [Biology](../topics/biology.md)
- [Labbench2](../topics/labbench2.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Science](../topics/science.md)

## Related Research

- [OpenAI #16: A History and a Proposal](openai-16-a-history-and-a-proposal-a6e162.md) (shared topics: Newsletter, Policy)
- [Why Your RAG System Fails Complex Questions? (And How Structure Fixes Everything)](why-your-rag-system-fails-complex-questions-and-how-structure-fi-c23a71.md) (shared topics: Newsletter, Search)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy)
- [Startups that adopt AI for internal use are more successful than those that don’t](startups-that-adopt-ai-for-internal-use-are-more-successful-than-b0b397.md) (shared topics: Newsletter, Policy)
- [MIT: A rising tide of automation is going to make good enough AI for most text-based tasks by 2029](mit-a-rising-tide-of-automation-is-going-to-make-good-enough-ai--3c3617.md) (shared topics: Newsletter, Policy)
- [Major forecasting study identifies a big paradox: people think we’ll get smarter machines but the impact on GDP growth will be minor](major-forecasting-study-identifies-a-big-paradox-people-think-we-ceb6a1.md) (shared topics: Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
