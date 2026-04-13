---
id: 2026-03-12-alphaxiv-paper-temporal-straightening-for-latent-planning-da3ce5a9
kind: paper
title: Temporal Straightening for Latent Planning
source_url: https://www.alphaxiv.org/abs/2603.12231
source_name: alphaXiv Papers
authors:
- Ying Wang
- Oumayma Bounou
- Gaoyue Zhou
- Randall Balestriero
- Tim G. J. Rudner
- Yann LeCun
- Mengye Ren
published_at: '2026-03-12T17:49:47Z'
ingested_at: '2026-04-09T23:39:09.770793Z'
content_hash: bb1233993c35b72daaea77cabe28d61eda2a7ca2cfd6d49c080ae110746defd7
identity_hash: 5461deaeebb648bf9437d78794e7053687dd1c75e2480ff503cf7a9b1828f992
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.LG
- deep-reinforcement-learning
- generative-models
- optimization-methods
- reinforcement-learning
- representation-learning
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
external_key: https://www.alphaxiv.org/abs/2603.12231
canonical_url: https://www.alphaxiv.org/abs/2603.12231
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T23:39:09.770798Z'
short_summary: Researchers introduced "temporal straightening," a geometric regularization technique that encourages straighter trajectories in latent space, improving representations for model-based reinforcement learning. This method, inspired by the perceptual straightening hypothesis, significantly enhances gradient-based planning performance by creating a latent space where Euclidean distances more accurately reflect true environmental distances, leading to substantial gains in goal-reaching success rates.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:42:57.921246Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 0abf3d00d8dde2217f7b87284132f335dd6b4b447b8c47be5e33a7eeb31edebb
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Temporal Straightening for Latent Planning

## alphaXiv Summary

Researchers introduced "temporal straightening," a geometric regularization technique that encourages straighter trajectories in latent space, improving representations for model-based reinforcement learning. This method, inspired by the perceptual straightening hypothesis, significantly enhances gradient-based planning performance by creating a latent space where Euclidean distances more accurately reflect true environmental distances, leading to substantial gains in goal-reaching success rates.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.12231
- Source paper: https://arxiv.org/abs/2603.12231
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.12231v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.12231v1.png
- GitHub: https://github.com/agentic-learning-ai-lab/temporal-straightening
- GitHub stars: 0
- Paper ID: 2603.12231
- Canonical ID: 2603.12231v1
- Paper group ID: 019ce5d5-babe-7c2c-a055-f41b880028b9
- Version ID: 019ce5d5-baf8-75f0-b11e-f959653964a2
- Version: v1
- Version order: 1
- Published at: 2026-03-12T17:49:47+00:00
- First published at: 2026-03-12T17:49:47+00:00
- Updated at: 2026-03-13T06:15:15.390000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0
- BibTeX saved in `alphaxiv-citation.bib`

## Authors

- Ying Wang
- Oumayma Bounou
- Gaoyue Zhou
- Randall Balestriero
- Tim G. J. Rudner
- Yann LeCun
- Mengye Ren

## Topics

- Computer Science
- cs.LG
- deep-reinforcement-learning
- generative-models
- optimization-methods
- reinforcement-learning
- representation-learning
- robotic-control

## Metrics

- Visits (all): 2687
- Visits (last 7 days): 241
- Total votes: 41
- Public total votes: 165
- X likes: 0

## Abstract

Learning good representations is essential for latent planning with world models. While pretrained visual encoders produce strong semantic visual features, they are not tailored to planning and contain information irrelevant -- or even detrimental -- to planning. Inspired by the perceptual straightening hypothesis in human visual processing, we introduce temporal straightening to improve representation learning for latent planning. Using a curvature regularizer that encourages locally straightened latent trajectories, we jointly learn an encoder and a predictor. We show that reducing curvature this way makes the Euclidean distance in latent space a better proxy for the geodesic distance and improves the conditioning of the planning objective. We demonstrate empirically that temporal straightening makes gradient-based planning more stable and yields significantly higher success rates across a suite of goal-reaching tasks.

## Problem

- Planning in learned latent spaces often involves highly non-convex objectives, hindering efficient gradient-based optimization and forcing reliance on computationally expensive search methods.
- Euclidean distances in existing curved latent spaces can inaccurately represent true geodesic distances, leading to suboptimal action sequences from planners.
- Current representation learning methods, such as reconstruction or frozen pre-trained features, may not effectively optimize the latent space geometry for efficient temporal dynamics and gradient-based planning.

## Method

- A novel "temporal straightening" geometric regularization term is proposed, which explicitly minimizes the angle between consecutive latent velocity vectors.
- A world model, comprising a sensory encoder (e.g., DINOv2 projector or ResNet) and a Vision Transformer predictor, is trained jointly with a prediction loss and this straightening loss.
- For visual features retaining spatial structure, a learnable pooling head aggregates patch-level representations into a global vector before applying the straightening penalty, balancing local detail with global straightness.

## Results

- Temporal straightening consistently improved goal-reaching success rates by 20-60% for open-loop planning and 20-30% for Model Predictive Control with gradient-based optimizers across various 2D environments.
- The method substantially reduced the performance gap between gradient descent and computationally more intensive search-based planning algorithms like CEM, sometimes outperforming unstraightened CEM baselines.
- Learned representations exhibited reduced curvature, and their latent Euclidean distances closely approximated ground-truth environmental geodesic distances, even in environments with non-visual dynamics like Teleported-PointMaze.

## Takeaways

- Explicitly promoting "straighter" latent trajectories (by penalizing curvature) significantly improves the conditioning of the planning objective's Hessian, enabling more efficient gradient-based optimization.
- Regularizing the latent space geometry creates a more faithful distance metric where Euclidean distances between latent states accurately reflect the true geodesic distances in the environment.
- The "perceptual straightening hypothesis" from human vision offers a valuable inspiration for designing latent spaces that facilitate efficient planning in artificial intelligence systems.

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

- MP3: https://paper-podcasts.alphaxiv.org/019ce5d5-babe-7c2c-a055-f41b880028b9/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019ce5d5-babe-7c2c-a055-f41b880028b9/transcript.json
- Transcript lines: 18
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/agentic-learning-ai-lab/temporal-straightening

## Similar Papers

- Latent Diffusion Planning for Imitation Learning (2504.16925v1): Stanford and UC Berkeley researchers develop Latent Diffusion Planning (LDP), a framework that enables robots to learn control policies from both suboptimal trajectories and action-free demonstrations through latent space planning, achieving competitive performance on manipulation tasks while reducing dependence on expensive expert demonstrations.
- Closing the Train-Test Gap in World Models for Gradient-Based Planning (2512.09929v1): Researchers from Columbia University and NYU introduced Online World Modeling (OWM) and Adversarial World Modeling (AWM) to mitigate the train-test gap in world models for gradient-based planning (GBP). These methods enabled GBP to achieve performance comparable to or better than search-based planning algorithms like CEM, while simultaneously reducing computation time by an order of magnitude across various robotic tasks.
- GeoWorld: Geometric World Models (2602.23058v1): GeoWorld integrates hyperbolic geometry into energy-based predictive world models to improve long-horizon visual planning. The framework achieves up to a 3% increase in Success Rate for 3-step planning compared to V-JEPA 2, demonstrating superior stability over longer horizons and outperforming LLM-based planners in visual planning tasks.
- Learning Latent Dynamics for Planning from Pixels (1811.04551v5): PlaNet, developed by researchers at Google Brain, DeepMind, and universities, introduces a purely model-based reinforcement learning agent capable of solving complex continuous control tasks directly from pixel observations. It leverages a novel Recurrent State-Space Model to learn latent dynamics and achieves data efficiency hundreds of times greater than leading model-free methods on tasks within the DeepMind Control Suite.
- Parallel Stochastic Gradient-Based Planning for World Models (2602.00475v1): GRASP, a novel gradient-based planning algorithm, enables world models to effectively solve long-horizon control tasks from high-dimensional visual inputs by combining parallelized planning, Langevin-style exploration, and a robust gradient-cutting mechanism. It achieves a 43.4% success rate in the Push-T environment at a 50-step horizon, significantly outperforming prior methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
