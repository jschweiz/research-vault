---
id: 2026-04-08-alphaxiv-paper-moright-motion-control-done-right-ca64d67b
kind: paper
title: 'MoRight: Motion Control Done Right'
source_url: https://www.alphaxiv.org/abs/2604.07348
source_name: alphaXiv Papers
authors:
- Shaowei Liu
- Xuanchi Ren
- Tianchang Shen
- Huan Ling
- Saurabh Gupta
- Shenlong Wang
- Sanja Fidler
- Jun Gao
published_at: '2026-04-08T17:59:22Z'
ingested_at: '2026-04-09T12:07:14.778708Z'
content_hash: a52052f3c800325f3fa392113efa408c733b20944eced8f34f4ebdc24583af25
identity_hash: d5794921568c46ae86bade6e2e99b3786c021ba0daa53c365b799b12609f2fac
tags:
- paper
- alphaxiv
- research
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
external_key: https://www.alphaxiv.org/abs/2604.07348
canonical_url: https://www.alphaxiv.org/abs/2604.07348
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:07:14.778714Z'
short_summary: MoRight, developed by researchers at NVIDIA and the University of Illinois Urbana-Champaign, introduces a Diffusion Transformer-based framework for controllable video generation. It achieves disentangled control of camera and object motion while integrating motion causality reasoning, allowing users to define object actions in a canonical view, independently adjust camera viewpoints, and infer physically plausible action-consequence relationships.
lightweight_enrichment_status: failed
lightweight_enriched_at: null
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 41ba29db2f6a58de385c410a3d03e7c3a77f393597ab04c0b57c3a0d2e6d510a
lightweight_enrichment_error: 'Ollama lightweight enrichment failed: timed out'
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
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

- A dual-stream Diffusion Transformer (DiT) architecture is employed, featuring a canonical stream for object motion in a static view and a target stream for the final video, interacting via shared weights and self-attention for disentangled camera-object control.
- Motion causality modeling is integrated through active/passive motion decomposition and motion dropout training, enabling the model to infer missing motion components and learn action-consequence relationships.
- A comprehensive data curation pipeline combines motion extraction, canonicalization, synthetic paired two-view video generation, and mixed training with real-world single-view data to enhance robustness and generalization.

## Results

- MoRight received superior human preference scores, with 53.5% for controllability, 54.6% for motion realism, and 55.9% for photorealism, outperforming state-of-the-art baselines.
- The framework demonstrated strong motion accuracy (e.g., best EPE and Rotation/Translation error on the Cooking benchmark) and visual quality (best FID and FVD on WISA and Cooking datasets) while maintaining consistent object dynamics.
- It achieved the highest Physical Commonsense score on WISA and successfully performed both forward (predicting consequences from actions) and inverse (inferring actions from desired outcomes) causal reasoning from sparse user inputs.

## Takeaways

- Object motion is unambiguously defined and transferred across different camera viewpoints when initially processed in a canonical static view, acting as a 'virtual anchor' within a dual-stream architecture.
- Decomposing object motion into active (user-driven) and passive (causal outcomes) components, combined with asymmetric supervision during training, enables the model to reason about and generate physically coherent action-consequence relationships.
- A hybrid training approach, leveraging both synthetic paired data for disentangled control and abundant single-view real-world data, significantly improves the model's robustness, generalization, and diversity in camera motion handling.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6ff4-39fa-7566-9a26-8a93c1dce29b/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ff4-39fa-7566-9a26-8a93c1dce29b/transcript.json

## Similar Papers

- Uni3C: Unifying Precisely 3D-Enhanced Camera and Human Motion Controls for Video Generation (2504.14899v2): The Uni3C framework from Alibaba DAMO Academy and Fudan University unifies precise 3D-enhanced camera and human motion controls for video generation, utilizing a lightweight, plug-and-play module and global 3D world guidance to achieve superior control accuracy and video quality compared to existing methods. This approach reduces hallucination rates while supporting flexible motion transfer and preserving foundational model generalization.
- Motion Prompting: Controlling Video Generation with Motion Trajectories (2412.02700v2): Researchers at Google DeepMind and partner institutions introduced "Motion Prompting," a framework for controlling video generation using spatio-temporal point trajectories. This method, built on the Lumiere model, enables fine-grained control over object and camera movements, achieving superior motion adherence and visual quality compared to baselines in both quantitative metrics and human evaluations.
- VideoMage: Multi-Subject and Motion Customization of Text-to-Video  Diffusion Models (2503.21781v1): A framework from National Taiwan University and NVIDIA enables simultaneous customization of multiple subject identities and their interactive motions in text-to-video generation through appearance-agnostic motion learning and spatial-temporal collaborative composition, addressing the appearance leakage problem while maintaining high video quality and temporal coherence.
- PhysCtrl: Generative Physics for Controllable and Physics-Grounded Video Generation (2509.20358v2): The PhysCtrl framework introduces a method for generating physically plausible videos from a single image, enabling explicit control over material properties and external forces. It leverages a diffusion-based generative physics network to produce 3D point trajectories, outperforming existing video generation and dynamics models in physical adherence, video quality, and trajectory accuracy.
- MagicMotion: Controllable Video Generation with Dense-to-Sparse Trajectory Guidance (2503.16421v3): MagicMotion, developed by Fudan University and Microsoft Research Asia, proposes a framework for controllable video generation that guides object movements from a single image using dense-to-sparse trajectories. The system, along with its introduced MagicData dataset and MagicBench evaluation platform, achieved an FID of 15.06, FVD of 112.69, and Mask IoU of 91.57% on MagicBench, outperforming existing trajectory-controllable methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
