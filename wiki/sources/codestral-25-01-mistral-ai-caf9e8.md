---
id: page:2025-01-13-mistral-research-codestral-25-01-mistral-ai-b8c278ab
page_type: source-note
title: Codestral 25.01 | Mistral AI
aliases:
- Codestral 25.01 | Mistral AI
source_refs:
- 2025-01-13-mistral-research-codestral-25-01-mistral-ai-b8c278ab
backlinks:
- page:2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
- page:2025-06-10-mistral-research-magistral-mistral-ai-f37de11b
- page:2025-07-10-mistral-research-upgrading-agentic-coding-capabilities-with-the-n-4a9a767c
- page:2025-07-30-mistral-research-announcing-codestral-25-08-and-the-complete-mist-98053d11
- page:2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
- topic:ai-model
- topic:code-generation
- topic:codestral
- topic:mistral-ai
updated_at: '2026-04-09T23:08:06.179594Z'
managed: true
---
# Codestral 25.01 | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/codestral-2501
- Document kind: blog-post
- Published at: 2025-01-13T08:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, codestral, mistral ai, code generation, sota, ai model
- Topics: [Code Generation](../topics/code-generation.md), [Mistral Ai](../topics/mistral-ai.md), [Ai Model](../topics/ai-model.md), [Codestral](../topics/codestral.md), [Mistral](../topics/mistral.md), [Official](../topics/official.md)
- Trend score: 68.20
- Novelty score: 2.20

## Summary

Mistral AI released Codestral 25.01, a new coding model that is faster and more efficient than its predecessor, making it state-of-the-art for fill-in-the-middle (FIM) tasks.

## Topic Map

- [Code Generation](../topics/code-generation.md)
- [Mistral Ai](../topics/mistral-ai.md)
- [Ai Model](../topics/ai-model.md)
- [Codestral](../topics/codestral.md)
- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)

## Related Research

- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Code Generation, Mistral, Official)
- [Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI](announcing-codestral-25-08-and-the-complete-mistral-coding-stack-cdf219.md) (shared topics: Codestral, Mistral, Official)
- [Magistral | Mistral AI](magistral-mistral-ai-df7660.md) (shared topics: Mistral, Mistral Ai, Official)
- [Codestral Embed | Mistral AI](codestral-embed-mistral-ai-1a4c58.md) (shared topics: Mistral, Mistral Ai, Official)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Mistral, Official)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Mistral, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Among all the innovations in AI over the past year, code generation has arguably been the most significant. Akin to how the assembly line streamlined manufacturing and the calculator transformed mathematics, coding models represent a significant step change in software development.
Mistral AI has been at the forefront of this change with [Codestral](https://docs.mistral.ai/capabilities/code_generation/), a state of the art (SOTA) coding model released earlier this year. Lightweight, fast, and proficient in over 80 programming languages, Codestral is optimized for low-latency, high-frequency usecases and supports tasks such as fill-in-the-middle (FIM), code correction and test generation. Codestral has been used by thousands of developers as a highly capable coding companion, regularly boosting productivity several times over. And today, Codestral is getting a big upgrade.
Codestral 25.01 features a more efficient architecture and an improved tokenizer than the original, generating and completing code about 2 times faster. The model is now the clear leader for coding in its weight class, and SOTA for FIM use cases across the board.
Benchmarks
We have benchmarked the new Codestral with the leading sub-100B parameter coding models that are widely considered to be best-in-class for FIM tasks.
Overview
| Python | SQL | Average on several languages | ||||||||
| Model | Context length | HumanEval | MBPP | CruxEval | LiveCodeBench | RepoBench | Spider | CanItEdit | HumanEval (average) | HumanEvalFIM (average) |
| Codestral-2501 | 256k | 86.6% | 80.2% | 55.5% | 37.9% | 38.0% | 66.5% | 50.5% | 71.4% | 85.9% |
| Codestral-2405 22B | 32k | 81.1% | 78.2% | 51.3% | 31.5% | 34.0% | 63.5% | 50.5% | 65.6% | 82.1% |
| Codellama 70B instruct | 4k | 67.1% | 70.8% | 47.3% | 20.0% | 11.4% | 37.0% | 29.5% | 55.3% | - |
| DeepSeek Coder 33B instruct | 16k | 77.4% | 80.2% | 49.5% | 27.0% | 28.4% | 60.0% | 47.6% | 65.1% | 85.3% |
| DeepSeek Coder V2 lite | 128k | 83.5% | 83.2% | 49.7% | 28.1% | 20.0% | 72.0% | 41.0% | 65.9% | 84.1% |
Per-language
| Model | HumanEval Python | HumanEval C++ | HumanEval Java | HumanEval Javascript | HumanEval Bash | HumanEval Typescript | HumanEval C# | HumanEval (average) |
|---|---|---|---|---|---|---|---|---|
| Codestral-2501 | 86.6% | 78.9% | 72.8% | 82.6% | 43.0% | 82.4% | 53.2% | 71.4% |
| Codestral-2405 22B | 81.1% | 68.9% | 78.5% | 71.4% | 40.5% | 74.8% | 43.7% | 65.6% |
| Codellama 70B instruct | 67.1% | 56.5% | 60.8% | 62.7% | 32.3% | 61.0% | 46.8% | 55.3% |
| DeepSeek Coder 33B instruct | 77.4% | 65.8% | 73.4% | 73.3% | 39.2% | 77.4% | 49.4% | 65.1% |
| DeepSeek Coder V2 lite | 83.5% | 68.3% | 65.2% | 80.8% | 34.2% | 82.4% | 46.8% | 65.9% |
FIM (single line exact match)
| Model | HumanEvalFIM Python | HumanEvalFIM Java | HumanEvalFIM JS | HumanEvalFIM (average) |
|---|---|---|---|---|
| Codestral-2501 | 80.2% | 89.6% | 87.96% | 85.89% |
| Codestral-2405 22B | 77.0% | 83.2% | 86.08% | 82.07% |
| OpenAI FIM API* | 80.0% | 84.8% | 86.5% | 83.7% |
| DeepSeek Chat API | 78.8% | 89.2% | 85.78% | 84.63% |
| DeepSeek Coder V2 lite | 78.7% | 87.8% | 85.90% | 84.13% |
| DeepSeek Coder 33B instruct | 80.1% | 89.0% | 86.80% | 85.3% |
FIM pass@1:
| Model | HumanEvalFIM Python | HumanEvalFIM Java | HumanEvalFIM JS | HumanEvalFIM (average) |
|---|---|---|---|---|
| Codestral-2501 | 92.5% | 97.1% | 96.1% | 95.3% |
| Codestral-2405 22B | 90.2% | 90.1% | 95.0% | 91.8% |
| OpenAI FIM API* | 91.1% | 91.8% | 95.2% | 92.7% |
| DeepSeek Chat API | 91.7% | 96.1% | 95.3% | 94.4% |
* GPT 3.5 Turbo is the latest FIM API available from OpenAI
Available starting today
Codestral 25.01 is being rolled out to developers worldwide through our IDE / IDE plugin partners. You can feel the difference in response quality and speed for code completion by selecting Codestral 25.01 in their respective model selector.
For enterprise use cases, especially ones that require data and model residency, Codestral 25.01 is available to deploy locally within y
