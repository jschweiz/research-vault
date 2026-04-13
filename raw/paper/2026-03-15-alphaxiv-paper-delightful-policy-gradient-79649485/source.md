---
id: 2026-03-15-alphaxiv-paper-delightful-policy-gradient-79649485
kind: paper
title: Delightful Policy Gradient
source_url: https://www.alphaxiv.org/abs/2603.14608
source_name: alphaXiv Papers
authors:
- Ian Osband
published_at: '2026-03-15T21:06:37Z'
ingested_at: '2026-04-09T23:13:16.724801Z'
content_hash: 232e299571ecc4af332a0209f1d5b847e2eb728b1a8c7217d4916d4591e11b79
identity_hash: aecabc1eda296d77872597312a5d9468c0e2bc0cf732dfd838a6f6aedf55fa91
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.AI
- cs.LG
- deep-reinforcement-learning
- Mathematics
- math.OC
- optimization-methods
status: active
asset_paths:
- alphaxiv-citation.bib
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-podcast.mp3
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2603.14608
canonical_url: https://www.alphaxiv.org/abs/2603.14608
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T23:13:16.724811Z'
short_summary: Google DeepMind's Delightful Policy Gradient (DG) reframes policy learning by re-weighting gradient terms based on both action advantage and surprisal, differentiating between rare successful actions and rare detrimental ones. This approach improves learning dynamics, leading to more efficient convergence and better performance across various reinforcement learning tasks, especially in complex settings.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:42:59.354946Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 11708f34295b8c3d5b72be7bd91c10dc0d0ad88f98ca9150666c7d323eb1543c
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Delightful Policy Gradient

## alphaXiv Summary

Google DeepMind's Delightful Policy Gradient (DG) reframes policy learning by re-weighting gradient terms based on both action advantage and surprisal, differentiating between rare successful actions and rare detrimental ones. This approach improves learning dynamics, leading to more efficient convergence and better performance across various reinforcement learning tasks, especially in complex settings.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.14608
- Source paper: https://arxiv.org/abs/2603.14608
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.14608v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.14608v1.png
- Paper ID: 2603.14608
- Canonical ID: 2603.14608v1
- Paper group ID: 019cfa00-5161-7487-80e3-5f28851a76a1
- Version ID: 019cfa00-5171-78c2-a0e8-58fbdbb9ced8
- Version: v1
- Version order: 1
- Published at: 2026-03-15T21:06:37+00:00
- First published at: 2026-03-15T21:06:37+00:00
- Updated at: 2026-03-17T04:14:10.785000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0
- BibTeX saved in `alphaxiv-citation.bib`

## Authors

- Ian Osband

## Topics

- Computer Science
- cs.AI
- cs.LG
- deep-reinforcement-learning
- Mathematics
- math.OC
- optimization-methods
- reinforcement-learning
- robotic-control
- sequence-modeling
- Statistics
- stat.ML
- transformers

## Metrics

- Visits (all): 741
- Visits (last 7 days): 59
- Total votes: 9
- Public total votes: 70
- X likes: 0

## Abstract

Standard policy gradients weight each sampled action by advantage alone, regardless of how likely that action was under the current policy. This creates two pathologies: within a single decision context (e.g. one image or prompt), a rare negative-advantage action can disproportionately distort the update direction; across many such contexts in a batch, the expected gradient over-allocates budget to contexts the policy already handles well. We introduce the \textit{Delightful Policy Gradient} (DG), which gates each term with a sigmoid of \emph{delight}, the product of advantage and action surprisal (negative log-probability). For $K$-armed bandits, DG provably improves directional accuracy in a single context and, across multiple contexts, shifts the expected gradient strictly closer to the supervised cross-entropy oracle. This second effect is not variance reduction: it persists even with infinite samples. Empirically, DG outperforms REINFORCE, PPO, and advantage-weighted baselines across MNIST, transformer sequence modeling, and continuous control, with larger gains on harder tasks.

## Problem

- Standard policy gradient methods are prone to "pathologies" that hinder optimal learning, particularly in deep learning settings where gradient direction is crucial.
- Rare actions with negative advantage can disproportionately distort the policy update direction, even if these actions are unlikely to occur under the current policy.
- The gradient budget is suboptimally allocated across diverse decision contexts, often favoring "easy" contexts where the policy already performs well, potentially stalling progress on more challenging scenarios.

## Method

- The Delightful Policy Gradient (DG) method modifies the standard policy gradient update rule by introducing a "delight"-based gating mechanism.
- This gate multiplies each standard policy gradient term, where "delight" is defined as the product of action advantage and action surprisal (negative log-probability of the action).
- The gating mechanism adaptively amplifies gradient contributions from rare, positive-advantage actions while significantly attenuating those from rare, negative-advantage actions.

## Results

- Theoretically, DG reduces perpendicular variance in single-context settings and shifts the expected gradient closer to the cross-entropy oracle in multi-context scenarios.
- Empirically, DG achieves faster learning and lower classification error in MNIST contextual bandit tasks, closing approximately half the gap to the supervised cross-entropy oracle.
- In Transformer sequence modeling and continuous control environments (DeepMind Control Suite), DG consistently outperforms or matches strong baselines, demonstrating more robust performance on complex tasks and avoiding catastrophic failures.

## Takeaways

- Delightful Policy Gradient operates through two distinct mechanisms: it reduces directional variance from noisy, low-probability, negative-advantage actions.
- It introduces a beneficial bias that rotates the expected gradient direction closer to a supervised cross-entropy oracle, a property that persists even with infinite samples.
- DG rebalances the expected gradient allocation across multiple contexts, shifting learning budget towards harder, less well-solved scenarios and away from already well-performing ones.

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

- MP3: https://paper-podcasts.alphaxiv.org/019cfa00-5161-7487-80e3-5f28851a76a1/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019cfa00-5161-7487-80e3-5f28851a76a1/transcript.json
- Transcript lines: 17
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- Proximal Policy Optimization Algorithms (1707.06347v2): Proximal Policy Optimization (PPO) algorithms offer a first-order optimization method for reinforcement learning, combining the reliable performance and data efficiency of trust-region methods with the implementation simplicity of policy gradient approaches, demonstrating competitive or superior performance across continuous control benchmarks and Atari games, notably in sample efficiency.
- Asymmetric REINFORCE for off-Policy Reinforcement Learning: Balancing positive and negative rewards (2506.20520v2): Researchers from FAIR at Meta and NYU developed Asymmetric REINFORCE (AsymRE), a simple off-policy reinforcement learning algorithm that stabilizes large language model fine-tuning. The method demonstrates that carefully selecting the baseline 'V' to be strictly less than the behavior policy's expected reward prevents catastrophic training collapses and improves accuracy in complex reasoning tasks.
- Does This Gradient Spark Joy? (2603.20526v1): Ian Osband from Google DeepMind presents the Kondo gate, a mechanism for selective backpropagation in policy gradient methods, which decides whether to compute a backward pass based on a forward-pass 'delight' signal. This approach reduces backward pass computations by up to two orders of magnitude while maintaining or enhancing learning quality across contextual bandit and transformer tasks.
- Delightful Distributed Policy Gradient (2603.20521v1): The Delightful Policy Gradient (DG) method enhances distributed reinforcement learning by selectively gating policy gradient updates based on action surprisal and advantage. This approach amplifies updates from surprising successful actions and suppresses those from surprising failed actions, achieving superior performance in environments with various frictions without requiring actor behavior probabilities.
- PG-Rainbow: Using Distributional Reinforcement Learning in Policy Gradient Methods (2407.13146v2): PG-Rainbow integrates an Implicit Quantile Network, an off-policy distributional reinforcement learning method, into the on-policy Proximal Policy Optimization framework to enhance value function representation. The approach improves average episodic returns across most Atari environments compared to standard PPO by enabling the agent to consider the full distribution of returns.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
