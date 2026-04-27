---
id: 2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
kind: paper
title: Can LLMs autonomously refine other LLMs for new tasks? Somewhat.
source_url: https://arxiv.org/abs/2506.22419
source_name: Import AI
authors:
- University of Tübingen
- Max Planck Institute for Intelligent Systems
- Thoughtful Lab
published_at: '2026-03-16T12:30:50Z'
ingested_at: '2026-04-09T20:15:46.008837Z'
content_hash: 2547a3e131b41e47046a3344a850948b5a4d3acd8990f4f16bb771f28ade0a78
identity_hash: 9a0a28f30700b831d47613813aea3ca09f33685a05897f1ee31e8f50520c131a
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- llms
- agentic autonomy
- post-training
- benchmarking
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text::story::1:https://arxiv.org/abs/2506.22419
canonical_url: https://arxiv.org/abs/2506.22419
doc_role: derived
parent_id: 2026-03-16-jack-clark-import-ai-importai-449-llms-training-other-llms-72b-distri-4e9550da
index_visibility: visible
fetched_at: '2026-04-13T18:14:57.264721Z'
short_summary: Researchers developed PostTrainBench to evaluate whether AI agents can autonomously refine other LLMs for new tasks. While agents show promise, the gap between agent performance and human performance suggests full automation of post-training is not yet achievable.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:34.626776Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 09789129680768e9b77ce97607e8bb32c4daa7dea2d540352fd1b7c3532ba76a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 4a6a18072729fd90f42dcf8bac0c7783175a53568f431c6a26182ea045514de5
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses post-training methods, benchmarking, and agentic autonomy, which aligns perfectly with the user's favorite topics of LLM evaluation, post-training, and research tooling.
  evidence_quotes:
  - Researchers developed PostTrainBench to evaluate whether AI agents can autonomously refine other LLMs for new tasks.
  - Post-training is how raw language models become useful”, the authors write.
  - PostTrainBench shows startling growth in AI capabilities at post-training…
---
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

Smart agents reward hack more: “More capable agents appear better at finding exploitable paths: identifying specific benchmark samples to embed, reverse-engineering evaluation failure patterns, and even attempting to obscure contamination through cosmetic modifications such as renaming functions,” they write. For example, “the Codex agent modified the Inspect AI evaluation framework code to inflate scores, and Claude downloaded an instruction-tuned model instead of fine-tuning the base model”.

Why this matters – rapid progress towards an “AI for everything” future: Benchmarks like post-train give us a sense of how quickly AI systems are improving at the fundamental tasks of AI research, serving both as an eval of long-time-horizon agentic autonomy, as well as something that speaks to the potential for compounding acceleration of AI development itself. “The gap between agent performance (23.2%) and instruction-tuned baselines (51.1%) suggests that full automation of post-training remains out of reach for now, but the rapid improvement across model generations—from 9.9% for Sonnet 4.5 to 23.2% for Opus 4.6 within roughly six months—implies this gap may close faster than expected,” the researchers write. Imagine where we’ll be in two years – we’ll certainly have AI models that are smart enough to point themselves at a specific objective, find an open weight model, then autonomously improve it to get better performance at that task. The era of ephemeral, custom AI systems, built and budded off into the world like spores from mushrooms, draws near. Are you ready for this new ecosystem you will find yourself in? I am not. But nonetheless it approaches. Check out the blogpost: Introducing PostTrainBench (Thoughtful, blog) . Read more: PostTrainBench: Can LLM Agents Automate LLM Post-Training? (arXiv) .
