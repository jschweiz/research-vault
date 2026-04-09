---
id: 2026-04-06-alphaxiv-paper-loma-local-feature-matching-revisited-388a071b
kind: paper
title: 'LoMa: Local Feature Matching Revisited'
source_url: https://www.alphaxiv.org/abs/2604.04931
source_name: alphaXiv Papers
authors:
- David Nordström
- Johan Edstedt
- Georg Bökman
- Jonathan Astermark
- Anders Heyden
- Viktor Larsson
- Mårten Wadenbäck
- Michael Felsberg
- Fredrik Kahl
published_at: '2026-04-06T17:59:49Z'
ingested_at: '2026-04-09T10:00:17.266899Z'
content_hash: ed78c5bba2775901e935e878427f3a74820786a5002626bc72cbe6ee71c14e47
identity_hash: 8be398192755b413a99d25bbd40178c9a90b985aa84a32f6d090554be9582b05
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CV
- data-curation
- embedding-methods
- optimization-methods
- representation-learning
- transfer-learning
- github
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
external_key: https://www.alphaxiv.org/abs/2604.04931
canonical_url: https://www.alphaxiv.org/abs/2604.04931
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:00:17.266905Z'
short_summary: 'The paper "LoMa: Local Feature Matching Revisited" re-examines local feature matching by applying modern data-driven techniques. It develops a family of descriptor-matcher models, LoMa, which achieve new state-of-the-art performance on various benchmarks, including a challenging new dataset called HardMatch, often surpassing current dense matching and feed-forward reconstruction methods.'
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# LoMa: Local Feature Matching Revisited

## alphaXiv Summary

The paper "LoMa: Local Feature Matching Revisited" re-examines local feature matching by applying modern data-driven techniques. It develops a family of descriptor-matcher models, LoMa, which achieve new state-of-the-art performance on various benchmarks, including a challenging new dataset called HardMatch, often surpassing current dense matching and feed-forward reconstruction methods.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04931
- Source paper: https://arxiv.org/abs/2604.04931
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04931v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04931v1.png
- GitHub: https://github.com/davnords/LoMa
- GitHub stars: 6
- Paper ID: 2604.04931
- Canonical ID: 2604.04931v1
- Paper group ID: 019d65c7-67a6-77bb-bac4-67e72b9ac07c
- Version ID: 019d65c7-67e4-711c-8704-3c0004654cb8
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:59:49+00:00
- First published at: 2026-04-06T17:59:49+00:00
- Updated at: 2026-04-07T02:31:00.262000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- David Nordström
- Johan Edstedt
- Georg Bökman
- Jonathan Astermark
- Anders Heyden
- Viktor Larsson
- Mårten Wadenbäck
- Michael Felsberg
- Fredrik Kahl

## Topics

- Computer Science
- cs.CV
- data-curation
- embedding-methods
- optimization-methods
- representation-learning
- transfer-learning

## Metrics

- Visits (all): 85
- Visits (last 7 days): 85
- Total votes: 0
- Public total votes: 10
- X likes: 0

## Abstract

Local feature matching has long been a fundamental component of 3D vision systems such as Structure-from-Motion (SfM), yet progress has lagged behind the rapid advances of modern data-driven approaches. The newer approaches, such as feed-forward reconstruction models, have benefited extensively from scaling dataset sizes, whereas local feature matching models are still only trained on a few mid-sized datasets. In this paper, we revisit local feature matching from a data-driven perspective. In our approach, which we call LoMa, we combine large and diverse data mixtures, modern training recipes, scaled model capacity, and scaled compute, resulting in remarkable gains in performance. Since current standard benchmarks mainly rely on collecting sparse views from successful 3D reconstructions, the evaluation of progress in feature matching has been limited to relatively easy image pairs. To address the resulting saturation of benchmarks, we collect 1000 highly challenging image pairs from internet data into a new dataset called HardMatch. Ground truth correspondences for HardMatch are obtained via manual annotation by the authors. In our extensive benchmarking suite, we find that LoMa makes outstanding progress across the board, outperforming the state-of-the-art method ALIKED+LightGlue by +18.6 mAA on HardMatch, +29.5 mAA on WxBS, +21.4 (1m, 10$^\circ$) on InLoc, +24.2 AUC on RUBIK, and +12.4 mAA on IMC 2022. We release our code and models publicly at this https URL.

## Problem

- Local feature matching was perceived to have inherent limitations, leading to a shift in research focus towards detector-free and feed-forward methods.
- Existing local feature matching models were typically trained on limited, mid-sized datasets, hindering generalization and robustness across diverse scenarios.
- Standard benchmarks for feature matching were becoming saturated, making it difficult to meaningfully assess progress or identify remaining challenges for state-of-the-art methods.

## Method

- The authors re-evaluated local feature matching by applying modern machine learning practices, including large-scale, diverse data mixtures, advanced training recipes, and increased model capacity and computational resources.
- A diverse training dataset was curated from 17 3D datasets, encompassing wide baseline and optical flow scenarios, with some existing data re-processed to generate higher-quality ground truth.
- A novel, manually annotated benchmark, HardMatch, was introduced, consisting of 1000 highly challenging image pairs to address benchmark saturation and evaluate performance in extreme matching scenarios.

## Results

- LoMa-G achieved 54.3 mAA@10px on the new HardMatch dataset, outperforming the previous state-of-the-art sparse method (ALIKED+LightGlue) by 18.6 mAA and dense matchers like RoMa v2 (46.5 mAA).
- LoMa models established new state-of-the-art performance across numerous benchmarks, including 73.4 mAA@10px on WxBS, 89.3% mAA on IMC 2022, and significant gains in relative pose estimation (e.g., 8.4 AUC@5° on MegaDepth).
- Ablation studies confirmed that increased data scale (transitioning to the full 17-dataset mixture) and increased model capacity (embedding dimensions from 256 to 1024) were the primary drivers of performance improvements.

## Takeaways

- Local feature matching, when modernized with sufficient data scale and model capacity, can achieve performance competitive with or superior to recent detector-free methods and feed-forward reconstruction pipelines.
- Scaling training data to a diverse mixture of 17 3D datasets and increasing model capacity (e.g., embedding dimensions up to 1024) significantly improves generalization and robustness in local feature matching.
- Current standard benchmarks are saturated, underscoring the critical need for more challenging datasets like HardMatch to accurately measure progress and identify real-world failure modes in feature matching.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65c7-67a6-77bb-bac4-67e72b9ac07c/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65c7-67a6-77bb-bac4-67e72b9ac07c/transcript.json

## Resources

- GitHub repository: https://github.com/davnords/LoMa

## Similar Papers

- Grounding Image Matching in 3D with MASt3R (2406.09756v1): MASt3R, developed by NAVER LABS Europe, presents an image matching framework that explicitly incorporates 3D scene information to establish pixel correspondences. The method achieves a 30% absolute improvement in VCRE AUC on the map-free localization benchmark and sets new state-of-the-art results for relative pose estimation on CO3Dv2 and RealEstate10k datasets.
- MASt3R-SfM: a Fully-Integrated Solution for Unconstrained Structure-from-Motion (2409.19152v1): MASt3R-SfM, from the authors at CentraleSupélec, presents a Structure-from-Motion pipeline that uses foundation models for 3D vision to reconstruct 3D scenes from unconstrained image collections. The system demonstrates improved robustness in challenging scenarios like limited overlap and pure rotation, while maintaining quasi-linear complexity with the number of images.
- MapGlue: Multimodal Remote Sensing Image Matching (2503.16185v1): A large-scale multimodal remote sensing image matching framework combines saliency-enhanced feature detection with dual graph structures to achieve 961.3% improvement in matching accuracy on challenging transformations while generalizing effectively across multiple remote sensing and natural image datasets.
- RoMa: Robust Dense Feature Matching (2305.15404v2): RoMa introduces a robust dense feature matching model that combines frozen DINOv2 features for coarse matching with specialized ConvNet features for fine localization, alongside a Transformer decoder and a scale-aware loss formulation. The approach achieves state-of-the-art performance across multiple benchmarks, including a 36% improvement in mean Average Accuracy on the WxBS benchmark for robustness.
- RoMa v2: Harder Better Faster Denser Feature Matching (2511.15706v2): RoMa v2 introduces a dense feature matching model that establishes new state-of-the-art accuracy and robustness across diverse benchmarks by leveraging DINOv3 features and novel multi-view context. The model achieves 1.7 times faster throughput than its predecessor while maintaining a similar memory footprint and also predicts pixel-wise error covariances.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
