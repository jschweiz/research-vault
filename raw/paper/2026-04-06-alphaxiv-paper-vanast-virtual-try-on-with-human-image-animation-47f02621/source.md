---
id: 2026-04-06-alphaxiv-paper-vanast-virtual-try-on-with-human-image-animation-47f02621
kind: paper
title: 'Vanast: Virtual Try-On with Human Image Animation via Synthetic Triplet Supervision'
source_url: https://www.alphaxiv.org/abs/2604.04934
source_name: alphaXiv Papers
authors:
- Hyunsoo Cha
- Wonjung Woo
- Byungjun Kim
- Hanbyul Joo
published_at: '2026-04-06T17:59:59Z'
ingested_at: '2026-04-09T10:01:32.561389Z'
content_hash: 11735109921d3236c342ff9f9af267a0c80fee7823c03d2c642dbb50c5af4ed4
identity_hash: 713fe3a66fd0e3d1ec11eb64960a8e4cccf2244519e30791b1f801b4acf54f71
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CV
- generative-models
- image-generation
- multi-modal-learning
- neural-rendering
- synthetic-data
- transformers
- zero-shot-learning
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
external_key: https://www.alphaxiv.org/abs/2604.04934
canonical_url: https://www.alphaxiv.org/abs/2604.04934
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:01:32.561399Z'
short_summary: The Vanast framework from Seoul National University introduces a single-stage video diffusion model for virtual try-on with human image animation, generating realistic and temporally consistent videos of a person wearing new garments and performing specified motions. The approach leverages a novel synthetic triplet supervision dataset and a dual-module architecture to overcome limitations of traditional multi-stage pipelines, achieving superior quantitative and qualitative results across various metrics.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Vanast: Virtual Try-On with Human Image Animation via Synthetic Triplet Supervision

## alphaXiv Summary

The Vanast framework from Seoul National University introduces a single-stage video diffusion model for virtual try-on with human image animation, generating realistic and temporally consistent videos of a person wearing new garments and performing specified motions. The approach leverages a novel synthetic triplet supervision dataset and a dual-module architecture to overcome limitations of traditional multi-stage pipelines, achieving superior quantitative and qualitative results across various metrics.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04934
- Source paper: https://arxiv.org/abs/2604.04934
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04934v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04934v1.png
- GitHub: https://github.com/snuvclab/vanast
- GitHub stars: 6
- Paper ID: 2604.04934
- Canonical ID: 2604.04934v1
- Paper group ID: 019d65d7-2948-7971-afd8-f93154c9ed37
- Version ID: 019d65d7-297d-7bef-98a4-91ac93ad503c
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:59:59+00:00
- First published at: 2026-04-06T17:59:59+00:00
- Updated at: 2026-04-07T02:48:12.872000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Hyunsoo Cha
- Wonjung Woo
- Byungjun Kim
- Hanbyul Joo

## Topics

- Computer Science
- cs.CV
- generative-models
- image-generation
- multi-modal-learning
- neural-rendering
- synthetic-data
- transformers
- zero-shot-learning

## Metrics

- Visits (all): 66
- Visits (last 7 days): 66
- Total votes: 1
- Public total votes: 10
- X likes: 0

## Abstract

We present Vanast, a unified framework that generates garment-transferred human animation videos directly from a single human image, garment images, and a pose guidance video. Conventional two-stage pipelines treat image-based virtual try-on and pose-driven animation as separate processes, which often results in identity drift, garment distortion, and front-back inconsistency. Our model addresses these issues by performing the entire process in a single unified step to achieve coherent synthesis. To enable this setting, we construct large-scale triplet supervision. Our data generation pipeline includes generating identity-preserving human images in alternative outfits that differ from garment catalog images, capturing full upper and lower garment triplets to overcome the single-garment-posed video pair limitation, and assembling diverse in-the-wild triplets without requiring garment catalog images. We further introduce a Dual Module architecture for video diffusion transformers to stabilize training, preserve pretrained generative quality, and improve garment accuracy, pose adherence, and identity preservation while supporting zero-shot garment interpolation. Together, these contributions allow Vanast to produce high-fidelity, identity-consistent animation across a wide range of garment types.

## Problem

- Existing two-stage pipelines for virtual try-on animation suffer from accumulating artifacts, identity drift, garment distortion, and front-back inconsistencies, alongside computational inefficiencies.
- A lack of large-scale, high-quality triplet supervision datasets (human image in alternative outfit, target garment, pose video) hinders the development of unified, single-stage models.
- Integrating multiple, distinct conditioning signals (human identity, garment information, pose guidance) into a single video diffusion transformer is challenging, often leading to unstable optimization or compromised output quality.

## Method

- Developed Vanast, a single-stage video diffusion model that directly generates garment-transferred human animation videos from a human image, garment images, and a pose guidance video.
- Designed a scalable pipeline to construct large-scale synthetic triplet datasets, crucially generating human images in *alternative* outfits (I_G') to compel the model to learn true garment transfer.
- Implemented a Dual Module architecture built upon a frozen Video Diffusion Transformer (DiT) backbone, distributing conditioning into specialized Human Animation and Garment Transfer modules for progressive context integration.

## Results

- Vanast consistently outperformed 16 baseline combinations, including state-of-the-art image VTON, subject-to-image generation, human animation models, and VACE variants, across most quantitative metrics (L1, LPIPS, FID, VFID, PSNR) on both Internet and ViViD datasets.
- Qualitative evaluations show Vanast produces animations with accurate pose following, precise garment transfer, faithful identity preservation, and higher overall visual fidelity compared to baselines.
- The model demonstrates zero-shot garment interpolation, multiple-garment transfer capabilities, and robust transfer from unconstrained in-the-wild garment images, maintaining temporal coherence.

## Takeaways

- Generating an identity-preserving human image wearing an *alternative* outfit (I_G') is critical for training, forcing the model to learn garment transfer rather than merely re-enacting motion with existing clothing.
- A distributed and cascaded Dual Module architecture effectively balances and propagates multiple, distinct conditioning signals (human identity, garment, pose) within a video diffusion transformer, leading to more stable and accurate generation.
- Freezing the pre-trained Video Diffusion Transformer backbone and optimizing only specialized conditioning modules allows for fast, stable convergence while preserving the backbone's high generative quality.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d7-2948-7971-afd8-f93154c9ed37/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d7-2948-7971-afd8-f93154c9ed37/transcript.json

## Resources

- GitHub repository: https://github.com/snuvclab/vanast

## Similar Papers

- Wan-Animate: Unified Character Animation and Replacement with Holistic Replication (2509.14055v1): Alibaba's HumanAIGC Team developed WAN-ANIMATE, a unified framework for character animation and replacement that delivers high-fidelity results. The open-sourced model outperforms existing open-source alternatives and is preferred over commercial products like Runway's Act-two and Bytedance's DreamActor-M1 in human evaluations across metrics like identity consistency and expression accuracy.
- 3DV-TON: Textured 3D-Guided Consistent Video Try-on via Diffusion Models (2504.17414v1): A framework combining textured 3D mesh guidance with diffusion models enables high-fidelity video try-on by reconstructing animated 3D avatars from single-frame try-on results, achieving superior temporal consistency and garment detail preservation compared to existing methods while introducing the HR-VVT dataset for evaluation of high-resolution video try-on.
- Concat-ID: Towards Universal Identity-Preserving Video Synthesis (2503.14151v3): Researchers from Renmin University of China, Tsinghua University, and Zhipu AI developed Concat-ID, a framework for identity-preserving video synthesis that leverages sequence-wise concatenation of VAE-encoded image features and existing 3D self-attention mechanisms. The method achieves superior identity consistency (ArcSim of 0.442 for single-identity) and facial editability (CLIPDist of 0.325) across single, multi-identity, and multi-subject scenarios without adding new modules or parameters, outperforming existing baselines as confirmed by quantitative metrics and user studies.
- Dress&Dance: Dress up and Dance as You Like It - Technical Preview (2508.21070v1)
- SteadyDancer: Harmonized and Coherent Human Image Animation with First-Frame Preservation (2511.19320v1): SteadyDancer introduces an Image-to-Video (I2V) framework for human image animation that prioritizes first-frame preservation and precise motion control by reconciling conflicting appearance and motion signals. The model achieves state-of-the-art video fidelity and temporal coherence, with an FVD of 326.49 on RealisDance-Val, while requiring significantly fewer training resources.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
