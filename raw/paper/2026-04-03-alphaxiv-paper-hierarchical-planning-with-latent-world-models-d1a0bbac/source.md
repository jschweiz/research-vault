---
id: 2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
kind: paper
title: Hierarchical Planning with Latent World Models
source_url: https://www.alphaxiv.org/abs/2604.03208
source_name: alphaXiv Papers
authors:
  - Wancong Zhang
  - Basile Terver
  - Artem Zholus
  - Soham Chitnis
  - Harsh Sutaria
  - Mido Assran
published_at: 2026-04-03T17:32:36Z
ingested_at: 2026-04-07T21:42:53.013251Z
content_hash: 50b3ec313bf35af62cca58bf5b15e4f21fea55f4151a487c3221a7421513ff6c
tags:
  - paper
  - alphaxiv
  - research
  - computer science
  - cs.lg
  - github
  - audio
  - summary
  - hierarchical planning
  - latent world models
status: active
asset_paths:
  - alphaxiv-ai-detection.json
  - alphaxiv-legacy.json
  - alphaxiv-metadata.json
  - alphaxiv-overview-status.json
  - alphaxiv-overview.json
  - alphaxiv-overview.md
  - alphaxiv-paper.json
  - alphaxiv-preview.json
  - alphaxiv-similar-papers.json
  - alphaxiv-transcript.json
  - alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.03208
canonical_url: https://www.alphaxiv.org/abs/2604.03208
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:27:42.405037Z
short_summary: # Hierarchical Planning with Latent World Models ## alphaXiv Summary Hierarchical Planning with Latent World Models (HWM) introduces a top-down hierarchical planning strategy that operates in learned latent spaces, enabling robust long-horizon control directly from high-dimensional observations. This framework successfully performs zero-shot, non-greedy manipulation on a real robot and enhances efficiency and generalization in complex simulated tasks.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-08T10:09:52.839193Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 50b3ec313bf35af62cca58bf5b15e4f21fea55f4151a487c3221a7421513ff6c
lightweight_enrichment_error: null
---
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

- Visits (all): 219
- Visits (last 7 days): 219
- Total votes: 3
- Public total votes: 14
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
- It improved long-horizon control on the Push-T task, achieving a 61% success rate at d=75 timesteps compared to 17% for the flat DINO-WM planner, while requiring approximately 3 times less compute.
- The framework demonstrated enhanced zero-shot generalization to out-of-distribution maze layouts, achieving an 83% success rate on hard mazes (D [13, 16]) versus 44% for flat PLDM, with up to 4 times less planning compute.

## Takeaways

- Decomposing long-horizon problems into a hierarchy of shorter-horizon subproblems significantly mitigates the accumulation of prediction errors and manages the exponential growth of the planning search space.
- Learning latent macro-actions for the high-level world model effectively compresses complex action sequences, enabling more efficient and effective long-horizon planning.
- Operating both high- and low-level planning within a shared latent space, derived from high-dimensional observations, facilitates zero-shot control and generalization without task-specific rewards or explicit policy training.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d60ff-5da4-7739-94cc-8568d61fc564/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d60ff-5da4-7739-94cc-8568d61fc564/transcript.json
- Transcript lines: 18
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Human
- Headline: Fully Human Written
- Fraction AI: 0
- Fraction AI-assisted: 0
- Fraction human: 1

## Resources

- GitHub repository: https://github.com/kevinghst/HWM_PLDM

## Similar Papers

- Embodied Long Horizon Manipulation with Closed-loop Code Generation and Incremental Few-shot Adaptation (2503.21969v3): The DAHLIA framework enables robots to perform complex, multi-step manipulation tasks by generating executable code directly from natural language instructions. It employs a closed-loop dual-tunnel system with incremental few-shot adaptation, achieving high success rates on various benchmarks and demonstrating robust error recovery in real-world scenarios without relying on extensive pre-trained policies.
- Closing the Train-Test Gap in World Models for Gradient-Based Planning (2512.09929v1): Researchers from Columbia University and NYU introduced Online World Modeling (OWM) and Adversarial World Modeling (AWM) to mitigate the train-test gap in world models for gradient-based planning (GBP). These methods enabled GBP to achieve performance comparable to or better than search-based planning algorithms like CEM, while simultaneously reducing computation time by an order of magnitude across various robotic tasks.
- What Drives Success in Physical Planning with Joint-Embedding Predictive World Models? (2512.24497v2): This research provides a systematic empirical study of Joint-Embedding Predictive World Models (JEPA-WMs), identifying the specific technical choices that contribute to their success in physical planning. It proposes optimized model configurations that consistently achieve higher success rates compared to existing baselines on diverse simulated and real-world robotic manipulation and navigation tasks.
- Vision-Language Model Predictive Control for Manipulation Planning and  Trajectory Generation (2504.05225v1): Shandong University and University of Manchester researchers develop a framework combining Vision-Language Models (VLMs) with Model Predictive Control for robotic manipulation, enabling robots to plan and execute complex tasks through trajectory optimization while achieving 85% success rate on real-world manipulation tasks without pre-defined motion primitives.
- Act2Goal: From World Model To General Goal-conditioned Policy (2512.23541v1): Act2Goal proposes a general goal-conditioned robotic policy integrating a vision-based world model for multi-scale planning and a reward-free online adaptation mechanism. The system exhibited strong zero-shot generalization in both simulated and real-world manipulation tasks, with autonomous improvements boosting success rates up to 8x in some simulations and from 0.30 to 0.90 in real-world unseen scenarios.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
