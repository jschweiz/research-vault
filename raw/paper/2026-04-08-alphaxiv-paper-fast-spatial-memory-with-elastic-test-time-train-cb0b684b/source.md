---
id: 2026-04-08-alphaxiv-paper-fast-spatial-memory-with-elastic-test-time-train-cb0b684b
kind: paper
title: Fast Spatial Memory with Elastic Test-Time Training
source_url: https://www.alphaxiv.org/abs/2604.07350
source_name: alphaXiv Papers
authors:
- Ziqiao Ma
- Xueyang Yu
- Haoyu Zhen
- Yuncong Yang
- Joyce Chai
- Chuang Gan
published_at: '2026-04-08T17:59:48Z'
ingested_at: '2026-04-09T12:06:58.538550Z'
content_hash: 488333eae899693d108a015a3436a809b33079d08f8319e47d41fa59366d59d9
identity_hash: a11bb199b030a83e4b034b1b9f2eda41bcb57163e45b4964deae9ca674010a45
tags:
- paper
- alphaxiv
- research
- computer science
- continual-learning
- cs.cv
- cs.gr
- cs.lg
- inference-optimization
- neural-rendering
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
external_key: https://www.alphaxiv.org/abs/2604.07350
canonical_url: https://www.alphaxiv.org/abs/2604.07350
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:06:58.538555Z'
short_summary: The paper introduces Fast Spatial Memory (FSM), an efficient model for 4D reconstruction that uses Elastic Test-Time Training (LaCET) to stabilize fast-weight updates. FSM learns spatiotemporal representations from long sequences to enable robust multi-chunk adaptation and high-quality novel view synthesis.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T14:34:23.341179Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: a57f58df30f5d19208f667475b160273698ff5fc122303e6328eb5e42feff7c4
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 34d02b1099d5f507811fcdf7ca633ff9856a6dab6adc88f8432b138f04a6c0b1
lightweight_score:
  relevance_score: 0.517
  source_fit_score: 0.55
  topic_fit_score: 0.4
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on 1 favorite-topic match.
  evidence_quotes:
  - The paper introduces Fast Spatial Memory (FSM), an efficient model for 4D reconstruction that uses Elastic Test-Time Training (LaCET) to stabilize fast-weight u
---
# Fast Spatial Memory with Elastic Test-Time Training

## alphaXiv Summary

Researchers from MIT-IBM Watson AI Lab, University of Michigan, and University of Massachusetts Amherst developed Elastic Test-Time Training (LaCET) to stabilize fast-weight updates in Transformer-based models, enabling robust multi-chunk adaptation for long 4D sequences. Their Fast Spatial Memory (FSM) model, incorporating LaCET, achieved a PSNR of 32.16 and LPIPS of 0.043 for 4D novel view synthesis on the Stereo4D dataset.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.07350
- Source paper: https://arxiv.org/abs/2604.07350
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.07350v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.07350v1.png
- GitHub: https://github.com/Mars-tin/fast-spatial-mem
- GitHub stars: 66
- Paper ID: 2604.07350
- Canonical ID: 2604.07350v1
- Paper group ID: 019d7000-b398-7a6d-8d19-56347f7e17ba
- Version ID: 019d7000-b3b4-75ec-be8b-7c259eeec950
- Version: v1
- Version order: 1
- Published at: 2026-04-08T17:59:48+00:00
- First published at: 2026-04-08T17:59:48+00:00
- Updated at: 2026-04-09T02:09:47.416000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Ziqiao Ma
- Xueyang Yu
- Haoyu Zhen
- Yuncong Yang
- Joyce Chai
- Chuang Gan

## Topics

- Computer Science
- continual-learning
- cs.CV
- cs.GR
- cs.LG
- inference-optimization
- neural-rendering
- online-learning
- optimization-methods
- representation-learning
- sequence-modeling

## Metrics

- Visits (all): 54
- Visits (last 7 days): 54
- Total votes: 1
- Public total votes: 1
- X likes: 0

## Abstract

Large Chunk Test-Time Training (LaCT) has shown strong performance on long-context 3D reconstruction, but its fully plastic inference-time updates remain vulnerable to catastrophic forgetting and overfitting. As a result, LaCT is typically instantiated with a single large chunk spanning the full input sequence, falling short of the broader goal of handling arbitrarily long sequences in a single pass. We propose Elastic Test-Time Training inspired by elastic weight consolidation, that stabilizes LaCT fast-weight updates with a Fisher-weighted elastic prior around a maintained anchor state. The anchor evolves as an exponential moving average of past fast weights to balance stability and plasticity. Based on this updated architecture, we introduce Fast Spatial Memory (FSM), an efficient and scalable model for 4D reconstruction that learns spatiotemporal representations from long observation sequences and renders novel view-time combinations. We pre-trained FSM on large-scale curated 3D/4D data to capture the dynamics and semantics of complex spatial environments. Extensive experiments show that FSM supports fast adaptation over long sequences and delivers high-quality 3D/4D reconstruction with smaller chunks and mitigating the camera-interpolation shortcut. Overall, we hope to advance LaCT beyond the bounded single-chunk setting toward robust multi-chunk adaptation, a necessary step for generalization to genuinely longer sequences, while substantially alleviating the activation-memory bottleneck.

## Problem

- Existing Large Reconstruction Models (LRMs) and Large View Synthesis Models (LVSMs) struggle with processing arbitrarily long 4D sequences due to activation memory constraints, leading to performance degradation beyond training context length.
- Previous Test-Time Training (TTT) methods like LaCT suffer from unstable fast-weight updates, causing catastrophic forgetting, overfitting, and instability, which limits them to single large chunks and prevents true long-sequence scalability.
- Models often exploit camera-pose interpolation shortcuts, failing to learn generalized spatiotemporal representations, which hinders performance in scenarios with sparse or novel viewpoints.

## Method

- Introduces Elastic Test-Time Training (LaCET), an enhancement to LaCT that incorporates an elastic regularization mechanism to stabilize fast-weight updates, mitigating catastrophic forgetting and overfitting during continuous adaptation.
- LaCET employs a Fisher-weighted quadratic penalty that pulls fast weights towards a dynamically evolving "anchor state," using a Streaming-EMA policy to balance stability and plasticity across multiple chunks.
- Integrates LaCET blocks into the Fast Spatial Memory (FSM) model, an end-to-end feedforward network that learns 4D scene representations from visual observations, utilizing Plücker ray maps and timestamp maps for spatiotemporal conditioning.

## Results

- FSM-LVSM achieved a PSNR of 32.16, LPIPS of 0.043, and SSIM of 0.931 on the Stereo4D dataset for 4D novel view synthesis, significantly outperforming prior rendering-based methods like MoVieS (PSNR 27.19).
- Ablation studies demonstrated that LaCET significantly reduced the generalization gap and improved stability over vanilla LaCT, with the Streaming-EMA anchoring policy showing the most effective elastic memory behavior.
- The model exhibited reduced susceptibility to camera-pose interpolation shortcuts, maintaining robust performance under sparse input views and achieving a substantially smaller performance gap between discrete-view and continuous-view regimes compared to LaCT.

## Takeaways

- Elastic regularization, particularly with a Streaming-EMA anchor update policy, effectively stabilizes fast-weight dynamics in Test-Time Training, enabling robust multi-chunk adaptation and improved information transfer over long sequences.
- Stabilized fast-weight updates help models learn more generalizable view-conditioned spatial representations, reducing the tendency to rely on camera-pose interpolation shortcuts and improving performance under sparse inputs.
- The FSM architecture, with its LaCET backbone and combined Plücker ray/timestamp map inputs, can efficiently compress visual observations into unified 4D representations for high-quality novel view synthesis.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d7000-b398-7a6d-8d19-56347f7e17ba/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7000-b398-7a6d-8d19-56347f7e17ba/transcript.json

## Resources

- GitHub repository: https://github.com/Mars-tin/fast-spatial-mem

## Similar Papers

- Test-Time Training Done Right (2505.23884v1): MIT and Adobe Research researchers develop LaCT (Large Chunk Test-Time Training), a framework that transforms test-time training from inefficient small mini-batch updates to extremely large chunk updates (2K to 1M tokens), achieving 70% GPU utilization while scaling nonlinear fast-weight networks up to 40% of model parameter size, demonstrating superior performance across three diverse tasks: novel view synthesis with 1M+ context length (39.1 PSNR vs 33.7 for Perceiver), long-context language modeling outperforming GLA and DeltaNet on retrieval accuracy, and 14B-parameter autoregressive video diffusion handling 56,000 visual tokens through pure PyTorch implementation that eliminates the need for custom kernels while integrating window attention for local dependencies.
- TTT3R: 3D Reconstruction as Test-Time Training (2509.26645v4): Researchers from Zhejiang University, Westlake University, University of Tübingen, and Tübingen AI Center developed TTT3R, a training-free approach to enhance recurrent neural network-based 3D reconstruction models. It introduces a confidence-guided state update rule that significantly improves length generalization and mitigates forgetting, reducing Absolute Translation Error by 2x on long sequences while maintaining real-time efficiency and constant memory usage.
- Streaming 4D Visual Geometry Transformer (2507.11539v2): A causal transformer model, StreamVGGT, was developed at Tsinghua University for efficient, low-latency 3D geometry reconstruction from streaming video inputs. It leverages a cached memory mechanism and knowledge distillation to provide incremental scene updates with accuracy comparable to state-of-the-art offline methods, achieving up to 2.4x faster inference and 2.2x less memory usage on shorter sequences than its teacher model.
- Video World Models with Long-term Spatial Memory (2506.05284v1): Researchers from Stanford University, Shanghai Jiao Tong University, NTU, and CUHK develop a memory-augmented video world model that overcomes the "forgetting problem" in long-term video generation by implementing three distinct memory mechanisms inspired by human cognition: working memory (recent context frames), geometry-grounded spatial memory (persistent 3D point clouds of static scenes updated via TSDF fusion), and sparse episodic memory (keyframes from previously explored regions), achieving substantial improvements in view recall consistency with 19.10 vs 11.71-12.16 PSNR when revisiting camera poses and demonstrating superior performance across VBench metrics for aesthetic quality (0.5835), temporal flickering (0.7580), and motion smoothness (0.9886) compared to baselines like TrajectoryCrafter and DaS, with the framework built upon CogVideoX-5B-I2V and trained on a custom 90K-sample dataset where static point clouds are extracted using CUT3R reconstruction and TSDF filtering to suppress dynamic elements, enabling infinite-length consistent world generation through explicit 3D geometry understanding rather than relying solely on image-based temporal contexts.
- Spatial-TTT: Streaming Visual-based Spatial Intelligence with Test-Time Training (2603.12255v1): Spatial-TTT equips Multimodal Large Language Models (MLLMs) with the ability to process and reason about 3D spaces from continuous video streams using a test-time training framework. It integrates a hybrid architecture and spatial-predictive mechanism, achieving state-of-the-art performance, including a 12.3 percentage point improvement on MindCube-Tiny and robust object counting over 120-minute videos.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
