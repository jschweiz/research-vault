---
id: 2026-04-08-alphaxiv-paper-improving-local-feature-matching-by-entropy-insp-2ef6c499
kind: paper
title: Improving Local Feature Matching by Entropy-inspired Scale Adaptability and Flow-endowed Local Consistency
source_url: https://www.alphaxiv.org/abs/2604.06713
source_name: alphaXiv Papers
authors:
- Ke Jin
- Jiming Chen
- Qi Ye
published_at: '2026-04-08T06:12:46Z'
ingested_at: '2026-04-09T10:02:39.623744Z'
content_hash: e6da809e08af9124e4ff38ff09c477ac36cb2c536d69b7651ac2508d212f10cf
identity_hash: 75a4311b84d18992c263d04db5f6d420b2ee7006f4772d3e39bc9e445c48b760
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CV
- optimization-methods
- representation-learning
- audio
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06713
canonical_url: https://www.alphaxiv.org/abs/2604.06713
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:02:39.623748Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Improving Local Feature Matching by Entropy-inspired Scale Adaptability and Flow-endowed Local Consistency

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06713
- Source paper: https://arxiv.org/abs/2604.06713
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06713v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06713v1.png
- Paper ID: 2604.06713
- Canonical ID: 2604.06713v1
- Paper group ID: 019d7022-69ff-771b-9003-6fb8a4ccdc92
- Version ID: 019d7022-6a25-7280-b5de-fa013f293893
- Version: v1
- Version order: 1
- Published at: 2026-04-08T06:12:46+00:00
- First published at: 2026-04-08T06:12:46+00:00
- Updated at: 2026-04-09T02:46:36.799000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Ke Jin
- Jiming Chen
- Qi Ye

## Topics

- Computer Science
- cs.CV
- optimization-methods
- representation-learning

## Metrics

- Visits (all): 16
- Visits (last 7 days): 16
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Recent semi-dense image matching methods have achieved remarkable success, but two long-standing issues still impair their performance. At the coarse stage, the over-exclusion issue of their mutual nearest neighbor (MNN) matching layer makes them struggle to handle cases with scale difference between images. To this end, we comprehensively revisit the matching mechanism and make a key observation that the hint concealed in the score matrix can be exploited to indicate the scale ratio. Based on this, we propose a scale-aware matching module which is exceptionally effective but introduces negligible overhead. At the fine stage, we point out that existing methods neglect the local consistency of final matches, which undermines their robustness. To this end, rather than independently predicting the correspondence for each source pixel, we reformulate the fine stage as a cascaded flow refinement problem and introduce a novel gradient loss to encourage local consistency of the flow field. Extensive experiments demonstrate that our novel matching pipeline, with these proposed modifications, achieves robust and accurate matching performance on downstream tasks.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d7022-69ff-771b-9003-6fb8a4ccdc92/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7022-69ff-771b-9003-6fb8a4ccdc92/transcript.json

## Similar Papers

- Grounding Image Matching in 3D with MASt3R (2406.09756v1): MASt3R, developed by NAVER LABS Europe, presents an image matching framework that explicitly incorporates 3D scene information to establish pixel correspondences. The method achieves a 30% absolute improvement in VCRE AUC on the map-free localization benchmark and sets new state-of-the-art results for relative pose estimation on CO3Dv2 and RealEstate10k datasets.
- RoMa: Robust Dense Feature Matching (2305.15404v2): RoMa introduces a robust dense feature matching model that combines frozen DINOv2 features for coarse matching with specialized ConvNet features for fine localization, alongside a Transformer decoder and a scale-aware loss formulation. The approach achieves state-of-the-art performance across multiple benchmarks, including a 36% improvement in mean Average Accuracy on the WxBS benchmark for robustness.
- RoMa v2: Harder Better Faster Denser Feature Matching (2511.15706v2): RoMa v2 introduces a dense feature matching model that establishes new state-of-the-art accuracy and robustness across diverse benchmarks by leveraging DINOv3 features and novel multi-view context. The model achieves 1.7 times faster throughput than its predecessor while maintaining a similar memory footprint and also predicts pixel-wise error covariances.
- CoMatch: Dynamic Covisibility-Aware Transformer for Bilateral  Subpixel-Level Semi-Dense Image Matching (2503.23925v1): CoMatch, from Wuhan University, proposes a semi-dense image matcher that leverages a dynamic covisibility-aware Transformer and bilateral subpixel refinement to enhance feature distinctiveness and match precision. The method achieves state-of-the-art accuracy on relative pose estimation and homography estimation benchmarks while being significantly faster than comparable dense matching approaches.
- MambaGlue: Fast and Robust Local Feature Matching With Mamba (2502.00462v1): KAIST and MIT researchers introduce MambaGlue, a novel feature matching framework that combines Mamba and Transformer architectures to achieve superior accuracy and speed in local feature matching, demonstrating significant improvements in homography estimation and visual localization while maintaining practical computational efficiency.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
