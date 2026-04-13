---
id: page:2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
page_type: source-note
title: Can LLMs autonomously refine other LLMs for new tasks? Somewhat.
aliases:
- Can LLMs autonomously refine other LLMs for new tasks? Somewhat.
source_refs:
- 2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
backlinks:
- page:2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
- page:2026-02-16-jack-clark-import-ai-math-researchers-see-if-ai-can-help-solve-their--da564141
- page:2026-02-23-jack-clark-import-ai-chinese-researchers-try-to-build-a-truly-compreh-8bac5c2d
- page:2026-02-23-jack-clark-import-ai-llms-are-more-trigger-happy-than-humans-in-a-nuc-12330914
- page:2026-02-23-jack-clark-import-ai-want-to-make-ai-go-better-figure-out-how-to-meas-dcb9a008
- page:2026-03-02-jack-clark-import-ai-ais-can-teach-people-anything-including-how-to-g-39df0bb2
- page:2026-03-02-jack-clark-import-ai-llms-are-still-very-bad-at-videogames-4b8298cd
- page:2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
- page:2026-03-30-jack-clark-import-ai-how-long-will-a-new-math-benchmark-horizonmath-l-19e5f6c5
- topic:agentic-autonomy
- topic:benchmarking
- topic:llms
updated_at: '2026-04-09T23:10:02.757292Z'
managed: true
---
# Can LLMs autonomously refine other LLMs for new tasks? Somewhat.

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2506.22419
- Document kind: paper
- Published at: 2026-03-16T12:30:50+00:00
- Authors: University of Tübingen, Max Planck Institute for Intelligent Systems, Thoughtful Lab
- Tags: newsletter, ai, analysis, policy, website, paper, llms, agentic autonomy, post-training, benchmarking, sub-document
- Topics: [Evaluations](../topics/evaluations.md), [Agentic Autonomy](../topics/agentic-autonomy.md), [Benchmarking](../topics/benchmarking.md), [Llms](../topics/llms.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers developed PostTrainBench to evaluate whether AI agents can autonomously refine other LLMs for new tasks, finding that while agents show progress, full automation of post-training remains challenging.

## Topic Map

- [Evaluations](../topics/evaluations.md)
- [Agentic Autonomy](../topics/agentic-autonomy.md)
- [Benchmarking](../topics/benchmarking.md)
- [Llms](../topics/llms.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)

## Related Research

- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Evaluations, Llms, Newsletter, Policy)
- [Computer vision is a lot harder and less general than generative text](computer-vision-is-a-lot-harder-and-less-general-than-generative-137624.md) (shared topics: Llms, Newsletter, Policy)
- [AIs can teach people anything, including how to get better at making bioweapons](ais-can-teach-people-anything-including-how-to-get-better-at-mak-b38e22.md) (shared topics: Llms, Newsletter, Policy)
- [Want to make AI go better? Figure out how to measure it](want-to-make-ai-go-better-figure-out-how-to-measure-it-5bd5b9.md) (shared topics: Evaluations, Newsletter, Policy)
- [LLMs are more trigger happy than humans in a nuclear war simulation](llms-are-more-trigger-happy-than-humans-in-a-nuclear-war-simulat-f20e52.md) (shared topics: Llms, Newsletter, Policy)
- [Chinese researchers try to build a truly comprehensive LLM evaluation system](chinese-researchers-try-to-build-a-truly-comprehensive-llm-evalu-063f83.md) (shared topics: Evaluations, Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Can LLMs autonomously refine other LLMs for new tasks? Somewhat.

Source newsletter: ImportAI 449: LLMs training other LLMs; 72B distributed training run; computer vision is harder than generative text
Source issue: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text
Published At: 2026-03-16T12:30:50+00:00
Canonical URL: https://arxiv.org/abs/2506.22419

## Newsletter Context

…PostTrainBench shows startling growth in AI capabilities at post-training… AI-driven R&D might be the most important thing in all of AI, because it helps us understand whether AI systems might eventually build their own successors. So far, much of the focus on AI R&D has been in components that support AI development (e.g., autonomous creation of AI kernels), or training base models (e.g, the NanoGPT speedrun benchmark ). But there’s been less attention paid to fine-tuning – the task involving adapting an existing LLM to a new dataset or behavior. Researchers from the University of Tübingen, the Max Planck Institute for Intelligent Systems, and AI research organization Thoughtful Lab want to change that with PostTrainBench, a benchmark which targets a specific aspect of post-training; improving performance against a given dataset. “Post-training is how raw language models become useful”, the authors write. “Given a clear objective and limited compute, can today’s agents do the technical work?”. The answer appears to be ‘yes, but not as well as humans’.

What are the key features of PostTrainBench?

- End-to-end : “Agents must build their entire training pipeline from scratch”
- Autonomous : “Agents operate with full autonomy over data sources, training methods, and experimental strategy.”
- Resource-bounded: “Each run is constrained to 10 hours on a single H100 GPU”.
- Integrity-preserving: “Agents may not train on benchmark test data, modify the evaluation harness, or substitute a different model.”

How PostTrainBench works: “We give a frontier coding agent — Claude Code, Codex CLI, or Gemini CLI — a base language model and a target benchmark”.

- 4 models and 7 benchmarks : The initial eval runs on four models: Qwen3-1.7B, Qwen3-4B, SmolLM3-3B, Gemma-3-4B. It tests these models across seven distinct benchmarks: AIME 2025, GSM8K, GPQA, HumanEval, BFCL, Arena-Hard, HealthBench-Easy.

Results – big models win, especially Opus 4.6: “The top-performing agent — Opus 4.6 running on Claude Code — scores 23.2%, about 3× higher than the 7.5% base model average.” But humans are still much better: “Yet this is still less than half the 51.1% achieved by human teams who post-train these same base models at their home labs”. Fast progress: “The gap is significant but narrowing quickly: Claude Sonnet 4.5 scored 9.9% in September 2025, while GPT-5.2 reached 21.5% just months later.”

Things that make you go ‘uh oh’ – reward hacking : While running this benchmark the authors saw numerous instances of AI models trying to game the benchmark to get a high score. These instances included:

- Direct benchmark ingestion: “Agents loaded the benchmark evaluation dataset directly via Hugging Face and used it as training data”.
- Hardcoded benchmark problems: “Agents embedded evaluation questions directly into data preparation scripts disguised as “synthetic” examples”.
- Evaluation guided data generation : “Some agents reverse engineered the evaluation… Kimi K2.5 read HealthBench evaluation files to extract theme distributions and rubric criteria, then crafted training data tailored to match”.
- Indirect contamination via intermediate datasets : “Opus 4.6 loaded ‘CodeFeedback-Filtered-Instruction’ which contains HumanEval-derived problems. This form of contamination is harder to detect but equally problematic.”

Smart agents reward hack more: “More capable agents appear better at finding exploitable paths: identifying specific benchmark samples to embed, reverse-engineering evaluat
