---
id: 2026-04-03-alphaxiv-paper-self-distilled-rlvr-597ff1e6
kind: paper
title: Self-Distilled RLVR
source_url: https://www.alphaxiv.org/abs/2604.03128
source_name: alphaXiv Papers
authors:
- Chenxu Yang
- Chuanyu Qin
- Qingyi Si
- Minghui Chen
- Naibin Gu
- Dingyu Yao
- Zheng Lin
- Weiping Wang
- Jiaqi Wang
- Nan Duan
published_at: '2026-04-08T08:22:36Z'
ingested_at: '2026-04-07T21:41:24.144696Z'
content_hash: dc3b6f99c20c9944196a20622c6858545f78528f8c8c730d285454f28d3383af
tags:
- paper
- alphaxiv
- research
- agents
- computer science
- cs.cl
- cs.lg
- deep-reinforcement-learning
- fine-tuning
- knowledge-distillation
- Computer Science
- cs.CL
- cs.LG
- optimization-methods
- text-generation
- transformers
- audio
- transcript
- summary
status: active
asset_paths:
- alphaxiv-ai-detection.json
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.03128
canonical_url: https://www.alphaxiv.org/abs/2604.03128
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:10:11.500472Z'
short_summary: Self-Distilled RLVR (RLSD) is a post-training framework for Large Language Models that enhances reasoning capabilities by providing fine-grained, token-level credit assignment while maintaining training stability. It achieves improved average accuracy by 4.69% over the base LLM and 2.32% over standard GRPO on multimodal reasoning benchmarks.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Self-Distilled RLVR

## alphaXiv Summary

Self-Distilled RLVR (RLSD) is a post-training framework for Large Language Models that enhances reasoning capabilities by providing fine-grained, token-level credit assignment while maintaining training stability. It achieves improved average accuracy by 4.69% over the base LLM and 2.32% over standard GRPO on multimodal reasoning benchmarks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03128
- Source paper: https://arxiv.org/abs/2604.03128
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03128v2.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03128v2.png
- Paper ID: 2604.03128
- Canonical ID: 2604.03128v2
- Paper group ID: 019d6086-b0ee-70bb-9a73-f40ebf136f94
- Version ID: 019d6fb0-bfe9-70b7-af65-04c4cb27eb7d
- Version: v2
- Version order: 2
- Published at: 2026-04-08T08:22:36+00:00
- First published at: 2026-04-03T15:50:07+00:00
- Updated at: 2026-04-06T02:02:13.102000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Chenxu Yang
- Chuanyu Qin
- Qingyi Si
- Minghui Chen
- Naibin Gu
- Dingyu Yao
- Zheng Lin
- Weiping Wang
- Jiaqi Wang
- Nan Duan

## Topics

- agents
- Computer Science
- cs.CL
- cs.LG
- deep-reinforcement-learning
- fine-tuning
- knowledge-distillation
- optimization-methods
- text-generation
- transformers

## Metrics

- Visits (all): 2291
- Visits (last 7 days): 2291
- Total votes: 50
- Public total votes: 108
- X likes: 0

## Abstract

On-policy distillation (OPD) has become a popular training paradigm in the LLM community. This paradigm selects a larger model as the teacher to provide dense, fine-grained signals for each sampled trajectory, in contrast to reinforcement learning with verifiable rewards (RLVR), which only obtains sparse signals from verifiable outcomes in the environment. Recently, the community has explored on-policy self-distillation (OPSD), where the same model serves as both teacher and student, with the teacher receiving additional privileged information such as reference answers to enable self-evolution. This paper demonstrates that learning signals solely derived from the privileged teacher result in severe information leakage and unstable long-term training. Accordingly, we identify the optimal niche for self-distillation and propose \textbf{RLSD} (\textbf{RL}VR with \textbf{S}elf-\textbf{D}istillation). Specifically, we leverage self-distillation to obtain token-level policy differences for determining fine-grained update magnitudes, while continuing to use RLVR to derive reliable update directions from environmental feedback (e.g., response correctness). This enables RLSD to simultaneously harness the strengths of both RLVR and OPSD, achieving a higher convergence ceiling and superior training stability.

## Problem

- Reinforcement Learning with Verifiable Rewards (RLVR) provides sparse, scalar rewards, limiting fine-grained credit assignment crucial for complex reasoning tasks.
- On-Policy Self-Distillation (OPSD) showed promise for dense, token-level supervision but suffered from privileged information leakage, performance degradation after initial gains, and training instability.
- Traditional On-Policy Distillation (OPD) is computationally expensive, requires an external teacher model, and limits scalability due to shared vocabulary requirements.

## Method

- The proposed RLSD framework decouples update direction (from sparse environmental rewards) and update magnitude (from dense, token-level self-distillation signals).
- It reconfigures the privileged teacher's signal to function as a magnitude evaluator for per-token credit assignment, rather than a direct generative target.
- The method computes `privileged information gain (Δ_t)` and `direction-aware evidence reweighting (w_t)` to adjust token-level advantages, then applies `clipped credit assignment (Â_t)` to stabilize training and gradually mix with uniform advantage.

## Results

- RLSD achieved the highest average accuracy across five multimodal reasoning benchmarks, surpassing the Base LLM by 4.69% and standard GRPO by 2.32%.
- It demonstrated superior performance and stable training dynamics compared to OPSD, avoiding performance degradation and maintaining consistently higher entropy levels.
- RLSD showed notable performance gains on complex mathematical reasoning datasets like MathVista (+1.9% relative to GRPO) and MathVision (+3.91% relative to GRPO).

## Takeaways

- OPSD's failure stems from a theoretical limitation: an irreducible conditional mutual information gap in its objective function, rendering the distribution-matching ill-posed.
- Privileged information leakage and performance degradation in OPSD are caused by a two-phase training dynamic where `r`-specific deviation components in gradients corrupt parameter updates.
- Decoupling credit assignment into direction (from verifiable outcomes) and magnitude (from self-distillation) allows for stable, leakage-free, and efficient fine-grained learning in LLMs.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6086-b0ee-70bb-9a73-f40ebf136f94/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6086-b0ee-70bb-9a73-f40ebf136f94/transcript.json
- Transcript lines: 19
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- Reinforcement Learning via Self-Distillation (2601.20802v2): Researchers from ETH Zurich, Max Planck Institute, MIT, and Stanford developed Self-Distillation Policy Optimization (SDPO), an on-policy algorithm that trains large language models by transforming rich environmental feedback into dense, token-level learning signals. This method yields a 10x speedup in training time, requires 4x fewer generations to reach baseline accuracy on competitive programming tasks, and enables solution discovery for hard problems with 3x fewer generations.
- Self-Distilled Reasoner: On-Policy Self-Distillation for Large Language Models (2601.18734v3): On-Policy Self-Distillation (OPSD) enables a single large language model to enhance its reasoning abilities by serving as both teacher and student, providing dense, token-level supervision on student-generated trajectories informed by ground-truth solutions. This method achieves performance comparable to or exceeding GRPO on mathematical reasoning tasks, while demonstrating 8-12x greater token efficiency.
- On-Policy Context Distillation for Language Models (2602.12275v2): On-Policy Context Distillation (OPCD) allows language models to internalize transient in-context knowledge into their permanent parameters using an on-policy training strategy and reverse Kullback-Leibler divergence. This method consistently outperforms off-policy context distillation baselines, achieving, for instance, 79.7% accuracy on a math task compared to 78.5% for the baseline, and better preserves out-of-distribution capabilities.
- ExGRPO: Learning to Reason from Experience (2510.02245v2): Researchers from University of Macau and Shanghai AI Laboratory developed ExGRPO, a framework that enhances large language model reasoning by strategically replaying past successful experiences in Reinforcement Learning from Verifiable Rewards (RLVR). ExGRPO improved performance by 3.5 to 7.6 points on reasoning benchmarks and stabilized training for weaker models by prioritizing experiences of intermediate difficulty and low-entropy reasoning chains.
- On-Policy RL Meets Off-Policy Experts: Harmonizing Supervised Fine-Tuning and Reinforcement Learning via Dynamic Weighting (2508.11408v3): Researchers at Alibaba Group developed CHORD, a framework that unifies Supervised Fine-Tuning and Reinforcement Learning for Large Language Models through dynamic weighting, employing both global and token-wise control. This approach facilitates stable and efficient learning, leading to superior performance on mathematical reasoning and tool-use tasks compared to sequential training methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
