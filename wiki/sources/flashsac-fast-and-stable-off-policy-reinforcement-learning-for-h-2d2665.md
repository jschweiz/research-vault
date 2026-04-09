---
id: page:2026-04-06-alphaxiv-paper-flashsac-fast-and-stable-off-policy-reinforcemen-78a7e5ed
page_type: source-note
title: 'FlashSAC: Fast and Stable Off-Policy Reinforcement Learning for High-Dimensional Robot Control'
aliases:
- 'FlashSAC: Fast and Stable Off-Policy Reinforcement Learning for High-Dimensional Robot Control'
source_refs:
- 2026-04-06-alphaxiv-paper-flashsac-fast-and-stable-off-policy-reinforcemen-78a7e5ed
backlinks:
- page:2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
- page:2026-04-08-alphaxiv-paper-a1-a-fully-transparent-open-source-adaptive-and--5f38d6e3
- topic:deep-reinforcement-learning
- topic:optimization-methods
- topic:reinforcement-learning
- topic:robotics
updated_at: '2026-04-09T16:35:04.382212Z'
managed: true
---
# FlashSAC: Fast and Stable Off-Policy Reinforcement Learning for High-Dimensional Robot Control

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04539
- Document kind: paper
- Published at: 2026-04-06T09:03:41+00:00
- Authors: Donghu Kim, Youngdo Lee, Minho Park, Kinam Kim, I Made Aswin Nahendra, Takuma Seno, Sehee Min, Daniel Palenicek, Florian Vogt, Danica Kragic, Jan Peters, Jaegul Choo, Hojoon Lee
- Tags: paper, alphaxiv, research, computer science, cs.lg, cs.ro, deep-reinforcement-learning, optimization-methods, reinforcement-learning, robotic-control
- Topics: [Reinforcement Learning](../topics/reinforcement-learning.md), [Robotics](../topics/robotics.md), [Computer Science](../topics/computer-science.md), [Deep Reinforcement Learning](../topics/deep-reinforcement-learning.md), [Machine Learning](../topics/machine-learning.md), [Optimization Methods](../topics/optimization-methods.md)
- Trend score: 96.95
- Novelty score: 6.80

## Summary

FlashSAC is an off-policy reinforcement learning algorithm designed for high-dimensional robotic control, integrating rapid training via scaled data throughput and model capacity with stability mechanisms like constrained critic updates. The algorithm consistently reduces wall-clock training time by up to an order of magnitude and achieves higher asymptotic performance across over 60 locomotion and manipulation tasks, including successful sim-to-real humanoid locomotion.

## Topic Map

- [Reinforcement Learning](../topics/reinforcement-learning.md)
- [Robotics](../topics/robotics.md)
- [Computer Science](../topics/computer-science.md)
- [Deep Reinforcement Learning](../topics/deep-reinforcement-learning.md)
- [Machine Learning](../topics/machine-learning.md)
- [Optimization Methods](../topics/optimization-methods.md)

## Related Research

- [Hierarchical Planning with Latent World Models](hierarchical-planning-with-latent-world-models-47379e.md) (shared topics: Computer Science, Machine Learning, Robotics)
- [Fast Spatial Memory with Elastic Test-Time Training](fast-spatial-memory-with-elastic-test-time-training-7fd9ac.md) (shared topics: Computer Science, Machine Learning)
- [A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model](a1-a-fully-transparent-open-source-adaptive-and-efficient-trunca-ac0efe.md) (shared topics: Computer Science, Robotics)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Computer Science, Machine Learning)
- [From folding boxes to fixing vacuums, GEN-1 robotics model hits 99% reliability](from-folding-boxes-to-fixing-vacuums-gen-1-robotics-model-hits-9-8d579f.md) (shared topics: Machine Learning, Robotics)
- [Synthetic Sandbox for Training Machine Learning Engineering Agents](synthetic-sandbox-for-training-machine-learning-engineering-agen-d6d706.md) (shared topics: Computer Science, Reinforcement Learning)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# FlashSAC: Fast and Stable Off-Policy Reinforcement Learning for High-Dimensional Robot Control

## alphaXiv Summary

FlashSAC is an off-policy reinforcement learning algorithm designed for high-dimensional robotic control, integrating rapid training via scaled data throughput and model capacity with stability mechanisms like constrained critic updates. The algorithm consistently reduces wall-clock training time by up to an order of magnitude and achieves higher asymptotic performance across over 60 locomotion and manipulation tasks, including successful sim-to-real humanoid locomotion.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04539
- Source paper: https://arxiv.org/abs/2604.04539
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04539v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04539v1.png
- GitHub: https://github.com/Holiday-Robot/FlashSAC
- GitHub stars: 6
- Paper ID: 2604.04539
- Canonical ID: 2604.04539v1
- Paper group ID: 019d667a-5472-7eaf-bbe9-68cafbe41f5a
- Version ID: 019d667a-54ee-7058-8cba-607b61d19588
- Version: v1
- Version order: 1
- Published at: 2026-04-06T09:03:41+00:00
- First published at: 2026-04-06T09:03:41+00:00
- Updated at: 2026-04-07T05:46:26.290000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Donghu Kim
- Youngdo Lee
- Minho Park
- Kinam Kim
- I Made Aswin Nahendra
- Takuma Seno
- Sehee Min
- Daniel Palenicek
- Florian Vogt
- Danica Kragic
- Jan Peters
- Jaegul Choo
- Hojoon Lee

## Topics

- Computer Science
- cs.LG
- cs.RO
- deep-reinforcement-learning
- optimization-methods
- reinforcement-learning
- robotic-control
- transfer-learning

## Metrics

- Visits (all): 140
- Visits (last 7 days): 140
- Total votes: 2
- Public total votes: 14
- X likes: 0

## Abstract

Reinforcement learning (RL) is a core approach for robot control when expert demonstrations are unavailable. On-policy methods such as Proximal Policy Optimization (PPO) are widely used for their stability, but their reliance on narrowly distributed on-policy data limits accurate policy evaluation in high-dimensional state and action spaces. Off-policy methods can overcome this limitation by learning from a broader state-action distribution, yet suffer from slow convergence and instability, as fitting a value function over diverse data requires many gradient updates, causing critic errors to accumulate through bootstrapping. We present FlashSAC, a fast and stable off-policy RL algorithm built on Soft Actor-Critic. Motivated by scaling laws observed in supervised learning, FlashSAC sharply reduces gradient updates while compensating with larger models and higher data throughput. To maintain stability at increased scale, FlashSAC explicitly bounds weight, feature, and gradient norms, curbing critic error accumulation. Across over 60 tasks in 10 simulators, FlashSAC consistently outperforms PPO and strong off-policy baselines in both final performance and training efficiency, with the largest gains on high-dimensional tasks such as dexterous manipulation. In sim-to-real humanoid locomotion, FlashSAC reduces training time from hours to minutes, demonstrating the promise of off-policy RL for sim-to-real transfer.

## Problem

- Traditional on-policy reinforcement learning methods are data inefficient for complex, high-dimensional robotic control tasks, leading to prohibitive training costs.
- Off-policy reinforcement learning, despite its data efficiency potential, often faces challenges of slow convergence and training instability, particularly when dealing with large models and bootstrapped value functions.
- Prior off-policy approaches struggled to simultaneously achieve both rapid training speed and robust stability, especially in environments demanding high model capacity.

## Method

- Introduced FlashSAC, an off-policy algorithm built on Soft Actor-Critic (SAC), integrating mechanisms for both rapid and stable learning.
- Achieves fast training by leveragin
