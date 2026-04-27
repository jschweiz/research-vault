---
id: 2026-04-08-alphaxiv-paper-spatialedit-benchmarking-fine-grained-image-spat-406cb2ca
kind: paper
title: 'SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing'
source_url: https://www.alphaxiv.org/abs/2604.04911
source_name: alphaXiv Papers
authors:
- Yicheng Xiao
- Wenhu Zhang
- Lin Song
- Yukang Chen
- Wenbo Li
- Nan Jiang
- Tianhe Ren
- Haokun Lin
- Wei Huang
- Haoyang Huang
- Xiu Li
- Nan Duan
- Xiaojuan Qi
published_at: '2026-04-08T04:54:06Z'
ingested_at: '2026-04-09T12:07:06.088330Z'
content_hash: 0b1f432f27260d162ef1bd516430ce51b976991678e00bd5ecb1846284a39191
identity_hash: 79f9e35edaccc3182b1adf92db1e3168e2f2481e782c90074a39660cb156c8a5
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cv
- generative-models
- geometric-deep-learning
- image-generation
- synthetic-data
- github
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04911
canonical_url: https://www.alphaxiv.org/abs/2604.04911
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:07:06.088336Z'
short_summary: This paper introduces SpatialEdit-Bench, a benchmark for fine-grained image spatial editing, and SpatialEdit-16B, a baseline model for spatial manipulation. It uses a synthetic dataset to evaluate perceptual plausibility and geometric fidelity in spatial editing tasks.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T16:19:42.845193Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: 27331e44509bd1b0a746ecf64390531fe1aada469982bae72b8e20242d41b8c1
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 3794a74c11edb8ff77bc9406a5689480ba939f9729e6423a30a977a50fbabf96
lightweight_score:
  relevance_score: 0.65
  source_fit_score: 0.55
  topic_fit_score: 0.85
  author_fit_score: 0.5
  evidence_fit_score: 0.95
  confidence_score: 0.9
  bucket_hint: worth_a_skim
  reason: The document is highly relevant due to its focus on benchmarking and synthetic data generation for generative models, aligning well with the user's interest in evaluation, reasoning, and efficiency.
  evidence_quotes:
  - We introduce SpatialEdit-Bench, a benchmark for fine-grained image spatial editing, and SpatialEdit-16B, a baseline model for spatial manipulation.
  - To address the data bottleneck for scalable training, we construct SpatialEdit-500k, a synthetic dataset generated with a controllable Blender pipeline that ren
  - Our method achieves competitive performance on general editing while substantially outperforming prior methods on spatial manipulation tasks.
---
# SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04911
- Source paper: https://arxiv.org/abs/2604.04911
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04911v2.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04911v2.png
- GitHub: https://github.com/EasonXiao-888/SpatialEdit
- GitHub stars: 44
- Paper ID: 2604.04911
- Canonical ID: 2604.04911v2
- Paper group ID: 019d65d7-b155-731f-9120-a8ca4f7ce509
- Version ID: 019d6fa8-81b1-7850-bf9b-aa94872dd1e4
- Version: v2
- Version order: 2
- Published at: 2026-04-08T04:54:06+00:00
- First published at: 2026-04-06T17:54:42+00:00
- Updated at: 2026-04-07T02:48:47.701000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Yicheng Xiao
- Wenhu Zhang
- Lin Song
- Yukang Chen
- Wenbo Li
- Nan Jiang
- Tianhe Ren
- Haokun Lin
- Wei Huang
- Haoyang Huang
- Xiu Li
- Nan Duan
- Xiaojuan Qi

## Topics

- Computer Science
- cs.CV
- generative-models
- geometric-deep-learning
- image-generation
- synthetic-data

## Metrics

- Visits (all): 74
- Visits (last 7 days): 74
- Total votes: 1
- Public total votes: 7
- X likes: 0

## Abstract

Image spatial editing performs geometry-driven transformations, allowing precise control over object layout and camera viewpoints. Current models are insufficient for fine-grained spatial manipulations, motivating a dedicated assessment suite. Our contributions are listed: (i) We introduce SpatialEdit-Bench, a complete benchmark that evaluates spatial editing by jointly measuring perceptual plausibility and geometric fidelity via viewpoint reconstruction and framing analysis. (ii) To address the data bottleneck for scalable training, we construct SpatialEdit-500k, a synthetic dataset generated with a controllable Blender pipeline that renders objects across diverse backgrounds and systematic camera trajectories, providing precise ground-truth transformations for both object- and camera-centric operations. (iii) Building on this data, we develop SpatialEdit-16B, a baseline model for fine-grained spatial editing. Our method achieves competitive performance on general editing while substantially outperforming prior methods on spatial manipulation tasks. All resources will be made public at this https URL.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d65d7-b155-731f-9120-a8ca4f7ce509/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d7-b155-731f-9120-a8ca4f7ce509/transcript.json

## Resources

- GitHub repository: https://github.com/EasonXiao-888/SpatialEdit

## Similar Papers

- ImgEdit: A Unified Image Editing Dataset and Benchmark (2505.20275v1): Peking University and Peng Cheng Laboratory developed ImgEdit, a 1.2-million-pair high-quality dataset and a comprehensive benchmark, to close the performance gap between open and closed-source image editing models. Their trained ImgEdit-E1 model demonstrates state-of-the-art performance among open-source systems, particularly in novel tasks like identity-consistent object extraction.
- VoxHammer: Training-Free Precise and Coherent 3D Editing in Native 3D Space (2508.19247v1): VoxHammer offers a training-free framework for precise and coherent 3D local editing, operating directly within native 3D latent space. It achieves superior unedited region preservation, with a Chamfer Distance of 0.012 and a masked PSNR of 41.68, and also introduces the human-annotated Edit3D-Bench dataset for evaluating 3D editing performance.
- BlobCtrl: Taming Controllable Blob for Element-level Image Editing (2503.13434v2)
- I2EBench: A Comprehensive Benchmark for Instruction-based Image Editing (2408.14180v2): I²EBench introduces a comprehensive, multi-dimensional benchmark for evaluating instruction-based image editing models, featuring 16 fine-grained dimensions and leveraging Multimodal Large Language Models (MLLMs) for high-level assessment and SSIM for low-level tasks. This benchmark demonstrates strong alignment with human perception, achieving Pearson correlation coefficients of 0.75 to 0.99 across dimensions when assessing 8 state-of-the-art IIE models.
- BlenderFusion: 3D-Grounded Visual Editing and Generative Compositing (2506.17450v2): BlenderFusion is a framework from Google DeepMind that integrates generative models with 3D graphics software like Blender to enable precise, 3D-aware visual editing and generative compositing. It achieves fine-grained, disentangled control over objects, camera, and background, yielding higher fidelity outputs compared to previous methods, with a human preference of 87.04%.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
