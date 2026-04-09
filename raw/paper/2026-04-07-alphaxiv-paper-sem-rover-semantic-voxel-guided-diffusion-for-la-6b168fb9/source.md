---
id: 2026-04-07-alphaxiv-paper-sem-rover-semantic-voxel-guided-diffusion-for-la-6b168fb9
kind: paper
title: 'SEM-ROVER: Semantic Voxel-Guided Diffusion for Large-Scale Driving Scene Generation'
source_url: https://www.alphaxiv.org/abs/2604.06113
source_name: alphaXiv Papers
authors:
- Hiba Dahmani
- Nathan Piasco
- Moussab Bennehar
- Luis Roldão
- Dzmitry Tsishkou
- Laurent Caraffa
- Jean-Philippe Tarel
- Roland Brémond
published_at: '2026-04-07T17:24:29Z'
ingested_at: '2026-04-09T10:03:11.170127Z'
content_hash: 9e3016c06e7530ae1a0c2856cd3f4b835ef1cebc11c0d48a2228c29b22ecf0b4
identity_hash: 525c76cc2628b342dfde6dc223c102a1c81a44fbd75c127cd57968eca33305d3
tags:
- paper
- alphaxiv
- research
- autonomous-vehicles
- Computer Science
- cs.CV
- generative-models
- geometric-deep-learning
- image-generation
- neural-rendering
- synthetic-data
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
external_key: https://www.alphaxiv.org/abs/2604.06113
canonical_url: https://www.alphaxiv.org/abs/2604.06113
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:03:11.170135Z'
short_summary: Researchers at Huawei Paris Research Center and Gustave Eiffel University developed SEM-ROVER, a framework for generating large-scale, photorealistic 3D driving scenes by employing a novel discrete surface representation called "Voxfield", a semantic-conditioned diffusion model, and a progressive outpainting strategy. The method generates geometrically consistent scenes over 100,000 m² with an 8 GB VRAM footprint, achieving competitive image quality and enhanced multi-view robustness compared to existing approaches.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# SEM-ROVER: Semantic Voxel-Guided Diffusion for Large-Scale Driving Scene Generation

## alphaXiv Summary

Researchers at Huawei Paris Research Center and Gustave Eiffel University developed SEM-ROVER, a framework for generating large-scale, photorealistic 3D driving scenes by employing a novel discrete surface representation called "Voxfield", a semantic-conditioned diffusion model, and a progressive outpainting strategy. The method generates geometrically consistent scenes over 100,000 m² with an 8 GB VRAM footprint, achieving competitive image quality and enhanced multi-view robustness compared to existing approaches.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06113
- Source paper: https://arxiv.org/abs/2604.06113
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06113v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06113v1.png
- Paper ID: 2604.06113
- Canonical ID: 2604.06113v1
- Paper group ID: 019d6aed-aca9-744b-83d6-a2173371c9cf
- Version ID: 019d6aed-ace8-7c7f-983c-9f6547607048
- Version: v1
- Version order: 1
- Published at: 2026-04-07T17:24:29+00:00
- First published at: 2026-04-07T17:24:29+00:00
- Updated at: 2026-04-08T02:30:54.377000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Hiba Dahmani
- Nathan Piasco
- Moussab Bennehar
- Luis Roldão
- Dzmitry Tsishkou
- Laurent Caraffa
- Jean-Philippe Tarel
- Roland Brémond

## Topics

- autonomous-vehicles
- Computer Science
- cs.CV
- generative-models
- geometric-deep-learning
- image-generation
- neural-rendering
- synthetic-data

## Metrics

- Visits (all): 19
- Visits (last 7 days): 19
- Total votes: 0
- Public total votes: 2
- X likes: 0

## Abstract

Scalable generation of outdoor driving scenes requires 3D representations that remain consistent across multiple viewpoints and scale to large areas. Existing solutions either rely on image or video generative models distilled to 3D space, harming the geometric coherence and restricting the rendering to training views, or are limited to small-scale 3D scene or object-centric generation. In this work, we propose a 3D generative framework based on $\Sigma$-Voxfield grid, a discrete representation where each occupied voxel stores a fixed number of colorized surface samples. To generate this representation, we train a semantic-conditioned diffusion model that operates on local voxel neighborhoods and uses 3D positional encodings to capture spatial structure. We scale to large scenes via progressive spatial outpainting over overlapping regions. Finally, we render the generated $\Sigma$-Voxfield grid with a deferred rendering module to obtain photorealistic images, enabling large-scale multiview-consistent 3D scene generation without per-scene optimization. Extensive experiments show that our approach can generate diverse large-scale urban outdoor scenes, renderable into photorealistic images with various sensor configurations and camera trajectories while maintaining moderate computation cost compared to existing approaches.

## Problem

- Existing 3D scene generation methods struggle to produce geometrically consistent and scalable scenes for large outdoor environments.
- Prior approaches often lack fine surface details, photorealistic appearance, or suffer from limited viewpoint consistency and editability.
- Computational overhead and memory requirements of current 3D generative models hinder their application to extensive urban driving scenes, often requiring per-scene optimization.

## Method

- A novel discrete surface representation, -Voxfield, is used to encode local geometry and appearance within voxels, providing a fixed-cardinality input for generative modeling.
- A semantic-conditioned 1D Diffusion Transformer generates local sets of -Voxfields, guided by semantic labels and 3D positional embeddings, ensuring coherent scene structure.
- A progressive spatial outpainting strategy iteratively expands scene generation to large environments, with a deferred rendering module converting the 3D output into photorealistic 2D images.

## Results

- The framework successfully generates diverse, large-scale (over 100,000 m²) urban outdoor scenes that maintain global semantic structure and local coherence, exhibiting multi-view consistency.
- Achieves competitive image quality with FID scores of 81.98 (seen views) and 89.20 (novel views), demonstrating improved robustness to viewpoint shifts compared to baselines.
- Operates with a significantly lower VRAM footprint of 8 GB (compared to up to 75 GB for other methods) and enables practical applications such as semantic editing and scene inpainting.

## Takeaways

- Direct 3D scene generation, leveraging a discrete surface representation (Σ-Voxfield) that captures local geometry and appearance, effectively addresses 3D consistency and photorealism challenges.
- A progressive spatial outpainting strategy allows for the scalable generation of arbitrarily large scenes by decoupling computational cost from overall scene size.
- Semantic conditioning and deterministic point ordering within the Σ-Voxfield representation are crucial for guiding the diffusion model and achieving high-quality, controllable 3D scene synthesis.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6aed-aca9-744b-83d6-a2173371c9cf/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6aed-aca9-744b-83d6-a2173371c9cf/transcript.json

## Similar Papers

- Generative Gaussian Splatting: Generating 3D Scenes with Video Diffusion  Priors (2503.13272v1): Meta Reality Labs researchers develop a framework that combines 3D Gaussian splatting with pre-trained video diffusion models to generate consistent 3D scenes from limited input images, achieving 20% improvement in FID scores on RealEstate10K and ScanNet++ datasets while maintaining high-quality view synthesis across arbitrary camera trajectories.
- Voyager: Long-Range and World-Consistent Video Diffusion for Explorable  3D Scene Generation (2506.04225v1): Voyager introduces a video diffusion model that generates long-range, world-consistent explorable 3D scenes by jointly producing RGB and depth videos from a single image and camera trajectory. The framework enables direct 3D scene reconstruction and scalable "infinite" world exploration with high visual and geometric fidelity.
- WorldGrow: Generating Infinite 3D World (2510.21682v1): WorldGrow presents a hierarchical framework for generating infinitely extendable 3D worlds by adapting powerful 3D foundation models. It produces continuous environments with coherent geometry and photorealistic appearance, demonstrating superior perceptual quality and structural plausibility in large-scale scenes.
- Matrix-3D: Omnidirectional Explorable 3D World Generation (2508.08086v1): Researchers from Skywork AI and collaborating institutions developed Matrix-3D, a framework that generates geometrically consistent, omnidirectional, and explorable 3D worlds from a single image or text prompt. This approach leverages trajectory-guided panoramic video diffusion and dual 3D reconstruction pipelines, achieving superior visual quality and introducing the Matrix-Pano dataset with detailed camera poses and depth annotations.
- BEV-VAE: Multi-view Image Generation with Spatial Consistency for Autonomous Driving (2507.00707v1): The BEV-VAE framework generates spatially consistent multi-view images for autonomous driving by operating within a structured 3D Bird's-Eye-View (BEV) latent space. It demonstrated improved multi-view spatial consistency compared to a large pre-trained image VAE and enabled controllable generation of diverse scenes conditioned on 3D object layouts.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
