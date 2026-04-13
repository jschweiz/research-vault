---
id: page:2026-03-13-anthropic-research-a-diff-tool-for-ai-finding-behavioral-difference-21425385
page_type: source-note
title: 'A “diff” tool for AI: Finding behavioral differences in new models'
aliases:
- 'A “diff” tool for AI: Finding behavioral differences in new models'
source_refs:
- 2026-03-13-anthropic-research-a-diff-tool-for-ai-finding-behavioral-difference-21425385
backlinks:
- page:2025-02-03-anthropic-research-constitutional-classifiers-defending-against-uni-bb6ac706
- topic:ai-safety
- topic:alignment
- topic:cross-architecture
- topic:model-auditing
- topic:model-diffing
updated_at: '2026-04-09T23:08:05.828170Z'
managed: true
---
# A “diff” tool for AI: Finding behavioral differences in new models

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/diff-tool
- Document kind: blog-post
- Published at: 2026-03-13T00:00:00+00:00
- Authors: Anthropic
- Tags: anthropic, official, research, website, blog-post, model diffing, ai safety, model auditing, cross-architecture, alignment
- Topics: [Alignment](../topics/alignment.md), [Ai Safety](../topics/ai-safety.md), [Anthropic](../topics/anthropic.md), [Cross Architecture](../topics/cross-architecture.md), [Model Auditing](../topics/model-auditing.md), [Model Diffing](../topics/model-diffing.md)
- Trend score: 104.44
- Novelty score: 4.20

## Summary

The authors propose a method called model diffing, which uses a specialized tool to compare different AI models to automatically find behavioral differences and potential risks. This approach allows researchers to identify 'unknown unknowns' and audit models by detecting features exclusive to specific architectures.

## Topic Map

- [Alignment](../topics/alignment.md)
- [Ai Safety](../topics/ai-safety.md)
- [Anthropic](../topics/anthropic.md)
- [Cross Architecture](../topics/cross-architecture.md)
- [Model Auditing](../topics/model-auditing.md)
- [Model Diffing](../topics/model-diffing.md)

## Related Research

- [Anthropic proposes model diffing to focus safety analysis on features unique to each model](anthropic-proposes-model-diffing-to-focus-safety-analysis-on-fea-9ba943.md) (shared topics: Anthropic, Model Diffing)
- [An update on our model deprecation commitments for Claude Opus 3](an-update-on-our-model-deprecation-commitments-for-claude-opus-3-857fcc.md) (shared topics: Ai Safety, Anthropic)
- [Constitutional Classifiers: Defending against universal jailbreaks](constitutional-classifiers-defending-against-universal-jailbreak-6b030e.md) (shared topics: Ai Safety, Anthropic)
- [Anthropic outlines Managed Agents system enabling reliable execution with decoupled infrastructure components](anthropic-outlines-managed-agents-system-enabling-reliable-execu-8a2e1c.md) (shared topics: Anthropic)
- [Anthropic launches Managed Agents to build and deploy agents without managing infrastructure or orchestration](anthropic-launches-managed-agents-to-build-and-deploy-agents-wit-b8b41d.md) (shared topics: Anthropic)
- [The 2-Sigma Problem: The 1:1 Tutor](the-2-sigma-problem-the-1-1-tutor-9725b7.md) (shared topics: Anthropic)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

A “diff” tool for AI: Finding behavioral differences in new models
Every time a new AI model is released, its developers run a suite of evaluations to measure its performance and safety. These tests are essential, but they are somewhat limited. Because these benchmarks are human-authored, they can only test for risks we have already conceptualized and learned to measure.
This approach to safety is inherently reactive. It’s effective at catching known problems, but by definition, it's incapable of discovering “unknown unknowns”—the novel, emergent behaviors that pose some of the most subtle risks in new models. Auditing a new model from scratch is like being handed a million lines of code and told to “find the security flaws.” It’s an almost impossible task when you don’t know what you’re looking for.
In software engineering, whenever a program is updated, developers face this exact problem of identifying a small, critical change within a vast sea of code. This is why “[diff](https://en.wikipedia.org/wiki/Diff)” tools were invented. No programmer would ever audit a million lines from scratch to approve an update; instead, they review only the 50 lines that have actually changed, as directed by their diff tool.
In recent years, AI safety researchers have started to apply this same principle to neural networks. This is known as [model](https://transformer-circuits.pub/2024/model-diffing/index.html) [diffing](https://transformer-circuits.pub/2024/crosscoders/index.html). Previous work has shown that model diffing is a powerful way to understand how models change during fine-tuning—for instance, to understand [chat model behavior](https://arxiv.org/pdf/2504.02922), reveal [hidden backdoors](https://transformer-circuits.pub/2024/model-diffing/index.html), or find [undesirable emergent behaviors](https://www.arxiv.org/pdf/2506.19823).
Our new [Anthropic Fellows](https://alignment.anthropic.com/2025/anthropic-fellows-program-2026/) research project extends model diffing to its most challenging and general use case: comparing models with entirely different architectures. By building a generic diff tool for AI models, we can stop searching for a needle in a haystack, and instead let the comparison automatically point us to potentially dangerous behavioral differences.
It's important to note that this method is not a silver bullet. A single diff can surface thousands of unique features (the basic units into which we decompose the model), and only a small fraction of these may correspond to meaningful behavioral risks. However, by acting as a high-recall screening tool, it allows us to identify areas in which the models may diverge.
Among the thousands of candidates our tool flagged, we've identified and validated several concepts that act like switches for specific model behaviors.1 For example, we discovered:
- A “Chinese Communist Party Alignment” feature found in the Qwen3-8B and DeepSeek-R1-0528-Qwen3-8B models. This controls pro-government censorship and propaganda in these Chinese-developed models, and is absent in the American models we compared them against.
- An “American Exceptionalism” feature found in Meta’s Llama-3.1-8B-Instruct. It controls the model’s tendency to generate assertions of US superiority, a control absent in the Chinese model it was compared against.
- A “Copyright Refusal Mechanism” feature exclusive to OpenAI’s
[GPT-OSS-20B.](http://gpt-oss-20b.it)It controls the model’s tendency to refuse to provide copyrighted material, a behavior absent in the model it was compared against.
To be clear, while our method identifies these model-exclusive features, it does not determine their origin. Such behaviors could be the result of deliberate training decisions on the part of the model developers, or they could emerge indirectly and unintentionally from the data the model was trained on. (We focused on open-source language models in this research as this was an Anthropic Fellows project.)
A bilingual dictionary for AI
