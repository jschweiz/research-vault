---
id: 2026-04-08-alphaxiv-paper-starvla-a-lego-like-codebase-for-vision-language-968bea71
kind: paper
title: 'StarVLA: A Lego-like Codebase for Vision-Language-Action Model Developing'
source_url: https://www.alphaxiv.org/abs/2604.05014
source_name: alphaXiv Papers
authors:
- StarVLA Community
published_at: '2026-04-06T17:59:21Z'
ingested_at: '2026-04-08T15:13:28.985248Z'
content_hash: 48c7893be0aed07e635c64753382586559799d8c412452f0df7efbb0336f789d
tags:
- paper
- alphaxiv
- research
- agents
- computer science
- cs.ai
- cs.cv
- cs.ro
- imitation-learning
- ml-systems
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
external_key: https://www.alphaxiv.org/abs/2604.05014
canonical_url: https://www.alphaxiv.org/abs/2604.05014
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:11:19.119272Z'
short_summary: StarVLA is an open-source, modular codebase for Vision-Language-Action (VLA) model development, unifying VLA research through interchangeable backbones and action heads. It provides reusable training strategies and benchmarks, enabling competitive performance across diverse robot manipulation tasks.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:45:50.022496Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: b2ead437b1e7e95b60f8a054c051c9e1d504a4eadca790ae3dbf86e840360098
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 9300cd67b09ce22828a96ef14d8753f79b0eb59769fb59fa4d0e2193572d3588
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses Vision-Language-Action (VLA) model development, which aligns perfectly with the user's favorite topics of language models, evaluation, and reasoning.
  evidence_quotes:
  - StarVLA is an open-source, modular codebase for Vision-Language-Action (VLA) model development, unifying VLA research through interchangeable backbones and acti
  - StarVLA addresses these challenges in three aspects. First, it provides a modular backbone--action-head architecture that supports both VLM backbones (e.g., Qwe
  - StarVLA is one of the most comprehensive open-source VLA frameworks available, and we expect it to lower the barrier for reproducing existing methods and protot
---
# StarVLA: A Lego-like Codebase for Vision-Language-Action Model Developing

## alphaXiv Summary

StarVLA introduces an open-source, modular codebase designed to unify Vision-Language-Action (VLA) model development by enabling interchangeable backbones and action heads. This framework provides competitive performance on various robot manipulation benchmarks, achieving, for instance, a 96.6% average success rate on LIBERO and demonstrating the ability for a single generalist model to enhance performance across diverse tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05014
- Source paper: https://arxiv.org/abs/2604.05014
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05014v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05014v1.png
- GitHub: https://github.com/starVLA/starVLA
- GitHub stars: 1556
- Paper ID: 2604.05014
- Canonical ID: 2604.05014v1
- Paper group ID: 019d6acc-811b-7b65-a893-213d8bc16919
- Version ID: 019d6acc-814c-70d9-9b49-c92020d53ef3
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:59:21+00:00
- First published at: 2026-04-06T17:59:21+00:00
- Updated at: 2026-04-08T01:54:40.539000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- StarVLA Community

## Topics

- agents
- Computer Science
- cs.AI
- cs.CV
- cs.RO
- imitation-learning
- ml-systems
- multi-modal-learning
- robotic-control
- robotics-perception
- transfer-learning
- transformers
- vision-language-models

## Metrics

- Visits (all): 143
- Visits (last 7 days): 143
- Total votes: 4
- Public total votes: 11
- X likes: 0

## Abstract

Building generalist embodied agents requires integrating perception, language understanding, and action, which are core capabilities addressed by Vision-Language-Action (VLA) approaches based on multimodal foundation models, including recent advances in vision-language models and world models. Despite rapid progress, VLA methods remain fragmented across incompatible architectures, codebases, and evaluation protocols, hindering principled comparison and reproducibility. We present StarVLA, an open-source codebase for VLA research. StarVLA addresses these challenges in three aspects. First, it provides a modular backbone--action-head architecture that supports both VLM backbones (e.g., Qwen-VL) and world-model backbones (e.g., Cosmos) alongside representative action-decoding paradigms, all under a shared abstraction in which backbone and action head can each be swapped independently. Second, it provides reusable training strategies, including cross-embodiment learning and multimodal co-training, that apply consistently across supported paradigms. Third, it integrates major benchmarks, including LIBERO, SimplerEnv, RoboTwin~2.0, RoboCasa-GR1, and BEHAVIOR-1K, through a unified evaluation interface that supports both simulation and real-robot deployment. StarVLA also ships simple, fully reproducible single-benchmark training recipes that, despite minimal data engineering, already match or surpass prior methods on multiple benchmarks with both VLM and world-model backbones. To our best knowledge, StarVLA is one of the most comprehensive open-source VLA frameworks available, and we expect it to lower the barrier for reproducing existing methods and prototyping new ones. StarVLA is being actively maintained and expanded; we will update this report as the project evolves. The code and documentation are available at this https URL.

## Problem

- Fragmentation in VLA research due to diverse and often incompatible architectural designs, training pipelines, and data processing methods.
- Lack of standardized evaluation protocols across different VLA benchmarks, hindering fair comparisons and cumulative research progress.
- Difficulty in reusing components and integrating different VLA methods due to tightly coupled codebase assumptions.

## Method

- Developed StarVLA, a unified and modular codebase based on a "backbone–action-head" decomposition, supporting both VLM and world-model backbones with pluggable action heads.
- Established a unified I/O interface and a policy-centric formulation to abstract and interpret diverse VLA systems consistently.
- Integrated a unified server-client testing abstraction for standardized evaluation across multiple benchmarks and real-robot deployment.

## Results

- StarVLA variants achieved strong performance on single benchmarks, with StarVLA-OFT reaching 96.6% average success on LIBERO and StarVLA-GR00T obtaining 65.3% on SimplerEnv (WidowX).
- Spatially Guided Co-training (ST4VLA) maintained approximately 70% of original grounding performance while boosting manipulation success rates (e.g., +6.4% on SimplerEnv WidowX).
- A single generalist StarVLA model trained across multiple benchmarks improved the average success rate on RoboCasa-GR1 from a specialist's 48.8% to 57.3%.
- The framework demonstrated robust computational scalability, achieving up to 2200.0 samples/s throughput on 256 GPUs with parallel efficiency stabilizing at 79–80% for larger setups.

## Takeaways

- A modular "backbone–action-head" architecture successfully unifies disparate VLA paradigms, facilitating flexible prototyping and systematic comparison.
- Multimodal co-training strategies are effective in preserving general-purpose visual reasoning and language grounding capabilities while improving manipulation performance.
- Cross-benchmark training with a single generalist model can achieve competitive performance and even improve results on challenging benchmarks, indicating potential for scalable pretraining.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6acc-811b-7b65-a893-213d8bc16919/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6acc-811b-7b65-a893-213d8bc16919/transcript.json
- Transcript lines: 21
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/starVLA/starVLA

## Similar Papers

- Rethinking the Practicality of Vision-language-action Model: A Comprehensive Benchmark and An Improved Baseline (2602.22663/thumbs-up-bzsugqwp.jsv1)
- Rethinking the Practicality of Vision-language-action Model: A Comprehensive Benchmark and An Improved Baseline (2602.22663/vlukgtr4xt1f.phpv1)
- Rethinking the Practicality of Vision-language-action Model: A Comprehensive Benchmark and An Improved Baseline (2602.22663/use-validate-comment-d_6zz240.jsv1)
- Rethinking the Practicality of Vision-language-action Model: A Comprehensive Benchmark and An Improved Baseline (2602.22663/use-media-query-dd27zxww.jsv1)
- Rethinking the Practicality of Vision-language-action Model: A Comprehensive Benchmark and An Improved Baseline (2602.22663/use-update-user-preference-c86ga7g1.jsv1)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
