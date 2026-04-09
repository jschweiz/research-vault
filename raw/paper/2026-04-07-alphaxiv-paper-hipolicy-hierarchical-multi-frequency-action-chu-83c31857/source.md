---
id: 2026-04-07-alphaxiv-paper-hipolicy-hierarchical-multi-frequency-action-chu-83c31857
kind: paper
title: 'HiPolicy: Hierarchical Multi-Frequency Action Chunking for Policy Learning'
source_url: https://www.alphaxiv.org/abs/2604.06067
source_name: alphaXiv Papers
authors:
- Jiyao Zhang
- Zimu Han
- Junhan Wang
- Xionghao Wu
- Shihong Lin
- Jinzhou Li
- Hongwei Fan
- Ruihai Wu
- Dongjiang Li
- Hao Dong
published_at: '2026-04-07T16:47:38Z'
ingested_at: '2026-04-09T09:58:43.186599Z'
content_hash: b1a0d89e7f9213fc4e916eac0eece1a151473d532584e57b63b4071a71d19e04
identity_hash: 0048a5dffdd2360bf80e3120f057fffbac31efaa7031fd8ccc6dc1eb96a461f7
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.RO
- github
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
external_key: https://www.alphaxiv.org/abs/2604.06067
canonical_url: https://www.alphaxiv.org/abs/2604.06067
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:58:43.186605Z'
short_summary: HiPolicy introduces a hierarchical multi-frequency action chunking framework for robotic imitation learning, enabling policies to simultaneously capture long-horizon dependencies and execute fine-grained control. The framework, incorporating an entropy-guided adaptive execution, significantly improves task success rates and execution speed across diverse simulated and real-world manipulation tasks.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# HiPolicy: Hierarchical Multi-Frequency Action Chunking for Policy Learning

## alphaXiv Summary

HiPolicy introduces a hierarchical multi-frequency action chunking framework for robotic imitation learning, enabling policies to simultaneously capture long-horizon dependencies and execute fine-grained control. The framework, incorporating an entropy-guided adaptive execution, significantly improves task success rates and execution speed across diverse simulated and real-world manipulation tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06067
- Source paper: https://arxiv.org/abs/2604.06067
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06067v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06067v1.png
- GitHub: https://github.com/HiPolicy/HiPolicy
- GitHub stars: 0
- Paper ID: 2604.06067
- Canonical ID: 2604.06067v1
- Paper group ID: 019d6b47-b547-771b-af2f-a0ad17e4029a
- Version ID: 019d6b47-b58d-765e-9ec1-4d9f9e29dd05
- Version: v1
- Version order: 1
- Published at: 2026-04-07T16:47:38+00:00
- First published at: 2026-04-07T16:47:38+00:00
- Updated at: 2026-04-08T04:09:14.823000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Jiyao Zhang
- Zimu Han
- Junhan Wang
- Xionghao Wu
- Shihong Lin
- Jinzhou Li
- Hongwei Fan
- Ruihai Wu
- Dongjiang Li
- Hao Dong

## Topics

- Computer Science
- cs.RO

## Metrics

- Visits (all): 40
- Visits (last 7 days): 40
- Total votes: 2
- Public total votes: 5
- X likes: 0

## Abstract

Robotic imitation learning faces a fundamental trade-off between modeling long-horizon dependencies and enabling fine-grained closed-loop control. Existing fixed-frequency action chunking approaches struggle to achieve both. Building on this insight, we propose HiPolicy, a hierarchical multi-frequency action chunking framework that jointly predicts action sequences at different frequencies to capture both coarse high-level plans and precise reactive motions. We extract and fuse hierarchical features from history observations aligned to each frequency for multi-frequency chunk generation, and introduce an entropy-guided execution mechanism that adaptively balances long-horizon planning with fine-grained control based on action uncertainty. Experiments on diverse simulated benchmarks and real-world manipulation tasks show that HiPolicy can be seamlessly integrated into existing 2D and 3D generative policies, delivering consistent improvements in performance while significantly enhancing execution efficiency.

## Problem

- Existing action chunking methods in robotic imitation learning face a fundamental trade-off: low-frequency chunks capture long-horizon dependencies but lack temporal resolution for precise control, while high-frequency chunks allow fine-grained adjustments but struggle with long-horizon planning.
- Conventional imitation learning approaches grapple with error accumulation and difficulty in modeling long-horizon, non-Markovian behaviors.
- Prior hierarchical approaches in robot learning have primarily focused on multi-level perceptual input or specific slow-fast policies, with few investigating a hierarchical structure for both perception and action at different temporal resolutions.

## Method

- HiPolicy jointly encodes multi-frequency observation histories and predicts a single hierarchical multi-frequency action chunk using a diffusion-based model.
- It employs Hierarchical FiLM Fusion for frequency-specific conditioning of action features and a Global Feature Fusion module, using cross-attention, to enable information exchange across different frequencies.
- An entropy-guided adaptive execution strategy dynamically selects the appropriate action frequency during inference based on the uncertainty of the predicted action chunk, balancing precision requirements with execution speed.

## Results

- HiPolicy achieved relative success rate advantages of 62% and 44% over Diffusion Policy (DP) and DP3 on RoboTwin 1.0 and 2.0 benchmarks, respectively, showing strong performance in high-precision and super-long-horizon tasks.
- Real-world experiments demonstrated a 42% higher average success rate and 14% faster average execution speed compared to the DP baseline across 8 manipulation tasks, successfully completing non-Markovian tasks like 'Close Microwave Door' where DP failed.
- Ablation studies confirmed that hierarchical observation conditioning, multi-frequency feature fusion, and the core hierarchical frequency structure are critical components, with entropy-guided execution improving speed by 25% with minimal impact on success rates.

## Takeaways

- Mimicking human motor control by explicitly modeling actions at multiple frequencies effectively reconciles the trade-off between long-horizon planning and fine-grained reactive control in robotic policies.
- Fusing features across different temporal resolutions (both frequency-specific and global) is crucial for a comprehensive policy that can interpret high-level goals and execute precise, short-term movements.
- An adaptive execution mechanism, driven by action entropy, can significantly improve both the efficiency and robustness of robotic policies by dynamically adjusting the control granularity based on the perceived uncertainty of the task state.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b47-b547-771b-af2f-a0ad17e4029a/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b47-b547-771b-af2f-a0ad17e4029a/transcript.json

## Resources

- GitHub repository: https://github.com/HiPolicy/HiPolicy

## Similar Papers

- Embodied Long Horizon Manipulation with Closed-loop Code Generation and Incremental Few-shot Adaptation (2503.21969v3): The DAHLIA framework enables robots to perform complex, multi-step manipulation tasks by generating executable code directly from natural language instructions. It employs a closed-loop dual-tunnel system with incremental few-shot adaptation, achieving high success rates on various benchmarks and demonstrating robust error recovery in real-world scenarios without relying on extensive pre-trained policies.
- H$^3$DP: Triply-Hierarchical Diffusion Policy for Visuomotor Learning (2505.07819v2): H3DP introduces a triply-hierarchical diffusion policy that enhances visuomotor learning by integrating hierarchical structures across depth-aware input, multi-scale visual representation, and action generation. The framework achieves average performance improvements of +27.5% in simulation and +32.3% in real-world bimanual tasks compared to diffusion policy baselines, particularly in cluttered and long-horizon scenarios.
- Mixture of Horizons in Action Chunking (2511.19433v1): Researchers from RUC, UNC, and CUHK introduced Mixture of Horizons (MoH), a strategy that combines predictions from multiple action chunk lengths in Vision-Language-Action (VLA) models. This approach addresses the trade-off between short-term precision and long-term foresight, achieving a 99% success rate on the LIBERO benchmark and improving real-world robotic manipulation.
- LoHoVLA: A Unified Vision-Language-Action Model for Long-Horizon  Embodied Tasks (2506.00411v1): Researchers from Fudan University, ShanghaiTech University, and Shanghai Jiao Tong University develop LoHoVLA, a unified Vision-Language-Action model that integrates high-level task planning and low-level motion control within a single framework, achieving 85.1% success on complex reasoning tasks like "put-even-blocks-in-same-color-zone" versus 8.2% for hierarchical baselines through joint prediction of linguistic sub-tasks and discrete action tokens using an augmented PaliGemma-3B backbone, while introducing a hierarchical closed-loop control mechanism that triggers sub-task re-planning only after consecutive failures exceed a threshold (K=2), thereby reducing redundant high-level planning steps, and creating LoHoSet, a synthetic dataset of 20 diverse long-horizon tasks with explicit sub-task annotations that enables two-stage training for optimal performance across both planning and control capabilities.
- MemER: Scaling Up Memory for Robot Control via Experience Retrieval (2510.20328v1): Researchers at Stanford University developed MemER, a hierarchical policy framework that equips existing generalist robot policies with long-term visual memory through intelligent experience retrieval. This method allows robots to successfully perform complex, multi-step, partially observable manipulation tasks requiring minutes of memory, outperforming memory-less and short-context baselines on real-world scenarios.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
