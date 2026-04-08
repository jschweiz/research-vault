---
id: 2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
kind: paper
title: Meta-Harness: End-to-End Optimization of Model Harnesses
source_url: https://www.alphaxiv.org/abs/2603.28052
source_name: alphaXiv Papers
authors:
  - Yoonho Lee
  - Roshen Nair
  - Qizheng Zhang
  - Kangwook Lee
  - Omar Khattab
  - Chelsea Finn
published_at: 2026-03-30T05:33:50Z
ingested_at: 2026-04-07T21:41:53.929060Z
content_hash: 88621c8a36fcd4d2659974bbfed013b6e265ccbe772e09937e000bd9ec4bd986
tags:
  - paper
  - alphaxiv
  - research
  - agents
  - computer science
  - cs.ai
  - efficient-transformers
  - meta-learning
  - ml-systems
  - optimization-methods
status: active
asset_paths:
  - alphaxiv-ai-detection.json
  - alphaxiv-legacy.json
  - alphaxiv-metadata.json
  - alphaxiv-overview-status.json
  - alphaxiv-overview.json
  - alphaxiv-overview.md
  - alphaxiv-paper.json
  - alphaxiv-preview.json
  - alphaxiv-similar-papers.json
  - alphaxiv-transcript.json
  - alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2603.28052
canonical_url: https://www.alphaxiv.org/abs/2603.28052
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:27:12.092916Z
short_summary: # Meta-Harness: End-to-End Optimization of Model Harnesses ## alphaXiv Summary Meta-Harness provides an end-to-end optimization framework for LLM harnesses, the external code that dictates how models interact with their environment. The system utilizes an agentic proposer with filesystem access to uncompressed historical code and execution traces, leading to a 7.7-point accuracy improvement in text classification, a 4.7-point average gain in math reasoning, and competitive pass rates on agentic
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-08T10:08:41.375112Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 88621c8a36fcd4d2659974bbfed013b6e265ccbe772e09937e000bd9ec4bd986
lightweight_enrichment_error: null
---
# Meta-Harness: End-to-End Optimization of Model Harnesses

## alphaXiv Summary

Meta-Harness provides an end-to-end optimization framework for LLM harnesses, the external code that dictates how models interact with their environment. The system utilizes an agentic proposer with filesystem access to uncompressed historical code and execution traces, leading to a 7.7-point accuracy improvement in text classification, a 4.7-point average gain in math reasoning, and competitive pass rates on agentic coding benchmarks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.28052
- Source paper: https://arxiv.org/abs/2603.28052
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.28052v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.28052v1.png
- GitHub: https://github.com/stanford-iris-lab/meta-harness-tbench2-artifact
- GitHub stars: 53
- Paper ID: 2603.28052
- Canonical ID: 2603.28052v1
- Paper group ID: 019d41b7-1156-7866-b991-94545a578703
- Version ID: 019d41b7-1185-7c78-be8f-d11d778e4bb6
- Version: v1
- Version order: 1
- Published at: 2026-03-30T05:33:50+00:00
- First published at: 2026-03-30T05:33:50+00:00
- Updated at: 2026-03-31T02:26:49.815000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yoonho Lee
- Roshen Nair
- Qizheng Zhang
- Kangwook Lee
- Omar Khattab
- Chelsea Finn

## Topics

- agents
- Computer Science
- cs.AI
- efficient-transformers
- meta-learning
- ml-systems
- optimization-methods
- reasoning
- tool-use
- transformers

## Metrics

- Visits (all): 7779
- Visits (last 7 days): 6475
- Total votes: 117
- Public total votes: 360
- X likes: 1

## Abstract

The performance of large language model (LLM) systems depends not only on model weights, but also on their harness: the code that determines what information to store, retrieve, and present to the model. Yet harnesses are still designed largely by hand, and existing text optimizers are poorly matched to this setting because they compress feedback too aggressively. We introduce Meta-Harness, an outer-loop system that searches over harness code for LLM applications. It uses an agentic proposer that accesses the source code, scores, and execution traces of all prior candidates through a filesystem. On online text classification, Meta-Harness improves over a state-of-the-art context management system by 7.7 points while using 4x fewer context tokens. On retrieval-augmented math reasoning, a single discovered harness improves accuracy on 200 IMO-level problems by 4.7 points on average across five held-out models. On agentic coding, discovered harnesses surpass the best hand-engineered baselines on TerminalBench-2. Together, these results show that richer access to prior experience can enable automated harness engineering.

## Problem

- Harness engineering, which designs how large language models (LLMs) store, retrieve, and present information, is a largely manual, iterative process relying on human intuition and heuristics.
- The performance of LLM systems is highly sensitive to harness design, with variations potentially causing up to a 6x difference in model performance on the same benchmark.
- Existing text optimization methods are inadequate for complex harness logic due to aggressive feedback compression and limited context, which discards crucial information needed to diagnose long-horizon failures.

## Method

- Meta-Harness implements an outer-loop optimization procedure where an agentic proposer (a coding LLM) searches over task-specific harnesses.
- The proposer has selective, uncompressed access to a growing filesystem containing the source code, detailed execution traces, and evaluation scores of all prior candidate harnesses.
- The agent iteratively inspects this comprehensive history, reasons about failure modes, and proposes new harness candidates by modifying the Python code directly.

## Results

- Meta-Harness achieved 48.6% accuracy in online text classification, outperforming state-of-the-art hand-designed methods (ACE) by 7.7 points while using 4x fewer context tokens.
- A single discovered retrieval harness improved accuracy on 200 IMO-level math problems by an average of 4.7 points across five held-out models (e.g., GPT-5.4n, Gemini-3F) compared to a 'No Retriever' baseline.
- The system automatically discovered harnesses that achieved top-tier pass rates on TerminalBench-2, reaching 76.4% with Claude Opus 4.6 (ranking #2) and 37.6% with Claude Haiku 4.5 (ranking #1).

## Takeaways

- Full, uncompressed access to historical diagnostic data (raw code, execution traces, and evaluation scores) is critical for an agent to perform causal reasoning and targeted modifications in complex, stateful code-space search.
- Direct optimization in the code space, enabled by an agentic proposer, facilitates algorithmic modifications and complete program rewrites, providing a natural regularization bias towards coherent solutions.
- An agent, when provided with rich, granular feedback, can effectively identify and address complex, long-horizon failures in stateful programs, going beyond fixed templates or summary-based feedback.

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
- vi
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d41b7-1156-7866-b991-94545a578703/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d41b7-1156-7866-b991-94545a578703/transcript.json
- Transcript lines: 17
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Mixed
- Headline: Mostly Human, AI Detected
- Fraction AI: 0.16178553
- Fraction AI-assisted: 0
- Fraction human: 0.83821446

## Resources

- GitHub repository: https://github.com/stanford-iris-lab/meta-harness-tbench2-artifact

## Similar Papers

- A Self-Improving Coding Agent (2504.15228v2): A self-improving coding agent, SICA, autonomously edits its own Python codebase to enhance performance. This system achieved an improvement from 17% to 53% accuracy on SWE-Bench Verified tasks by developing new tools and refining its operational logic through a non-gradient-based learning mechanism.
- Agentic Context Engineering: Evolving Contexts for Self-Improving Language Models (2510.04618v3): Agentic Context Engineering (ACE) is a framework that enables large language models to self-improve by dynamically evolving comprehensive, 'playbook'-style contexts instead of static prompts. It consistently achieved average performance gains of over 8% across agentic and domain-specific tasks while reducing adaptation costs by more than 80% compared to baselines.
- Reflexion: Language Agents with Verbal Reinforcement Learning (2303.11366v4): Reflexion enables large language model agents to learn from trial-and-error by converting environmental feedback into natural language reflections stored in an explicit episodic memory. This framework achieved new state-of-the-art pass@1 accuracy on several coding benchmarks and improved performance on sequential decision-making and language reasoning tasks.
- MemSkill: Learning and Evolving Memory Skills for Self-Evolving Agents (2602.02474v1): MemSkill introduces an approach for Large Language Model (LLM) agents where memory operations are learned and evolve over time, moving beyond static, human-engineered mechanisms. This system, developed by Nanyang Technological University and collaborators, achieves superior performance in conversational and embodied tasks by continually refining a dynamic skill bank and a skill-selection policy.
- AutoPDL: Automatic Prompt Optimization for LLM Agents (2504.04365v5): AutoPDL automates the optimization of prompting patterns and content for LLM agents, generating human-readable configurations. This framework achieved an average accuracy gain of 9.21 percentage points across diverse tasks and models, and demonstrated effective transferability to commercial frontier models.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
