---
id: 2026-04-08-alphaxiv-paper-action-images-end-to-end-policy-learning-via-mul-84530c13
kind: paper
title: 'Action Images: End-to-End Policy Learning via Multiview Video Generation'
source_url: https://www.alphaxiv.org/abs/2604.06168
source_name: alphaXiv Papers
authors:
- Haoyu Zhen
- Zixian Gao
- Qiao Sun
- Yilin Zhao
- Yuncong Yang
- Yilun Du
published_at: '2026-04-07T17:59:30Z'
ingested_at: '2026-04-08T15:13:24.631292Z'
content_hash: 85ad19483ef5fbe5f065e048938e7a833880503f051957fe409751be0d9900bd
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cv
- cs.ro
- deep-reinforcement-learning
- generative-models
- multi-modal-learning
- representation-learning
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
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06168
canonical_url: https://www.alphaxiv.org/abs/2604.06168
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:11:29.005050Z'
short_summary: Action Images reformulates robot policy learning as multiview video generation by translating 7-DoF actions into pixel-grounded action images. This unified world action model enables superior zero-shot policy generalization and improved video-action joint generation quality.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:44:56.143996Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: dd725cdfac670a8089bb99b87bf3ff98fe7a7bbea9ddb6c1627e9eb113ed52ee
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: cb923950dd5f49fc62d8006f1f13c23fa38f5bd7231f13d42d1a57c8143f64c2
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.5
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses core favorite topics like LLM architecture, reasoning, and research tooling within the domain of embodied AI and policy learning.
  evidence_quotes:
  - Action Images reformulates robot policy learning as multiview video generation, converting 7-DoF robot actions into pixel-grounded action images.
  - This pixel-grounded action representation allows the video backbone itself to act as a zero-shot policy, without a separate policy head or action module.
  - On RLBench and real-world evaluations, our model achieves the strongest zero-shot success rates and improves video-action joint generation quality over prior vi
---
# Action Images: End-to-End Policy Learning via Multiview Video Generation

## alphaXiv Summary

Action Images reformulates robot policy learning as multiview video generation, converting 7-DoF robot actions into pixel-grounded images. This approach enables a unified world model to achieve superior zero-shot policy generalization on unseen tasks and environments, alongside improved video-action joint generation quality.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06168
- Source paper: https://arxiv.org/abs/2604.06168
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06168v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06168v1.png
- GitHub: https://github.com/UMass-Embodied-AGI/ActionImages
- GitHub stars: 1
- Paper ID: 2604.06168
- Canonical ID: 2604.06168v1
- Paper group ID: 019d6ace-b299-761c-925a-07359b48eb4d
- Version ID: 019d6ace-b2c0-7a95-92ff-a3406b0a3664
- Version: v1
- Version order: 1
- Published at: 2026-04-07T17:59:30+00:00
- First published at: 2026-04-07T17:59:30+00:00
- Updated at: 2026-04-08T01:57:04.281000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Haoyu Zhen
- Zixian Gao
- Qiao Sun
- Yilin Zhao
- Yuncong Yang
- Yilun Du
- Tsun-Hsuan Wang
- Yi-Ling Qiao
- Chuang Gan

## Topics

- Computer Science
- cs.CV
- cs.RO
- deep-reinforcement-learning
- generative-models
- multi-modal-learning
- representation-learning
- robotic-control
- robotics-perception
- zero-shot-learning

## Metrics

- Visits (all): 131
- Visits (last 7 days): 131
- Total votes: 0
- Public total votes: 9
- X likes: 0

## Abstract

World action models (WAMs) have emerged as a promising direction for robot policy learning, as they can leverage powerful video backbones to model the future states. However, existing approaches often rely on separate action modules, or use action representations that are not pixel-grounded, making it difficult to fully exploit the pretrained knowledge of video models and limiting transfer across viewpoints and environments. In this work, we present Action Images, a unified world action model that formulates policy learning as multiview video generation. Instead of encoding control as low-dimensional tokens, we translate 7-DoF robot actions into interpretable action images: multi-view action videos that are grounded in 2D pixels and explicitly track robot-arm motion. This pixel-grounded action representation allows the video backbone itself to act as a zero-shot policy, without a separate policy head or action module. Beyond control, the same unified model supports video-action joint generation, action-conditioned video generation, and action labeling under a shared representation. On RLBench and real-world evaluations, our model achieves the strongest zero-shot success rates and improves video-action joint generation quality over prior video-space world models, suggesting that interpretable action images are a promising route to policy learning.

## Problem

- Existing robotics world models struggle to translate strong video generation capabilities into robust policy generalization, especially in novel environments.
- Current action representations are often detached from visual space or rely on separate policy heads, limiting the direct leverage of rich, pre-trained video knowledge for control and hindering transferability.
- Many generalist robot policy models face challenges with zero-shot transfer to entirely new environments, often failing to adapt beyond training scenes.

## Method

- Robot 7-DoF actions (position, orientation, gripper) are converted into multi-view pixel-grounded 'action images' by projecting semantic 3D points (end-effector position, up, normal) into 2D Gaussian heatmaps across multiple camera views.
- A large pre-trained video generator is fine-tuned to jointly model multi-view robot observation videos and the newly created multi-view action videos within a unified video-space.
- Diverse masking strategies are employed during training to enable a single model to perform multiple tasks, including video-action joint generation, action-conditioned video generation, and video-to-action labeling.

## Results

- Achieved superior zero-shot policy success rates on unseen tasks, for example, up to 60% for 'reach target' on RLBench and 45% for 'close drawer' on real-world tasks, outperforming baselines which often showed 0-20% success.
- Demonstrated improved video-action joint generation quality, with 'Action Images' outperforming baselines like TesserAct in video quality (PSNR 23.48 vs 20.83, SSIM 78.62% vs 59.20%) and maintaining competitive action quality.
- Outperformed specialized baselines in action-conditioned video generation (e.g., PSNR 31.35 vs. Tora's 19.76) and video-to-action labeling (trajectory error 5.785 vs. TAPIR's 14.80), showcasing the model's versatility.

## Takeaways

- Grounding robot actions directly in the pixel space as visual signals allows large video backbones to inherently leverage their extensive visual knowledge for action reasoning and control.
- Representing actions as multi-view images resolves 3D ambiguities and integrates action directly into the visual prediction problem, enabling the video backbone itself to function as a zero-shot policy without separate modules.
- A unified video-space representation of observations and actions enables a single generative model to perform diverse robot learning tasks, simplifying architecture and training across different objectives.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6ace-b299-761c-925a-07359b48eb4d/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ace-b299-761c-925a-07359b48eb4d/transcript.json
- Transcript lines: 14
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/UMass-Embodied-AGI/ActionImages

## Similar Papers

- UniVLA: Learning to Act Anywhere with Task-centric Latent Actions (2505.06111v3): A generalist robot policy framework learns task-centric latent actions from internet-scale, action-label free videos. This approach achieves average success rates of 95.2% on LIBERO and 47.1% on Room2Room, demonstrating efficient, cross-embodiment generalization and robust real-world performance.
- Unified World Models: Coupling Video and Action Diffusion for  Pretraining on Large Robotic Datasets (2504.02792v3): Unified World Models (UWM), developed by researchers at the University of Washington and Toyota Research Institute, presents a diffusion-based framework that unifies robot policy learning and world modeling within a single transformer, enabling it to learn from both action-labeled robotic data and action-free video datasets. The model demonstrates improved task success rates and robustness on real-world robot manipulation tasks, outperforming existing baselines.
- Cosmos Policy: Fine-Tuning Video Models for Visuomotor Control and Planning (2601.16163v1): Researchers from NVIDIA and Stanford University fine-tune a large, pretrained latent video diffusion model, Cosmos-Predict2, into a unified robot policy for visuomotor control and planning. This method achieves state-of-the-art average success rates of 98.5% on LIBERO, 67.1% on RoboCasa, and 93.6% on ALOHA, demonstrating enhanced data efficiency and robustness for complex manipulation tasks.
- Causal World Modeling for Robot Control (2601.21998v2): Researchers developed LingBot-VA, an autoregressive diffusion framework that unifies visual dynamics prediction and action inference for robot control. This model incorporates causal world modeling and persistent memory, enabling reactive closed-loop control and achieving state-of-the-art performance across diverse manipulation tasks in both simulation and real-world settings.
- DreamDojo: A Generalist Robot World Model from Large-Scale Human Videos (2602.06949v1): DreamDojo introduces a foundation world model that learns to simulate diverse, dexterous robot tasks by training on an unprecedented 44,711 hours of egocentric human video data. The model achieves real-time inference at 10.81 FPS and demonstrates a strong correlation (Pearson r=0.995) between simulated and real-world policy evaluation success rates.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
