---
id: page:2026-04-08-alphaxiv-paper-spatialedit-benchmarking-fine-grained-image-spat-406cb2ca
page_type: source-note
title: 'SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing'
aliases:
- 'SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing'
source_refs:
- 2026-04-08-alphaxiv-paper-spatialedit-benchmarking-fine-grained-image-spat-406cb2ca
backlinks:
- page:2026-03-20-the-batch-research-apples-atoken-a-multimodal-model-with-a-single-e-2ba5af34
- page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
- page:2026-04-05-alphaxiv-paper-aura-always-on-understanding-and-real-time-assis-1479c6fc
- page:2026-04-06-alphaxiv-paper-boxer-robust-lifting-of-open-world-2d-bounding-b-c5cf6b5c
- page:2026-04-06-alphaxiv-paper-general-multimodal-protein-design-enables-dna-en-7f68965d
- page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
- page:2026-04-08-alphaxiv-paper-fast-spatial-memory-with-elastic-test-time-train-cb0b684b
- page:2026-04-08-alphaxiv-paper-genlca-3d-diffusion-for-full-body-avatars-from-i-a129272c
- page:2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
- topic:computer-science
- topic:computer-vision
- topic:generative-models
- topic:geometric-deep-learning
- topic:image-generation
- topic:synthetic-data
updated_at: '2026-04-09T23:10:02.365286Z'
managed: true
---
# SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04911
- Document kind: paper
- Published at: 2026-04-08T04:54:06+00:00
- Authors: Yicheng Xiao, Wenhu Zhang, Lin Song, Yukang Chen, Wenbo Li, Nan Jiang, Tianhe Ren, Haokun Lin, Wei Huang, Haoyang Huang, Xiu Li, Nan Duan, Xiaojuan Qi
- Tags: paper, alphaxiv, research, computer science, cs.cv, generative-models, geometric-deep-learning, image-generation, synthetic-data, github
- Topics: [Computer Science](../topics/computer-science.md), [Computer Vision](../topics/computer-vision.md), [Generative Models](../topics/generative-models.md), [Geometric Deep Learning](../topics/geometric-deep-learning.md), [Image Generation](../topics/image-generation.md), [Synthetic Data](../topics/synthetic-data.md)
- Trend score: 96.95
- Novelty score: 6.80

## Summary

This paper introduces SpatialEdit-Bench, a benchmark for fine-grained image spatial editing, and SpatialEdit-16B, a baseline model for spatial manipulation. It uses a synthetic dataset to evaluate perceptual plausibility and geometric fidelity in spatial editing tasks.

## Topic Map

- [Computer Science](../topics/computer-science.md)
- [Computer Vision](../topics/computer-vision.md)
- [Generative Models](../topics/generative-models.md)
- [Geometric Deep Learning](../topics/geometric-deep-learning.md)
- [Image Generation](../topics/image-generation.md)
- [Synthetic Data](../topics/synthetic-data.md)

## Related Research

- [GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos](genlca-3d-diffusion-for-full-body-avatars-from-in-the-wild-video-d8c0b8.md) (shared topics: Computer Science, Computer Vision, Generative Models, Geometric Deep Learning, Image Generation)
- [General Multimodal Protein Design Enables DNA-Encoding of Chemistry](general-multimodal-protein-design-enables-dna-encoding-of-chemis-734bb9.md) (shared topics: Computer Science, Generative Models, Geometric Deep Learning)
- [Fast Spatial Memory with Elastic Test-Time Training](fast-spatial-memory-with-elastic-test-time-training-7fd9ac.md) (shared topics: Computer Science, Computer Vision)
- [MoRight: Motion Control Done Right](moright-motion-control-done-right-47f0f6.md) (shared topics: Computer Science, Computer Vision)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Computer Science, Generative Models)
- [Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D](boxer-robust-lifting-of-open-world-2d-bounding-boxes-to-3d-7de5d7.md) (shared topics: Computer Science, Computer Vision)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
- I2EBench: A Comprehensive Benchmark for Instruction-based Image Editing (2408.14180v2): I²EBench introduces a comprehensive, multi-dimensional benchmark for evaluating instruction-based image editing models, featuring 16 fine-grained dimensions and leveraging Multimodal Large Language Models (MLLMs) for high-level assessment and SSIM for low-level tasks. Thi
