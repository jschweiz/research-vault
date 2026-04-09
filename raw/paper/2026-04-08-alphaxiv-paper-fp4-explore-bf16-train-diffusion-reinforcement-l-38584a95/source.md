---
id: 2026-04-08-alphaxiv-paper-fp4-explore-bf16-train-diffusion-reinforcement-l-38584a95
kind: paper
title: 'FP4 Explore, BF16 Train: Diffusion Reinforcement Learning via Efficient Rollout Scaling'
source_url: https://www.alphaxiv.org/abs/2604.06916
source_name: alphaXiv Papers
authors:
- Yitong Li
- Junsong Chen
- Shuchen Xue
- Pengcuo Zeren
- Siyuan Fu
- Dinghao Yang
- Yangyang Tang
- Junjie Bai
- Ping Luo
- Song Han
- Enze Xie
published_at: '2026-04-08T10:14:47Z'
ingested_at: '2026-04-09T10:03:18.391695Z'
content_hash: ba0cf6436dce97cfdd2b45c66511d1154f157dcff6f3e7345d70373a33821b28
identity_hash: a75f26b13015a488d945a0b2e3b9951a0c1cde34dd150475efdc288c0e96ceeb
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.AI
- cs.CV
- cs.LG
- generative-models
- hardware-aware-algorithms
- inference-optimization
- lightweight-models
- model-compression
- multi-modal-learning
- optimization-methods
- reinforcement-learning
- github
- audio
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06916
canonical_url: https://www.alphaxiv.org/abs/2604.06916
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:03:18.391700Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# FP4 Explore, BF16 Train: Diffusion Reinforcement Learning via Efficient Rollout Scaling

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06916
- Source paper: https://arxiv.org/abs/2604.06916
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06916v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06916v1.png
- GitHub: https://github.com/lyttttt3333/Sol-RL
- GitHub stars: 0
- Paper ID: 2604.06916
- Canonical ID: 2604.06916v1
- Paper group ID: 019d703d-e51b-78fc-9d94-ae3da8dab2bc
- Version ID: 019d703d-e5b5-764a-a739-6404d58b4e4c
- Version: v1
- Version order: 1
- Published at: 2026-04-08T10:14:47+00:00
- First published at: 2026-04-08T10:14:47+00:00
- Updated at: 2026-04-09T03:16:37.787000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Yitong Li
- Junsong Chen
- Shuchen Xue
- Pengcuo Zeren
- Siyuan Fu
- Dinghao Yang
- Yangyang Tang
- Junjie Bai
- Ping Luo
- Song Han
- Enze Xie

## Topics

- Computer Science
- cs.AI
- cs.CV
- cs.LG
- generative-models
- hardware-aware-algorithms
- inference-optimization
- lightweight-models
- model-compression
- multi-modal-learning
- optimization-methods
- reinforcement-learning

## Metrics

- Visits (all): 15
- Visits (last 7 days): 15
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Reinforcement-Learning-based post-training has recently emerged as a promising paradigm for aligning text-to-image diffusion models with human preferences. In recent studies, increasing the rollout group size yields pronounced performance improvements, indicating substantial room for further alignment gains. However, scaling rollouts on large-scale foundational diffusion models (e.g., FLUX.1-12B) imposes a heavy computational burden. To alleviate this bottleneck, we explore the integration of FP4 quantization into Diffusion RL rollouts. Yet, we identify that naive quantized pipelines inherently introduce risks of performance degradation. To overcome this dilemma between efficiency and training integrity, we propose Sol-RL (Speed-of-light RL), a novel FP4-empowered Two-stage Reinforcement Learning framework. First, we utilize high-throughput NVFP4 rollouts to generate a massive candidate pool and extract a highly contrastive subset. Second, we regenerate these selected samples in BF16 precision and optimize the policy exclusively on them. By decoupling candidate exploration from policy optimization, Sol-RL integrates the algorithmic mechanisms of rollout scaling with the system-level throughput gains of NVFP4. This synergistic algorithm-hardware design effectively accelerates the rollout phase while reserving high-fidelity samples for optimization. We empirically demonstrate that our framework maintains the training integrity of BF16 precision pipeline while fully exploiting the throughput gains enabled by FP4 arithmetic. Extensive experiments across SANA, FLUX.1, and SD3.5-L substantiate that our approach delivers superior alignment performance across multiple metrics while accelerating training convergence by up to $4.64\times$, unlocking the power of massive rollout scaling at a fraction of the cost.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d703d-e51b-78fc-9d94-ae3da8dab2bc/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d703d-e51b-78fc-9d94-ae3da8dab2bc/transcript.json

## Resources

- GitHub repository: https://github.com/lyttttt3333/Sol-RL

## Similar Papers

- DiffusionNFT: Online Diffusion Reinforcement with Forward Process (2509.16117v2): DiffusionNFT introduces an online reinforcement learning framework for diffusion models, optimizing the forward (noising) process via a flow matching objective and negative-aware fine-tuning. This method achieves 3x to 25x greater efficiency and superior performance compared to existing approaches, notably generating high-quality images without Classifier-Free Guidance and outperforming larger, CFG-based models in multi-reward settings.
- QeRL: Beyond Efficiency -- Quantization-enhanced Reinforcement Learning for LLMs (2510.11696v1): A framework called QeRL significantly improves the efficiency and performance of Reinforcement Learning for Large Language Models by employing hardware-accelerated NVFP4 quantization and leveraging quantization noise as a dynamic exploration mechanism. It achieves over 1.5x rollout speedup, enables training of a 32B LLM on a single GPU, and outperforms existing methods in reasoning accuracy on mathematical benchmarks.
- History Rhymes: Accelerating LLM Reinforcement Learning with RhymeRL (2508.18588v1): RhymeRL is an LLM reinforcement learning (RL) system that leverages historical rollout information to accelerate training. It achieves up to 2.6x end-to-end performance improvement over state-of-the-art methods while maintaining algorithmic accuracy and demonstrating scalability in production environments.
- Distribution Matching Distillation Meets Reinforcement Learning (2511.13649v4): Researchers from HKUST, Alibaba Group, CUHK, and other institutions developed DMDR, a two-stage framework that unifies Distribution Matching Distillation (DMD) and Reinforcement Learning (RL) for diffusion models. This approach enables few-step generative models to consistently surpass the performance of multi-step teacher models in terms of visual quality and prompt adherence, achieving higher scores on benchmarks like GenEval and DPG Bench while maintaining computational efficiency.
- Part II: ROLL Flash - Accelerating RLVR and Agentic Training with Asynchrony (2510.11345v1): ROLL Flash enhances the efficiency and scalability of Reinforcement Learning post-training for Large Language Models by introducing asynchronous execution and fine-grained parallelism. This system achieves up to 2.24x higher throughput for RLVR tasks and a 2.72x speedup for agentic tasks, while maintaining or improving final model performance.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
