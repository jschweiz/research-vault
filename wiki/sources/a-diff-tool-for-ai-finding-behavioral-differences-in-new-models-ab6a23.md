---
id: page:2026-03-13-anthropic-research-a-diff-tool-for-ai-finding-behavioral-difference-21425385
page_type: source-note
title: 'A “diff” tool for AI: Finding behavioral differences in new models'
aliases:
- 'A “diff” tool for AI: Finding behavioral differences in new models'
source_refs:
- 2026-03-13-anthropic-research-a-diff-tool-for-ai-finding-behavioral-difference-21425385
backlinks:
- page:2026-03-24-anthropic-research-anthropic-economic-index-report-learning-curves-490c7dff
- topic:ai-finding
- topic:ai-finding-behavioral
- topic:evaluations
updated_at: '2026-04-09T12:15:42.076681Z'
managed: true
---
# A “diff” tool for AI: Finding behavioral differences in new models

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/diff-tool
- Document kind: blog-post
- Published at: 2026-03-13T00:00:00+00:00
- Tags: anthropic, official, research, website, blog-post
- Topics: [Anthropic](../topics/anthropic.md), [Official](../topics/official.md), [Website](../topics/website.md), [Evaluations](../topics/evaluations.md), [Ai Finding](../topics/ai-finding.md), [Ai Finding Behavioral](../topics/ai-finding-behavioral.md)
- Trend score: 56.46
- Novelty score: 2.00

## Topic Map

- [Anthropic](../topics/anthropic.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Evaluations](../topics/evaluations.md)
- [Ai Finding](../topics/ai-finding.md)
- [Ai Finding Behavioral](../topics/ai-finding-behavioral.md)

## Related Research

- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-9e1ca2.md) (shared topics: Anthropic, Official, Website)
- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-147fc4.md) (shared topics: Anthropic, Official, Website)
- [Anthropic Economic Index report: Learning curves](anthropic-economic-index-report-learning-curves-7597c7.md) (shared topics: Anthropic, Official, Website)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Evaluations, Official, Website)
- [Vibe physics: The AI grad student](vibe-physics-the-ai-grad-student-1b7b0a.md) (shared topics: Anthropic, Official, Website)
- [Long-running Claude for scientific computing](long-running-claude-for-scientific-computing-b8d3ec.md) (shared topics: Anthropic, Official, Website)

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
