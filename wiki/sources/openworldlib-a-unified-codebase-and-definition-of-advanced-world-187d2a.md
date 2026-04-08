---
id: page:2026-04-06-alphaxiv-paper-openworldlib-a-unified-codebase-and-definition-o-349dac12
page_type: source-note
title: OpenWorldLib: A Unified Codebase and Definition of Advanced World Models
aliases:
  - OpenWorldLib: A Unified Codebase and Definition of Advanced World Models
source_refs:
  - 2026-04-06-alphaxiv-paper-openworldlib-a-unified-codebase-and-definition-o-349dac12
backlinks:
  - page:2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
  - page:2026-03-17-openai-website-introducing-gpt-5-4-mini-and-nano-8afdb503
  - page:2026-04-02-alphaxiv-paper-coral-towards-autonomous-multi-agent-evolution-f-3739abbd
  - page:2026-04-02-alphaxiv-paper-skill0-in-context-agentic-reinforcement-learning-9e84a0d6
  - page:2026-04-03-alphaxiv-paper-agentic-mme-what-agentic-capability-really-bring-688666ad
  - page:2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
  - page:2026-04-03-alphaxiv-paper-self-distilled-rlvr-597ff1e6
  - page:2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
  - page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
  - page:2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
  - page:2026-04-06-alphaxiv-paper-vero-an-open-rl-recipe-for-general-visual-reason-80650390
  - topic:agents
  - topic:computer-science
  - topic:computer-vision
  - topic:deep-reinforcement-learning
  - topic:multimodal
  - topic:world-models
updated_at: 2026-04-08T07:14:52.297397Z
managed: true
---
# OpenWorldLib: A Unified Codebase and Definition of Advanced World Models

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04707
- Document kind: paper
- Published at: 2026-04-06T14:19:48+00:00
- Authors: DataFlow Team, Bohan Zeng, Daili Hua, Kaixin Zhu, Yifan Dai, Bozhou Li
- Tags: paper, alphaxiv, research, agents, computer science, cs.cv, deep-reinforcement-learning, generative-models, inference-optimization, ml-systems
- Topics: [Agents](../topics/agents.md), [Computer Vision](../topics/computer-vision.md), [World Models](../topics/world-models.md), [Multimodal](../topics/multimodal.md), [Computer Science](../topics/computer-science.md), [Deep Reinforcement Learning](../topics/deep-reinforcement-learning.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# OpenWorldLib: A Unified Codebase and Definition of Advanced World Models ## alphaXiv Summary Researchers from Peking University, Kuaishou Technology, and other institutions developed OpenWorldLib, a unified inference framework for world models, alongside a standardized definition clarifying their scope and capabilities. This work provides a common codebase for interactive video generation, 3D generation, multimodal reasoning, and Vision-Language-Action tasks, facilitating structured developmen

## Topic Map

- [Agents](../topics/agents.md)
- [Computer Vision](../topics/computer-vision.md)
- [World Models](../topics/world-models.md)
- [Multimodal](../topics/multimodal.md)
- [Computer Science](../topics/computer-science.md)
- [Deep Reinforcement Learning](../topics/deep-reinforcement-learning.md)

## Related Research

- [Self-Distilled RLVR](self-distilled-rlvr-1944ab.md) (shared topics: Agents, Computer Science, Deep Reinforcement Learning)
- [SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization](skill0-in-context-agentic-reinforcement-learning-for-skill-inter-b7a513.md) (shared topics: Agents, Computer Science, Deep Reinforcement Learning)
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](coral-towards-autonomous-multi-agent-evolution-for-open-ended-di-462c70.md) (shared topics: Agents, Computer Science, Deep Reinforcement Learning)
- [TriAttention: Efficient Long Reasoning with Trigonometric KV Compression](triattention-efficient-long-reasoning-with-trigonometric-kv-comp-d601e8.md) (shared topics: Computer Science, Computer Vision)
- [Vero: An Open RL Recipe for General Visual Reasoning](vero-an-open-rl-recipe-for-general-visual-reasoning-a332b2.md) (shared topics: Agents, Computer Vision)
- [A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens](a-frame-is-worth-one-token-efficient-generative-world-modeling-w-98472f.md) (shared topics: Computer Science, Computer Vision)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# OpenWorldLib: A Unified Codebase and Definition of Advanced World Models

## alphaXiv Summary

Researchers from Peking University, Kuaishou Technology, and other institutions developed OpenWorldLib, a unified inference framework for world models, alongside a standardized definition clarifying their scope and capabilities. This work provides a common codebase for interactive video generation, 3D generation, multimodal reasoning, and Vision-Language-Action tasks, facilitating structured development and comparison within the research community.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04707
- Source paper: https://arxiv.org/abs/2604.04707
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04707v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04707v1.png
- GitHub: https://github.com/OpenDCAI/OpenWorldLib
- GitHub stars: 334
- Paper ID: 2604.04707
- Canonical ID: 2604.04707v1
- Paper group ID: 019d65d2-2cf1-7623-9688-179eb39c3f6d
- Version ID: 019d65d2-2d9a-789e-92dd-e8ac5361fc1b
- Version: v1
- Version order: 1
- Published at: 2026-04-06T14:19:48+00:00
- First published at: 2026-04-06T14:19:48+00:00
- Updated at: 2026-04-07T02:42:46.129000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- DataFlow Team
- Bohan Zeng
- Daili Hua
- Kaixin Zhu
- Yifan Dai
- Bozhou Li
- Yuran Wang
- Chengzhuo Tong
- Yifan Yang
- Mingkun Chang
- Jianbin Zhao
- Zhou Liu
- Hao Liang
- Xiaochen Ma
- Ruichuan An
- Junbo Niu
- Zimo Meng
- Tianyi Bai
- Meiyi Qiang
- Huanyao Zhang
- Zhiyou Xiao
- Tianyu Guo
- Qinhan Yu
- Runhao Zhao
- Zhengpin Li
- Xinyi Huang
- Yisheng Pan
- Yiwen Tang
- Yang Shi
- Yue Ding
- Xinlong Chen
- Hongcheng Gao
- Minglei Shi
- Jialong Wu
- Zekun Wang
- Yuanxing Zhang
- Xintao Wang
- Pengfei Wan
- Yiren Song
- Mike Zheng Shou
- Wentao Zhang

## Topics

- agents
- Computer Science
- cs.CV
- deep-reinforcement-learning
- generative-models
- inference-optimization
- ml-systems
- reasoning
- representation-learning

## Metrics

- Visits (all): 107
- Visits (last 7 days): 107
- Total votes: 2
- Public total votes: 11
- X likes: 0

## Abstract

World models have garnered significant attention as a promising research direction in artificial intelligence, yet a clear and unified definition remains lacking. In this paper, we introduce OpenWorldLib, a comprehensive and standardized inference framework for Advanced World Models. Drawing on the evolution of world models, we propose a clear definition: a world model is a model or framework centered on perception, equipped with interaction and long-term memory capabilities, for understanding and predicting the complex world. We further systematically categorize the essential capabilities of world models. Based on this definition, OpenWorldLib integrates models across different tasks within a unified framework, enabling efficient reuse and collaborative inference. Finally, we present additional reflections and analyses on potential future directions for world model research. Code link: this https URL

## Problem

- The field of world models lacked a universally accepted, clear, and unified definition, leading to diverse interpretations and a fragmented research landscape.
- Ambiguity in defining world model scope hindered systematic research, comparison of methods, and integration of diverse capabilities in AI.
- A practical, unified inference framework was needed to standardize the invocation and integration of various world model-related tasks, accelerating development and application.

## Method

- Proposed a standardized definition for world models as models centered on building internal representations from perception, equipped with action-conditioned simulation and long-term memory for understanding and predicting complex world dynamics.
- Introduced OpenWorldLib, a comprehensive, modular inference framework with five core components (Operator, Synthesis, Reasoning, Representation, Memory) and a top-level Pipeline module,
