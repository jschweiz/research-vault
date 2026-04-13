---
id: page:2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
page_type: source-note
title: 'Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI'
aliases:
- 'Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI'
source_refs:
- 2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
backlinks:
- page:2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
- page:2025-01-13-mistral-research-codestral-25-01-mistral-ai-b8c278ab
- page:2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
- page:2025-02-17-mistral-research-mistral-saba-mistral-ai-7649c064
- page:2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
- page:2025-05-21-mistral-research-devstral-mistral-ai-f4d5cce5
- page:2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
- page:2025-07-15-mistral-research-voxtral-mistral-ai-d4863455
- page:2025-07-30-mistral-research-announcing-codestral-25-08-and-the-complete-mist-98053d11
- page:2025-12-09-mistral-research-introducing-devstral-2-and-mistral-vibe-cli-mist-3175b131
- page:2026-02-04-mistral-research-voxtral-transcribes-at-the-speed-of-sound-mistra-4bb4537b
- topic:code-generation
- topic:formal-proof
- topic:lean-4
- topic:leanstral
- topic:mistral
updated_at: '2026-04-09T23:10:03.287921Z'
managed: true
---
# Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/leanstral
- Document kind: blog-post
- Published at: 2026-03-16T16:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, leanstral, open-source, code agent, lean 4, formal proof
- Topics: [Code Generation](../topics/code-generation.md), [Formal Proof](../topics/formal-proof.md), [Lean 4](../topics/lean-4.md), [Leanstral](../topics/leanstral.md), [Mistral](../topics/mistral.md), [Official](../topics/official.md)
- Trend score: 68.20
- Novelty score: 2.20

## Summary

Leanstral is an open-source code agent designed for Lean 4, enabling the formal proof of software implementations. It is designed to be efficient and powerful, offering competitive performance against closed-source models.

## Topic Map

- [Code Generation](../topics/code-generation.md)
- [Formal Proof](../topics/formal-proof.md)
- [Lean 4](../topics/lean-4.md)
- [Leanstral](../topics/leanstral.md)
- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)

## Related Research

- [Codestral 25.01 | Mistral AI](codestral-25-01-mistral-ai-caf9e8.md) (shared topics: Code Generation, Mistral, Official)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Mistral, Official)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Mistral, Official)
- [Introducing Mistral OCR 3 | Mistral AI](introducing-mistral-ocr-3-mistral-ai-0ff4ac.md) (shared topics: Mistral, Official)
- [Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI](introducing-devstral-2-and-mistral-vibe-cli-mistral-ai-5539ea.md) (shared topics: Mistral, Official)
- [Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI](announcing-codestral-25-08-and-the-complete-mistral-coding-stack-cdf219.md) (shared topics: Mistral, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

AI agents have proven to be highly capable tools at code generation. Yet, as we push these models to high-stakes domains, ranging from frontier research mathematics to mission-critical software, we encounter a scaling bottleneck: the human review. The time and specialized expertise required to manually verify become the primary impedance of engineering velocity.
We envision a more helpful generation of coding agents to both carry out their tasks and formally prove their implementations against strict specifications. Instead of debugging machine-generated logic, humans dictate what they want. Today, we are taking the first major step toward that vision.
Introducing Leanstral
We release Leanstral, the first open-source code agent designed for Lean 4. Lean4 is a proof assistant capable of expressing complex mathematical objects such as [perfectoid spaces](https://xenaproject.wordpress.com/2020/12/05/liquid-tensor-experiment/) and software specifications like [properties of Rust fragments](https://github.com/AeneasVerif/aeneas). Unlike existing proving systems that act as wrappers around large generalist models or focus on single math problems, Leanstral is designed to be highly efficient (with 6B active parameters) and trained for operating in realistic formal repositories.
-
Open and accessible: We release Leanstral weights under an Apache 2.0 license, in an agent mode within Mistral vibe, and through a free API endpoint. We will also release a tech report detailing our training approach, and a new evaluation suite FLTEval, to move evaluations beyond their focus on competition math.
-
Efficient and mighty: We use a highly sparse architecture for Leanstral, and optimise it for proof engineering tasks. Leveraging parallel inference with Lean as a perfect verifier, Leanstral is both performant and cost-efficient against existing closed-source competitors.
-
Upgradable via MCP: Leanstral supports arbitrary MCPs through vibe, and was specifically trained to achieve maximal performance with the frequently used lean-lsp-mcp.
Evaluation
To reflect usefulness in realistic proof engineering scenarios, we benchmark Leanstral for completing all formal proofs and correctly defining new mathematical concepts in each PR to the FLT project, instead of isolated mathematical problems. We compare Leanstral against leading coding agents (Claude Opus 4.6, Sonnet 4.6, Haiku 4.5) and open-source models (Qwen3.5 397B-A17B, Kimi-K2.5 1T-A32B, GLM5 744B-A40B).
Leanstral vs. OSS Models
Leanstral-120B-A6B demonstrates a significant efficiency advantage over its much larger open-source peers. While models like GLM5-744B-A40B and Kimi-K2.5-1T-32B struggle to scale, capping their FLTEval scores at approximately 16.6 and 20.1 respectively, Leanstral outperforms them both with just a single pass.
Even Qwen3.5-397B-A17B, the strongest OSS competitor shown, requires 4 passes to reach a score of 25.4. In contrast, Leanstral achieves a superior score of 26.3 with half that investment (pass@2) and continues to scale linearly, reaching 29.3 at the same cost level.
Leanstral vs. Claude Family
Leanstral serves as a high-value alternative to the Claude suite, offering competitive performance at a fraction of the price: Leanstral pass@2 reaches a score of 26.3, beating Sonnet by 2.6 points, while costing only $36 to run, compared to Sonnet’s $549. At pass@16, Leanstral reaches a score of 31.9, comfortably beating Sonnet by 8 points. While Claude Opus 4.6 remains the leader in quality, it carries a staggering cost of $1,650, 92 times higher than running Leanstral.
In our benchmarking, we used Mistral Vibe as the scaffold with no modifications specifically for the evaluation.
| Model | Cost ($) | Score |
|---|---|---|
| Haiku | 184 | 23.0 |
| Sonnet | 549 | 23.7 |
| Opus | 1,650 | 39.6 |
| Leanstral | 18 | 21.9 |
| Leanstral pass@2 | 36 | 26.3 |
| Leanstral pass@4 | 72 | 29.3 |
| Leanstral pass@8 | 145 | 31.0 |
| Leanstral pass@16 | 290 | 31.9 |
Case studies
Answering stac
