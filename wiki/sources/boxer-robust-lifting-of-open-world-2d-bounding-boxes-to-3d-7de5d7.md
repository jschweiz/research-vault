---
id: page:2026-04-06-alphaxiv-paper-boxer-robust-lifting-of-open-world-2d-bounding-b-c5cf6b5c
page_type: source-note
title: 'Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D'
aliases:
- 'Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D'
source_refs:
- 2026-04-06-alphaxiv-paper-boxer-robust-lifting-of-open-world-2d-bounding-b-c5cf6b5c
backlinks:
- page:2026-04-08-alphaxiv-paper-fast-spatial-memory-with-elastic-test-time-train-cb0b684b
- page:2026-04-08-alphaxiv-paper-genlca-3d-diffusion-for-full-body-avatars-from-i-a129272c
- page:2026-04-08-alphaxiv-paper-spatialedit-benchmarking-fine-grained-image-spat-406cb2ca
- topic:computer-vision
- topic:multi-modal-learning
- topic:object-detection
- topic:robotics-perception
- topic:transfer-learning
updated_at: '2026-04-09T16:35:03.812896Z'
managed: true
---
# Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.05212
- Document kind: paper
- Published at: 2026-04-06T22:18:02+00:00
- Authors: Daniel DeTone, Tianwei Shen, Fan Zhang, Lingni Ma, Julian Straub, Richard Newcombe, Jakob Engel
- Tags: paper, alphaxiv, research, computer science, cs.cv, multi-modal-learning, object-detection, robotics-perception, transfer-learning, transformers
- Topics: [Computer Vision](../topics/computer-vision.md), [Computer Science](../topics/computer-science.md), [Multi Modal Learning](../topics/multi-modal-learning.md), [Object Detection](../topics/object-detection.md), [Robotics Perception](../topics/robotics-perception.md), [Transfer Learning](../topics/transfer-learning.md)
- Trend score: 96.95
- Novelty score: 6.80

## Summary

Boxer introduces an algorithm that robustly lifts open-world 2D bounding box detections to static, global 3D bounding boxes in metric world space. Its transformer-based BoxerNet, trained on a large dataset, improves 3D bounding box estimation over prior methods, particularly for smaller objects, across diverse inputs like sparse point clouds or dense depth maps.

## Topic Map

- [Computer Vision](../topics/computer-vision.md)
- [Computer Science](../topics/computer-science.md)
- [Multi Modal Learning](../topics/multi-modal-learning.md)
- [Object Detection](../topics/object-detection.md)
- [Robotics Perception](../topics/robotics-perception.md)
- [Transfer Learning](../topics/transfer-learning.md)

## Related Research

- [GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos](genlca-3d-diffusion-for-full-body-avatars-from-in-the-wild-video-d8c0b8.md) (shared topics: Computer Science, Computer Vision, Multi Modal Learning)
- [Fast Spatial Memory with Elastic Test-Time Training](fast-spatial-memory-with-elastic-test-time-training-7fd9ac.md) (shared topics: Computer Science, Computer Vision)
- [MoRight: Motion Control Done Right](moright-motion-control-done-right-47f0f6.md) (shared topics: Computer Science, Computer Vision)
- [SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing](spatialedit-benchmarking-fine-grained-image-spatial-editing-3317d6.md) (shared topics: Computer Science, Computer Vision)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Computer Science, Multi Modal Learning)
- [MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale](mineru2-5-pro-pushing-the-limits-of-data-centric-document-parsin-394662.md) (shared topics: Computer Science, Computer Vision)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
- A transformer-based network, BoxerNet, is introduced to lift 2D bounding box proposals into 7-DoF 3D bounding boxes, integrating visual features, median depth patch encoding (for diverse depth inputs), and camera cal
