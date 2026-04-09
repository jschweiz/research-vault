---
id: page:2026-04-07-alphaxiv-paper-autosota-an-end-to-end-automated-research-system-3756ab92
page_type: source-note
title: 'AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery'
aliases:
- 'AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery'
source_refs:
- 2026-04-07-alphaxiv-paper-autosota-an-end-to-end-automated-research-system-3756ab92
backlinks:
- page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
- page:2026-04-05-alphaxiv-paper-clawarena-benchmarking-ai-agents-in-evolving-inf-2c8b2340
- page:2026-04-05-alphaxiv-paper-combee-scaling-prompt-learning-for-self-improvin-f786b4be
- page:2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
- topic:agentic-frameworks
- topic:cs-ce
- topic:language-modeling
- topic:ml-systems
updated_at: '2026-04-09T16:35:03.699571Z'
managed: true
---
# AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.05550
- Document kind: paper
- Published at: 2026-04-07T07:52:01+00:00
- Authors: Yu Li, Chenyang Shao, Xinyang Liu, Ruotong Zhao, Peijie Liu, Hongyuan Su, Zhibin Chen, Qinglong Yang, Anjie Xu, Yi Fang, Qingbin Zeng, Tianxing Li, Jingbo Xu, Fengli Xu, Yong Li, Tie-Yan Liu
- Tags: paper, alphaxiv, research, agentic-frameworks, agents, computer science, cs.ce, cs.cl, ml-systems, neural-architecture-search
- Topics: [Agents](../topics/agents.md), [Agentic Frameworks](../topics/agentic-frameworks.md), [Computer Science](../topics/computer-science.md), [Cs Ce](../topics/cs-ce.md), [Language Modeling](../topics/language-modeling.md), [Ml Systems](../topics/ml-systems.md)
- Trend score: 155.17
- Novelty score: 6.80

## Summary

An end-to-end automated research system named AutoSOTA, developed by Tsinghua University and Zhongguancun Academy, discovers new State-of-the-Art AI models from unstructured research papers. The system autonomously reproduces and optimizes original methods, achieving an average performance improvement of approximately 10% across 105 diverse AI papers within about five hours of execution per paper.

## Topic Map

- [Agents](../topics/agents.md)
- [Agentic Frameworks](../topics/agentic-frameworks.md)
- [Computer Science](../topics/computer-science.md)
- [Cs Ce](../topics/cs-ce.md)
- [Language Modeling](../topics/language-modeling.md)
- [Ml Systems](../topics/ml-systems.md)

## Related Research

- [Synthetic Sandbox for Training Machine Learning Engineering Agents](synthetic-sandbox-for-training-machine-learning-engineering-agen-d6d706.md) (shared topics: Agentic Frameworks, Agents, Computer Science, Language Modeling)
- [Combee: Scaling Prompt Learning for Self-Improving Language Model Agents](combee-scaling-prompt-learning-for-self-improving-language-model-b157c0.md) (shared topics: Agentic Frameworks, Agents, Computer Science, Language Modeling)
- [ClawArena: Benchmarking AI Agents in Evolving Information Environments](clawarena-benchmarking-ai-agents-in-evolving-information-environ-bdca98.md) (shared topics: Agentic Frameworks, Agents, Computer Science)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Agents, Computer Science)
- [Deep Researcher Agent: An Autonomous Framework for 24/7 Deep Learning Experimentation with Zero-Cost Monitoring](deep-researcher-agent-an-autonomous-framework-for-24-7-deep-lear-4ba06b.md) (shared topics: Agents, Computer Science)
- [AI Assistance Reduces Persistence and Hurts Independent Performance](ai-assistance-reduces-persistence-and-hurts-independent-performa-21bf42.md) (shared topics: Agents, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery

## alphaXiv Summary

An end-to-end automated research system named AutoSOTA, developed by Tsinghua University and Zhongguancun Academy, discovers new State-of-the-Art AI models from unstructured research papers. The system autonomously reproduces and optimizes original methods, achieving an average performance improvement of approximately 10% across 105 diverse AI papers within about five hours of execution per paper.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05550
- Source paper: https://arxiv.org/abs/2604.05550
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05550v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05550v1.png
- Paper ID: 2604.05550
- Canonical ID: 2604.05550v1
- Paper group ID: 019d6b00-2ced-78a3-bc60-c75fc74c1cea
- Version ID: 019d6b00-2d31-7587-a344-63dabc43735e
- Version: v1
- Version order: 1
- Published at: 2026-04-07T07:52:01+00:00
- First published at: 2026-04-07T07:52:01+00:00
- Updated at: 2026-04-08T02:51:06.861000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yu Li
- Chenyang Shao
- Xinyang Liu
- Ruotong Zhao
- Peijie Liu
- Hongyuan Su
- Zhibin Chen
- Qinglong Yang
- Anjie Xu
- Yi Fang
- Qingbin Zeng
- Tianxing Li
- Jingbo Xu
- Fengli Xu
- Yong Li
- Tie-Yan Liu

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.CE
- cs.CL
- ml-systems
- neural-architecture-search
- optimization-methods
- training-orchestration

## Metrics

- Visits (all): 48
- Visits (last 7 days): 48
- Total votes: 0
- Public total votes: 3
- X likes: 0

## Abstract

Artificial intelligence research increasingly depends on prolonged cycles of reproduction, debugging, and iterative refinement to achieve State-Of-The-Art (SOTA) performance, creating a growing need for systems that can accelerate the full pipeline of empirical model optimization. In this work, we introduce AutoSOTA, an end-to-end automated research system that advances the latest SOTA models published in top-tier AI papers to reproducible and empirically improved new SOTA models. We formulate this problem through three tightly coupled stages: resource preparation and goal setting; experiment evaluation; and reflection and ideation. To tackle this problem, AutoSOTA adopts a multi-agent architecture with eight specialized agents that collaboratively ground papers to code and dependencies, initialize and repair execution environments, track long-horizon experiments, generate and schedule optimization ideas, and supervise validity to avoid spurious gains. We evaluate AutoSOTA on recent research papers collected from eight top-tier AI conferences under filters for code availability and execution cost. Across these papers, AutoSOTA achieves strong end-to-end performance in both automated replication and subsequent optimization. Specifically, it successfully discovers 105 new SOTA models that surpass the original reported methods, averaging approximately five hours per paper. Case studies spanning LLM, NLP, computer vision, time series, and optimization further show that the system can move beyond routine hyperparameter tuning to identify architectural innovation, algorithmic redesigns, and workflow-level improvements. These results suggest that end-to-end research automation can serve not only as a performance optimizer, but also as a new form of research infrastructure that reduces repetitive experimental burden and helps redirect human attention toward higher-level scientific creativity.

## Problem

- Achieving State-of-the-Art (SOTA) performance in AI research requires extensive, repetitive cycles of implementation, reproduction, debugging, and refinement, consuming significant human effort.
- Existing Automated Machine Learning (AutoML) systems are limited to predefined search spaces and lack the ability to invent novel algorithms, synthesize external knowledge, or perform complex debuggin
