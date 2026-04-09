---
id: 2026-04-05-alphaxiv-paper-adaptive-action-chunking-at-inference-time-for-v-ecfb6d09
kind: paper
title: Adaptive Action Chunking at Inference-time for Vision-Language-Action Models
source_url: https://www.alphaxiv.org/abs/2604.04161
source_name: alphaXiv Papers
authors:
- Yuanchang Liang
- Xiaobo Wang
- Kai Wang
- Shuo Wang
- Xiaojiang Peng
- Haoyu Chen
- David Kim Huat Chua
- Prahlad Vadakkepat
published_at: '2026-04-05T16:03:32Z'
ingested_at: '2026-04-09T10:01:06.034654Z'
content_hash: 94275613455a3ba592eedd6081881f8e741186b46fd3d65c132a5626260deab3
identity_hash: 1b5bce0384f89b4b476fc78a9864f2986d47b43d1d4ce301132414e2c139466a
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.RO
- audio
- summary
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
external_key: https://www.alphaxiv.org/abs/2604.04161
canonical_url: https://www.alphaxiv.org/abs/2604.04161
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:01:06.034659Z'
short_summary: A new inference-time strategy, Adaptive Action Chunking (AAC), allows Vision-Language-Action (VLA) models to dynamically determine action chunk sizes based on predictive uncertainty. This method enhances task success rates on RoboCasa Kitchen and LIBERO benchmarks in simulation, achieving an average 2.3% and 0.9% increase respectively, and improves real-world robot manipulation by 15% across several tasks.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Adaptive Action Chunking at Inference-time for Vision-Language-Action Models

## alphaXiv Summary

A new inference-time strategy, Adaptive Action Chunking (AAC), allows Vision-Language-Action (VLA) models to dynamically determine action chunk sizes based on predictive uncertainty. This method enhances task success rates on RoboCasa Kitchen and LIBERO benchmarks in simulation, achieving an average 2.3% and 0.9% increase respectively, and improves real-world robot manipulation by 15% across several tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04161
- Source paper: https://arxiv.org/abs/2604.04161
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04161v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04161v1.png
- Paper ID: 2604.04161
- Canonical ID: 2604.04161v1
- Paper group ID: 019d65a5-389c-70e4-88c2-1bcd35911ce8
- Version ID: 019d65a5-38d7-7228-9f32-b5251dcda7fc
- Version: v1
- Version order: 1
- Published at: 2026-04-05T16:03:32+00:00
- First published at: 2026-04-05T16:03:32+00:00
- Updated at: 2026-04-07T01:53:39.996000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yuanchang Liang
- Xiaobo Wang
- Kai Wang
- Shuo Wang
- Xiaojiang Peng
- Haoyu Chen
- David Kim Huat Chua
- Prahlad Vadakkepat

## Topics

- Computer Science
- cs.RO

## Metrics

- Visits (all): 68
- Visits (last 7 days): 68
- Total votes: 0
- Public total votes: 9
- X likes: 0

## Abstract

In Vision-Language-Action (VLA) models, action chunking (i.e., executing a sequence of actions without intermediate replanning) is a key technique to improve robotic manipulation abilities. However, a large chunk size reduces the model's responsiveness to new information, while a small one increases the likelihood of mode-jumping, jerky behavior resulting from discontinuities between chunks. Therefore, selecting the optimal chunk size is an urgent demand to balance the model's reactivity and consistency. Unfortunately, a dominant trend in current VLA models is an empirical fixed chunk length at inference-time, hindering their superiority and scalability across diverse manipulation tasks. To address this issue, we propose a novel Adaptive Action Chunking (AAC) strategy, which exploits action entropy as the cue to adaptively determine the chunk size based on current predictions. Extensive experiments on a wide range of simulated and real-world robotic manipulation tasks have demonstrated that our approach substantially improves performance over the state-of-the-art alternatives. The videos and source code are publicly available at this https URL.

## Problem

- Fixed action chunk sizes in Vision-Language-Action (VLA) models necessitate a trade-off between reactivity to new environmental information (requiring small chunks) and temporal consistency/computational efficiency (benefiting from large chunks).
- The optimal action chunk size varies considerably across different robotic manipulation tasks and even within distinct phases of a single task, making manual empirical tuning challenging and inherently suboptimal.
- Previous adaptive chunking approaches often rely on hand-crafted value functions, require task-specific reward signals unavailable in real-world scenarios, or do not offer true dynamic adaptation, limiting their generalization and practical deployment.

## Method

- Introduces Adaptive Action Chunking (AAC), an inference-time strategy that dynamically selects the optimal action chunk size based on the VLA model's predictive uncertainty, without requiring additional training or architectural modifications.
- Utilizes action entropy as a metric to quantify the uncertainty of predicted actions; lower entropy suggests higher reliability for longer action chunks, while higher entropy indicates uncertain predictions warranting smaller chunk sizes and more frequent replanning.
- Calculates average action entropy by sampling multiple candidate action chunks in parallel, using Gaussian differential entropy for continuous control components (translation, rotation) and standard discrete entropy for discrete components (gripper), then identifies the optimal chunk size where the increase in average entropy is maximal, constrained by a minimum action magnitude.

## Results

- In simulation, AAC improved average success rates by 2.3% on RoboCasa Kitchen (62.0% vs 59.7%) and 0.9% on LIBERO (95.0% vs 94.1%), demonstrating consistent gains across diverse benchmarks and notably a 4% increase in LIBERO-Long tasks.
- Real-world experiments on a robot showed a 15% average increase in success rate (from 67.0% to 82.0%) across banana pick-and-place, emergency button pressing, and long-horizon toy manipulation tasks, attributed to better gripper alignment and precision.
- AAC enhanced robustness in out-of-distribution scenarios and improved operational safety in real-world deployments by preventing collisions and enabling smoother, more precise actions when predictions indicated high uncertainty.

## Takeaways

- Action entropy, derived from parallel sampling of predicted actions, provides a robust and model-agnostic indicator of a VLA model's predictive uncertainty for both continuous and discrete control outputs.
- Dynamically adjusting action chunk sizes based on this uncertainty enables VLA models to adapt their control granularity to specific task phases, leveraging larger chunks for confident, coarse movements and smaller ones for critical, fine-grained manipulations.
- The point of maximum differential in average action entropy, combined with a minimum action magnitude constraint, effectively determines an optimal chunk size at inference time, balancing temporal consistency with reactivity to environmental changes.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65a5-389c-70e4-88c2-1bcd35911ce8/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65a5-389c-70e4-88c2-1bcd35911ce8/transcript.json

## Similar Papers

- Fine-Tuning Vision-Language-Action Models: Optimizing Speed and Success (2502.19645v2): Researchers at Stanford University developed an Optimized Fine-Tuning (OFT) recipe for Vision-Language-Action (VLA) models, substantially increasing their inference speed and task success on new robotic setups, including complex bimanual manipulation, by integrating parallel decoding, action chunking, and L1 regression with continuous actions.
- Real-Time Execution of Action Chunking Flow Policies (2506.07339v2): Real-Time Chunking (RTC) is an inference-time algorithm developed by Physical Intelligence and UC Berkeley that enables smooth, asynchronous execution of action chunking policies for high-latency diffusion- and flow-based Vision-Language-Action models. By treating policy execution as an inpainting problem with soft masking, RTC achieves robust performance and high task throughput on both simulated and real-world bimanual manipulation tasks, even with significant inference delays.
- VOTE: Vision-Language-Action Optimization with Trajectory Ensemble Voting (2507.05116v4)
- VLA-Cache: Efficient Vision-Language-Action Manipulation via Adaptive Token Caching (2502.02175v2): VLA-Cache introduces an adaptive token caching framework that reduces the computational overhead of Vision-Language-Action (VLA) models by intelligently reusing static and non-task-relevant visual tokens across consecutive frames. The method achieves up to 1.63x speedup in CUDA latency and a 27.31% FLOP reduction in simulations with minimal performance drop, and improves real-world robot success rates by 2.4%.
- ActiveVLA: Injecting Active Perception into Vision-Language-Action Models for Precise 3D Robotic Manipulation (2601.08325v1): Fudan University researchers developed ActiveVLA, a Vision-Language-Action (VLA) framework that injects active perception into 3D robotic manipulation by enabling robots to actively select optimal camera viewpoints and dynamically zoom in on crucial regions. This approach achieves new state-of-the-art success rates of 91.8% on RLBench and 65.9% on COLOSSEUM, and demonstrates robust performance in real-world occlusion-heavy tasks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
