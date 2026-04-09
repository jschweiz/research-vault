---
id: 2026-04-08-alphaxiv-paper-tc-ae-unlocking-token-capacity-for-deep-compress-66b58635
kind: paper
title: 'TC-AE: Unlocking Token Capacity for Deep Compression Autoencoders'
source_url: https://www.alphaxiv.org/abs/2604.07340
source_name: alphaXiv Papers
authors:
- Teng Li
- Ziyuan Huang
- Cong Chen
- Yangfu Li
- Yuanhuiyi Lyu
- Dandan Zheng
- Chunhua Shen
- Jun Zhang
published_at: '2026-04-08T17:53:52Z'
ingested_at: '2026-04-09T10:00:25.165461Z'
content_hash: 698a3675d1bab33bf93633fe642df6ea4db3fc0ead91d873b5b0897a83487496
identity_hash: dbaa0dc67a01ff04830f242e6e26a1d5b598b45ad087a41f3c601608af34b9fa
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CV
- generative-models
- image-generation
- lightweight-models
- model-compression
- representation-learning
- self-supervised-learning
- transformers
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
external_key: https://www.alphaxiv.org/abs/2604.07340
canonical_url: https://www.alphaxiv.org/abs/2604.07340
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:00:25.165466Z'
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
# TC-AE: Unlocking Token Capacity for Deep Compression Autoencoders

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.07340
- Source paper: https://arxiv.org/abs/2604.07340
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.07340v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.07340v1.png
- GitHub: https://github.com/inclusionAI/TC-AE
- GitHub stars: 1
- Paper ID: 2604.07340
- Canonical ID: 2604.07340v1
- Paper group ID: 019d6fee-1731-71db-ba1d-aa89811cba3b
- Version ID: 019d6fee-1769-70bb-b8ab-10a31611b960
- Version: v1
- Version order: 1
- Published at: 2026-04-08T17:53:52+00:00
- First published at: 2026-04-08T17:53:52+00:00
- Updated at: 2026-04-09T01:49:27.729000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Teng Li
- Ziyuan Huang
- Cong Chen
- Yangfu Li
- Yuanhuiyi Lyu
- Dandan Zheng
- Chunhua Shen
- Jun Zhang

## Topics

- Computer Science
- cs.CV
- generative-models
- image-generation
- lightweight-models
- model-compression
- representation-learning
- self-supervised-learning
- transformers

## Metrics

- Visits (all): 19
- Visits (last 7 days): 19
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

We propose TC-AE, a ViT-based architecture for deep compression autoencoders. Existing methods commonly increase the channel number of latent representations to maintain reconstruction quality under high compression ratios. However, this strategy often leads to latent representation collapse, which degrades generative performance. Instead of relying on increasingly complex architectures or multi-stage training schemes, TC-AE addresses this challenge from the perspective of the token space, the key bridge between pixels and image latents, through two complementary innovations: Firstly, we study token number scaling by adjusting the patch size in ViT under a fixed latent budget, and identify aggressive token-to-latent compression as the key factor that limits effective scaling. To address this issue, we decompose token-to-latent compression into two stages, reducing structural information loss and enabling effective token number scaling for generation. Secondly, to further mitigate latent representation collapse, we enhance the semantic structure of image tokens via joint self-supervised training, leading to more generative-friendly latents. With these designs, TC-AE achieves substantially improved reconstruction and generative performance under deep compression. We hope our research will advance ViT-based tokenizer for visual generation.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6fee-1731-71db-ba1d-aa89811cba3b/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6fee-1731-71db-ba1d-aa89811cba3b/transcript.json

## Resources

- GitHub repository: https://github.com/inclusionAI/TC-AE

## Similar Papers

- Bridging Continuous and Discrete Tokens for Autoregressive Visual Generation (2503.16430v3): TokenBridge, a collaboration between the University of Hong Kong, ByteDance Seed, École Polytechnique, and Peking University, proposes a method for autoregressive visual generation that discretizes pre-trained continuous VAE latent features after training. It achieves an ImageNet 256x256 FID of 1.55, matching or surpassing complex diffusion-based token prediction methods while demonstrating a 5.94x faster inference speed.
- GigaTok: Scaling Visual Tokenizers to 3 Billion Parameters for Autoregressive Image Generation (2504.08736v2): GigaTok introduces a method for scaling visual tokenizers to 3 billion parameters, successfully addressing the "reconstruction vs. generation dilemma" in autoregressive image generation. This approach yields state-of-the-art performance, including a gFID of 1.98 for 1.4B AR models and improved representation quality on ImageNet.
- Flow to the Mode: Mode-Seeking Diffusion Autoencoders for State-of-the-Art Image Tokenization (2503.11056v3): Researchers from Stanford University and the University of Michigan developed FlowMo, a transformer-based diffusion autoencoder with a mode-seeking training strategy, for image tokenization. This approach sets a new state-of-the-art for perceptual image reconstruction on ImageNet-1K, with FlowMo-Lo achieving an rFID of 0.95 at 0.070 BPP and FlowMo-Hi reaching 0.56 rFID at 0.219 BPP, without relying on convolutions or adversarial losses.
- H3AE: High Compression, High Speed, and High Quality AutoEncoder for Video Diffusion Models (2504.10567v2): Researchers from Snap Inc. and Northeastern University developed H3AE, a high compression, high speed, and high quality autoencoder designed for video diffusion models. This framework systematically optimizes architectural design and training strategies to achieve ultra-high compression ratios and real-time decoding speeds on mobile devices, while significantly improving video reconstruction fidelity and unifying support for various generation tasks.
- Towards Scalable Pre-training of Visual Tokenizers for Generation (2512.13687v2)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
