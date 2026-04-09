# Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D

Source: alphaXiv Papers
Published: 2026-04-06T22:18:02+00:00
Canonical URL: https://www.alphaxiv.org/abs/2604.05212

## Summary

Boxer introduces an algorithm that robustly lifts open-world 2D bounding box detections to static, global 3D bounding boxes in metric world space. Its transformer-based BoxerNet, trained on a large dataset, improves 3D bounding box estimation over prior methods, particularly for smaller objects, across diverse inputs like sparse point clouds or dense depth maps.

## Audio

https://paper-podcasts.alphaxiv.org/019d6b09-94d6-756b-b5fb-6d1c19a026e3/podcast.mp3

## Text

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

## Summary

Boxer introduces an algorithm that robustly lifts open-world 2D bounding box detections to static, global 3D bounding boxes in metric world space. Its transformer-based BoxerNet, trained on a large dataset, improves 3D bounding box estimation over prior methods, particularly for smaller objects, across diverse inputs like sparse point clouds or dense depth maps.

## Takeaways

- Decoupling 2D localization from 3D lifting allows for leveraging the scalability and broad semantic coverage of existing open-world 2D detectors, while focusing the core model's capacity on precise 3D geometric estimation.
- The median depth patch encoding strategy, combined with an aleatoric uncertainty head within BoxerNet's transformer architecture, enables robust performance across various depth input types (sparse or dense) and camera models.
- Effective multi-view temporal fusion, incorporating both geometric and semantic consistency, is crucial for synthesizing stable, de-duplicated 3D object representations from individual frame predictions into a coherent scene-level understanding.
