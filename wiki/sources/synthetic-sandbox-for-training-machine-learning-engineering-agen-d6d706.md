---
id: page:2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
page_type: source-note
title: Synthetic Sandbox for Training Machine Learning Engineering Agents
aliases:
- Synthetic Sandbox for Training Machine Learning Engineering Agents
source_refs:
- 2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
backlinks:
- page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
- page:2026-04-05-alphaxiv-paper-combee-scaling-prompt-learning-for-self-improvin-f786b4be
- page:2026-04-06-alphaxiv-paper-flashsac-fast-and-stable-off-policy-reinforcemen-78a7e5ed
- page:2026-04-07-alphaxiv-paper-autosota-an-end-to-end-automated-research-system-3756ab92
- topic:agentic-frameworks
- topic:fine-tuning
- topic:language-modeling
- topic:reinforcement-learning
updated_at: '2026-04-09T23:08:04.918000Z'
managed: true
---
# Synthetic Sandbox for Training Machine Learning Engineering Agents

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04872
- Document kind: paper
- Published at: 2026-04-06T17:19:29+00:00
- Authors: Yuhang Zhou, Lizhu Zhang, Yifan Wu, Jiayi Liu, Xiangjun Fan, Zhuokai Zhao, Hong Yan
- Tags: paper, alphaxiv, research, agentic-frameworks, agents, computer science, cs.cl, cs.lg, fine-tuning, ml-systems
- Topics: [Agents](../topics/agents.md), [Fine-Tuning](../topics/fine-tuning.md), [Reinforcement Learning](../topics/reinforcement-learning.md), [Agentic Frameworks](../topics/agentic-frameworks.md), [Computer Science](../topics/computer-science.md), [Language Modeling](../topics/language-modeling.md)
- Trend score: 223.43
- Novelty score: 6.80

## Summary

SandMLE is a framework that creates synthetic, micro-scale machine learning engineering environments, making on-policy trajectory-wise reinforcement learning practical for training LLM agents. This approach reduces average code execution time by 13.7 times, enabling Qwen3 models to achieve up to a 100.7% relative improvement in "Any Medal" rates on MLE-Bench-Lite compared to baseline methods.

## Topic Map

- [Agents](../topics/agents.md)
- [Fine-Tuning](../topics/fine-tuning.md)
- [Reinforcement Learning](../topics/reinforcement-learning.md)
- [Agentic Frameworks](../topics/agentic-frameworks.md)
- [Computer Science](../topics/computer-science.md)
- [Language Modeling](../topics/language-modeling.md)

## Related Research

- [AutoSOTA: An End-to-End Automated Research System for State-of-the-Art AI Model Discovery](autosota-an-end-to-end-automated-research-system-for-state-of-th-79db5b.md) (shared topics: Agentic Frameworks, Agents, Computer Science, Language Modeling)
- [Combee: Scaling Prompt Learning for Self-Improving Language Model Agents](combee-scaling-prompt-learning-for-self-improving-language-model-b157c0.md) (shared topics: Agentic Frameworks, Agents, Computer Science, Language Modeling)
- [ClawArena: Benchmarking AI Agents in Evolving Information Environments](clawarena-benchmarking-ai-agents-in-evolving-information-environ-bdca98.md) (shared topics: Agentic Frameworks, Agents, Computer Science)
- [Embarrassingly Simple Self-Distillation Improves Code Generation](embarrassingly-simple-self-distillation-improves-code-generation-c213e5.md) (shared topics: Computer Science, Fine-Tuning, Language Modeling)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Agents, Computer Science)
- [Deep Researcher Agent: An Autonomous Framework for 24/7 Deep Learning Experimentation with Zero-Cost Monitoring](deep-researcher-agent-an-autonomous-framework-for-24-7-deep-lear-4ba06b.md) (shared topics: Agents, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Synthetic Sandbox for Training Machine Learning Engineering Agents

## alphaXiv Summary

SandMLE is a framework that creates synthetic, micro-scale machine learning engineering environments, making on-policy trajectory-wise reinforcement learning practical for training LLM agents. This approach reduces average code execution time by 13.7 times, enabling Qwen3 models to achieve up to a 100.7% relative improvement in "Any Medal" rates on MLE-Bench-Lite compared to baseline methods.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04872
- Source paper: https://arxiv.org/abs/2604.04872
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04872v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04872v1.png
- Paper ID: 2604.04872
- Canonical ID: 2604.04872v1
- Paper group ID: 019d65d7-7578-7816-83a9-18e52c67232c
- Version ID: 019d65d7-75b7-7cd6-8911-58cd23ba0104
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:19:29+00:00
- First published at: 2026-04-06T17:19:29+00:00
- Updated at: 2026-04-07T02:48:32.376000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yuhang Zhou
- Lizhu Zhang
- Yifan Wu
- Jiayi Liu
- Xiangjun Fan
- Zhuokai Zhao
- Hong Yan

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.CL
- cs.LG
- fine-tuning
- ml-systems
- multi-agent-learning
- reinforcement-learning
- synthetic-data
- tool-use
- transformers

## Metrics

- Visits (all): 90
- Visits (last 7 days): 90
- Total votes: 3
- Public total votes: 13
- X likes: 0

## Abstract

As large language model agents advance beyond software engineering (SWE) tasks toward machine learning engineering (MLE), verifying agent behavior becomes orders of magnitude more expensive: while SWE tasks can be verified via fast-executing unit tests, MLE verification requires running full ML pipelines -- data preprocessing, model training, and metric evaluation -- on large datasets at each rollout step, rendering trajectory-wise on-policy reinforcement learning (RL) prohibitively slow. Existing approaches retreat to supervised fine-tuning (SFT) or offline proxy rewards, sacrificing the exploration and generalization benefits of on-policy RL. We observe that sandbox data size is the primary source of this bottleneck. Based on this insight, we introduce SandMLE, a multi-agent framework that generates diverse, verifiable synthetic MLE environments from a small number of seed tasks, preserving the structural and technical complexity of real-world problems while constraining datasets to micro-scale (each task is paired with only 50-200 training samples). Through extensive experiments, we show that SandMLE reduces execution time by over 13 times, enabling large-scale, on-policy trajectory-wise RL for the first time in the MLE domain. On MLE-bench-lite, SandMLE yields significant gains over SFT baselines across Qwen3-8B, 14B, and 30B-A3B, with relative medal rate improvements ranging from 20.3% to 66.9%. Furthermore, the trained policy generalizes across unseen agentic scaffolds, achieving up to 32.4% better HumanRank score on MLE-Dojo.

## Problem

- Applying on-policy trajectory-wise Reinforcement Learning (RL) to Machine Learning Engineering (MLE) tasks is computationally infeasible due to the long execution times of full ML pipelines.
- Each MLE code execution takes around 200 seconds, making the large-scale rollouts required for on-policy RL impractical.
- Existing methods like supervised fine-tuning (SFT) or step-wise RL with proxy rewards for MLE agents fail to leverage the exploration and generalization benefits of on-policy RL.

## Method

- Developed a multi-agent framework to autonomously generate diverse, verifiable synthetic MLE environments with micro-scale datasets (50-200 samples).
- Constrained synthetic datasets drastically reduce execution latency from approximately 200 seconds to about 14 seconds per task.
- Applied trajectory-wise Group Relative Policy Optimization (GRPO) with a dense,
