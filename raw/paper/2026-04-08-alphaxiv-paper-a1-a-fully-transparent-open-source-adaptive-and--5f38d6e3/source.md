---
id: 2026-04-08-alphaxiv-paper-a1-a-fully-transparent-open-source-adaptive-and--5f38d6e3
kind: paper
title: 'A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model'
source_url: https://www.alphaxiv.org/abs/2604.05672
source_name: alphaXiv Papers
authors:
- Kaidong Zhang
- Jian Zhang
- Rongtao Xu
- Yu Sun
- Shuoshuo Xue
- Youpeng Wen
published_at: '2026-04-08T08:24:30Z'
ingested_at: '2026-04-09T12:06:50.157230Z'
content_hash: f1e6070b38e8d58a68d312ca1a79508834095d408d130998aa74b07ccb3a0c7a
identity_hash: 1559fcba401fe2cf1a3f0da41bfa8ca6af42beec23a899c4e2be8fc9c4266b85
tags:
- paper
- alphaxiv
- research
- computer science
- cs.ro
- github
- audio
- summary
- vision-language-action
- robotics
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
external_key: https://www.alphaxiv.org/abs/2604.05672
canonical_url: https://www.alphaxiv.org/abs/2604.05672
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:06:50.157237Z'
short_summary: A1 is a fully open-source Vision-Language-Action (VLA) framework that efficiently controls robots by adaptively accelerating the VLM backbone and action head. It achieves significant reductions in inference time while maintaining high manipulation success rates across various tasks.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T14:34:23.313241Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 62b869f72fbbbd2fae6c78b2a22179f3f07f73dec6485e5bb42058d350b43078
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 6733d9ac2a3e398f068f79e53903251b76ba2c67f5939b90dfd58ef153ca20df
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
  - A1 is a fully open-source Vision-Language-Action (VLA) framework that efficiently controls robots by adaptively accelerating the VLM backbone and action head. I
---
# A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model

## alphaXiv Summary

Researchers from SYSU and MBZUAI developed A1, a fully open-source Vision-Language-Action (VLA) framework designed for efficient, real-time robotic control. A1 adaptively accelerates both its VLM backbone and flow-matching action head, achieving up to a 72.3% reduction in inference time while maintaining high manipulation success rates across diverse real-world and simulated tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05672
- Source paper: https://arxiv.org/abs/2604.05672
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05672v2.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05672v2.png
- GitHub: https://github.com/ATeam-Research/A1
- GitHub stars: 3
- Paper ID: 2604.05672
- Canonical ID: 2604.05672v2
- Paper group ID: 019d6acc-c27f-798f-a358-b7c5679e836e
- Version ID: 019d6faa-c31c-7ec7-ac99-66cb8f3adec3
- Version: v2
- Version order: 2
- Published at: 2026-04-08T08:24:30+00:00
- First published at: 2026-04-07T10:18:40+00:00
- Updated at: 2026-04-08T01:54:57.279000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Kaidong Zhang
- Jian Zhang
- Rongtao Xu
- Yu Sun
- Shuoshuo Xue
- Youpeng Wen
- Xiaoyu Guo
- Minghao Guo
- Weijia Liufu
- Liu Zihou
- Kangyi Ji
- Yangsong Zhang
- Jiarun Zhu
- Jingzhi Liu
- Zihang Li
- Ruiyi Chen
- Meng Cao
- Jingming Zhang
- Shen Zhao
- Xiaojun Chang
- Feng Zheng
- Ivan Laptev
- Xiaodan Liang

## Topics

- Computer Science
- cs.RO

## Metrics

- Visits (all): 72
- Visits (last 7 days): 72
- Total votes: 0
- Public total votes: 5
- X likes: 0

## Abstract

Vision-Language-Action (VLA) models have emerged as a powerful paradigm for open-world robot manipulation, but their practical deployment is often constrained by cost: billion-scale VLM backbones and iterative diffusion/flow-based action heads incur high latency and compute, making real-time control expensive on commodity hardware. We present A1, a fully open-source and transparent VLA framework designed for low-cost, high-throughput inference without sacrificing manipulation success; Our approach leverages pretrained VLMs that provide implicit affordance priors for action generation. We release the full training stack (training code, data/data-processing pipeline, intermediate checkpoints, and evaluation scripts) to enable end-to-end reproducibility. Beyond optimizing the VLM alone, A1 targets the full inference pipeline by introducing a budget-aware adaptive inference scheme that jointly accelerates the backbone and the action head. Specifically, we monitor action consistency across intermediate VLM layers to trigger early termination, and propose Inter-Layer Truncated Flow Matching that warm-starts denoising across layers, enabling accurate actions with substantially fewer effective denoising iterations. Across simulation benchmarks (LIBERO, VLABench) and real robots (Franka, AgiBot), A1 achieves state-of-the-art success rates while significantly reducing inference cost (e.g., up to 72% lower per-episode latency for flow-matching inference and up to 76.6% backbone computation reduction with minor performance degradation). On RoboChallenge, A1 achieves an average success rate of 29.00%, outperforming baselines including pi0(28.33%), X-VLA (21.33%), and RDT-1B (15.00%).

## Problem

- Existing Vision-Language-Action (VLA) models suffer from high computational cost and latency, primarily due to multi-billion-parameter VLM backbones and numerous iterative denoising steps in their action heads.
- The computational demands of current VLA models restrict real-time deployment on commodity hardware, necessitating expensive hardware and significant energy budgets.
- While VLM latency reduction has been explored, the action head often remains an unaddressed bottleneck, increasing overall inference time and hindering practical adoption.

## Method

- A1 integrates a Molmo-7B VLM backbone with a Qwen3-based flow-matching (A1-FM) or MLP (A1-MLP) action head, pre-trained on a diverse, large-scale robotic trajectory corpus.
- A budget-aware adaptive inference mechanism jointly accelerates the VLM and action head using multi-exit training and early-termination based on action-consistency thresholding.
- Inter-Layer Truncated Flow Matching warm-starts denoising for the FM head across VLM layers, significantly reducing iterative denoising steps from 10 to 2 and decreasing per-episode inference time.

## Results

- A1 achieved an average success rate of 96.6% on the LIBERO benchmark and 56.7% on real-world tasks across four robot platforms (Franka, AgiBot, WuJie-Arm, Dobot-Arm), outperforming baselines like π0 and π0.5.
- Inter-Layer Truncated Flow Matching reduced per-episode inference time by 72.3% (from 37.8s to 10.5s) while maintaining a 96.4% success rate, by reducing denoising steps from 10 to 2 and using warm-start initialization.
- The model demonstrated robust zero-shot generalization on the LIBERO-Plus benchmark, achieving a 75.3% success rate even under significant distribution shifts, exceeding OpenVLA-OFT (69.6%).

## Takeaways

- Flow-matching trajectories often converge to correct action modes within few denoising steps (fewer than three), indicating redundancy in extensive iterative denoising.
- Robot actions often evolve smoothly across consecutive control steps, suggesting that full VLA re-evaluation at every timestep may be inefficient.
- Intermediate hidden states within the VLM backbone can encode sufficient spatial and visual features to adequately seed downstream action prediction, allowing for earlier exits.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6acc-c27f-798f-a358-b7c5679e836e/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6acc-c27f-798f-a358-b7c5679e836e/transcript.json

## Resources

- GitHub repository: https://github.com/ATeam-Research/A1

## Similar Papers

- OpenVLA: An Open-Source Vision-Language-Action Model (2406.09246v3): OpenVLA introduces a fully open-source, 7B-parameter Vision-Language-Action model that sets a new state of the art for generalist robot manipulation, outperforming larger closed-source models by 16.5% absolute success rate. The model also demonstrates effective and efficient fine-tuning strategies for adapting to new robot setups and tasks on commodity hardware.
- Fine-Tuning Vision-Language-Action Models: Optimizing Speed and Success (2502.19645v2): Researchers at Stanford University developed an Optimized Fine-Tuning (OFT) recipe for Vision-Language-Action (VLA) models, substantially increasing their inference speed and task success on new robotic setups, including complex bimanual manipulation, by integrating parallel decoding, action chunking, and L1 regression with continuous actions.
- SmolVLA: A Vision-Language-Action Model for Affordable and Efficient  Robotics (2506.01844v1): Hugging Face researchers develop SmolVLA, a 450-million parameter vision-language-action model that achieves competitive robotic manipulation performance using 7x less memory and 40% faster training than larger VLA models like π0 (3.3B parameters), demonstrating 78.3% success rate on real-world SO-100 tasks compared to 61.7% for π0 and introducing an asynchronous inference stack that enables 30% faster task completion (9.7s vs 13.75s) by decoupling action prediction from execution, while being trained exclusively on community-contributed datasets totaling fewer than 30,000 episodes and deployable on consumer-grade hardware including CPUs.
- VLA-Adapter: An Effective Paradigm for Tiny-Scale Vision-Language-Action Model (2509.09372v2): Researchers from Beijing University of Posts and Telecommunications, Westlake University, and Zhejiang University, along with the OpenHelix Team, introduce VLA-Adapter, an efficient method to bridge vision-language representations to robotic actions. The approach enables state-of-the-art level performance with a tiny-scale 0.5B parameter backbone without robotic data pre-training, achieving a 97.3% average success rate on the LIBERO benchmark and providing a 3x faster inference speed (219.2 Hz) than comparable methods.
- VOTE: Vision-Language-Action Optimization with Trajectory Ensemble Voting (2507.05116v4)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
