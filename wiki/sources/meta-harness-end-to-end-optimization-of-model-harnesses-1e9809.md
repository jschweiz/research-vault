---
id: page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-7bb194d2
page_type: source-note
title: Meta-Harness: End-to-End Optimization of Model Harnesses
aliases:
  - Meta-Harness: End-to-End Optimization of Model Harnesses
source_refs:
  - 2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-7bb194d2
backlinks:
  - page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
  - page:2026-04-01-alphaxiv-paper-test-time-scaling-makes-overtraining-compute-opt-3a3760da
  - page:2026-04-03-alphaxiv-paper-joyai-llm-flash-advancing-mid-scale-llms-with-to-7299ba1c
  - page:2026-04-04-alphaxiv-paper-lightthinker-from-reasoning-compression-to-memor-0d96ca8a
  - page:2026-04-06-alphaxiv-paper-memory-intelligence-agent-c0e4c961
  - page:2026-04-06-alphaxiv-paper-skillx-automatically-constructing-skill-knowledg-f4c5cea3
  - topic:efficient-transformers
  - topic:meta-learning
  - topic:ml-systems
updated_at: 2026-04-08T07:14:52.247348Z
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
- Tags: paper, alphaxiv, research, agents, computer science, cs.ai, efficient-transformers, meta-learning, ml-systems, optimization-methods
- Topics: [Agents](../topics/agents.md), [Artificial Intelligence](../topics/artificial-intelligence.md), [Computer Science](../topics/computer-science.md), [Efficient Transformers](../topics/efficient-transformers.md), [Meta Learning](../topics/meta-learning.md), [Ml Systems](../topics/ml-systems.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# Meta-Harness: End-to-End Optimization of Model Harnesses ## alphaXiv Summary Meta-Harness provides an end-to-end optimization framework for LLM harnesses, the external code that dictates how models interact with their environment. The system utilizes an agentic proposer with filesystem access to uncompressed historical code and execution traces, leading to a 7.7-point accuracy improvement in text classification, a 4.7-point average gain in math reasoning, and competitive pass rates on agentic

## Topic Map

- [Agents](../topics/agents.md)
- [Artificial Intelligence](../topics/artificial-intelligence.md)
- [Computer Science](../topics/computer-science.md)
- [Efficient Transformers](../topics/efficient-transformers.md)
- [Meta Learning](../topics/meta-learning.md)
- [Ml Systems](../topics/ml-systems.md)

## Related Research

- [Meta-Harness: End-to-End Optimization of Model Harnesses](meta-harness-end-to-end-optimization-of-model-harnesses-ebb80b.md) (shared topics: Agents, Artificial Intelligence, Computer Science, Efficient Transformers, Meta Learning, Ml Systems)
- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Agents, Artificial Intelligence, Computer Science)
- [Memory Intelligence Agent](memory-intelligence-agent-7ffa81.md) (shared topics: Agents, Artificial Intelligence, Computer Science)
- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Agents, Artificial Intelligence, Computer Science)
- [JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency](joyai-llm-flash-advancing-mid-scale-llms-with-token-efficiency-ea0c5b.md) (shared topics: Artificial Intelligence, Computer Science, Efficient Transformers)
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](coral-towards-autonomous-multi-agent-evolution-for-open-ended-di-462c70.md) (shared topics: Agents, Artificial Intelligence, Computer Science)

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

- Visits (all): 7311
- Visits (last 7 days): 6671
- Total votes: 108
- Public total votes: 351
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
