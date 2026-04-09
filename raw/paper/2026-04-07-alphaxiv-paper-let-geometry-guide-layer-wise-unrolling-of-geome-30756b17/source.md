---
id: 2026-04-07-alphaxiv-paper-let-geometry-guide-layer-wise-unrolling-of-geome-30756b17
kind: paper
title: 'Let Geometry GUIDE: Layer-wise Unrolling of Geometric Priors in Multimodal LLMs'
source_url: https://www.alphaxiv.org/abs/2604.05695
source_name: alphaXiv Papers
authors:
- Chongyu Wang
- Ting Huang
- Chunyu Sun
- Xinyu Ning
- Di Wang
- Hao Tang
published_at: '2026-04-07T10:45:28Z'
ingested_at: '2026-04-09T09:56:22.145544Z'
content_hash: 9c7250ae2a1c51770c628f710fc3ff0ebbdf5d76100e3c50d91f020fd8103981
identity_hash: 587ad4ce190467d7327d44d84b00b71f2ecb27889b9f03e01f05ee14e5678316
tags:
- paper
- alphaxiv
- research
- attention-mechanisms
- Computer Science
- cs.CV
- geometric-deep-learning
- multi-modal-learning
- representation-learning
- robotics-perception
- transformers
- vision-language-models
- visual-reasoning
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
external_key: https://www.alphaxiv.org/abs/2604.05695
canonical_url: https://www.alphaxiv.org/abs/2604.05695
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:56:22.145551Z'
short_summary: The GUIDE framework enhances multimodal large language models (MLLMs) with physical spatial awareness by progressively injecting multi-granularity geometric priors into their early layers, dynamically modulated by a context-aware gating mechanism. This approach led to an average score of 64.2 on VSI-Bench and achieved new state-of-the-art on 3D Visual Grounding (ScanRefer) with 59.6 Acc@0.25 among models using only 2D inputs.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Let Geometry GUIDE: Layer-wise Unrolling of Geometric Priors in Multimodal LLMs

## alphaXiv Summary

The GUIDE framework enhances multimodal large language models (MLLMs) with physical spatial awareness by progressively injecting multi-granularity geometric priors into their early layers, dynamically modulated by a context-aware gating mechanism. This approach led to an average score of 64.2 on VSI-Bench and achieved new state-of-the-art on 3D Visual Grounding (ScanRefer) with 59.6 Acc@0.25 among models using only 2D inputs.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05695
- Source paper: https://arxiv.org/abs/2604.05695
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05695v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05695v1.png
- Paper ID: 2604.05695
- Canonical ID: 2604.05695v1
- Paper group ID: 019d6b79-1e7a-7e8c-9385-d78f3cd8b982
- Version ID: 019d6b79-1e94-773c-87f5-4dba4593f8de
- Version: v1
- Version order: 1
- Published at: 2026-04-07T10:45:28+00:00
- First published at: 2026-04-07T10:45:28+00:00
- Updated at: 2026-04-08T05:03:13.018000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Chongyu Wang
- Ting Huang
- Chunyu Sun
- Xinyu Ning
- Di Wang
- Hao Tang

## Topics

- attention-mechanisms
- Computer Science
- cs.CV
- geometric-deep-learning
- multi-modal-learning
- representation-learning
- robotics-perception
- transformers
- vision-language-models
- visual-reasoning

## Metrics

- Visits (all): 31
- Visits (last 7 days): 31
- Total votes: 1
- Public total votes: 2
- X likes: 0

## Abstract

Multimodal Large Language Models (MLLMs) have achieved remarkable progress in 2D visual tasks but still exhibit limited physical spatial awareness when processing real-world visual streams. Recently, feed-forward geometric foundation models, which implicitly extract geometric priors, have provided a new pathway to address this issue. However, existing geometry-aware MLLMs are predominantly constrained by the paradigm of single deep-layer extraction and input-level fusion. This flattened fusion leads to the loss of local geometric details and causes semantic mismatches in the early layers. To break this bottleneck, we propose GUIDE (Geometric Unrolling Inside MLLM Early-layers), a progressive geometric priors injection framework. GUIDE performs multi-level sampling within the geometric encoder, comprehensively capturing multi-granularity features ranging from local edges to global topologies. Subsequently, we rigorously align and fuse these multi-level geometric priors step-by-step with the early layers of the MLLM. Building upon the injection of multi-granularity geometric information, this design guides the model to progressively learn the 2D-to-3D transitional process. Furthermore, we introduce a context-aware gating that enables the model to fetch requisite spatial cues based on current semantics, thereby maximizing the utilization efficiency of spatial priors and effectively suppressing redundant geometric noise. Extensive experiments demonstrate that GUIDE significantly outperforms existing baselines on multiple complex spatial reasoning and perception tasks, establishing a novel paradigm for integrating 3D geometric priors into large models.

## Problem

- Multimodal Large Language Models (MLLMs) lack robust physical spatial awareness when processing 2D visual streams, hindering tasks requiring precise metric measurements, occlusion understanding, and macroscopic scene layout comprehension.
- Existing geometry-aware MLLMs primarily rely on 'Input-Level Fusion and Deep-Layer Extraction,' which leads to the loss of crucial local geometric details due to deep-layer smoothing.
- Single-shot injection of geometric features to the MLLM entrance creates a bottleneck, preventing continuous access to multi-granularity cues and causing early-layer cross-modal semantic mismatches.

## Method

- The GUIDE (Geometric Unrolling Inside MLLM Early-layers) framework progressively injects multi-granularity geometric priors from a parallel geometric encoder into the first few decoder layers of the MLLM.
- It implements strict spatial grid alignment between visual and geometric features and extracts a multi-level stack of features from the geometric encoder, spanning from local edges to global topologies.
- A dual context-aware gating mechanism, composed of token-wise semantic-guided and layer-wise global gates, adaptively modulates the injection strength of geometric features to prevent semantic interference.

## Results

- GUIDE-9B achieved an average score of 64.2 on VSI-Bench, outperforming VLM-3R (60.9) and VG LLM-8B* (62.2), and its 5B variant surpassed closed-source models like GPT-5 (55.0) and Gemini-2.5-Pro (53.6).
- On 3D Visual Grounding (ScanRefer), GUIDE-9B achieved 59.6 Acc@0.25 with proposal refinement, establishing a new state-of-the-art for models without explicit 3D inputs and surpassing models utilizing 3D data like LLaVA-3D.
- For 3D Dense Captioning (Scan2Cap), GUIDE-9B attained 81.2 on CIDEr (C@0.5), exceeding strong baselines including VG LLM-8B (80.0) and models with full 3D point cloud inputs like Video-3D LLM (80.0).

## Takeaways

- Progressive, layer-wise injection of multi-granularity geometric priors into early MLLM layers is more effective than single-shot input-level fusion for internalizing 2D-to-3D transitional knowledge.
- Unfiltered geometric features can cause catastrophic interference with the MLLM's semantic space, demonstrating the critical role of context-aware gating in dynamically modulating injection strength and suppressing noise.
- There is an optimal injection depth for geometric priors (found to be 6 layers); over-introducing low-level geometric information into deeper, abstract semantic layers leads to performance degradation due to cross-modal mismatches.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b79-1e7a-7e8c-9385-d78f3cd8b982/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b79-1e7a-7e8c-9385-d78f3cd8b982/transcript.json

## Similar Papers

- VLM-3R: Vision-Language Models Augmented with Instruction-Aligned 3D Reconstruction (2505.20279v3): VLM-3R is a framework that augments Vision-Language Models with 3D spatial and temporal reasoning from monocular video. It introduces implicit 3D reconstructive tokens and a fusion mechanism, achieving leading performance on new spatial and spatio-temporal benchmarks, including outperforming proprietary models on VSTI-Bench.
- Spatial-MLLM: Boosting MLLM Capabilities in Visual-based Spatial  Intelligence (2505.23747v1): Tsinghua University researchers develop Spatial-MLLM, a framework that enhances multimodal large language models' spatial reasoning from 2D videos by combining a standard visual encoder with a spatial encoder initialized from a visual geometry foundation model (VGGT), achieving state-of-the-art performance on VSI-Bench and substantially outperforming existing video MLLMs on ScanQA and SQA3D through a dual-encoder architecture, space-aware frame sampling strategy, and reinforcement learning training on their new Spatial-MLLM-120k dataset covering diverse spatial understanding tasks.
- G$^2$VLM: Geometry Grounded Vision Language Model with Unified 3D Reconstruction and Spatial Reasoning (2511.21688v2): G
G

²VLM integrates 3D reconstruction and spatial reasoning within a single Vision-Language Model, addressing the spatial intelligence limitations of current VLMs. It learns explicit visual geometry from 2D data using a Mixture-of-Transformer-Experts architecture, leading to robust spatial understanding and strong performance on both 3D reconstruction and complex spatial reasoning benchmarks.
- MM-Spatial: Exploring 3D Spatial Understanding in Multimodal LLMs (2503.13111v2): Apple researchers developed MM-Spatial, a Multimodal Large Language Model (MLLM) architecture, to significantly enhance 3D spatial understanding. The work introduces the Cubify Anything VQA (CA-VQA) dataset, enabling MM-Spatial to achieve state-of-the-art performance on 3D spatial tasks while retaining generalist MLLM capabilities, and demonstrating surprising intrinsic metric depth estimation abilities.
- SpatialLLM: A Compound 3D-Informed Design towards Spatially-Intelligent  Large Multimodal Models (2505.00788v3): Researchers at Johns Hopkins University developed SpatialLLM, a compound 3D-informed design that systematically enhances Large Multimodal Models' 3D spatial reasoning capabilities. SpatialLLM achieved 62.7% accuracy on the new SpatialVQA benchmark, outperforming GPT-4o by 8.7% and the best open-source spatial-centric models by 10.5%.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
