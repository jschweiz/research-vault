---
id: 2026-04-06-alphaxiv-paper-direct-video-mashup-creation-via-hierarchical-mu-3a83dc17
kind: paper
title: 'DIRECT: Video Mashup Creation via Hierarchical Multi-Agent Planning and Intent-Guided Editing'
source_url: https://www.alphaxiv.org/abs/2604.04875
source_name: alphaXiv Papers
authors:
- Ke Li
- Maoliang Li
- Jialiang Chen
- Jiayu Chen
- Zihao Zheng
- Shaoqi Wang
- Xiang Chen
published_at: '2026-04-06T17:26:04Z'
ingested_at: '2026-04-09T09:57:19.456355Z'
content_hash: 42ba3ac3712ecc4f3bf53986e846a99ac05075aef0a07f23e082cc7f60fea11a
identity_hash: 0485b5f3d1dfedb210e465ab70ee1a134cf4379ccbe03d4f327f85b899499573
tags:
- paper
- alphaxiv
- research
- agents
- Computer Science
- cs.AI
- cs.CV
- cs.MM
- generative-models
- human-ai-interaction
- multi-agent-learning
- multi-modal-learning
- optimization-methods
- sequence-modeling
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
external_key: https://www.alphaxiv.org/abs/2604.04875
canonical_url: https://www.alphaxiv.org/abs/2604.04875
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:57:19.456361Z'
short_summary: Researchers from Peking University and Huazhong University of Science and Technology developed DIRECT, a hierarchical multi-agent framework for automated video mashup creation, framing the task as a Multimodal Coherency Satisfaction Problem. The system integrates MLLM-based planning with fine-grained multimodal perception, significantly outperforming baselines in visual continuity and auditory synchronization metrics, and achieving higher subjective quality scores in user studies.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# DIRECT: Video Mashup Creation via Hierarchical Multi-Agent Planning and Intent-Guided Editing

## alphaXiv Summary

Researchers from Peking University and Huazhong University of Science and Technology developed DIRECT, a hierarchical multi-agent framework for automated video mashup creation, framing the task as a Multimodal Coherency Satisfaction Problem. The system integrates MLLM-based planning with fine-grained multimodal perception, significantly outperforming baselines in visual continuity and auditory synchronization metrics, and achieving higher subjective quality scores in user studies.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04875
- Source paper: https://arxiv.org/abs/2604.04875
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04875v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04875v1.png
- GitHub: https://github.com/AK-DREAM/DIRECT-Claw
- GitHub stars: 1
- Paper ID: 2604.04875
- Canonical ID: 2604.04875v1
- Paper group ID: 019d6610-042b-71ab-a992-05e729470973
- Version ID: 019d6610-0475-74bb-a8ad-f15205912a79
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:26:04+00:00
- First published at: 2026-04-06T17:26:04+00:00
- Updated at: 2026-04-07T03:50:18.923000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Ke Li
- Maoliang Li
- Jialiang Chen
- Jiayu Chen
- Zihao Zheng
- Shaoqi Wang
- Xiang Chen

## Topics

- agents
- Computer Science
- cs.AI
- cs.CV
- cs.MM
- generative-models
- human-ai-interaction
- multi-agent-learning
- multi-modal-learning
- optimization-methods
- sequence-modeling
- video-understanding

## Metrics

- Visits (all): 37
- Visits (last 7 days): 37
- Total votes: 0
- Public total votes: 7
- X likes: 0

## Abstract

Video mashup creation represents a complex video editing paradigm that recomposes existing footage to craft engaging audio-visual experiences, demanding intricate orchestration across semantic, visual, and auditory dimensions and multiple levels. However, existing automated editing frameworks often overlook the cross-level multimodal orchestration to achieve professional-grade fluidity, resulting in disjointed sequences with abrupt visual transitions and musical misalignment. To address this, we formulate video mashup creation as a Multimodal Coherency Satisfaction Problem (MMCSP) and propose the DIRECT framework. Simulating a professional production pipeline, our hierarchical multi-agent framework decomposes the challenge into three cascade levels: the Screenwriter for source-aware global structural anchoring, the Director for instantiating adaptive editing intent and guidance, and the Editor for intent-guided shot sequence editing with fine-grained optimization. We further introduce Mashup-Bench, a comprehensive benchmark with tailored metrics for visual continuity and auditory alignment. Extensive experiments demonstrate that DIRECT significantly outperforms state-of-the-art baselines in both objective metrics and human subjective evaluation. Project page and code: this https URL

## Problem

- Automated video mashup creation is a complex task requiring intricate orchestration across semantic, visual, and auditory dimensions at multiple levels.
- Existing automated video editing frameworks are primarily semantic-centric, often overlooking fine-grained multimodal cues like motion dynamics, fluent visual transitions, and deeper musical progression matching.
- The lack of cross-level multimodal orchestration in current methods leads to generated sequences that frequently lack professional-grade fluidity, exhibiting disjointed visuals, abrupt transitions, and auditory misalignments.

## Method

- Formulates video mashup creation as a Multimodal Coherency Satisfaction Problem (MMCSP) to jointly satisfy cross-level coherency constraints, encompassing both high-level perceptual goals and low-level explicit metrics.
- Introduces DIRECT, a hierarchical multi-agent framework (Screenwriter, Director, Editor) that simulates a professional editing pipeline by integrating MLLM-based planning with fine-grained multimodal perception and optimization.
- Constructs Mashup-Bench, a comprehensive benchmark dataset with tailored metrics to enable robust and objective evaluation of video mashup quality, specifically for visual continuity and auditory synchronization.

## Results

- DIRECT significantly outperformed state-of-the-art baselines in objective metrics, achieving Motion Continuity ($m_3$) of 77.26 (vs. 62.24 for VideoAgent) and Beat-Cut Synchronization ($m_5$) of 98.69 (vs. 88.43 for VideoAgent).
- In a blind user study, DIRECT received superior subjective ratings across all dimensions, with an Overall Quality score of 5.9 and a 40% increase in Local Segment Cohesion over the best baseline.
- Ablation studies confirmed the critical roles of the Screenwriter for establishing global narrative flow, the Director for adaptive editing heuristics, and dynamic sliding-window trimming for precise, seamless visual transitions.

## Takeaways

- Decomposing complex video editing into a hierarchical multi-agent system, where MLLM agents handle global planning and local intent, and a dedicated Editor focuses on fine-grained optimization, effectively addresses cross-level multimodal orchestration challenges.
- Achieving professional-grade video mashups requires a unified optimization objective (MMCSP) that holistically combines low-level quantifiable metrics (e.g., motion continuity, beat-cut synchronization) with high-level perceptual goals (e.g., narrative flow, segment aesthetics).
- Dynamic, closed-loop feedback from the Director agent, which adapts editing intents based on validation, coupled with frame-level precise shot trimming, is crucial for resolving editing failures and ensuring seamless visual transitions.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6610-042b-71ab-a992-05e729470973/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6610-042b-71ab-a992-05e729470973/transcript.json

## Resources

- GitHub repository: https://github.com/AK-DREAM/DIRECT-Claw

## Similar Papers

- Automated Movie Generation via Multi-Agent CoT Planning (2503.07314v1): Show Lab researchers at NUS introduce MovieAgent, a groundbreaking multi-agent framework that automates long-form video generation through Chain of Thought planning, achieving superior narrative coherence and visual quality while requiring minimal human intervention through innovative coordination between specialized AI agents acting as director, scene planner, and shot designer.
- Long-Video Audio Synthesis with Multi-Agent Collaboration (2503.10719v2)
- Scaling Instruction-Based Video Editing with a High-Quality Synthetic Dataset (2510.15742v2): The Ditto framework introduces a scalable, cost-efficient pipeline to generate Ditto-1M, a high-quality synthetic dataset containing over one million instruction-based video editing examples. This extensive dataset enables the Editto model to achieve state-of-the-art performance across instruction adherence, temporal consistency, and visual quality for complex video modifications.
- MultiShotMaster: A Controllable Multi-Shot Video Generation Framework (2512.03041v1): MultiShotMaster, a framework developed by researchers from Dalian University of Technology, Kuaishou Technology's Kling Team, and The Chinese University of Hong Kong, enables controllable multi-shot video generation by modifying Rotary Position Embedding (RoPE) and employing an automated data curation pipeline. The approach achieved a 0.702 semantic consistency score and a 1.41 transition deviation, outperforming state-of-the-art baselines in multi-shot text-to-video and reference-to-video generation while demonstrating precise shot control and coherent narratives.
- DreaMontage: Arbitrary Frame-Guided One-Shot Video Generation (2512.21252v2)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
