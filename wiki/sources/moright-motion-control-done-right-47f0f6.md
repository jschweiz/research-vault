---
id: page:2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
page_type: source-note
title: 'MoRight: Motion Control Done Right'
aliases:
- 'MoRight: Motion Control Done Right'
source_refs:
- 2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
backlinks:
- page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
- page:2026-04-05-alphaxiv-paper-aura-always-on-understanding-and-real-time-assis-1479c6fc
- page:2026-04-06-alphaxiv-paper-boxer-robust-lifting-of-open-world-2d-bounding-b-c5cf6b5c
- page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
- page:2026-04-07-alphaxiv-paper-ai-assistance-reduces-persistence-and-hurts-inde-17db6a91
- page:2026-04-07-alphaxiv-paper-deep-researcher-agent-an-autonomous-framework-fo-7bbe612a
- page:2026-04-08-alphaxiv-paper-fast-spatial-memory-with-elastic-test-time-train-cb0b684b
- page:2026-04-08-alphaxiv-paper-genlca-3d-diffusion-for-full-body-avatars-from-i-a129272c
- page:2026-04-08-alphaxiv-paper-spatialedit-benchmarking-fine-grained-image-spat-406cb2ca
- topic:artificial-intelligence
- topic:attention-mechanisms
- topic:causal-inference
- topic:computer-science
- topic:computer-vision
- topic:cs-gr
updated_at: '2026-04-09T16:35:03.908542Z'
managed: true
---
# MoRight: Motion Control Done Right

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.07348
- Document kind: paper
- Published at: 2026-04-08T17:59:22+00:00
- Authors: Shaowei Liu, Xuanchi Ren, Tianchang Shen, Huan Ling, Saurabh Gupta, Shenlong Wang, Sanja Fidler, Jun Gao
- Tags: paper, alphaxiv, research, attention-mechanisms, causal-inference, computer science, cs.ai, cs.cv, cs.gr, cs.lg
- Topics: [Artificial Intelligence](../topics/artificial-intelligence.md), [Attention Mechanisms](../topics/attention-mechanisms.md), [Causal Inference](../topics/causal-inference.md), [Computer Science](../topics/computer-science.md), [Computer Vision](../topics/computer-vision.md), [Cs Gr](../topics/cs-gr.md)
- Trend score: 96.95
- Novelty score: 6.80

## Summary

MoRight, developed by researchers at NVIDIA and the University of Illinois Urbana-Champaign, introduces a Diffusion Transformer-based framework for controllable video generation. It achieves disentangled control of camera and object motion while integrating motion causality reasoning, allowing users to define object actions in a canonical view, independently adjust camera viewpoints, and infer physically plausible action-consequence relationships.

## Topic Map

- [Artificial Intelligence](../topics/artificial-intelligence.md)
- [Attention Mechanisms](../topics/attention-mechanisms.md)
- [Causal Inference](../topics/causal-inference.md)
- [Computer Science](../topics/computer-science.md)
- [Computer Vision](../topics/computer-vision.md)
- [Cs Gr](../topics/cs-gr.md)

## Related Research

- [Fast Spatial Memory with Elastic Test-Time Training](fast-spatial-memory-with-elastic-test-time-training-7fd9ac.md) (shared topics: Computer Science, Computer Vision, Cs Gr)
- [AI Assistance Reduces Persistence and Hurts Independent Performance](ai-assistance-reduces-persistence-and-hurts-independent-performa-21bf42.md) (shared topics: Artificial Intelligence, Causal Inference, Computer Science)
- [GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos](genlca-3d-diffusion-for-full-body-avatars-from-in-the-wild-video-d8c0b8.md) (shared topics: Computer Science, Computer Vision)
- [SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing](spatialedit-benchmarking-fine-grained-image-spatial-editing-3317d6.md) (shared topics: Computer Science, Computer Vision)
- [Neural Computers](neural-computers-2823b1.md) (shared topics: Artificial Intelligence, Computer Science)
- [Deep Researcher Agent: An Autonomous Framework for 24/7 Deep Learning Experimentation with Zero-Cost Monitoring](deep-researcher-agent-an-autonomous-framework-for-24-7-deep-lear-4ba06b.md) (shared topics: Artificial Intelligence, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# MoRight: Motion Control Done Right

## alphaXiv Summary

MoRight, developed by researchers at NVIDIA and the University of Illinois Urbana-Champaign, introduces a Diffusion Transformer-based framework for controllable video generation. It achieves disentangled control of camera and object motion while integrating motion causality reasoning, allowing users to define object actions in a canonical view, independently adjust camera viewpoints, and infer physically plausible action-consequence relationships.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.07348
- Source paper: https://arxiv.org/abs/2604.07348
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.07348v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.07348v1.png
- Paper ID: 2604.07348
- Canonical ID: 2604.07348v1
- Paper group ID: 019d6ff4-39fa-7566-9a26-8a93c1dce29b
- Version ID: 019d6ff4-3a2e-7b99-9837-027b96f0ef06
- Version: v1
- Version order: 1
- Published at: 2026-04-08T17:59:22+00:00
- First published at: 2026-04-08T17:59:22+00:00
- Updated at: 2026-04-09T01:56:09.850000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Shaowei Liu
- Xuanchi Ren
- Tianchang Shen
- Huan Ling
- Saurabh Gupta
- Shenlong Wang
- Sanja Fidler
- Jun Gao

## Topics

- attention-mechanisms
- causal-inference
- Computer Science
- cs.AI
- cs.CV
- cs.GR
- cs.LG
- cs.RO
- generative-models
- reasoning
- representation-learning
- video-understanding

## Metrics

- Visits (all): 49
- Visits (last 7 days): 49
- Total votes: 1
- Public total votes: 1
- X likes: 0

## Abstract

Generating motion-controlled videos--where user-specified actions drive physically plausible scene dynamics under freely chosen viewpoints--demands two capabilities: (1) disentangled motion control, allowing users to separately control the object motion and adjust camera viewpoint; and (2) motion causality, ensuring that user-driven actions trigger coherent reactions from other objects rather than merely displacing pixels. Existing methods fall short on both fronts: they entangle camera and object motion into a single tracking signal and treat motion as kinematic displacement without modeling causal relationships between object motion. We introduce MoRight, a unified framework that addresses both limitations through disentangled motion modeling. Object motion is specified in a canonical static-view and transferred to an arbitrary target camera viewpoint via temporal cross-view attention, enabling disentangled camera and object control. We further decompose motion into active (user-driven) and passive (consequence) components, training the model to learn motion causality from data. At inference, users can either supply active motion and MoRight predicts consequences (forward reasoning), or specify desired passive outcomes and MoRight recovers plausible driving actions (inverse reasoning), all while freely adjusting the camera viewpoint. Experiments on three benchmarks demonstrate state-of-the-art performance in generation quality, motion controllability, and interaction awareness.

## Problem

- Existing controllable video generation methods often entangle camera and object motion, making it challenging to control movements independently of the camera viewpoint.
- Current models frequently treat motion as kinematic displacement, neglecting underlying causal relationships, which requires laborious detailed inputs or external physics engines for physically plausible interactions.
- Generating interactive scenes typically demands extensive, privileged motion inputs (e.g., per-frame depth maps, 3D object trajectories) or relies on external models, increasing complexity and potential for error.

## Method

- A dual-stream Diffusion Transformer (DiT) architecture is employed, featuring a canonical stream for object motion in a static view and a target stream for the final video, interacting via shared weights and self-attention for disentangled camera-object
