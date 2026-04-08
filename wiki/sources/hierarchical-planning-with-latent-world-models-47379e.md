---
id: page:2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
page_type: source-note
title: Hierarchical Planning with Latent World Models
aliases:
  - Hierarchical Planning with Latent World Models
source_refs:
  - 2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
backlinks:
  - page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
  - topic:audio
  - topic:hierarchical-planning
  - topic:latent-world-models
  - topic:machine-learning
  - topic:world-models
updated_at: 2026-04-08T07:14:52.403865Z
managed: true
---
# Hierarchical Planning with Latent World Models

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.03208
- Document kind: paper
- Published at: 2026-04-03T17:32:36+00:00
- Authors: Wancong Zhang, Basile Terver, Artem Zholus, Soham Chitnis, Harsh Sutaria, Mido Assran
- Tags: paper, alphaxiv, research, computer science, cs.lg, github, audio, summary, hierarchical planning, latent world models
- Topics: [Audio](../topics/audio.md), [World Models](../topics/world-models.md), [Hierarchical Planning](../topics/hierarchical-planning.md), [Computer Science](../topics/computer-science.md), [Latent World Models](../topics/latent-world-models.md), [Machine Learning](../topics/machine-learning.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# Hierarchical Planning with Latent World Models ## alphaXiv Summary Hierarchical Planning with Latent World Models (HWM) introduces a top-down hierarchical planning strategy that operates in learned latent spaces, enabling robust long-horizon control directly from high-dimensional observations. This framework successfully performs zero-shot, non-greedy manipulation on a real robot and enhances efficiency and generalization in complex simulated tasks.

## Topic Map

- [Audio](../topics/audio.md)
- [World Models](../topics/world-models.md)
- [Hierarchical Planning](../topics/hierarchical-planning.md)
- [Computer Science](../topics/computer-science.md)
- [Latent World Models](../topics/latent-world-models.md)
- [Machine Learning](../topics/machine-learning.md)

## Related Research

- [MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale](mineru2-5-pro-pushing-the-limits-of-data-centric-document-parsin-394662.md) (shared topics: Audio, Computer Science)
- [OpenWorldLib: A Unified Codebase and Definition of Advanced World Models](openworldlib-a-unified-codebase-and-definition-of-advanced-world-187d2a.md) (shared topics: Computer Science, World Models)
- [SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization](skill0-in-context-agentic-reinforcement-learning-for-skill-inter-b7a513.md) (shared topics: Computer Science, Machine Learning)
- [Test-Time Scaling Makes Overtraining Compute-Optimal](test-time-scaling-makes-overtraining-compute-optimal-7627f8.md) (shared topics: Computer Science, Machine Learning)
- [TriAttention: Efficient Long Reasoning with Trigonometric KV Compression](triattention-efficient-long-reasoning-with-trigonometric-kv-comp-d601e8.md) (shared topics: Computer Science)
- [A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens](a-frame-is-worth-one-token-efficient-generative-world-modeling-w-98472f.md) (shared topics: Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Hierarchical Planning with Latent World Models

## alphaXiv Summary

Hierarchical Planning with Latent World Models (HWM) introduces a top-down hierarchical planning strategy that operates in learned latent spaces, enabling robust long-horizon control directly from high-dimensional observations. This framework successfully performs zero-shot, non-greedy manipulation on a real robot and enhances efficiency and generalization in complex simulated tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03208
- Source paper: https://arxiv.org/abs/2604.03208
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03208v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03208v1.png
- GitHub: https://github.com/kevinghst/HWM_PLDM
- GitHub stars: 4
- Paper ID: 2604.03208
- Canonical ID: 2604.03208v1
- Paper group ID: 019d60ff-5da4-7739-94cc-8568d61fc564
- Version ID: 019d60ff-5dc8-7fbf-a60c-00319ed02acf
- Version: v1
- Version order: 1
- Published at: 2026-04-03T17:32:36+00:00
- First published at: 2026-04-03T17:32:36+00:00
- Updated at: 2026-04-06T04:14:01.636000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Wancong Zhang
- Basile Terver
- Artem Zholus
- Soham Chitnis
- Harsh Sutaria
- Mido Assran
- Randall Balestriero
- Amir Bar
- Adrien Bardes
- Yann LeCun
- Nicolas Ballas

## Topics

- Computer Science
- cs.LG

## Metrics

- Visits (all): 166
- Visits (last 7 days): 166
- Total votes: 1
- Public total votes: 12
- X likes: 0

## Abstract

Model predictive control (MPC) with learned world models has emerged as a promising paradigm for embodied control, particularly for its ability to generalize zero-shot when deployed in new environments. However, learned world models often struggle with long-horizon control due to the accumulation of prediction errors and the exponentially growing search space. In this work, we address these challenges by learning latent world models at multiple temporal scales and performing hierarchical planning across these scales, enabling long-horizon reasoning while substantially reducing inference-time planning complexity. Our approach serves as a modular planning abstraction that applies across diverse latent world-model architectures and domains. We demonstrate that this hierarchical approach enables zero-shot control on real-world non-greedy robotic tasks, achieving a 70% success rate on pick-&-place using only a final goal specification, compared to 0% for a single-level world model. In addition, across physics-based simulated environments including push manipulation and maze navigation, hierarchical planning achieves higher success while requiring up to 4x less planning-time compute.

## Problem

- Learned world models struggle with robust long-horizon control due to compounding prediction errors over extended rollouts.
- The planning search space expands exponentially with increasing horizon, making long-term planning computationally intractable.
- Existing hierarchical methods often require low-dimensional state spaces, hand-engineered representations, or task-specific training, limiting their applicability to high-dimensional zero-shot settings.

## Method

- HWM employs a top-down hierarchical planning strategy that operates entirely in a shared learned latent space during inference.
- A high-level planner, using a long-horizon world model and learned latent macro-actions, generates immediate subgoals in the latent space.
- A low-level planner utilizes a short-horizon world model and primitive actions to achieve the immediate subgoals, with the entire process using receding-horizon Model Predictive Control (MPC).

## Results

- HWM achieved a 70% success rate on real-robot pick-and-place tasks, outperforming single-level VJEPA2-AC (0% success) and strong vision-language-action baselines.
- It improved long-horizon control on the Push-T task, achieving a 61% success rate at d=75 timesteps compared to 17% for the flat DINO-WM planner, while r
