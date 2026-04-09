---
id: 2026-04-06-alphaxiv-paper-flashsac-fast-and-stable-off-policy-reinforcemen-78a7e5ed
kind: paper
title: 'FlashSAC: Fast and Stable Off-Policy Reinforcement Learning for High-Dimensional Robot Control'
source_url: https://www.alphaxiv.org/abs/2604.04539
source_name: alphaXiv Papers
authors:
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
published_at: '2026-04-06T09:03:41Z'
ingested_at: '2026-04-09T12:06:09.767570Z'
content_hash: 062ee35f12c0a2a57be5e0664b11fa0d83fa3455ed700d630e24d2f2692028c4
identity_hash: 81722bf8fcbe1475e156e123e5f26408cb3099f37688988340f707bb4dda3f52
tags:
- paper
- alphaxiv
- research
- computer science
- cs.lg
- cs.ro
- deep-reinforcement-learning
- optimization-methods
- reinforcement-learning
- robotic-control
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04539
canonical_url: https://www.alphaxiv.org/abs/2604.04539
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:06:09.767575Z'
short_summary: FlashSAC is an off-policy reinforcement learning algorithm designed for high-dimensional robotic control, integrating rapid training via scaled data throughput and model capacity with stability mechanisms like constrained critic updates. The algorithm consistently reduces wall-clock training time by up to an order of magnitude and achieves higher asymptotic performance across over 60 locomotion and manipulation tasks, including successful sim-to-real humanoid locomotion.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T16:19:42.612305Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 79992fbb66ed4227d8c5da13ee1bce8908bb258a8939deed18f9535340b100a2
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback+alphaxiv-metrics-v1
lightweight_scoring_input_hash: 6449af71f4a49eb7c889cf6e6cf411f78572d234d7da55960d8cd826b3659a27
lightweight_score:
  relevance_score: 0.557
  source_fit_score: 0.5959
  topic_fit_score: 0.4
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.5959
  bucket_hint: worth_a_skim
  reason: 'Heuristic fallback based on 1 favorite-topic match. alphaXiv engagement signals: 14 public votes, 2 total votes, 140 visits in the last 7 days.'
  evidence_quotes:
  - 'FlashSAC is an off-policy reinforcement learning algorithm designed for high-dimensional robotic control, integrating rapid training via scaled data throughput '
---
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
- Achieves fast training by leveraging massively parallel simulation, a 10 million transition replay buffer, larger networks (2.5M parameters), large batch sizes (2048), and a low updates-to-data ratio.
- Ensures stability through a suite of techniques including an inverted residual network backbone, pre-activation batch normalization, cross-batch value prediction, a distributional critic with adaptive reward scaling, and weight normalization.

## Results

- FlashSAC reduced the wall-clock training time for sim-to-real humanoid locomotion by nearly an order of magnitude compared to PPO, achieving stable real-world behaviors.
- Consistently attained higher asymptotic performance and faster convergence across more than 60 locomotion and manipulation tasks in diverse simulators, including dexterous manipulation and vision-based control.
- Outperformed or matched other state-of-the-art off-policy and model-based methods across a wide range of benchmarks, demonstrating robustness with a single set of hyperparameters.

## Takeaways

- Scaling laws observed in supervised learning can be effectively applied to off-policy RL, where increasing model capacity and data throughput with reduced gradient updates leads to faster convergence, provided stability is maintained.
- Robust critic stabilization through architectural designs (e.g., inverted residual blocks, pre-activation batch norm) and norm constraints is essential to prevent error accumulation and ensure stable training in high-dimensional, data-rich off-policy settings.
- Broad and efficient exploration in high-dimensional spaces can be facilitated by a unified entropy target and lightweight noise repetition, avoiding complex task-specific tuning.

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
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d667a-5472-7eaf-bbe9-68cafbe41f5a/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d667a-5472-7eaf-bbe9-68cafbe41f5a/transcript.json

## Resources

- GitHub repository: https://github.com/Holiday-Robot/FlashSAC

## Similar Papers

- Evolutionary Policy Optimization (2503.19037v3)
- Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement
  Learning with a Stochastic Actor (1801.01290v2): Soft Actor-Critic (SAC), developed by researchers at BAIR lab, introduces an off-policy maximum entropy deep reinforcement learning algorithm for continuous control. It achieves state-of-the-art performance and high stability across various tasks while demonstrating excellent sample efficiency.
- Uncertainty-Aware Robotic World Model Makes Offline Model-Based Reinforcement Learning Work on Real Robots (2504.16680v3): Researchers at ETH Zurich developed a pipeline for offline Model-Based Reinforcement Learning that effectively trains and deploys policies on physical quadruped and humanoid robots, utilizing an Uncertainty-Aware Robotic World Model and uncertainty-penalized policy optimization. This approach yields policies from fixed datasets that achieve robust performance on real hardware, even surpassing online model-free baselines when combining simulated and real-world offline data.
- FastTD3: Simple, Fast, and Capable Reinforcement Learning for Humanoid  Control (2505.22642v3): FastTD3, developed by researchers at UC Berkeley including Pieter Abbeel, is an optimized off-policy reinforcement learning algorithm based on TD3. It achieves state-of-the-art wall-clock training times for complex robotic tasks, solving many HumanoidBench tasks in under 3 hours on a single A100 GPU, and demonstrated successful sim-to-real transfer to a physical humanoid robot.
- Policy Agnostic RL: Offline RL and Online RL Fine-Tuning of Any Class and Backbone (2412.06685v1): This paper introduces Policy Agnostic Reinforcement Learning (PA-RL), a novel framework that decouples the RL algorithm from the policy class, enabling effective training of diverse policy types including Gaussian, diffusion, and transformer policies. PA-RL achieved substantial performance gains in simulated D4RL benchmarks and demonstrated successful fine-tuning of expressive policies like Diffusion Policies and OpenVLA on real-world robotic manipulation tasks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
