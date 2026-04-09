---
id: 2026-04-07-alphaxiv-paper-omnicamera-a-unified-framework-for-multi-task-vi-7b3fb9a9
kind: paper
title: 'OmniCamera: A Unified Framework for Multi-task Video Generation with Arbitrary Camera Control'
source_url: https://www.alphaxiv.org/abs/2604.06010
source_name: alphaXiv Papers
authors:
- Yukun Wang
- Ruihuang Li
- Jiale Tao
- Shiyuan Yang
- Liyi Chen
- Zhantao Yang
- Handz
- Yulan Guo
- Shuai Shao
- Qinglin Lu
published_at: '2026-04-07T16:06:02Z'
ingested_at: '2026-04-09T09:58:52.667977Z'
content_hash: 6b14c0c64f4833cbd46eb818e4f179b59dbc93d6a4b08db5ffd5941a1ecc1646
identity_hash: 86529ce444f80b3ebe94cffce70bf6821b47ac9f8026a1091d5809a7ccd73dd5
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CV
- domain-adaptation
- generative-models
- multi-modal-learning
- multi-task-learning
- representation-learning
- synthetic-data
- transfer-learning
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
external_key: https://www.alphaxiv.org/abs/2604.06010
canonical_url: https://www.alphaxiv.org/abs/2604.06010
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:58:52.667981Z'
short_summary: OmniCamera is a unified framework for multi-task video generation that disentangles scene content from camera pose. It enables arbitrary combinations of three camera conditions (text, 3D trajectory, motion reference video) and three content conditions (text, image, source video), achieving enhanced control and photorealistic output across nine distinct generation tasks using a single model.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# OmniCamera: A Unified Framework for Multi-task Video Generation with Arbitrary Camera Control

## alphaXiv Summary

OmniCamera is a unified framework for multi-task video generation that disentangles scene content from camera pose. It enables arbitrary combinations of three camera conditions (text, 3D trajectory, motion reference video) and three content conditions (text, image, source video), achieving enhanced control and photorealistic output across nine distinct generation tasks using a single model.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06010
- Source paper: https://arxiv.org/abs/2604.06010
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06010v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06010v1.png
- Paper ID: 2604.06010
- Canonical ID: 2604.06010v1
- Paper group ID: 019d6acf-bb69-7fa0-b070-a715fa8d2e39
- Version ID: 019d6acf-bb9d-7653-85c5-b7e219cdfa78
- Version: v1
- Version order: 1
- Published at: 2026-04-07T16:06:02+00:00
- First published at: 2026-04-07T16:06:02+00:00
- Updated at: 2026-04-08T01:58:12.073000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Yukun Wang
- Ruihuang Li
- Jiale Tao
- Shiyuan Yang
- Liyi Chen
- Zhantao Yang
- Handz
- Yulan Guo
- Shuai Shao
- Qinglin Lu

## Topics

- Computer Science
- cs.CV
- domain-adaptation
- generative-models
- multi-modal-learning
- multi-task-learning
- representation-learning
- synthetic-data
- transfer-learning

## Metrics

- Visits (all): 44
- Visits (last 7 days): 44
- Total votes: 0
- Public total votes: 4
- X likes: 0

## Abstract

Video fundamentally intertwines two crucial axes: the dynamic content of a scene and the camera motion through which it is observed. However, existing generation models often entangle these factors, limiting independent control. In this work, we introduce OmniCamera, a unified framework designed to explicitly disentangle and command these two dimensions. This compositional approach enables flexible video generation by allowing arbitrary pairings of camera and content conditions, unlocking unprecedented creative control. To overcome the fundamental challenges of modality conflict and data scarcity inherent in such a system, we present two key innovations. First, we construct OmniCAM, a novel hybrid dataset combining curated real-world videos with synthetic data that provides diverse paired examples for robust multi-task learning. Second, we propose a Dual-level Curriculum Co-Training strategy that mitigates modality interference and synergistically learns from diverse data sources. This strategy operates on two levels: first, it progressively introduces control modalities by difficulties (condition-level), and second, trains for precise control on synthetic data before adapting to real data for photorealism (data-level). As a result, OmniCamera achieves state-of-the-art performance, enabling flexible control for complex camera movements while maintaining superior visual quality.

## Problem

- Existing video generation models often entangle scene content and camera motion, hindering independent and flexible control and limiting creative possibilities.
- Current camera control methods are typically restricted to a single modality, each with inherent limitations (e.g., text is too coarse, 3D trajectories are hard to acquire), and generally lack unification.
- A significant challenge is the scarcity of high-quality real-world data with precise camera annotations, essential for training models that balance photorealism and accurate control.

## Method

- Proposes OmniCamera, a unified framework that explicitly decouples video generation into independent scene content and camera pose control, supporting nine distinct task combinations within a single model.
- Constructs OmniCAM, a hybrid dataset combining 500K synthetic UE5 videos with precise camera pose annotations and 300K curated real-world videos with estimated trajectories.
- Introduces a Dual-level Curriculum Co-Training strategy, progressively introducing conditioning modalities and integrating synthetic and real data to mitigate modality conflicts and domain gaps.
- Employs 3D Condition Rotary Positional Embeddings (RoPE) to address spatial-temporal ambiguity and disentangle different control modalities effectively.

## Results

- Achieved significantly improved motion accuracy for text-controlled camera motion (e.g., 92.4% MotionAcc for T2V vs. 31.4% for baseline) while maintaining competitive visual fidelity.
- Demonstrated highly accurate camera motion control for reference-video and 3D trajectory inputs, outperforming baselines with lower translation and rotation errors (e.g., 2.064 TransErr for T2V vs. 7.542 for AC3D).
- Successfully combined distinct camera conditions for composite effects and maintained high visual quality across all nine multi-task generation combinations using a single parameter-efficient model.

## Takeaways

- Explicitly decoupling scene content and camera motion is crucial for achieving flexible, precise, and multi-modal control in video generation.
- A hybrid training dataset, leveraging the precision of synthetic data and the realism of curated real-world data, is essential for robust models that excel in both geometric accuracy and visual quality.
- A progressive, dual-level curriculum strategy is effective for stable training of multi-task, multi-modal video generation models, preventing optimization collapse and representation conflicts.
- Conditions with more explicit geometric information (e.g., 3D trajectories) tend to override less precise inputs (e.g., text) when multiple, potentially conflicting, camera conditions are provided.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6acf-bb69-7fa0-b070-a715fa8d2e39/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6acf-bb69-7fa0-b070-a715fa8d2e39/transcript.json

## Similar Papers

- ReCamMaster: Camera-Controlled Generative Rendering from A Single Video (2503.11647v2): ReCamMaster introduces a framework for camera-controlled generative video re-rendering, enabling the synthesis of new videos from a single input video with novel camera trajectories. The method leverages a novel "Frame Dimension Conditioning" mechanism and a large-scale synthetic dataset, achieving improved visual quality, camera accuracy, and view synchronization over prior approaches.
- Uni3C: Unifying Precisely 3D-Enhanced Camera and Human Motion Controls for Video Generation (2504.14899v2): The Uni3C framework from Alibaba DAMO Academy and Fudan University unifies precise 3D-enhanced camera and human motion controls for video generation, utilizing a lightweight, plug-and-play module and global 3D world guidance to achieve superior control accuracy and video quality compared to existing methods. This approach reduces hallucination rates while supporting flexible motion transfer and preserving foundational model generalization.
- TrajectoryCrafter: Redirecting Camera Trajectory for Monocular Videos  via Diffusion Models (2503.05638v1): Tencent and CUHK researchers introduce TrajectoryCrafter, a groundbreaking framework that enables high-quality camera trajectory redirection in monocular videos through an innovative dual-stream diffusion model, achieving state-of-the-art performance in novel view synthesis while maintaining temporal consistency through clever separation of view transformation and content generation.
- ConMo: Controllable Motion Disentanglement and Recomposition for  Zero-Shot Motion Transfer (2504.02451v1): Researchers from Peking University and BUPT introduce ConMo, a framework for zero-shot motion transfer in text-to-video generation that disentangles and recomposes individual subject motions from reference videos, enabling precise control over multiple subjects while preserving motion accuracy across different shapes and semantics.
- Plenoptic Video Generation (2601.05239v1): PlenopticDreamer, developed by NVIDIA, CUHK, and Georgia Tech, introduces an autoregressive, memory-based framework for camera-controlled video re-rendering that enforces spatio-temporal consistency across multiple views. It achieves superior view synchronization with the highest Matched Pixels (41.2K) and lowest FVD (425.8) on the Basic benchmark, while also supporting diverse camera transformations and coherent long-video generation.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
