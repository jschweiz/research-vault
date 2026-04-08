---
id: page:2026-04-03-alphaxiv-paper-self-distilled-rlvr-597ff1e6
page_type: source-note
title: Self-Distilled RLVR
aliases:
  - Self-Distilled RLVR
source_refs:
  - 2026-04-03-alphaxiv-paper-self-distilled-rlvr-597ff1e6
backlinks:
  - page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
  - page:2026-04-02-alphaxiv-paper-coral-towards-autonomous-multi-agent-evolution-f-3739abbd
  - page:2026-04-02-alphaxiv-paper-skill0-in-context-agentic-reinforcement-learning-9e84a0d6
  - page:2026-04-06-alphaxiv-paper-openworldlib-a-unified-codebase-and-definition-o-349dac12
  - page:2026-04-06-alphaxiv-paper-vero-an-open-rl-recipe-for-general-visual-reason-80650390
  - topic:agents
  - topic:deep-reinforcement-learning
  - topic:distillation
  - topic:fine-tuning
  - topic:knowledge-distillation
updated_at: 2026-04-08T07:14:52.266113Z
managed: true
---
# Self-Distilled RLVR

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.03128
- Document kind: paper
- Published at: 2026-04-03T15:50:07+00:00
- Authors: Chenxu Yang, Chuanyu Qin, Qingyi Si, Minghui Chen, Naibin Gu, Dingyu Yao
- Tags: paper, alphaxiv, research, agents, computer science, cs.cl, cs.lg, deep-reinforcement-learning, fine-tuning, knowledge-distillation
- Topics: [Agents](../topics/agents.md), [Fine-Tuning](../topics/fine-tuning.md), [Distillation](../topics/distillation.md), [Computer Science](../topics/computer-science.md), [Deep Reinforcement Learning](../topics/deep-reinforcement-learning.md), [Knowledge Distillation](../topics/knowledge-distillation.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# Self-Distilled RLVR ## alphaXiv Summary Researchers at the Chinese Academy of Sciences and JD.COM formally analyzed fundamental limitations in existing On-Policy Self-Distillation (OPSD) for training reasoning LLMs, then proposed a new paradigm, RLSD, that separates environment-anchored update direction from self-distilled update magnitude. RLSD achieves an average of 2.32% absolute accuracy improvement over standard GRPO on multimodal reasoning benchmarks while ensuring training stability and

## Topic Map

- [Agents](../topics/agents.md)
- [Fine-Tuning](../topics/fine-tuning.md)
- [Distillation](../topics/distillation.md)
- [Computer Science](../topics/computer-science.md)
- [Deep Reinforcement Learning](../topics/deep-reinforcement-learning.md)
- [Knowledge Distillation](../topics/knowledge-distillation.md)

## Related Research

- [SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization](skill0-in-context-agentic-reinforcement-learning-for-skill-inter-b7a513.md) (shared topics: Agents, Computer Science, Deep Reinforcement Learning, Fine-Tuning)
- [OpenWorldLib: A Unified Codebase and Definition of Advanced World Models](openworldlib-a-unified-codebase-and-definition-of-advanced-world-187d2a.md) (shared topics: Agents, Computer Science, Deep Reinforcement Learning)
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](coral-towards-autonomous-multi-agent-evolution-for-open-ended-di-462c70.md) (shared topics: Agents, Computer Science, Deep Reinforcement Learning)
- [Embarrassingly Simple Self-Distillation Improves Code Generation](embarrassingly-simple-self-distillation-improves-code-generation-c213e5.md) (shared topics: Computer Science, Fine-Tuning, Knowledge Distillation)
- [Vero: An Open RL Recipe for General Visual Reasoning](vero-an-open-rl-recipe-for-general-visual-reasoning-a332b2.md) (shared topics: Agents, Fine-Tuning)
- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Agents, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Self-Distilled RLVR

## alphaXiv Summary

Researchers at the Chinese Academy of Sciences and JD.COM formally analyzed fundamental limitations in existing On-Policy Self-Distillation (OPSD) for training reasoning LLMs, then proposed a new paradigm, RLSD, that separates environment-anchored update direction from self-distilled update magnitude. RLSD achieves an average of 2.32% absolute accuracy improvement over standard GRPO on multimodal reasoning benchmarks while ensuring training stability and preventing information leakage.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03128
- Source paper: https://arxiv.org/abs/2604.03128
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03128v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03128v1.png
- Paper ID: 2604.03128
- Canonical ID: 2604.03128v1
- Paper group ID: 019d6086-b0ee-70bb-9a73-f40ebf136f94
- Version ID: 019d6086-b131-734a-86cd-85f6423a901b
- Version: v1
- Version order: 1
- Published at: 2026-04-03T15:50:07+00:00
- First published at: 2026-04-03T15:50:07+00:00
- Updated at: 2026-04-06T02:02:13.102000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Chenxu Yang
- Chuanyu Qin
- Qingyi Si
- Minghui Chen
- Naibin Gu
- Dingyu Yao
- Zheng Lin
- Weiping Wang
- Jiaqi Wang
- Nan Duan

## Topics

- agents
- Computer Science
- cs.CL
- cs.LG
- deep-reinforcement-learning
- fine-tuning
- knowledge-distillation
- optimization-methods
- text-generation
- transformers

## Metrics

- Visits (all): 1040
- Visits (last 7 days): 1040
- Total votes: 21
- Public total votes: 51
- X likes: 0

## Abstract

On-policy distillation (OPD) has become a popular training paradigm in the LLM community. This paradigm selects a larger model as the teacher to provide dense, fine-grained signals for each sampled trajectory, in contrast to reinforcement learning with verifiable rewards (RLVR), which only obtains sparse signals from verifiable outcomes in the environment. Recently, the community has explored on-policy self-distillation (OPSD), where the same model serves as both teacher and student, with the teacher receiving additional privileged information such as reference answers to enable self-evolution. This paper demonstrates that learning signals solely derived from the privileged teacher result in severe information leakage and unstable long-term training. Accordingly, we identify the optimal niche for self-distillation and propose \textbf{RLSD} (\textbf{RL}VR with \textbf{S}elf-\textbf{D}istillation). Specifically, we leverage self-distillation to obtain token-level policy differences for determining fine-grained update magnitudes, while continuing to use RLVR to derive reliable update directions from environmental feedback (e.g., response correctness). This enables RLSD to simultaneously harness the strengths of both RLVR and OPSD, achieving a higher convergence ceiling and superior training stability.

## Problem

- Reinforcement Learning with Verifiable Rewards (RLVR) methods struggle with sparse, sequence-level rewards, leading to coarse credit assignment for long-horizon reasoning tasks.
- On-Policy Self-Distillation (OPSD) promises dense, token-level supervision but empirically exhibits information leakage and training instability, causing performance degradation.
- Standard On-Policy Distillation (OPD) requires a separate, often larger, teacher model, leading to substantial computational overhead and scalability limitations.

## Method

- A theoretical and empirical analysis formally proves that OPSD's distribution-matching objective contains an irreducible mutual information gap, causing gradient corruption and information leakage.
- RLSD (RLVR with Self-Distillation) is proposed to repurpose the privileged teacher signal, using it solely to modulate the *magnitude* of token-level credit assignment, while environment rewards dictate the update *direction*.
- RLSD integrates with GRPO by computing a direction-aware evidence
