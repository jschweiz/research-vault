---
id: page:2026-04-05-alphaxiv-paper-combee-scaling-prompt-learning-for-self-improvin-f786b4be
page_type: source-note
title: 'Combee: Scaling Prompt Learning for Self-Improving Language Model Agents'
aliases:
- 'Combee: Scaling Prompt Learning for Self-Improving Language Model Agents'
source_refs:
- 2026-04-05-alphaxiv-paper-combee-scaling-prompt-learning-for-self-improvin-f786b4be
backlinks:
- page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
- page:2026-04-05-alphaxiv-paper-clawarena-benchmarking-ai-agents-in-evolving-inf-2c8b2340
- page:2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
- page:2026-04-07-alphaxiv-paper-ai-assistance-reduces-persistence-and-hurts-inde-17db6a91
- page:2026-04-07-alphaxiv-paper-autosota-an-end-to-end-automated-research-system-3756ab92
- page:2026-04-07-alphaxiv-paper-deep-researcher-agent-an-autonomous-framework-fo-7bbe612a
- page:2026-04-07-alphaxiv-paper-neural-computers-503b0501
- topic:agentic-frameworks
- topic:artificial-intelligence
- topic:distributed-learning
- topic:language-modeling
updated_at: '2026-04-09T23:08:05.135596Z'
managed: true
---
# Combee: Scaling Prompt Learning for Self-Improving Language Model Agents

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04247
- Document kind: paper
- Published at: 2026-04-05T20:07:48+00:00
- Authors: Hanchen Li, Runyuan He, Qizheng Zhang, Changxiu Ji, Qiuyang Mang, Xiaokun Chen, Lakshya A Agrawal, Wei-Liang Liao, Eric Yang, Alvin Cheung, James Zou, Kunle Olukotun, Ion Stoica, Joseph E. Gonzalez
- Tags: paper, alphaxiv, research, agentic-frameworks, agents, computer science, cs.ai, cs.cl, cs.lg, distributed-learning
- Topics: [Agents](../topics/agents.md), [Agentic Frameworks](../topics/agentic-frameworks.md), [Artificial Intelligence](../topics/artificial-intelligence.md), [Computer Science](../topics/computer-science.md), [Distributed Learning](../topics/distributed-learning.md), [Language Modeling](../topics/language-modeling.md)
- Trend score: 223.43
- Novelty score: 6.80

## Summary

Combee presents a distributed framework for scaling prompt learning in self-improving language model agents. It effectively tackles the "context overload" challenge in parallel aggregation, yielding up to a 17x speedup compared to sequential methods while preserving or enhancing accuracy on benchmarks such as AppWorld and Terminal-Bench 2.0.

## Topic Map

- [Agents](../topics/agents.md)
- [Agentic Frameworks](../topics/agentic-frameworks.md)
- [Artificial Intelligence](../topics/artificial-intelligence.md)
- [Computer Science](../topics/computer-science.md)
- [Distributed Learning](../topics/distributed-learning.md)
- [Language Modeling](../topics/language-modeling.md)

## Related Research

- [AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery](autosota-an-end-to-end-automated-research-system-for-state-of-th-79db5b.md) (shared topics: Agentic Frameworks, Agents, Computer Science, Language Modeling)
- [Synthetic Sandbox for Training Machine Learning Engineering Agents](synthetic-sandbox-for-training-machine-learning-engineering-agen-d6d706.md) (shared topics: Agentic Frameworks, Agents, Computer Science, Language Modeling)
- [ClawArena: Benchmarking AI Agents in Evolving Information Environments](clawarena-benchmarking-ai-agents-in-evolving-information-environ-bdca98.md) (shared topics: Agentic Frameworks, Agents, Artificial Intelligence, Computer Science)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Agents, Artificial Intelligence, Computer Science)
- [Deep Researcher Agent: An Autonomous Framework for 24/7 Deep Learning Experimentation with Zero-Cost Monitoring](deep-researcher-agent-an-autonomous-framework-for-24-7-deep-lear-4ba06b.md) (shared topics: Agents, Artificial Intelligence, Computer Science)
- [AI Assistance Reduces Persistence and Hurts Independent Performance](ai-assistance-reduces-persistence-and-hurts-independent-performa-21bf42.md) (shared topics: Agents, Artificial Intelligence, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Combee: Scaling Prompt Learning for Self-Improving Language Model Agents

## alphaXiv Summary

Combee presents a distributed framework for scaling prompt learning in self-improving language model agents. It effectively tackles the "context overload" challenge in parallel aggregation, yielding up to a 17x speedup compared to sequential methods while preserving or enhancing accuracy on benchmarks such as AppWorld and Terminal-Bench 2.0.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04247
- Source paper: https://arxiv.org/abs/2604.04247
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04247v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04247v1.png
- Paper ID: 2604.04247
- Canonical ID: 2604.04247v1
- Paper group ID: 019d65ff-90bb-7060-907e-fa43c4f93a58
- Version ID: 019d65ff-9120-778a-8fe3-1bc7ac1bd9c1
- Version: v1
- Version order: 1
- Published at: 2026-04-05T20:07:48+00:00
- First published at: 2026-04-05T20:07:48+00:00
- Updated at: 2026-04-07T03:32:20.795000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Hanchen Li
- Runyuan He
- Qizheng Zhang
- Changxiu Ji
- Qiuyang Mang
- Xiaokun Chen
- Lakshya A Agrawal
- Wei-Liang Liao
- Eric Yang
- Alvin Cheung
- James Zou
- Kunle Olukotun
- Ion Stoica
- Joseph E. Gonzalez

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.CL
- cs.LG
- distributed-learning
- meta-learning
- ml-systems
- optimization-methods

## Metrics

- Visits (all): 114
- Visits (last 7 days): 114
- Total votes: 2
- Public total votes: 12
- X likes: 0

## Abstract

Recent advances in prompt learning allow large language model agents to acquire task-relevant knowledge from inference-time context without parameter changes. For example, existing methods (like ACE or GEPA) can learn system prompts to improve accuracy based on previous agent runs. However, these methods primarily focus on single-agent or low-parallelism settings. This fundamentally limits their ability to efficiently learn from a large set of collected agentic traces. It would be efficient and beneficial to run prompt learning in parallel to accommodate the growing trend of learning from many agentic traces or parallel agent executions. Yet without a principled strategy for scaling, current methods suffer from quality degradation with high parallelism. To improve both the efficiency and quality of prompt learning, we propose Combee, a novel framework to scale parallel prompt learning for self-improving agents. Combee speeds up learning and enables running many agents in parallel while learning from their aggregate traces without quality degradation. To achieve this, Combee leverages parallel scans and employs an augmented shuffle mechanism; Combee also introduces a dynamic batch size controller to balance quality and delay. Evaluations on AppWorld, Terminal-Bench, Formula, and FiNER demonstrate that Combee achieves up to 17x speedup over previous methods with comparable or better accuracy and equivalent cost.

## Problem

- Existing prompt learning methods for LLM agents are inefficient and not designed for high-parallelism scenarios, hindering rapid adaptation.
- Naive parallelization of prompt learning leads to "context overload," where aggregator LLMs fail to distill high-quality insights from numerous reflections, causing information loss and performance degradation.
- This limitation restricts the ability of self-improving LLM agents to learn efficiently from vast interaction traces in real-world, large-scale deployments.

## Method

- Combee introduces a distributed Map-Shuffle-Reduce paradigm for prompt learning, integrating parallel scan aggregation, augmented shuffling, and a dynamic batch size controller.
- Parallel scan aggregation employs a hierarchical, multi-level approach to combine reflections, preventing context overload for individual aggregator LLMs.
- Augmented shuffling duplicates and shuffles reflections to ensure critical information is
