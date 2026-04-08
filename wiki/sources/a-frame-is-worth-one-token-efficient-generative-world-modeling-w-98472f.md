---
id: page:2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
page_type: source-note
title: A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens
aliases:
  - A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens
source_refs:
  - 2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
backlinks:
  - page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
  - page:2026-04-01-alphaxiv-paper-test-time-scaling-makes-overtraining-compute-opt-3a3760da
  - page:2026-04-02-alphaxiv-paper-the-latent-space-foundation-evolution-mechanism--4559cf35
  - page:2026-04-03-alphaxiv-paper-hierarchical-planning-with-latent-world-models-d1a0bbac
  - page:2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
  - page:2026-04-06-alphaxiv-paper-openworldlib-a-unified-codebase-and-definition-o-349dac12
  - page:2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
  - topic:computer-science
  - topic:computer-vision
  - topic:generative-models
  - topic:inference-optimization
  - topic:lightweight-models
  - topic:model-compression
updated_at: 2026-04-08T07:14:52.407822Z
managed: true
---
# A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04913
- Document kind: paper
- Published at: 2026-04-06T17:55:05+00:00
- Authors: Tommie Kerssies, Gabriele Berton, Ju He, Qihang Yu, Wufei Ma, Daan de Geus
- Tags: paper, alphaxiv, research, computer science, cs.cv, generative-models, inference-optimization, lightweight-models, model-compression, representation-learning
- Topics: [Computer Vision](../topics/computer-vision.md), [Computer Science](../topics/computer-science.md), [Generative Models](../topics/generative-models.md), [Inference Optimization](../topics/inference-optimization.md), [Lightweight Models](../topics/lightweight-models.md), [Model Compression](../topics/model-compression.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens ## Metadata - alphaXiv URL: https://www.alphaxiv.org/abs/2604.04913 - Source paper: https://arxiv.org/abs/2604.04913 - PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04913v1.pdf - Cover image: https://www.alphaxiv.org/image/2604.04913v1.png - GitHub: https://github.com/amazon-far/deltatok - GitHub stars: 4 - Paper ID: 2604.04913 - Canonical ID: 2604.04913v1 - Paper group ID: 019d65d0-64d9-7de9-92fd-a1a1afd79dcc -

## Topic Map

- [Computer Vision](../topics/computer-vision.md)
- [Computer Science](../topics/computer-science.md)
- [Generative Models](../topics/generative-models.md)
- [Inference Optimization](../topics/inference-optimization.md)
- [Lightweight Models](../topics/lightweight-models.md)
- [Model Compression](../topics/model-compression.md)

## Related Research

- [TriAttention: Efficient Long Reasoning with Trigonometric KV Compression](triattention-efficient-long-reasoning-with-trigonometric-kv-comp-d601e8.md) (shared topics: Computer Science, Computer Vision)
- [MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale](mineru2-5-pro-pushing-the-limits-of-data-centric-document-parsin-394662.md) (shared topics: Computer Science, Computer Vision)
- [OpenWorldLib: A Unified Codebase and Definition of Advanced World Models](openworldlib-a-unified-codebase-and-definition-of-advanced-world-187d2a.md) (shared topics: Computer Science, Computer Vision)
- [The Latent Space: Foundation, Evolution, Mechanism, Ability, and Outlook](the-latent-space-foundation-evolution-mechanism-ability-and-outl-af2bc6.md) (shared topics: Computer Science, Generative Models)
- [Test-Time Scaling Makes Overtraining Compute-Optimal](test-time-scaling-makes-overtraining-compute-optimal-7627f8.md) (shared topics: Computer Science, Inference Optimization)
- [Embarrassingly Simple Self-Distillation Improves Code Generation](embarrassingly-simple-self-distillation-improves-code-generation-c213e5.md) (shared topics: Computer Science, Generative Models)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens

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

- Visits (all): 58
- Visits (last 7 days): 58
- Total votes: 1
- Public total votes: 7
- X likes: 0

## Abstract

Anticipating diverse future states is a central challenge in video world modeling. Discriminative world models produce a deterministic prediction that implicitly averages over possible futures, while existing generative world models remain computationally expensive. Recent work demonstrates that predicting the future in the feature space of a vision foundation model (VFM), rather than a latent space optimized for pixel reconstruction, requires significantly fewer world model parameters. However, most such approaches remain discriminative. In this work, we introduce DeltaTok, a tokenizer that encodes the VFM feature difference between consecutive frames into a single continuous "delta" token, and DeltaWorld, a generative world model operating on these tokens to efficiently generate diverse plausible futures. Delta tokens reduce video from a three-dimensional spatio-temporal representation to a one-dimensional temporal sequence, for example yielding a 1,024x token reduction with 512x512 frames. This compact representation enables tractable multi-hypothesis training, where many futures are generated in parallel and only the best is supervised. At inference, this leads to diverse predictions in a single forward pass. Experiments on dense forecasting tasks demonstrate that DeltaWorld forecasts futures that more closely align with real-world outcomes, while having over 35x fewer parameters and using 2,000x fewer FLOPs than existing generative world models. Code and weights: this https URL.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d65d0-64d9-7de9-92fd-a1a1afd79dcc/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d0-64d9-7de9-92fd-a1a1afd79dcc/transcript.json

## Resources

- GitHub repository: https://github.com/amazon-far/deltatok

## Similar Papers

- AdaWorld: Learning Adaptable World Models with Latent Actions (2503.18938v4): AdaWorld introduces a novel approach to world model learning that extracts context-invariant latent actions from unlabeled videos, enabling efficient adaptation to new environments. This method achieves superior action transfer (e.g., 70.5% human success rate on LIBERO vs. 20% for baseline) and faster world model adaptation with limited data, improving visual planning success rates in game and robotic tasks.
- Back to the Features: DINO as a Foundation for Video World Models (2507.19468v1): Meta FAIR's DINO-world introduces an efficient generalist video world model by leveraging a frozen DINOv2 encoder to predict future states in a semantic latent space, outperforming pixel-based models in dense feature forecasting and enabling effective action-conditioned planning from uncurated video data.
- Autoregressive Video Genera
