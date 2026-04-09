---
id: page:2026-04-08-alphaxiv-paper-genlca-3d-diffusion-for-full-body-avatars-from-i-a129272c
page_type: source-note
title: 'GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos'
aliases:
- 'GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos'
source_refs:
- 2026-04-08-alphaxiv-paper-genlca-3d-diffusion-for-full-body-avatars-from-i-a129272c
backlinks:
- page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
- page:2026-04-05-alphaxiv-paper-aura-always-on-understanding-and-real-time-assis-1479c6fc
- page:2026-04-06-alphaxiv-paper-boxer-robust-lifting-of-open-world-2d-bounding-b-c5cf6b5c
- page:2026-04-06-alphaxiv-paper-general-multimodal-protein-design-enables-dna-en-7f68965d
- page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
- page:2026-04-07-alphaxiv-paper-neural-computers-503b0501
- page:2026-04-08-alphaxiv-paper-fast-spatial-memory-with-elastic-test-time-train-cb0b684b
- page:2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
- page:2026-04-08-alphaxiv-paper-spatialedit-benchmarking-fine-grained-image-spat-406cb2ca
- topic:computer-science
- topic:computer-vision
- topic:generative-models
- topic:geometric-deep-learning
- topic:image-generation
- topic:multi-modal-learning
updated_at: '2026-04-09T16:35:03.832889Z'
managed: true
---
# GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.07273
- Document kind: paper
- Published at: 2026-04-08T16:34:07+00:00
- Authors: Yiqian Wu, Rawal Khirodkar, Egor Zakharov, Timur Bagautdinov, Lei Xiao, Zhaoen Su, Shunsuke Saito, Xiaogang Jin, Junxuan Li
- Tags: paper, alphaxiv, research, computer science, cs.cv, generative-models, geometric-deep-learning, image-generation, multi-modal-learning, neural-rendering
- Topics: [Image Generation](../topics/image-generation.md), [Computer Science](../topics/computer-science.md), [Computer Vision](../topics/computer-vision.md), [Generative Models](../topics/generative-models.md), [Geometric Deep Learning](../topics/geometric-deep-learning.md), [Multi Modal Learning](../topics/multi-modal-learning.md)
- Trend score: 96.95
- Novelty score: 6.80

## Summary

GenLCA is a diffusion-based generative model that creates and edits photorealistic full-body avatars from text and image inputs. It achieves this by training a 3D diffusion model natively in 3D using large-scale real-world video data.

## Topic Map

- [Image Generation](../topics/image-generation.md)
- [Computer Science](../topics/computer-science.md)
- [Computer Vision](../topics/computer-vision.md)
- [Generative Models](../topics/generative-models.md)
- [Geometric Deep Learning](../topics/geometric-deep-learning.md)
- [Multi Modal Learning](../topics/multi-modal-learning.md)

## Related Research

- [SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing](spatialedit-benchmarking-fine-grained-image-spatial-editing-3317d6.md) (shared topics: Computer Science, Computer Vision, Generative Models, Geometric Deep Learning, Image Generation)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Computer Science, Generative Models, Multi Modal Learning)
- [Boxer: Robust Lifting of Open-World 2D Bounding Boxes to 3D](boxer-robust-lifting-of-open-world-2d-bounding-boxes-to-3d-7de5d7.md) (shared topics: Computer Science, Computer Vision, Multi Modal Learning)
- [General Multimodal Protein Design Enables DNA-Encoding of Chemistry](general-multimodal-protein-design-enables-dna-encoding-of-chemis-734bb9.md) (shared topics: Computer Science, Generative Models, Geometric Deep Learning)
- [Fast Spatial Memory with Elastic Test-Time Training](fast-spatial-memory-with-elastic-test-time-training-7fd9ac.md) (shared topics: Computer Science, Computer Vision)
- [MoRight: Motion Control Done Right](moright-motion-control-done-right-47f0f6.md) (shared topics: Computer Science, Computer Vision)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.07273
- Source paper: https://arxiv.org/abs/2604.07273
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.07273v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.07273v1.png
- Paper ID: 2604.07273
- Canonical ID: 2604.07273v1
- Paper group ID: 019d7014-6d53-738d-8883-ffdc0c9a52de
- Version ID: 019d7014-6d98-7b75-9925-dcd0d6685c67
- Version: v1
- Version order: 1
- Published at: 2026-04-08T16:34:07+00:00
- First published at: 2026-04-08T16:34:07+00:00
- Updated at: 2026-04-09T02:31:20.147000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Yiqian Wu
- Rawal Khirodkar
- Egor Zakharov
- Timur Bagautdinov
- Lei Xiao
- Zhaoen Su
- Shunsuke Saito
- Xiaogang Jin
- Junxuan Li

## Topics

- Computer Science
- cs.CV
- generative-models
- geometric-deep-learning
- image-generation
- multi-modal-learning
- neural-rendering
- representation-learning
- transfer-learning
- video-understanding

## Metrics

- Visits (all): 42
- Visits (last 7 days): 42
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

We present GenLCA, a diffusion-based generative model for generating and editing photorealistic full-body avatars from text and image inputs. The generated avatars are faithful to the inputs, while supporting high-fidelity facial and full-body animations. The core idea is a novel paradigm that enables training a full-body 3D diffusion model from partially observable 2D data, allowing the training dataset to scale to millions of real-world videos. This scalability contributes to the superior photorealism and generalizability of GenLCA. Specifically, we scale up the dataset by repurposing a pretrained feed-forward avatar reconstruction model as an animatable 3D tokenizer, which encodes unstructured video frames into structured 3D tokens. However, most real-world videos only provide partial observations of body parts, resulting in excessive blurring or transparency artifacts in the 3D tokens. To address this, we propose a novel visibility-aware diffusion training strategy that replaces invalid regions with learnable tokens and computes losses only over valid regions. We then train a flow-based diffusion model on the token dataset, inherently maintaining the photorealism and animatability provided by the pretrained avatar reconstruction model. Our approach effectively enables the use of large-scale real-world video data to train a diffusion model natively in 3D. We demonstrate the efficacy of our method through diverse and high-fidelity generation and editing results, outperforming existing solutions by a large margin. The project page is available at this https URL.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d7014-6d53-738d-8883-ffdc0c9a52de/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7014-6d53-738d-8883-ffdc0c9a52de/transcript.json

## Similar Papers

- FaceCraft4D: Animated 3D Facial Avatar Generation from a Single Image (2504.15179v1): FaceCraft4D is a framework that generates high-quality, animatable 4D facial avatars from a single image input, achieving superior performance over existing methods in animation quality, identity preservation, and view consistency. This is accomplished by leveraging multiple forms of prior knowledge to synthesize consistent multi-view data and introducing a novel training strategy to robustly optimize a 4D representation.
- Text-based Animatable 3D Avatars with Morphable Model Alignment (2504.15835v1): AnimPortrait3D is a framework developed by researchers from ETH Zürich and Zhejiang University that generates high-quality, animatable 3D head avatars from text descriptions. It addresses challenges in appearance-geometry alignment and animation fidelity through a two-stage process, enabling realistic expressions and poses.
- Gaussian Variation Field Diffusion for Hig
