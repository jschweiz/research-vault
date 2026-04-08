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
published_at: 2026-04-03T15:50:07Z
ingested_at: 2026-04-07T21:41:24.144696Z
content_hash: ae0405b2edce649c664b9f265f8c23be29d4e870818cedf27e9b7a46e2e83845
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
fetched_at: 2026-04-08T09:25:51.916625Z
short_summary: Researchers at the Chinese Academy of Sciences and JD.COM formally analyzed fundamental limitations in existing On-Policy Self-Distillation (OPSD) for training reasoning LLMs, then proposed a new paradigm, RLSD, that separates environment-anchored update direction from self-distilled update magnitude. RLSD achieves an average of 2.32% absolute accuracy improvement over standard GRPO on multimodal reasoning benchmarks while ensuring training stability and preventing information leakage.
lightweight_enrichment_status: failed
lightweight_enriched_at: null
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: ae0405b2edce649c664b9f265f8c23be29d4e870818cedf27e9b7a46e2e83845
lightweight_enrichment_error: "Attempt to overwrite 'operation_run_id' in LogRecord"
---
# Self-Distilled RLVR

## alphaXiv Summary

Researchers at the Chinese Academy of Sciences and JD.COM formally analyzed fundamental limitations in existing On-Policy Self-Distillation (OPSD) for training reasoning LLMs, then proposed a new paradigm, RLSD, that separates environment-anchored update direction from self-distilled update magnitude. RLSD achieves an average of 2.32% absolute accuracy improvement over standard GRPO on multimodal reasoning benchmarks while ensuring training stability and preventing information leakage.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03128
- Source paper: https://arxiv.org/abs/2604.03128
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03128v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03128v1.png
- Paper ID: 2604.03128
- Canonical ID: 2604.03128v1
- Paper group ID: 019d6086-b0ee-70bb-9a73-f40ebf136f94
- Version ID: 019d6086-b131-734a-86cd-85f6423a901b
- Version: v1
- Version order: 1
- Published at: 2026-04-03T15:50:07+00:00
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

- Visits (all): 1498
- Visits (last 7 days): 1498
- Total votes: 33
- Public total votes: 63
- X likes: 0

## Abstract

On-policy distillation (OPD) has become a popular training paradigm in the LLM community. This paradigm selects a larger model as the teacher to provide dense, fine-grained signals for each sampled trajectory, in contrast to reinforcement learning with verifiable rewards (RLVR), which only obtains sparse signals from verifiable outcomes in the environment. Recently, the community has explored on-policy self-distillation (OPSD), where the same model serves as both teacher and student, with the teacher receiving additional privileged information such as reference answers to enable self-evolution. This paper demonstrates that learning signals solely derived from the privileged teacher result in severe information leakage and unstable long-term training. Accordingly, we identify the optimal niche for self-distillation and propose \textbf{RLSD} (\textbf{RL}VR with \textbf{S}elf-\textbf{D}istillation). Specifically, we leverage self-distillation to obtain token-level policy differences for determining fine-grained update magnitudes, while continuing to use RLVR to derive reliable update directions from environmental feedback (e.g., response correctness). This enables RLSD to simultaneously harness the strengths of both RLVR and OPSD, achieving a higher convergence ceiling and superior training stability.

## Problem

- Reinforcement Learning with Verifiable Rewards (RLVR) methods struggle with sparse, sequence-level rewards, leading to coarse credit assignment for long-horizon reasoning tasks.
- On-Policy Self-Distillation (OPSD) promises dense, token-level supervision but empirically exhibits information leakage and training instability, causing performance degradation.
- Standard On-Policy Distillation (OPD) requires a separate, often larger, teacher model, leading to substantial computational overhead and scalability limitations.

## Method

- A theoretical and empirical analysis formally proves that OPSD's distribution-matching objective contains an irreducible mutual information gap, causing gradient corruption and information leakage.
- RLSD (RLVR with Self-Distillation) is proposed to repurpose the privileged teacher signal, using it solely to modulate the *magnitude* of token-level credit assignment, while environment rewards dictate the update *direction*.
- RLSD integrates with GRPO by computing a direction-aware evidence reweighting factor (`P_T/P_S` or `P_S/P_T`) for each token, which is then clipped and used to replace the uniform advantage in the GRPO objective.

## Results

- RLSD achieved the highest average accuracy across five multimodal reasoning benchmarks, surpassing the Base LLM by 4.69% and standard GRPO by 2.32% on average for a 4K context length.
- RLSD demonstrated superior training stability and a higher convergence ceiling compared to GRPO, effectively avoiding the performance degradation and information leakage observed in OPSD.
- The method effectively assigns fine-grained credit, distributing larger credit to decisive reasoning steps in correct trajectories and concentrating blame on erroneous calculations in incorrect ones, while maintaining higher entropy throughout training.

## Takeaways

- Existing OPSD methods fail due to an inherent 'irreducible mutual information gap' between the privileged teacher and less-informed student, which prevents true convergence and leads to information leakage via corrupted gradients.
- Decoupling the roles of privileged information—using it to modulate update *magnitudes* rather than as a generative target for distribution matching—resolves OPSD's fundamental issues of leakage and instability.
- Fine-grained, token-level credit assignment, when controlled by the environment reward's direction and scaled by self-distilled magnitude, significantly improves the efficiency, stability, and convergence ceiling of reasoning LLM training.

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

## AI Detection

- State: done
- Prediction: Mixed
- Headline: Mostly Human, AI Detected
- Fraction AI: 0.23685598
- Fraction AI-assisted: 0.026288025
- Fraction human: 0.736856

## Similar Papers

- Reinforcement Learning via Self-Distillation (2601.20802v2): Researchers from ETH Zurich, Max Planck Institute, MIT, and Stanford developed Self-Distillation Policy Optimization (SDPO), an on-policy algorithm that trains large language models by transforming rich environmental feedback into dense, token-level learning signals. This method yields a 10x speedup in training time, requires 4x fewer generations to reach baseline accuracy on competitive programming tasks, and enables solution discovery for hard problems with 3x fewer generations.
- Self-Distilled Reasoner: On-Policy Self-Distillation for Large Language Models (2601.18734v3): On-Policy Self-Distillation (OPSD) enables a single large language model to enhance its reasoning abilities by serving as both teacher and student, providing dense, token-level supervision on student-generated trajectories informed by ground-truth solutions. This method achieves performance comparable to or exceeding GRPO on mathematical reasoning tasks, while demonstrating 8-12x greater token efficiency.
- On-Policy Context Distillation for Language Models (2602.12275v2): On-Policy Context Distillation (OPCD) allows language models to internalize transient in-context knowledge into their permanent parameters using an on-policy training strategy and reverse Kullback-Leibler divergence. This method consistently outperforms off-policy context distillation baselines, achieving, for instance, 79.7% accuracy on a math task compared to 78.5% for the baseline, and better preserves out-of-distribution capabilities.
- ExGRPO: Learning to Reason from Experience (2510.02245v2): Researchers from University of Macau and Shanghai AI Laboratory developed ExGRPO, a framework that enhances large language model reasoning by strategically replaying past successful experiences in Reinforcement Learning from Verifiable Rewards (RLVR). ExGRPO improved performance by 3.5 to 7.6 points on reasoning benchmarks and stabilized training for weaker models by prioritizing experiences of intermediate difficulty and low-entropy reasoning chains.
- On-Policy RL Meets Off-Policy Experts: Harmonizing Supervised Fine-Tuning and Reinforcement Learning via Dynamic Weighting (2508.11408v3): Researchers at Alibaba Group developed CHORD, a framework that unifies Supervised Fine-Tuning and Reinforcement Learning for Large Language Models through dynamic weighting, employing both global and token-wise control. This approach facilitates stable and efficient learning, leading to superior performance on mathematical reasoning and tool-use tasks compared to sequential training methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
