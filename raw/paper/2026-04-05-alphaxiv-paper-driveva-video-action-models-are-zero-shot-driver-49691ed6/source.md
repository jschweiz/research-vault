---
id: 2026-04-05-alphaxiv-paper-driveva-video-action-models-are-zero-shot-driver-49691ed6
kind: paper
title: 'DriveVA: Video Action Models are Zero-Shot Drivers'
source_url: https://www.alphaxiv.org/abs/2604.04198
source_name: alphaXiv Papers
authors:
- Mengmeng Liu
- Diankun Zhang
- Jiuming Liu
- Jianfeng Cui
- Hongwei Xie
- Guang Chen
- Hangjun Ye
- Michael Ying Yang
- Francesco Nex
- Hao Cheng
published_at: '2026-04-05T17:43:16Z'
ingested_at: '2026-04-09T09:57:46.228025Z'
content_hash: 14c634a77c50ad1d3478bb786e93120695fc88e889da812bd05d672460f0867f
identity_hash: 5f4672d5b47214590f032b6f803f26a19ebecba971b5c1c4a433d3f8e49b0d4d
tags:
- paper
- alphaxiv
- research
- autonomous-vehicles
- Computer Science
- cs.CV
- cs.RO
- domain-adaptation
- generative-models
- multi-modal-learning
- reinforcement-learning
- robotic-control
- transfer-learning
- transformers
- zero-shot-learning
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
external_key: https://www.alphaxiv.org/abs/2604.04198
canonical_url: https://www.alphaxiv.org/abs/2604.04198
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:57:46.228031Z'
short_summary: DriveVA, an autonomous driving world model developed by researchers including those from the University of Twente and Xiaomi EV, jointly predicts future visual scene evolution and vehicle actions within a shared latent space. The model achieved a 90.9 PDM score on the NAVSIM v1 benchmark and demonstrated zero-shot generalization, reducing average L2 error by 78.9% and collision rate by 83.3% on nuScenes compared to previous state-of-the-art.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# DriveVA: Video Action Models are Zero-Shot Drivers

## alphaXiv Summary

DriveVA, an autonomous driving world model developed by researchers including those from the University of Twente and Xiaomi EV, jointly predicts future visual scene evolution and vehicle actions within a shared latent space. The model achieved a 90.9 PDM score on the NAVSIM v1 benchmark and demonstrated zero-shot generalization, reducing average L2 error by 78.9% and collision rate by 83.3% on nuScenes compared to previous state-of-the-art.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04198
- Source paper: https://arxiv.org/abs/2604.04198
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04198v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04198v1.png
- Paper ID: 2604.04198
- Canonical ID: 2604.04198v1
- Paper group ID: 019d65cf-5da1-7c36-a6d4-45ab90624c7d
- Version ID: 019d65cf-5dd1-74c8-925c-3705a2cc8712
- Version: v1
- Version order: 1
- Published at: 2026-04-05T17:43:16+00:00
- First published at: 2026-04-05T17:43:16+00:00
- Updated at: 2026-04-07T02:39:41.985000+00:00
- License: http://creativecommons.org/licenses/by-nc-nd/4.0/
- Citations: 0

## Authors

- Mengmeng Liu
- Diankun Zhang
- Jiuming Liu
- Jianfeng Cui
- Hongwei Xie
- Guang Chen
- Hangjun Ye
- Michael Ying Yang
- Francesco Nex
- Hao Cheng

## Topics

- autonomous-vehicles
- Computer Science
- cs.CV
- cs.RO
- domain-adaptation
- generative-models
- multi-modal-learning
- reinforcement-learning
- robotic-control
- transfer-learning
- transformers
- zero-shot-learning

## Metrics

- Visits (all): 103
- Visits (last 7 days): 103
- Total votes: 3
- Public total votes: 15
- X likes: 0

## Abstract

Generalization is a central challenge in autonomous driving, as real-world deployment requires robust performance under unseen scenarios, sensor domains, and environmental conditions. Recent world-model-based planning methods have shown strong capabilities in scene understanding and multi-modal future prediction, yet their generalization across datasets and sensor configurations remains limited. In addition, their loosely coupled planning paradigm often leads to poor video-trajectory consistency during visual imagination. To overcome these limitations, we propose DriveVA, a novel autonomous driving world model that jointly decodes future visual forecasts and action sequences in a shared latent generative process. DriveVA inherits rich priors on motion dynamics and physical plausibility from well-pretrained large-scale video generation models to capture continuous spatiotemporal evolution and causal interaction patterns. To this end, DriveVA employs a DiT-based decoder to jointly predict future action sequences (trajectories) and videos, enabling tighter alignment between planning and scene evolution. We also introduce a video continuation strategy to strengthen long-duration rollout consistency. DriveVA achieves an impressive closed-loop performance of 90.9 PDM score on the challenge NAVSIM. Extensive experiments also demonstrate the zero-shot capability and cross-domain generalization of DriveVA, which reduces average L2 error and collision rate by 78.9% and 83.3% on nuScenes and 52.5% and 52.4% on the Bench2drive built on CARLA v2 compared with the state-of-the-art world-model-based planner.

## Problem

- Autonomous driving models often lack generalization across diverse, unseen scenarios, sensor domains, and environmental conditions, hindering real-world deployment.
- Existing world-model-based planning methods frequently exhibit inconsistency between their visual predictions and planned vehicle actions, leading to misaligned behaviors.
- Current Vision-Language-Action (VLA) models, typically pretrained on static image-text pairs, do not adequately capture the spatiotemporal dynamics and causal interaction patterns required for robust closed-loop planning and cross-dataset transfer.

## Method

- DriveVA unifies video and action modeling by jointly decoding future visual forecasts (videos) and action sequences (trajectories) within a shared latent generative process.
- It leverages a large pre-trained video generation model (Wan2.2-TI2V-5B) as its backbone, integrating its rich spatiotemporal priors into an end-to-end planning framework.
- A single Diffusion Transformer (DiT) decoder places future video latents and action tokens in a shared latent space, enabling bidirectional interaction and mutual conditioning to ensure strong video-trajectory consistency.

## Results

- DriveVA achieved a closed-loop performance of 90.9 PDM score on the NAVSIM v1 benchmark, outperforming existing end-to-end and world-model-based methods.
- The model demonstrated strong zero-shot generalization capabilities, reducing average L2 error by 78.9% and collision rate by 83.3% on nuScenes, and L2 error by 52.5% and collision rate by 52.4% on Bench2Drive, compared to previous state-of-the-art.
- Quantitative analysis using an independent visual odometry system (DPVO) confirmed high video-trajectory consistency, with an average L2 error of 0.15m between predicted trajectories and those reconstructed from generated videos.

## Takeaways

- Integrating spatiotemporal priors from large-scale video generation models directly into an end-to-end planning framework is crucial for achieving strong zero-shot generalization in autonomous driving.
- Jointly modeling future visual imaginations and action sequences within a unified latent space significantly enhances video-trajectory consistency and overall planning performance.
- Dense video-level supervision is essential for substantial improvements in planning and for learning truly transferable priors, rather than treating video prediction as merely an auxiliary loss.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65cf-5da1-7c36-a6d4-45ab90624c7d/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65cf-5da1-7c36-a6d4-45ab90624c7d/transcript.json

## Similar Papers

- Epona: Autoregressive Diffusion World Model for Autonomous Driving (2506.24113v1): Epona, developed by researchers from Horizon Robotics and several universities, introduces an autoregressive diffusion world model for autonomous driving that generates minutes-long, high-fidelity future driving scenes while enabling real-time, accurate trajectory planning. The model achieves a state-of-the-art FVD of 82.8 on NuScenes for video quality and a lowest 1-second collision rate of 0.01% among end-to-end planners, demonstrating implicit traffic rule understanding.
- DriveVLA-W0: World Models Amplify Data Scaling Law in Autonomous Driving (2510.12796v2): DriveVLA-W0 introduces a world modeling paradigm for Vision-Language-Action models in autonomous driving, addressing their supervision deficit and demonstrating amplified data scaling laws with increasing dataset size. This approach achieves state-of-the-art performance on NAVSIM benchmarks and improves performance on a 70M-frame dataset, while also enabling real-time deployment through a lightweight action expert.
- Vista: A Generalizable Driving World Model with High Fidelity and Versatile Controllability (2405.17398v5): Vista introduces a driving world model that generates high-fidelity, long-horizon future predictions at 10 Hz and 576x1024 resolution, capable of cross-dataset generalization and versatile control via various action modalities. The model also functions as a generalizable reward function by leveraging its prediction uncertainty to evaluate actions.
- Distilling Multi-modal Large Language Models for Autonomous Driving (2501.09757v1): This paper introduces a framework for distilling knowledge from multi-modal language models into vision-based autonomous driving systems to improve robustness while maintaining efficiency
- Drive-JEPA: Video JEPA Meets Multimodal Trajectory Distillation for End-to-End Driving (2601.22032v1): Drive-JEPA integrates V-JEPA video pretraining with multimodal trajectory distillation to develop an end-to-end autonomous driving framework, achieving state-of-the-art performance on NAVSIM v2 with 87.8 EPDMS and Bench2Drive with a 64.52 Driving Score using only a single front-view camera. This approach effectively learns planning-aligned representations and diverse driving behaviors.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
