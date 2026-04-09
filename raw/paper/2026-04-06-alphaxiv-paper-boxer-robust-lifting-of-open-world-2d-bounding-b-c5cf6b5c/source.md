---
id: 2026-04-06-alphaxiv-paper-boxer-robust-lifting-of-open-world-2d-bounding-b-c5cf6b5c
kind: paper
title: 'Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D'
source_url: https://www.alphaxiv.org/abs/2604.05212
source_name: alphaXiv Papers
authors:
- Daniel DeTone
- Tianwei Shen
- Fan Zhang
- Lingni Ma
- Julian Straub
- Richard Newcombe
published_at: '2026-04-06T22:18:02Z'
ingested_at: '2026-04-09T12:08:55.041402Z'
content_hash: e99d0cbbd166b063eab3b1beb2617b995e7d2dfd10e15db702718377597a760b
identity_hash: 65b6dae017300526100385b61fb15071ee71e9592eedb13484c654cb577c3b98
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cv
- multi-modal-learning
- object-detection
- robotics-perception
- transfer-learning
- transformers
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
external_key: https://www.alphaxiv.org/abs/2604.05212
canonical_url: https://www.alphaxiv.org/abs/2604.05212
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:08:55.041407Z'
short_summary: Boxer is an algorithm that robustly lifts open-world 2D bounding boxes to static, global 3D bounding boxes in metric world space. It uses a transformer-based network to estimate 3D bounding boxes from 2D detections, improving performance across diverse inputs.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T15:00:27.726612Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 18b213fb655ef96fd3b3f7be9943231a1e29b248057607ec6a6c65437a53607c
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 22d6d8f0c911484e04105edb3b67fba89999be709fb6430c0aacc7908b0e7e9b
lightweight_score:
  relevance_score: 0.418
  source_fit_score: 0.55
  topic_fit_score: 0.18
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on generic profile-fit fallback.
  evidence_quotes:
  - Boxer is an algorithm that robustly lifts open-world 2D bounding boxes to static, global 3D bounding boxes in metric world space. It uses a transformer-based ne
---
# Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D

## alphaXiv Summary

Boxer introduces an algorithm that robustly lifts open-world 2D bounding box detections to static, global 3D bounding boxes in metric world space. Its transformer-based BoxerNet, trained on a large dataset, improves 3D bounding box estimation over prior methods, particularly for smaller objects, across diverse inputs like sparse point clouds or dense depth maps.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05212
- Source paper: https://arxiv.org/abs/2604.05212
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05212v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05212v1.png
- GitHub: https://github.com/facebookresearch/boxer
- GitHub stars: 2
- Paper ID: 2604.05212
- Canonical ID: 2604.05212v1
- Paper group ID: 019d6b09-94d6-756b-b5fb-6d1c19a026e3
- Version ID: 019d6b09-951d-7688-abf9-cc6d1e14f3e5
- Version: v1
- Version order: 1
- Published at: 2026-04-06T22:18:02+00:00
- First published at: 2026-04-06T22:18:02+00:00
- Updated at: 2026-04-08T03:01:23.286000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Daniel DeTone
- Tianwei Shen
- Fan Zhang
- Lingni Ma
- Julian Straub
- Richard Newcombe
- Jakob Engel

## Topics

- Computer Science
- cs.CV
- multi-modal-learning
- object-detection
- robotics-perception
- transfer-learning
- transformers
- uncertainty-estimation
- zero-shot-learning

## Metrics

- Visits (all): 45
- Visits (last 7 days): 45
- Total votes: 0
- Public total votes: 1
- X likes: 0

## Abstract

Detecting and localizing objects in space is a fundamental computer vision problem. While much progress has been made to solve 2D object detection, 3D object localization is much less explored and far from solved, especially for open-world categories. To address this research challenge, we propose Boxer, an algorithm to estimate static 3D bounding boxes (3DBBs) from 2D open-vocabulary object detections, posed images and optional depth either represented as a sparse point cloud or dense depth. At its core is BoxerNet, a transformer-based network which lifts 2D bounding box (2DBB) proposals into 3D, followed by multi-view fusion and geometric filtering to produce globally consistent de-duplicated 3DBBs in metric world space. Boxer leverages the power of existing 2DBB detection algorithms (e.g. DETIC, OWLv2, SAM3) to localize objects in 2D. This allows the main BoxerNet model to focus on lifting to 3D rather than detecting, ultimately reducing the demand for costly annotated 3DBB training data. Extending the CuTR formulation, we incorporate an aleatoric uncertainty for robust regression, a median depth patch encoding to support sparse depth inputs, and large-scale training with over 1.2 million unique 3DBBs. BoxerNet outperforms state-of-the-art baselines in open-world 3DBB lifting, including CuTR in egocentric settings without dense depth (0.532 vs. 0.010 mAP) and on CA-1M with dense depth available (0.412 vs. 0.250 mAP).

## Problem

- Open-world 3D object localization is hindered by the high cost and limited availability of metric 3D bounding box annotations compared to readily available 2D data.
- Existing 'closed-set' 3D detection methods are often restricted to predefined categories, sensitive to specific camera models or sensor modalities, and struggle with diverse 3D data.
- There is a lack of a universal interface that effectively integrates powerful open-world 2D semantics with precise metric 3D geometry, adaptable to various geometric cues and camera types.

## Method

- The 3D detection problem is decomposed into two stages: utilizing off-the-shelf open-world 2D detectors for initial localization, followed by a dedicated metric 3D lifting process.
- A transformer-based network, BoxerNet, is introduced to lift 2D bounding box proposals into 7-DoF 3D bounding boxes, integrating visual features, median depth patch encoding (for diverse depth inputs), and camera calibration information.
- A multi-view temporal fusion pipeline aggregates per-frame 3D predictions into globally consistent, de-duplicated 3DBBs for the entire scene, employing geometric and semantic filtering, clustering, and rotation-aware averaging.

## Results

- BoxerNet consistently outperforms state-of-the-art baselines, including CuTR and 3D-MOOD, in per-frame 3D bounding box estimation, achieving significant mAP improvements (e.g., 0.296 mAP vs. CuTR's 0.010 mAP on NymeriaPlus with RGB and ground truth 2D boxes).
- The multi-view temporal fusion stage further enhances performance in per-scene 3D detection, producing more stable and consistent global 3DBBs across datasets (e.g., 0.278 mAP on NymeriaPlus with RGB+Depth for BoxerNet with OWLv2, compared to 0.013 mAP for CuTR).
- Ablation studies demonstrate the importance of depth input, the aleatoric uncertainty head, and large-scale, diverse training data for Boxer's robustness, with its performance advantage over baselines being most pronounced for smaller, more frequently occurring objects.

## Takeaways

- Decoupling 2D localization from 3D lifting allows for leveraging the scalability and broad semantic coverage of existing open-world 2D detectors, while focusing the core model's capacity on precise 3D geometric estimation.
- The median depth patch encoding strategy, combined with an aleatoric uncertainty head within BoxerNet's transformer architecture, enables robust performance across various depth input types (sparse or dense) and camera models.
- Effective multi-view temporal fusion, incorporating both geometric and semantic consistency, is crucial for synthesizing stable, de-duplicated 3D object representations from individual frame predictions into a coherent scene-level understanding.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b09-94d6-756b-b5fb-6d1c19a026e3/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b09-94d6-756b-b5fb-6d1c19a026e3/transcript.json

## Resources

- GitHub repository: https://github.com/facebookresearch/boxer

## Similar Papers

- BoxDreamer: Dreaming Box Corners for Generalizable Object Pose Estimation (2504.07955v2): A new method for generalizable object pose estimation determines 6D poses for unseen objects using sparse RGB images by predicting 2D projections of 3D bounding box corners with a transformer decoder. It achieves state-of-the-art performance on LINEMOD and YCB-Video datasets, demonstrating particular robustness in sparse-view and occlusion conditions while maintaining real-time inference speed of 17ms per query image.
- LabelAny3D: Label Any Object 3D in the Wild (2601.01676v1): University of Virginia researchers developed LabelAny3D, an automatic pipeline that leverages vision foundation models to generate high-quality 3D bounding box annotations from single "in-the-wild" images. This method enabled the creation of COCO3D, a diverse new benchmark which, when used for training, improved open-vocabulary monocular 3D detection performance on the benchmark by 5.05 AP3D over baselines.
- LocateAnything3D: Vision-Language 3D Detection with Chain-of-Sight (2511.20648v2)
- Training an Open-Vocabulary Monocular 3D Object Detection Model without 3D Data (2411.15657v1): Researchers from Tsinghua University, NVIDIA Research, and Stanford University developed OVM3D-Det, a framework that trains open-vocabulary 3D object detectors using only RGB images, eliminating the need for expensive 3D data during training. The method demonstrates improved average precision by up to 16.8% on various datasets and exhibits strong zero-shot detection capabilities.
- OV-Uni3DETR: Towards Unified Open-Vocabulary 3D Object Detection via Cycle-Modality Propagation (2403.19580v2)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
