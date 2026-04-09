---
id: 2026-04-08-alphaxiv-paper-flowinone-unifying-multimodal-generation-as-imag-7d92e584
kind: paper
title: FlowInOne:Unifying Multimodal Generation as Image-in, Image-out Flow Matching
source_url: https://www.alphaxiv.org/abs/2604.06757
source_name: alphaXiv Papers
authors:
- Junchao Yi
- Rui Zhao
- Jiahao Tang
- Weixian Lei
- Linjie Li
- Qisheng Su
- Zhengyuan Yang
- Lijuan Wang
- Xiaofeng Zhu
- Alex Jinpeng Wang
published_at: '2026-04-08T07:22:08Z'
ingested_at: '2026-04-09T09:57:09.730602Z'
content_hash: 38479fdd6f68b044e1a70ec6e75275423ed42cef9b03f429ddb95bd798f40dde
identity_hash: 5ad8629251e1f8ce09c195b579e7e22b153843e0bd01d5e066ef060d109160f0
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CV
- data-curation
- generative-models
- image-generation
- multi-modal-learning
- representation-learning
- vision-language-models
- visual-reasoning
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
external_key: https://www.alphaxiv.org/abs/2604.06757
canonical_url: https://www.alphaxiv.org/abs/2604.06757
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:57:09.730625Z'
short_summary: FlowInOne unifies multimodal generation tasks by converting diverse inputs into visual prompts within an "image-in, image-out" flow matching framework. This vision-centric approach achieves higher average pass rates and DINOv3 Sim scores compared to open-source models, demonstrating robust instruction adherence and spatial precision across text-to-image generation and image editing tasks.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# FlowInOne:Unifying Multimodal Generation as Image-in, Image-out Flow Matching

## alphaXiv Summary

FlowInOne unifies multimodal generation tasks by converting diverse inputs into visual prompts within an "image-in, image-out" flow matching framework. This vision-centric approach achieves higher average pass rates and DINOv3 Sim scores compared to open-source models, demonstrating robust instruction adherence and spatial precision across text-to-image generation and image editing tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06757
- Source paper: https://arxiv.org/abs/2604.06757
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06757v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06757v1.png
- GitHub: https://github.com/CSU-JPG/FlowInOne
- GitHub stars: 1
- Paper ID: 2604.06757
- Canonical ID: 2604.06757v1
- Paper group ID: 019d7022-26bd-7d91-a3e5-7b17211f9b0d
- Version ID: 019d7022-2704-75bc-8cde-b6ff15cc5b9d
- Version: v1
- Version order: 1
- Published at: 2026-04-08T07:22:08+00:00
- First published at: 2026-04-08T07:22:08+00:00
- Updated at: 2026-04-09T02:46:19.581000+00:00
- License: http://creativecommons.org/licenses/by-nc-nd/4.0/
- Citations: 0

## Authors

- Junchao Yi
- Rui Zhao
- Jiahao Tang
- Weixian Lei
- Linjie Li
- Qisheng Su
- Zhengyuan Yang
- Lijuan Wang
- Xiaofeng Zhu
- Alex Jinpeng Wang

## Topics

- Computer Science
- cs.CV
- data-curation
- generative-models
- image-generation
- multi-modal-learning
- representation-learning
- vision-language-models
- visual-reasoning

## Metrics

- Visits (all): 26
- Visits (last 7 days): 26
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Multimodal generation has long been dominated by text-driven pipelines where language dictates vision but cannot reason or create within it. We challenge this paradigm by asking whether all modalities, including textual descriptions, spatial layouts, and editing instructions, can be unified into a single visual representation. We present FlowInOne, a framework that reformulates multimodal generation as a purely visual flow, converting all inputs into visual prompts and enabling a clean image-in, image-out pipeline governed by a single flow matching model. This vision-centric formulation naturally eliminates cross-modal alignment bottlenecks, noise scheduling, and task-specific architectural branches, unifying text-to-image generation, layout-guided editing, and visual instruction following under one coherent paradigm. To support this, we introduce VisPrompt-5M, a large-scale dataset of 5 million visual prompt pairs spanning diverse tasks including physics-aware force dynamics and trajectory prediction, alongside VP-Bench, a rigorously curated benchmark assessing instruction faithfulness, spatial precision, visual realism, and content consistency. Extensive experiments demonstrate that FlowInOne achieves state-of-the-art performance across all unified generation tasks, surpassing both open-source models and competitive commercial systems, establishing a new foundation for fully vision-centric generative modeling where perception and creation coexist within a single continuous visual space.

## Problem

- Multimodal generation often relies on text-dominant paradigms, leading to an asymmetry where language dictates visual output and vision lacks autonomous reasoning capabilities.
- Unifying diverse tasks like visual understanding, editing, and generation within a single model architecture is challenging due to cross-modal alignment complexities and fragmented approaches.
- Traditional generative models, such as diffusion models, often involve complex noise schedules and can face inefficiencies in sampling and optimization stability.

## Method

- Reformulates multimodal generation as a purely visual "image-in, image-out" flow matching process, where all input modalities (text, spatial layouts, editing instructions) are converted into visual representations.
- Develops a Flow Matching model augmented with a Dual-Path Spatially-Adaptive Modulation mechanism to dynamically balance structural preservation and instruction adherence during generation.
- Creates a large-scale VisPrompt-5M dataset with 5 million visual prompt pairs and a curated VP-Bench benchmark for training and rigorously evaluating the model in a unified visual paradigm.

## Results

- Achieved the highest average pass rates (39.2% by GPT-5.2, 50.3% by Qwen3.5, and 44.9% by human evaluators) compared to open-source models, and competitive performance against commercial models.
- Demonstrated superior fine-grained spatial and physical control with the highest DINOv3 Sim score of 48.7%, particularly in tasks involving force/trajectory understanding and text bounding box editing.
- Ablation studies validated the efficacy of the MLP+MLP projection, Dual-Path Spatially-Adaptive Modulation (SAM), and joint training strategy, confirming their essential roles in the model's overall performance.

## Takeaways

- A single vision-centric flow matching model can effectively unify diverse generative tasks, such as text-to-image and image editing, by operating entirely within the visual space without relying on text encoders or task-specific architectures.
- Converting all input modalities into visual prompts directly onto an image canvas effectively bridges the modality gap between discrete language and continuous visual data while preserving spatial layouts and structural priors.
- The Dual-Path Spatially-Adaptive Modulation mechanism is crucial for dynamically injecting source image priors and selectively preserving background regions during editing, ensuring high instruction faithfulness and content consistency.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d7022-26bd-7d91-a3e5-7b17211f9b0d/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7022-26bd-7d91-a3e5-7b17211f9b0d/transcript.json

## Resources

- GitHub repository: https://github.com/CSU-JPG/FlowInOne

## Similar Papers

- UniToken: Harmonizing Multimodal Understanding and Generation through  Unified Visual Encoding (2504.04423v1): Researchers from Fudan University and Meituan develop UniToken, a unified multimodal model that harmonizes visual understanding and generation through a novel dual visual encoder combining continuous semantic features and discrete tokens, achieving competitive performance across multiple benchmarks while addressing the limitations of discrete-only and decoupled encoding approaches.
- NextFlow: Unified Sequential Modeling Activates Multimodal Understanding and Generation (2601.02204v1): Researchers at ByteDance developed NextFlow, a unified autoregressive transformer model that integrates multimodal understanding and generation. It achieves leading performance in image generation, editing, and reasoning tasks, notably generating 1024x1024 images in 5 seconds while demonstrating state-of-the-art prompt following and editing capabilities.
- GoT: Unleashing Reasoning Capability of Multimodal Large Language Model  for Visual Generation and Editing (2503.10639v1): A unified framework integrates reasoning capabilities into visual generation and editing by combining multimodal language models with a semantic-spatial guidance module, demonstrating superior performance on GenEval and Emu-Edit benchmarks while enabling interactive control through explicit reasoning chains.
- Nexus-Gen: Unified Image Understanding, Generation, and Editing via Prefilled Autoregression in Shared Embedding Space (2504.21356v3): Nexus-Gen, developed by Zhejiang University and Alibaba Group, unifies image understanding, generation, and editing within a single 7B-parameter framework, introducing a "prefilled autoregression" strategy to mitigate error accumulation in continuous embedding prediction. The model achieves state-of-the-art performance across diverse benchmarks and releases a new high-quality instruction-guided image editing dataset.
- OneCAT: Decoder-Only Auto-Regressive Model for Unified Understanding and Generation (2509.03498v3): OneCAT, developed by Meituan Inc. and Shanghai Jiao Tong University, introduces a pure decoder-only, encoder-free, and VAE tokenizer-free multimodal model for unified understanding, generation, and editing. This architecture significantly improves inference efficiency, achieving up to 61% faster time-to-first-token for high-resolution understanding and approximately 10x faster image generation compared to diffusion-based models, while setting new state-of-the-art among unified models on various benchmarks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
