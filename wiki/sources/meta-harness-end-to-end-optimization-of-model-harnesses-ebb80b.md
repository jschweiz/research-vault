---
id: page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
page_type: source-note
title: 'Meta-Harness: End-to-End Optimization of Model Harnesses'
aliases:
- 'Meta-Harness: End-to-End Optimization of Model Harnesses'
source_refs:
- 2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
backlinks:
- page:2026-04-05-alphaxiv-paper-clawarena-benchmarking-ai-agents-in-evolving-inf-2c8b2340
- page:2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
- page:2026-04-07-alphaxiv-paper-ai-assistance-reduces-persistence-and-hurts-inde-17db6a91
- page:2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
- topic:evaluations
- topic:tool-use
updated_at: '2026-04-09T12:15:41.999248Z'
managed: true
---
# Meta-Harness: End-to-End Optimization of Model Harnesses

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2603.28052
- Document kind: paper
- Published at: 2026-03-30T05:33:50+00:00
- Authors: Yoonho Lee, Roshen Nair, Qizheng Zhang, Kangwook Lee, Omar Khattab, Chelsea Finn
- Tags: paper, alphaxiv, research, agents, Computer Science, cs.AI, efficient-transformers, meta-learning, ml-systems, optimization-methods, reasoning, tool-use
- Topics: [Agents](../topics/agents.md), [Audio](../topics/audio.md), [Reasoning](../topics/reasoning.md), [Tool Use](../topics/tool-use.md), [Evaluations](../topics/evaluations.md), [Artificial Intelligence](../topics/artificial-intelligence.md)
- Trend score: 249.90
- Novelty score: 6.80

## Summary

Meta-Harness provides an end-to-end optimization framework for LLM harnesses, the external code that dictates how models interact with their environment. The system utilizes an agentic proposer with filesystem access to uncompressed historical code and execution traces, leading to a 7.7-point accuracy improvement in text classification, a 4.7-point average gain in math reasoning, and competitive pass rates on agentic coding benchmarks.

## Topic Map

- [Agents](../topics/agents.md)
- [Audio](../topics/audio.md)
- [Reasoning](../topics/reasoning.md)
- [Tool Use](../topics/tool-use.md)
- [Evaluations](../topics/evaluations.md)
- [Artificial Intelligence](../topics/artificial-intelligence.md)

## Related Research

- [ClawArena: Benchmarking AI Agents in Evolving Information Environments](clawarena-benchmarking-ai-agents-in-evolving-information-environ-bdca98.md) (shared topics: Agents, Artificial Intelligence, Audio, Evaluations, Reasoning)
- [AI Assistance Reduces Persistence and Hurts Independent Performance](ai-assistance-reduces-persistence-and-hurts-independent-performa-21bf42.md) (shared topics: Agents, Artificial Intelligence, Audio, Reasoning)
- [MoRight: Motion Control Done Right](moright-motion-control-done-right-47f0f6.md) (shared topics: Artificial Intelligence, Audio, Reasoning)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Agents, Artificial Intelligence, Audio)
- [Deep Researcher Agent: An Autonomous Framework for 24/7 Deep Learning Experimentation with Zero-Cost Monitoring](deep-researcher-agent-an-autonomous-framework-for-24-7-deep-lear-4ba06b.md) (shared topics: Agents, Artificial Intelligence, Audio)
- [Synthetic Sandbox for Training Machine Learning Engineering Agents](synthetic-sandbox-for-training-machine-learning-engineering-agen-d6d706.md) (shared topics: Agents, Audio, Tool Use)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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

- Visits (all): 8242
- Visits (last 7 days): 6164
- Total votes: 116
- Public total votes: 388
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

- Meta-Harness achieved 48.6% accuracy in online text classification, outperforming state-of-th
