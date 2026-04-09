---
id: 2026-04-07-alphaxiv-paper-pressure-what-pressure-sycophancy-disentanglemen-a4e42052
kind: paper
title: Pressure, What Pressure? Sycophancy Disentanglement in Language Models via Reward Decomposition
source_url: https://www.alphaxiv.org/abs/2604.05279
source_name: alphaXiv Papers
authors:
- Muhammad Ahmed Mohsin
- Ahsan Bilal
- Muhammad Umer
- Emily Fox
published_at: '2026-04-07T00:28:17Z'
ingested_at: '2026-04-09T10:01:39.865233Z'
content_hash: f6af6bbf35485ae9c3871dc10cb52b72f410d4c7ff1bc8711780d09a74bc8f81
identity_hash: 9d0a5c8b30a17264eb0151544e37882c237ff862b161ab8d0fbcda0298710bda
tags:
- paper
- alphaxiv
- research
- adversarial-robustness
- Computer Science
- cs.AI
- data-curation
- fine-tuning
- human-ai-interaction
- reasoning
- reinforcement-learning
- transformers
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
external_key: https://www.alphaxiv.org/abs/2604.05279
canonical_url: https://www.alphaxiv.org/abs/2604.05279
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:01:39.865238Z'
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
# Pressure, What Pressure? Sycophancy Disentanglement in Language Models via Reward Decomposition

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05279
- Source paper: https://arxiv.org/abs/2604.05279
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05279v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05279v1.png
- Paper ID: 2604.05279
- Canonical ID: 2604.05279v1
- Paper group ID: 019d6b83-52c7-7071-a99d-4d33f88b2b87
- Version ID: 019d6b83-52df-7543-99c3-8065cea6f986
- Version: v1
- Version order: 1
- Published at: 2026-04-07T00:28:17+00:00
- First published at: 2026-04-07T00:28:17+00:00
- Updated at: 2026-04-08T05:14:21.767000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Muhammad Ahmed Mohsin
- Ahsan Bilal
- Muhammad Umer
- Emily Fox

## Topics

- adversarial-robustness
- Computer Science
- cs.AI
- data-curation
- fine-tuning
- human-ai-interaction
- reasoning
- reinforcement-learning
- transformers

## Metrics

- Visits (all): 18
- Visits (last 7 days): 18
- Total votes: 0
- Public total votes: 1
- X likes: 0

## Abstract

Large language models exhibit sycophancy, the tendency to shift their stated positions toward perceived user preferences or authority cues regardless of evidence. Standard alignment methods fail to correct this because scalar reward models conflate two distinct failure modes into a single signal: pressure capitulation, where the model changes a correct answer under social pressure, and evidence blindness, where the model ignores the provided context entirely. We operationalise sycophancy through formal definitions of pressure independence and evidence responsiveness, serving as a working framework for disentangled training rather than a definitive characterisation of the phenomenon. We propose the first approach to sycophancy reduction via reward decomposition, introducing a multi-component Group Relative Policy Optimisation (GRPO) reward that decomposes the training signal into five terms: pressure resistance, context fidelity, position consistency, agreement suppression, and factual correctness. We train using a contrastive dataset pairing pressure-free baselines with pressured variants across three authority levels and two opposing evidence contexts. Across five base models, our two-phase pipeline consistently reduces sycophancy on all metric axes, with ablations confirming that each reward term governs an independent behavioural dimension. The learned resistance to pressure generalises beyond our training methodology and prompt structure, reducing answer-priming sycophancy by up to 17 points on SycophancyEval despite the absence of such pressure forms during training.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6b83-52c7-7071-a99d-4d33f88b2b87/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b83-52c7-7071-a99d-4d33f88b2b87/transcript.json

## Similar Papers

- GDPO: Group reward-Decoupled Normalization Policy Optimization for Multi-reward RL Optimization (2601.05242v1): GDPO (Group reward-Decoupled Normalization Policy Optimization) improves multi-reward reinforcement learning for large language model alignment by addressing "reward signal collapse" inherent in existing GRPO methods. It achieves this by decoupling the normalization of individual reward components, leading to more stable training and enhanced performance across various tasks, such as increasing mathematical reasoning accuracy by up to 6.3% on AIME.
- Optimizing Safe and Aligned Language Generation: A Multi-Objective GRPO  Approach (2503.21819v1): Researchers at HydroX AI introduce an alignment method that combines Group Relative Policy Optimization (GRPO) with a multi-label reward regression model to achieve more balanced alignment across objectives like politeness, meaningfulness, actionability, and safety. The approach demonstrates computational efficiency, training stability, and consistent quantitative improvements across various model sizes, particularly in safety.
- Improving LLM Safety Alignment with Dual-Objective Optimization (2503.03710v3): Researchers at UC Berkeley developed Dual-Objective Optimization for Refusal (DOOR) and its weighted variant (W-DOOR) to improve Large Language Model (LLM) safety alignment. This framework enhances robustness against diverse jailbreak attacks, like prefilling and multi-turn, by achieving significantly lower Attack Success Rates (ASR) while largely preserving general model capabilities, notably outperforming Direct Preference Optimization (DPO).
- Sycophancy Is Not One Thing: Causal Separation of Sycophantic Behaviors in LLMs (2509.21305v3): Researchers demonstrated that sycophantic agreement, genuine agreement, and sycophantic praise in large language models are encoded along distinct linear directions in the latent space. They showed these behaviors can be independently amplified or suppressed through targeted interventions, challenging the view of sycophancy as a monolithic phenomenon.
- ELEPHANT: Measuring and understanding social sycophancy in LLMs (2505.13995v2): Researchers from Stanford, Carnegie Mellon, and Oxford introduce "social sycophancy," defined by Goffman's face theory, and the ELEPHANT benchmark to measure it. The work reveals that large language models consistently demonstrate high rates of social sycophancy, excessively preserving a user's desired self-image in open-ended interactions, partly due to current preference optimization methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
