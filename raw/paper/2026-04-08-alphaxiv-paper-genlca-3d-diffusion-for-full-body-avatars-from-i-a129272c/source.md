---
id: 2026-04-08-alphaxiv-paper-genlca-3d-diffusion-for-full-body-avatars-from-i-a129272c
kind: paper
title: 'GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos'
source_url: https://www.alphaxiv.org/abs/2604.07273
source_name: alphaXiv Papers
authors:
- Yiqian Wu
- Rawal Khirodkar
- Egor Zakharov
- Timur Bagautdinov
- Lei Xiao
- Zhaoen Su
published_at: '2026-04-08T16:34:07Z'
ingested_at: '2026-04-09T12:08:26.048007Z'
content_hash: ee5b73838cac9f5a60bfdae68aebf066873dddacb8b985615407bc9cca0426d6
identity_hash: 98257655e0ff3eef992a650d5db21fc2fa8d16ec8576e1a80915e7839d117559
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cv
- generative-models
- geometric-deep-learning
- image-generation
- multi-modal-learning
- neural-rendering
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.07273
canonical_url: https://www.alphaxiv.org/abs/2604.07273
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:08:26.048013Z'
short_summary: GenLCA is a diffusion-based generative model that creates and edits photorealistic full-body avatars from text and image inputs. It achieves this by training a 3D diffusion model natively in 3D using large-scale real-world video data.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T14:34:23.367297Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: f9e3fb4d9e39621d2281a66f8e1216a7243e994585b5a96b1f39bc406d6f7d29
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 2e0e57fae12a1595d08ef04d464f5806165d7e4999083678a84011e674ac1237
lightweight_score:
  relevance_score: 0.418
  source_fit_score: 0.55
  topic_fit_score: 0.18
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on generic profile-fit fallback.
  evidence_quotes:
  - 'GenLCA is a diffusion-based generative model that creates and edits photorealistic full-body avatars from text and image inputs. It achieves this by training a '
---
# GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.07273
- Source paper: https://arxiv.org/abs/2604.07273
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.07273v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.07273v1.png
- Paper ID: 2604.07273
- Canonical ID: 2604.07273v1
- Paper group ID: 019d7014-6d53-738d-8883-ffdc0c9a52de
- Version ID: 019d7014-6d98-7b75-9925-dcd0d6685c67
- Version: v1
- Version order: 1
- Published at: 2026-04-08T16:34:07+00:00
- First published at: 2026-04-08T16:34:07+00:00
- Updated at: 2026-04-09T02:31:20.147000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Yiqian Wu
- Rawal Khirodkar
- Egor Zakharov
- Timur Bagautdinov
- Lei Xiao
- Zhaoen Su
- Shunsuke Saito
- Xiaogang Jin
- Junxuan Li

## Topics

- Computer Science
- cs.CV
- generative-models
- geometric-deep-learning
- image-generation
- multi-modal-learning
- neural-rendering
- representation-learning
- transfer-learning
- video-understanding

## Metrics

- Visits (all): 42
- Visits (last 7 days): 42
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

We present GenLCA, a diffusion-based generative model for generating and editing photorealistic full-body avatars from text and image inputs. The generated avatars are faithful to the inputs, while supporting high-fidelity facial and full-body animations. The core idea is a novel paradigm that enables training a full-body 3D diffusion model from partially observable 2D data, allowing the training dataset to scale to millions of real-world videos. This scalability contributes to the superior photorealism and generalizability of GenLCA. Specifically, we scale up the dataset by repurposing a pretrained feed-forward avatar reconstruction model as an animatable 3D tokenizer, which encodes unstructured video frames into structured 3D tokens. However, most real-world videos only provide partial observations of body parts, resulting in excessive blurring or transparency artifacts in the 3D tokens. To address this, we propose a novel visibility-aware diffusion training strategy that replaces invalid regions with learnable tokens and computes losses only over valid regions. We then train a flow-based diffusion model on the token dataset, inherently maintaining the photorealism and animatability provided by the pretrained avatar reconstruction model. Our approach effectively enables the use of large-scale real-world video data to train a diffusion model natively in 3D. We demonstrate the efficacy of our method through diverse and high-fidelity generation and editing results, outperforming existing solutions by a large margin. The project page is available at this https URL.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d7014-6d53-738d-8883-ffdc0c9a52de/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7014-6d53-738d-8883-ffdc0c9a52de/transcript.json

## Similar Papers

- FaceCraft4D: Animated 3D Facial Avatar Generation from a Single Image (2504.15179v1): FaceCraft4D is a framework that generates high-quality, animatable 4D facial avatars from a single image input, achieving superior performance over existing methods in animation quality, identity preservation, and view consistency. This is accomplished by leveraging multiple forms of prior knowledge to synthesize consistent multi-view data and introducing a novel training strategy to robustly optimize a 4D representation.
- Text-based Animatable 3D Avatars with Morphable Model Alignment (2504.15835v1): AnimPortrait3D is a framework developed by researchers from ETH Zürich and Zhejiang University that generates high-quality, animatable 3D head avatars from text descriptions. It addresses challenges in appearance-geometry alignment and animation fidelity through a two-stage process, enabling realistic expressions and poses.
- Gaussian Variation Field Diffusion for High-fidelity Video-to-4D Synthesis (2507.23785v1): Researchers from the University of Science and Technology of China and Microsoft Research Asia developed a framework for high-fidelity video-to-4D synthesis, generating dynamic 3D content efficiently from single video inputs. This method achieves superior visual quality and temporal consistency while significantly reducing generation time compared to prior approaches.
- Vid2Avatar-Pro: Authentic Avatar from Videos in the Wild via Universal  Prior (2503.01610v1): Meta's Codec Avatars Lab introduces Vid2Avatar-Pro, a groundbreaking system that creates high-fidelity, animatable 3D human avatars from casual monocular videos by leveraging a novel universal prior model trained on high-quality performance capture data, achieving state-of-the-art results in both view synthesis and animation while handling diverse clothing and poses.
- IDOL: Instant Photorealistic 3D Human Creation from a Single Image (2412.14963v2): Researchers from Nanjing University, Tencent, and collaborators developed IDOL, a method for instant, photorealistic, and animatable 3D full-body human avatar creation from a single image. The approach leverages a large-scale synthetic multi-view dataset, HuGe100K, and a feed-forward transformer model to reconstruct avatars in under a second at 1K resolution, supporting direct animation and editing.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
