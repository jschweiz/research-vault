---
id: 2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
kind: paper
title: A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens
source_url: https://www.alphaxiv.org/abs/2604.04913
source_name: alphaXiv Papers
authors:
  - Tommie Kerssies
  - Gabriele Berton
  - Ju He
  - Qihang Yu
  - Wufei Ma
  - Daan de Geus
  - Gijs Dubbelman
  - Liang-Chieh Chen
published_at: 2026-04-06T17:55:05Z
ingested_at: 2026-04-07T21:43:21.505060Z
content_hash: 0839181fa6d5e5befbbc209048ac5b0a1e0f1cc57cdf1ad0dfea777b698442ff
tags:
  - paper
  - alphaxiv
  - research
  - computer science
  - cs.cv
  - generative-models
  - inference-optimization
  - lightweight-models
  - model-compression
  - representation-learning
  - Computer Science
  - cs.CV
  - sequence-modeling
  - transformers
  - video-understanding
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
external_key: https://www.alphaxiv.org/abs/2604.04913
canonical_url: https://www.alphaxiv.org/abs/2604.04913
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:27:52.378560Z
short_summary: Researchers from Amazon and Eindhoven University of Technology developed DeltaWorld, an efficient generative world model that employs 'delta tokens' to encode temporal changes and uses a Best-of-Many training objective. The system generates diverse future predictions with over 35 times fewer parameters and 2,000 times fewer FLOPs than prior generative models, while achieving superior predictive accuracy.
lightweight_enrichment_status: failed
lightweight_enriched_at: null
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 0839181fa6d5e5befbbc209048ac5b0a1e0f1cc57cdf1ad0dfea777b698442ff
lightweight_enrichment_error: "Attempt to overwrite 'operation_run_id' in LogRecord"
---
# A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens

## alphaXiv Summary

Researchers from Amazon and Eindhoven University of Technology developed DeltaWorld, an efficient generative world model that employs 'delta tokens' to encode temporal changes and uses a Best-of-Many training objective. The system generates diverse future predictions with over 35 times fewer parameters and 2,000 times fewer FLOPs than prior generative models, while achieving superior predictive accuracy.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04913
- Source paper: https://arxiv.org/abs/2604.04913
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04913v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04913v1.png
- GitHub: https://github.com/amazon-far/deltatok
- GitHub stars: 4
- Paper ID: 2604.04913
- Canonical ID: 2604.04913v1
- Paper group ID: 019d65d0-64d9-7de9-92fd-a1a1afd79dcc
- Version ID: 019d65d0-6518-767c-ab44-770fe563bf14
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:55:05+00:00
- First published at: 2026-04-06T17:55:05+00:00
- Updated at: 2026-04-07T02:40:49.369000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Tommie Kerssies
- Gabriele Berton
- Ju He
- Qihang Yu
- Wufei Ma
- Daan de Geus
- Gijs Dubbelman
- Liang-Chieh Chen

## Topics

- Computer Science
- cs.CV
- generative-models
- inference-optimization
- lightweight-models
- model-compression
- representation-learning
- sequence-modeling
- transformers
- video-understanding

## Metrics

- Visits (all): 91
- Visits (last 7 days): 91
- Total votes: 1
- Public total votes: 7
- X likes: 0

## Abstract

Anticipating diverse future states is a central challenge in video world modeling. Discriminative world models produce a deterministic prediction that implicitly averages over possible futures, while existing generative world models remain computationally expensive. Recent work demonstrates that predicting the future in the feature space of a vision foundation model (VFM), rather than a latent space optimized for pixel reconstruction, requires significantly fewer world model parameters. However, most such approaches remain discriminative. In this work, we introduce DeltaTok, a tokenizer that encodes the VFM feature difference between consecutive frames into a single continuous "delta" token, and DeltaWorld, a generative world model operating on these tokens to efficiently generate diverse plausible futures. Delta tokens reduce video from a three-dimensional spatio-temporal representation to a one-dimensional temporal sequence, for example yielding a 1,024x token reduction with 512x512 frames. This compact representation enables tractable multi-hypothesis training, where many futures are generated in parallel and only the best is supervised. At inference, this leads to diverse predictions in a single forward pass. Experiments on dense forecasting tasks demonstrate that DeltaWorld forecasts futures that more closely align with real-world outcomes, while having over 35x fewer parameters and using 2,000x fewer FLOPs than existing generative world models. Code and weights: this https URL.

## Problem

- Discriminative world models produce single, deterministic predictions, failing to capture diverse plausible outcomes in inherently uncertain environments.
- Existing generative world models are computationally inefficient due to pixel-level reconstruction, multiple sequential forward passes for generation, and spatio-temporal redundancy in video representations.
- Standard video tokenizers encode each frame into dense spatial tokens, leading to long, redundant sequences when only small changes occur between consecutive frames.

## Method

- Operate prediction within the feature space of Vision Foundation Models (VFMs) to focus on semantically relevant information rather than computationally intensive pixel-level details.
- Implement a 'Best-of-Many' (BoM) training objective, allowing the model to generate multiple distinct future hypotheses in a single forward pass by mapping different stochastic inputs to different plausible outcomes.
- Introduce 'DeltaTok,' a novel tokenizer that compresses the *difference* between consecutive VFM feature maps into a single continuous 'delta' token, effectively transforming a 3D spatio-temporal video representation into a 1D temporal sequence.

## Results

- DeltaWorld achieves over 35x fewer parameters and more than 2,000x fewer FLOPs for generating 20 samples compared to leading generative world models like Cosmos-4B and Cosmos-12B.
- On dense forecasting benchmarks (segmentation, depth estimation), DeltaWorld's 'best-of-20' predictions consistently surpass Cosmos models and discriminative baselines, demonstrating superior accuracy (e.g., +5.6 mIoU on Cityscapes mid-horizon over DINO-world).
- The DeltaTok component reduces video representation from 1024 spatial tokens per frame to a single delta token, enabling a 1,024x token reduction per frame and making the predictor's FLOPs negligible (0.5% of total inference FLOPs).

## Takeaways

- Encoding only the temporal difference between VFM feature maps into a single 'delta' token significantly reduces data redundancy and computational load for video dynamics modeling.
- Combining a Best-of-Many training objective with VFM feature space operation enables efficient, single-pass generation of diverse and plausible future states.
- A compact, purely temporal representation via delta tokens can improve both generative world models (for diverse forecasting) and discriminative models (for efficiency) without compromising performance.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d0-64d9-7de9-92fd-a1a1afd79dcc/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d0-64d9-7de9-92fd-a1a1afd79dcc/transcript.json

## Resources

- GitHub repository: https://github.com/amazon-far/deltatok

## Similar Papers

- AdaWorld: Learning Adaptable World Models with Latent Actions (2503.18938v4): AdaWorld introduces a novel approach to world model learning that extracts context-invariant latent actions from unlabeled videos, enabling efficient adaptation to new environments. This method achieves superior action transfer (e.g., 70.5% human success rate on LIBERO vs. 20% for baseline) and faster world model adaptation with limited data, improving visual planning success rates in game and robotic tasks.
- Back to the Features: DINO as a Foundation for Video World Models (2507.19468v1): Meta FAIR's DINO-world introduces an efficient generalist video world model by leveraging a frozen DINOv2 encoder to predict future states in a semantic latent space, outperforming pixel-based models in dense feature forecasting and enabling effective action-conditioned planning from uncurated video data.
- Autoregressive Video Generation without Vector Quantization (2412.14169v2): NOVA, from BAAI and collaborators, introduces the first non-quantized autoregressive model for video generation, achieving state-of-the-art text-to-image alignment with a GenEval score of 0.75 at reduced training costs (127 GPU days for 0.6B parameters). This model also rivals leading diffusion and autoregressive video models in performance, reaching a VBench score of 80.12, while offering enhanced flexibility for variable-length and zero-shot multi-task video generation.
- Astra: General Interactive World Model with Autoregressive Denoising (2512.08931v3): ASTRA, developed by researchers from Tsinghua University and Kuaishou Technology, introduces an interactive general world model capable of generating real-world futures with precise action interactions and long-term consistency. The model leverages an autoregressive denoising framework to enhance a pre-trained video diffusion backbone, demonstrating superior performance in instruction following and visual quality across diverse interactive scenarios.
- Vid2World: Crafting Video Diffusion Models to Interactive World Models (2505.14357v3)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
