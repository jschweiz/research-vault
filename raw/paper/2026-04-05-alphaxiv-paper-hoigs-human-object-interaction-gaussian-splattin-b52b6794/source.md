---
id: 2026-04-05-alphaxiv-paper-hoigs-human-object-interaction-gaussian-splattin-b52b6794
kind: paper
title: 'HOIGS: Human-Object Interaction Gaussian Splatting'
source_url: https://www.alphaxiv.org/abs/2604.04016
source_name: alphaXiv Papers
authors:
- Taewoo Kim
- Suwoong Yeom
- Jaehyun Pyun
- Geonho Cha
- Dongyoon Wee
- Joonsik Nam
- Yun-Seong Jeong
- Kyeongbo Kong
- Suk-Ju Kang
published_at: '2026-04-05T08:27:28Z'
ingested_at: '2026-04-09T09:59:24.804871Z'
content_hash: 546ce5e40fcd5713164b7184251f55e77b305c6ebb4bf7f4e49fa89bf7e3c8c1
identity_hash: c1ca0be2f5ab3c2e29ff5984d5dbb3993ed8168d1fa959391b67cd2d9c44191e
tags:
- paper
- alphaxiv
- research
- attention-mechanisms
- Computer Science
- cs.AI
- cs.CV
- geometric-deep-learning
- image-generation
- multi-modal-learning
- neural-rendering
- representation-learning
- transformers
- video-understanding
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
external_key: https://www.alphaxiv.org/abs/2604.04016
canonical_url: https://www.alphaxiv.org/abs/2604.04016
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:59:24.804877Z'
short_summary: The HOIGS framework reconstructs dynamic human-object interactions from monocular video by disentangling human and object motions with entity-specific deformation models and unifying them via a cross-attention interaction module. This approach achieved high visual quality and geometric accuracy on HOSNeRF, BEHAVE, and ARCTIC datasets, effectively reducing common reconstruction artifacts.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# HOIGS: Human-Object Interaction Gaussian Splatting

## alphaXiv Summary

The HOIGS framework reconstructs dynamic human-object interactions from monocular video by disentangling human and object motions with entity-specific deformation models and unifying them via a cross-attention interaction module. This approach achieved high visual quality and geometric accuracy on HOSNeRF, BEHAVE, and ARCTIC datasets, effectively reducing common reconstruction artifacts.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04016
- Source paper: https://arxiv.org/abs/2604.04016
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04016v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04016v1.png
- Paper ID: 2604.04016
- Canonical ID: 2604.04016v1
- Paper group ID: 019d65e0-5172-762c-9262-9a5a696a6ae8
- Version ID: 019d65e0-51ce-7fa0-8f3f-9335508748f8
- Version: v1
- Version order: 1
- Published at: 2026-04-05T08:27:28+00:00
- First published at: 2026-04-05T08:27:28+00:00
- Updated at: 2026-04-07T02:58:12.978000+00:00
- License: http://creativecommons.org/licenses/by-nc-sa/4.0/
- Citations: 0

## Authors

- Taewoo Kim
- Suwoong Yeom
- Jaehyun Pyun
- Geonho Cha
- Dongyoon Wee
- Joonsik Nam
- Yun-Seong Jeong
- Kyeongbo Kong
- Suk-Ju Kang

## Topics

- attention-mechanisms
- Computer Science
- cs.AI
- cs.CV
- geometric-deep-learning
- image-generation
- multi-modal-learning
- neural-rendering
- representation-learning
- transformers
- video-understanding

## Metrics

- Visits (all): 32
- Visits (last 7 days): 32
- Total votes: 0
- Public total votes: 2
- X likes: 0

## Abstract

Reconstructing dynamic scenes with complex human-object interactions is a fundamental challenge in computer vision and graphics. Existing Gaussian Splatting methods either rely on human pose priors while neglecting dynamic objects, or approximate all motions within a single field, limiting their ability to capture interaction-rich dynamics. To address this gap, we propose Human-Object Interaction Gaussian Splatting (HOIGS), which explicitly models interaction-induced deformation between humans and objects through a cross-attention-based HOI module. Distinct deformation baselines are employed to extract features: HexPlane for humans and Cubic Hermite Spline (CHS) for objects. By integrating these heterogeneous features, HOIGS effectively captures interdependent motions and improves deformation estimation in scenarios involving occlusion, contact, and object manipulation. Comprehensive experiments on multiple datasets demonstrate that our method consistently outperforms state-of-the-art human-centric and 4D Gaussian approaches, highlighting the importance of explicitly modeling human-object interactions for high-fidelity reconstruction.

## Problem

- Human-centric scene reconstruction methods often neglect dynamic objects, leading to artifacts or incomplete representations in human-object interaction scenarios.
- General dynamic scene reconstruction (4D Gaussian Splatting) struggles to capture high-frequency details of human articulation and rigid object movements due to over-smoothing.
- Accurately modeling the complex, interdependent spatial and temporal relationships between humans and objects from monocular video remains a challenge.

## Method

- Employs entity-specific deformation baselines: a HexPlane-based model with SMPL-X priors for humans and Cubic Hermite Splines for object motion, tailored to their distinct kinematic properties.
- Introduces a cross-attention-based Human-Object Interaction (HOI) module to explicitly model bidirectional dependencies between humans and objects, incorporating a distance mask to filter non-interacting elements.
- Applies interaction-aware residual corrections to SMPL-X pose parameters and object Gaussian mean offsets, derived from the HOI module, to ensure interaction-consistent trajectories.

## Results

- HOIGS achieved the highest PSNR and lowest LPIPS across HOSNeRF (PSNR 25.89, LPIPS 0.114), BEHAVE (PSNR 31.51, LPIPS 0.034), and ARCTIC datasets, outperforming 4DGS and human-centric baselines.
- Produced photorealistic novel views without common artifacts such as ghosting, floating geometry, or body-background overlap, maintaining high visual fidelity in interaction regions under severe occlusion.
- Ablation studies confirmed the critical contributions of the CHS-based object deformation (approx. 0.5 PSNR gain) and the explicit cross-attention HOI module (approx. 0.65 PSNR gain) to the overall performance.

## Takeaways

- Disentangling human and object representations and applying specialized deformation strategies for each entity (articulated human vs. rigid object) significantly improves the accuracy of complex HOI reconstruction.
- Explicitly modeling bidirectional human-object dependencies through a cross-attention mechanism effectively mitigates interaction artifacts and ensures more physically plausible motion, even in close contact or occlusion.
- Leveraging robust object initialization with diffusion priors and incorporating depth supervision enhances geometric fidelity, particularly for plausibly completing 3D geometry in occluded object regions.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65e0-5172-762c-9262-9a5a696a6ae8/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65e0-5172-762c-9262-9a5a696a6ae8/transcript.json

## Similar Papers

- EgoGaussian: Dynamic Scene Understanding from Egocentric Video with 3D Gaussian Splatting (2406.19811v2): Researchers at ETH Zürich developed EgoGaussian, a method for reconstructing 3D dynamic scenes and tracking 3D object motion using only egocentric RGB video. It improves reconstruction quality over state-of-the-art dynamic 3D Gaussian Splatting methods by explicitly separating dynamic objects from the static background.
- BIGS: Bimanual Category-agnostic Interaction Reconstruction from  Monocular Videos via 3D Gaussian Splatting (2504.09097v1): BIGS reconstructs animatable 3D representations of bimanual hand-object interactions with unknown objects from monocular video by leveraging 3D Gaussian Splatting and Score Distillation Sampling for occluded region completion. It outperforms the prior state-of-the-art method HOLD on the ARCTIC dataset, achieving an F-score of 83.93 for object reconstruction compared to 63.92 and significantly improving contact accuracy.
- Reconstructing In-the-Wild Open-Vocabulary Human-Object Interactions (2503.15898v1): Researchers from Shanghai Jiao Tong University developed Open3DHOI, the first large-scale open-vocabulary 3D human-object interaction dataset sourced from real-world 2D images, and introduced the Gaussian-HOI optimizer, a training-free method leveraging 3D Gaussian Splatting to reconstruct accurate human-object interactions from single images.
- GASPACHO: Gaussian Splatting for Controllable Humans and Objects (2503.09342v2)
- Guiding Human-Object Interactions with Rich Geometry and Relations (2503.20172v1): A framework called ROG synthesizes human-object interactions by integrating rich object geometry and spatiotemporal relationships into a diffusion model through an Interactive Distance Field and a relation model. The approach achieves a Fréchet Inception Distance of 5.119 and a Top-3 R-Precision of 0.902, demonstrating enhanced realism and semantic alignment compared to prior methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
