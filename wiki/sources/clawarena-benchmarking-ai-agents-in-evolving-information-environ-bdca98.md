---
id: page:2026-04-05-alphaxiv-paper-clawarena-benchmarking-ai-agents-in-evolving-inf-2c8b2340
page_type: source-note
title: 'ClawArena: Benchmarking AI Agents in Evolving Information Environments'
aliases:
- 'ClawArena: Benchmarking AI Agents in Evolving Information Environments'
source_refs:
- 2026-04-05-alphaxiv-paper-clawarena-benchmarking-ai-agents-in-evolving-inf-2c8b2340
backlinks:
- page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
- page:2026-04-05-alphaxiv-paper-combee-scaling-prompt-learning-for-self-improvin-f786b4be
- page:2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
- page:2026-04-07-alphaxiv-paper-ai-assistance-reduces-persistence-and-hurts-inde-17db6a91
- page:2026-04-07-alphaxiv-paper-deep-researcher-agent-an-autonomous-framework-fo-7bbe612a
- page:2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
- topic:agentic-frameworks
- topic:artificial-intelligence
- topic:evaluations
- topic:reasoning
updated_at: '2026-04-09T12:15:42.519622Z'
managed: true
---
# ClawArena: Benchmarking AI Agents in Evolving Information Environments

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04202
- Document kind: paper
- Published at: 2026-04-05T17:55:23+00:00
- Authors: Haonian Ji, Kaiwen Xiong, Siwei Han, Peng Xia, Shi Qiu, Yiyang Zhou, Jiaqi Liu, Jinlong Li, Bingzhou Li, Zeyu Zheng, Cihang Xie, Huaxiu Yao
- Tags: paper, alphaxiv, research, agentic-frameworks, agents, Computer Science, continual-learning, cs.AI, cs.CL, cs.LG, human-ai-interaction, reasoning
- Topics: [Agents](../topics/agents.md), [Audio](../topics/audio.md), [Reasoning](../topics/reasoning.md), [Evaluations](../topics/evaluations.md), [Agentic Frameworks](../topics/agentic-frameworks.md), [Artificial Intelligence](../topics/artificial-intelligence.md)
- Trend score: 249.90
- Novelty score: 6.80

## Summary

ClawArena introduces a benchmark for evaluating AI agents in complex, dynamic information environments, focusing on multi-source conflict reasoning, dynamic belief revision, and implicit personalization. Experiments indicate that underlying language model capabilities more significantly impact overall performance (0.154 range) than agent framework design, though sophisticated frameworks like MetaClaw can enhance execution-oriented tasks.

## Topic Map

- [Agents](../topics/agents.md)
- [Audio](../topics/audio.md)
- [Reasoning](../topics/reasoning.md)
- [Evaluations](../topics/evaluations.md)
- [Agentic Frameworks](../topics/agentic-frameworks.md)
- [Artificial Intelligence](../topics/artificial-intelligence.md)

## Related Research

- [Meta-Harness: End-to-End Optimization of Model Harnesses](meta-harness-end-to-end-optimization-of-model-harnesses-ebb80b.md) (shared topics: Agents, Artificial Intelligence, Audio, Evaluations, Reasoning)
- [AI Assistance Reduces Persistence and Hurts Independent Performance](ai-assistance-reduces-persistence-and-hurts-independent-performa-21bf42.md) (shared topics: Agents, Artificial Intelligence, Audio, Reasoning)
- [Combee: Scaling Prompt Learning for Self-Improving Language Model Agents](combee-scaling-prompt-learning-for-self-improving-language-model-b157c0.md) (shared topics: Agentic Frameworks, Agents, Artificial Intelligence, Audio)
- [MoRight: Motion Control Done Right](moright-motion-control-done-right-47f0f6.md) (shared topics: Artificial Intelligence, Audio, Reasoning)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Agents, Artificial Intelligence, Audio)
- [Deep Researcher Agent: An Autonomous Framework for 24/7 Deep Learning Experimentation with Zero-Cost Monitoring](deep-researcher-agent-an-autonomous-framework-for-24-7-deep-lear-4ba06b.md) (shared topics: Agents, Artificial Intelligence, Audio)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# ClawArena: Benchmarking AI Agents in Evolving Information Environments

## alphaXiv Summary

ClawArena introduces a benchmark for evaluating AI agents in complex, dynamic information environments, focusing on multi-source conflict reasoning, dynamic belief revision, and implicit personalization. Experiments indicate that underlying language model capabilities more significantly impact overall performance (0.154 range) than agent framework design, though sophisticated frameworks like MetaClaw can enhance execution-oriented tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04202
- Source paper: https://arxiv.org/abs/2604.04202
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04202v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04202v1.png
- GitHub: https://github.com/aiming-lab/ClawArena
- GitHub stars: 3
- Paper ID: 2604.04202
- Canonical ID: 2604.04202v1
- Paper group ID: 019d65dc-b043-70b0-8cb7-b5cdacb96183
- Version ID: 019d65dc-b081-7036-b3bf-27189cb11a51
- Version: v1
- Version order: 1
- Published at: 2026-04-05T17:55:23+00:00
- First published at: 2026-04-05T17:55:23+00:00
- Updated at: 2026-04-07T02:54:15.107000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Haonian Ji
- Kaiwen Xiong
- Siwei Han
- Peng Xia
- Shi Qiu
- Yiyang Zhou
- Jiaqi Liu
- Jinlong Li
- Bingzhou Li
- Zeyu Zheng
- Cihang Xie
- Huaxiu Yao

## Topics

- agentic-frameworks
- agents
- Computer Science
- continual-learning
- cs.AI
- cs.CL
- cs.LG
- human-ai-interaction
- reasoning
- test-time-inference

## Metrics

- Visits (all): 144
- Visits (last 7 days): 144
- Total votes: 4
- Public total votes: 20
- X likes: 0

## Abstract

AI agents deployed as persistent assistants must maintain correct beliefs as their information environment evolves. In practice, evidence is scattered across heterogeneous sources that often contradict one another, new information can invalidate earlier conclusions, and user preferences surface through corrections rather than explicit instructions. Existing benchmarks largely assume static, single-authority settings and do not evaluate whether agents can keep up with this complexity. We introduce ClawArena, a benchmark for evaluating AI agents in evolving information environments. Each scenario maintains a complete hidden ground truth while exposing the agent only to noisy, partial, and sometimes contradictory traces across multi-channel sessions, workspace files, and staged updates. Evaluation is organized around three coupled challenges: multi-source conflict reasoning, dynamic belief revision, and implicit personalization, whose interactions yield a 14-category question taxonomy. Two question formats, multi-choice (set-selection) and shell-based executable checks, test both reasoning and workspace grounding. The current release contains 64 scenarios across 8 professional domains, totaling 1{,}879 evaluation rounds and 365 dynamic updates. Experiments on five agent frameworks and five language models show that both model capability (15.4% range) and framework design (9.2%) substantially affect performance, that self-evolving skill frameworks can partially close model-capability gaps, and that belief revision difficulty is determined by update design strategy rather than the mere presence of updates. Code is available at this https URL.

## Problem

- Existing AI agent benchmarks operate on simplified assumptions, typically using static environments with a single source of truth, failing to mirror real-world complexities.
- Agents struggle with resolving conflicting information originating from multiple heterogeneous sources (e.g., chat, files) and discerning source reliability.
- Current evaluation methods do not adequately assess an agent's ability to revise prior beliefs in response to new, evolving information or to learn and apply implicit user preferences over time.

## Method

- ClawArena provides a benchmark of 64 scenarios across 8 profes
