---
id: 2026-04-06-alphaxiv-paper-genserve-efficient-co-serving-of-heterogeneous-d-92094ca9
kind: paper
title: 'GENSERVE: Efficient Co-Serving of Heterogeneous Diffusion Model Workloads'
source_url: https://www.alphaxiv.org/abs/2604.04335
source_name: alphaXiv Papers
authors:
- Fanjiang Ye
- Zhangke Li
- Xinrui Zhong
- Ethan Ma
- Russell Chen
- Kaijian Wang
- Jingwei Zuo
- Desen Sun
- Ye Cao
- Triston Cao
- Myungjin Lee
- Arvind Krishnamurthy
- Yuke Wang
published_at: '2026-04-06T01:02:02Z'
ingested_at: '2026-04-09T10:01:14.816896Z'
content_hash: 70c8c0826d62b210c3fbcf0cfde9cfd367e1caac3d9fcf15869a5b7b0762c172
identity_hash: 6610fe1f028baad35702ef486ede8791f70f11cabdf9940deb118329f16be0ca
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.DC
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
external_key: https://www.alphaxiv.org/abs/2604.04335
canonical_url: https://www.alphaxiv.org/abs/2604.04335
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:01:14.816905Z'
short_summary: GENSERVE is a co-serving system for heterogeneous text-to-image (T2I) and text-to-video (T2V) diffusion model workloads on shared GPU clusters. It improves Service Level Objective (SLO) attainment rates by up to 44% and reduces image request tail latency by 3.1x through dynamic resource allocation that leverages model-specific execution properties.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# GENSERVE: Efficient Co-Serving of Heterogeneous Diffusion Model Workloads

## alphaXiv Summary

GENSERVE is a co-serving system for heterogeneous text-to-image (T2I) and text-to-video (T2V) diffusion model workloads on shared GPU clusters. It improves Service Level Objective (SLO) attainment rates by up to 44% and reduces image request tail latency by 3.1x through dynamic resource allocation that leverages model-specific execution properties.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04335
- Source paper: https://arxiv.org/abs/2604.04335
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04335v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04335v1.png
- Paper ID: 2604.04335
- Canonical ID: 2604.04335v1
- Paper group ID: 019d65b6-6302-779a-884e-f661b641f942
- Version ID: 019d65b6-6341-7069-ae0a-090a2a235804
- Version: v1
- Version order: 1
- Published at: 2026-04-06T01:02:02+00:00
- First published at: 2026-04-06T01:02:02+00:00
- Updated at: 2026-04-07T02:12:24.962000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Fanjiang Ye
- Zhangke Li
- Xinrui Zhong
- Ethan Ma
- Russell Chen
- Kaijian Wang
- Jingwei Zuo
- Desen Sun
- Ye Cao
- Triston Cao
- Myungjin Lee
- Arvind Krishnamurthy
- Yuke Wang

## Topics

- Computer Science
- cs.DC

## Metrics

- Visits (all): 35
- Visits (last 7 days): 35
- Total votes: 1
- Public total votes: 5
- X likes: 0

## Abstract

Diffusion models have emerged as the prevailing approach for text-to-image (T2I) and text-to-video (T2V) generation, yet production platforms must increasingly serve both modalities on shared GPU clusters while meeting stringent latency SLOs. Co-serving such heterogeneous workloads is challenging: T2I and T2V requests exhibit vastly different compute demands, parallelism characteristics, and latency requirements, leading to significant SLO violations in existing serving systems. We present GENSERVE, a co-serving system that leverages the inherent predictability of the diffusion process to optimize serving efficiency. A central insight is that diffusion inference proceeds in discrete, predictable steps and is naturally preemptible at step boundaries, opening a new design space for heterogeneity-aware resource management. GENSERVE introduces step-level resource adaptation through three coordinated mechanisms: intelligent video preemption, elastic sequence parallelism with dynamic batching, and an SLO-aware scheduler that jointly optimizes resource allocation across all concurrent requests. Experimental results show that GENSERVE improves the SLO attainment rate by up to 44% over the strongest baseline across diverse configurations.

## Problem

- Existing serving systems struggle to manage the disparate computational demands and latency targets of T2I and T2V diffusion model requests on shared infrastructure.
- Conventional scheduling policies (e.g., FIFO, SJF) cause head-of-line blocking for latency-sensitive image requests or starvation for long-running video tasks, leading to SLO violations.
- Static resource management and dedicated GPU partitioning for different modalities result in suboptimal GPU utilization and resource fragmentation.

## Method

- GENSERVE employs an SLO-aware online scheduler using a knapsack-style dynamic programming algorithm to jointly optimize resource allocation for all in-flight requests.
- It integrates intelligent video preemption at denoising step boundaries to free up GPUs for urgent image tasks while considering video deadlines and minimal overhead.
- The system utilizes elastic resource allocation, dynamically adjusting Sequence Parallelism (SP) for video tasks and applying SLO-aware dynamic batching for image tasks.

## Results

- GENSERVE achieved up to 78% overall SLO Attainment Rate (SAR) at a default strictness (σ=1.0), outperforming SRTF (71%) and FCFS (59%), with the highest SAR across varying workloads and arrival rates.
- It reduced the p90 tail latency for image requests by 3.1x compared to FCFS (from 18.0s to 5.8s), effectively mitigating head-of-line blocking.
- The overheads for the DP solver, preemption (pause/resume), and SP reconfiguration were consistently low, typically less than 0.25% of a single 720p video denoising step, confirming practical efficiency.

## Takeaways

- Diffusion model inference is highly predictable due to a fixed number of denoising steps with stable per-step costs, enabling accurate runtime estimation for proactive scheduling.
- Diffusion models are naturally preemptible at step boundaries because their compact intermediate latent states can be stored in GPU memory with negligible overhead, allowing for fine-grained resource redistribution.
- T2I and T2V workloads have distinct computational profiles and parallelism characteristics (e.g., T2I benefits from batching, T2V from SP) that can be exploited for adaptive resource management.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65b6-6302-779a-884e-f661b641f942/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65b6-6302-779a-884e-f661b641f942/transcript.json

## Similar Papers

- Niyama : Breaking the Silos of LLM Inference Serving (2503.22562v1): Microsoft Research India introduces Niyama, a QoS-driven LLM inference serving system that enables efficient co-scheduling of diverse workloads on shared infrastructure, increasing serving capacity by 32% while reducing GPU requirements by 13-32% compared to siloed deployments through adaptive scheduling and hybrid prioritization techniques.
- ModServe: Modality- and Stage-Aware Resource Disaggregation for Scalable Multimodal Model Serving (2502.00937v3): ModServe implements modality- and stage-aware resource disaggregation to efficiently serve Large Multimodal Models (LMMs) in production environments. The system, validated with Azure production traces, achieves 3.3
	5.5
	 higher throughput and reduces GPU costs by 25
	41.3% compared to monolithic serving systems, effectively meeting tail latency Service Level Objectives.
- xDiT: an Inference Engine for Diffusion Transformers (DiTs) with Massive Parallelism (2411.01738v1): xDiT is an inference engine for Diffusion Transformers (DiTs) designed to accelerate high-resolution content generation through massive parallelism. It achieves up to a 13.29x speedup for 4096px image generation on 16 L40 GPUs and enables the decoding of images up to 8192px, utilizing a hybrid parallel approach across diverse hardware.
- vLLM-Omni: Fully Disaggregated Serving for Any-to-Any Multimodal Models (2602.02204v1): vLLM-Omni introduces a fully disaggregated serving system for any-to-any multimodal models, enabling efficient deployment of complex AI architectures that integrate diverse components like LLMs and Diffusion Transformers. The system achieves substantial reductions in job completion time and improved throughput by abstracting models into stages served by specialized engines.
- StreamDiffusionV2: A Streaming System for Dynamic and Interactive Video Generation (2511.07399v2): StreamDiffusionV2 presents a training-free inference system that adapts state-of-the-art video diffusion models for real-time, interactive video generation. This system achieves an ultra-low Time-to-First-Frame (TTFF) of 0.37s and maintains robust performance up to 61.57 FPS on a 1.3B-parameter model with 4x H100 GPUs, ensuring high temporal consistency and adaptability to dynamic content.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
