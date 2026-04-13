---
id: 2026-03-25-alphaxiv-paper-why-does-self-distillation-sometimes-degrade-the-a681105d
kind: paper
title: Why Does Self-Distillation (Sometimes) Degrade the Reasoning Capability of LLMs?
source_url: https://www.alphaxiv.org/abs/2603.24472
source_name: alphaXiv Papers
authors:
- Jeonghye Kim
- Xufang Luo
- Minbeom Kim
- Sangmook Lee
- Dohyung Kim
- Jiwon Jeon
- Dongsheng Li
- Yuqing Yang
published_at: '2026-03-25T16:14:52Z'
ingested_at: '2026-04-09T23:35:23.461755Z'
content_hash: ae27f4852d7f553d87dfc28b21e097c6db790d44fb6ad2832a84ee0c257f170a
identity_hash: f6e52a58be56ec601da8b032e9c1a9b070abf50bfe95893bdca1a32737116c0b
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CL
- cs.LG
- domain-adaptation
- explainable-ai
- fine-tuning
- inference-optimization
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-podcast.mp3
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2603.24472
canonical_url: https://www.alphaxiv.org/abs/2603.24472
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T23:35:23.461763Z'
short_summary: Research from Microsoft Research, KAIST, and Seoul National University reveals that while self-distillation consistently shortens LLM reasoning traces, it can degrade mathematical reasoning capabilities, particularly on out-of-distribution tasks. This performance drop is linked to the suppression of "epistemic verbalization," or expressions of uncertainty, which are found to be critical for robust generalization.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:42:59.564975Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 61a3c7eed424da5cc30990c8b1aaddcee85b6a5eb23b332a711de91198a93be0
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Why Does Self-Distillation (Sometimes) Degrade the Reasoning Capability of LLMs?

## alphaXiv Summary

Research from Microsoft Research, KAIST, and Seoul National University reveals that while self-distillation consistently shortens LLM reasoning traces, it can degrade mathematical reasoning capabilities, particularly on out-of-distribution tasks. This performance drop is linked to the suppression of "epistemic verbalization," or expressions of uncertainty, which are found to be critical for robust generalization.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.24472
- Source paper: https://arxiv.org/abs/2603.24472
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.24472v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.24472v1.png
- GitHub: https://github.com/beanie00/self-distillation-analysis
- GitHub stars: 36
- Paper ID: 2603.24472
- Canonical ID: 2603.24472v1
- Paper group ID: 019d280b-ccb3-73b8-8227-1792bb4dac48
- Version ID: 019d280b-ccde-7b4a-a788-fd5a0a09deda
- Version: v1
- Version order: 1
- Published at: 2026-03-25T16:14:52+00:00
- First published at: 2026-03-25T16:14:52+00:00
- Updated at: 2026-03-26T02:49:15.187000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Jeonghye Kim
- Xufang Luo
- Minbeom Kim
- Sangmook Lee
- Dohyung Kim
- Jiwon Jeon
- Dongsheng Li
- Yuqing Yang

## Topics

- Computer Science
- cs.CL
- cs.LG
- domain-adaptation
- explainable-ai
- fine-tuning
- inference-optimization
- knowledge-distillation
- model-interpretation
- reasoning
- transformers
- uncertainty-estimation

## Metrics

- Visits (all): 2314
- Visits (last 7 days): 1236
- Total votes: 64
- Public total votes: 205
- X likes: 0

## Abstract

Self-distillation has emerged as an effective post-training paradigm for LLMs, often improving performance while shortening reasoning traces. However, in mathematical reasoning, we find that it can reduce response length while degrading performance. We trace this degradation to the suppression of epistemic verbalization - the model's expression of uncertainty during reasoning. Through controlled experiments varying conditioning context richness and task coverage, we show that conditioning the teacher on rich information suppresses uncertainty expression, enabling rapid in-domain optimization with limited task coverage but harming OOD performance, where unseen problems benefit from expressing uncertainty and adjusting accordingly. Across Qwen3-8B, DeepSeek-Distill-Qwen-7B, and Olmo3-7B-Instruct, we observe performance drops of up to 40%. Our findings highlight that exposing appropriate levels of uncertainty is crucial for robust reasoning and underscore the importance of optimizing reasoning behavior beyond merely reinforcing correct answer traces.

## Problem

- Self-distillation, a post-training method, frequently improves LLM performance and efficiency by producing shorter reasoning traces across various domains.
- Despite reducing response length, self-distillation often leads to performance degradation in mathematical reasoning tasks, contrasting with positive results in other fields.
- The underlying mechanisms for this domain-specific degradation and the role of response length reduction needed investigation.

## Method

- The study conducted controlled experiments varying the informational richness of the teacher model's conditioning context to observe its impact on response length and epistemic verbalization.
- Researchers performed supervised fine-tuning (SFT) using datasets of correct but epistemically rich versus epistemically suppressed responses to isolate the effect of reasoning style.
- They compared on-policy self-distillation (SDPO) against GRPO (Generalized Reinforcement with Policy Optimization) across different models and task coverage levels in mathematical benchmarks.

## Results

- Solution-guided generation (richer context) reduced average response length from 13,054 to 1,873 tokens and epistemic tokens from 182.5 to 8.8.
- SFT on epistemically suppressed training data degraded DeepSeek-R1-Distill-Qwen-7B's AIME24 score from 54.79 to 20.21, while SFT on epistemically rich data showed no significant change.
- On-policy SDPO frequently resulted in up to 40% performance drops on math benchmarks (e.g., AIME24) across various models (DeepSeek-R1-Distill-Qwen-7B, Qwen3-8B, OLMo-3-7B-Instruct), whereas GRPO maintained or slightly improved performance.

## Takeaways

- Richer conditioning contexts in self-distillation monotonically reduce response length and suppress epistemic verbalization (expressions of uncertainty) in LLMs.
- Suppressing epistemic verbalization during training, even with correct solutions, hinders an LLM's ability to perform robust mathematical reasoning and generalize to out-of-distribution problems.
- There exists a trade-off: self-distillation enables rapid optimization and efficiency for tasks with low coverage but becomes detrimental for broad task coverage where epistemic verbalization is crucial for generalization.

## Full Overview

Saved in `alphaxiv-overview.md` and `alphaxiv-overview.json`.

## Overview Languages

- de
- en
- es
- fr
- hi
- ja
- ko
- ru
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d280b-ccb3-73b8-8227-1792bb4dac48/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d280b-ccb3-73b8-8227-1792bb4dac48/transcript.json
- Transcript lines: 23
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/beanie00/self-distillation-analysis

## Similar Papers

- Missing Premise exacerbates Overthinking: Are Reasoning Models losing  Critical Thinking Skill? (2504.06514v2): The paper identifies and characterizes "MiP-Overthinking," a phenomenon where reasoning-focused large language models generate excessively long, redundant responses to questions with missing premises. It demonstrates that unlike general-purpose models, these specialized models often fail to abstain despite internal awareness of the missing information, challenging the effectiveness of increased inference-time computation in such scenarios.
- When Thinking Fails: The Pitfalls of Reasoning for Instruction-Following in LLMs (2505.11423v3): Researchers at Harvard and Amazon discovered that explicit Chain-of-Thought reasoning consistently reduces large language models' ability to follow instructions on two benchmarks. The study revealed this degradation stems from models neglecting simple constraints or introducing extraneous content, and an external classifier for selective reasoning proved most effective in mitigating these issues, improving performance for nearly all models.
- Beyond Semantics: The Unreasonable Effectiveness of Reasonless Intermediate Tokens (2505.13775v3): Arizona State University researchers investigated the role of intermediate tokens in transformer models, demonstrating that their effectiveness in improving reasoning task performance does not rely on semantic correctness or faithfulness to an underlying algorithm. Models trained with structurally consistent but semantically irrelevant "swapped" traces performed comparably to or better than those trained with correct traces, particularly on out-of-distribution tasks.
- Does Math Reasoning Improve General LLM Capabilities? Understanding Transferability of LLM Reasoning (2507.00432v2): This research investigates how fine-tuning methods for math reasoning affect the broader capabilities of Large Language Models (LLMs), revealing that Reinforcement Learning (RL) approaches foster superior generalization across diverse reasoning and non-reasoning tasks compared to Supervised Fine-Tuning (SFT). RL-tuned models successfully transfer math gains and preserve performance on general tasks, while SFT models often exhibit narrow specialization and degradation in other domains.
- Between Underthinking and Overthinking: An Empirical Study of Reasoning  Length and correctness in LLMs (2505.00127v1): An empirical analysis demonstrates a non-monotonic relationship between reasoning length and accuracy in Large Language Models, revealing that while longer reasoning initially improves performance, excessive length can degrade results, with incorrect responses typically being longer than correct ones across math reasoning benchmarks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
