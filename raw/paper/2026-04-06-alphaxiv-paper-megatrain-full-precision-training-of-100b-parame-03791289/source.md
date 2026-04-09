---
id: 2026-04-06-alphaxiv-paper-megatrain-full-precision-training-of-100b-parame-03791289
kind: paper
title: 'MegaTrain: Full Precision Training of 100B+ Parameter Large Language Models on a Single GPU'
source_url: https://www.alphaxiv.org/abs/2604.05091
source_name: alphaXiv Papers
authors:
- Zhengqing Yuan
- Hanchi Sun
- Lichao Sun
- Yanfang Ye
published_at: '2026-04-06T18:43:56Z'
ingested_at: '2026-04-09T08:10:41.117313Z'
content_hash: 571a93de3eb3e25fb6cba49e17ae12a1d1f0befde875888c175e83196b1b1ec5
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cl
- cs.dc
- cs.os
- efficient-transformers
- hardware-aware-algorithms
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
external_key: https://www.alphaxiv.org/abs/2604.05091
canonical_url: https://www.alphaxiv.org/abs/2604.05091
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:10:41.117320Z'
short_summary: MegaTrain is a memory-centric system that allows full-precision training of LLMs over 100B parameters on a single GPU by using host memory for model states. It achieves this through a pipelined execution engine and stateless layer templates to minimize device state and optimize throughput.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:40:50.554676Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: ad04b60e3a24caf4ca4834c4571adc12785255d5d27be75653c6daf3bace9bdb
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: f77e4659411c4ababe77249d8d146dd84bea993f8c9f2f1ffeeb6d6e6344f83d
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.75
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses the user's favorite topics of LLM training, memory optimization, and research tooling.
  evidence_quotes:
  - MegaTrain is a memory-centric system that allows full-precision training of LLMs over 100B parameters on a single GPU by using host memory for model states.
  - Decoupling model scale from limited GPU device memory is achievable by using host memory as the primary authoritative store for persistent training states.
  - It achieves 1.84$ imes$ the training throughput of DeepSpeed ZeRO-3 with CPU offloading when training 14B models.
---
# MegaTrain: Full Precision Training of 100B+ Parameter Large Language Models on a Single GPU

## alphaXiv Summary

MegaTrain is a memory-centric training system developed by researchers from the University of Notre Dame and Lehigh University that enables full-precision training of Large Language Models over 100 billion parameters on a single GPU. It achieves this by making host memory the primary storage for model states, while GPUs function as transient compute units, demonstrating superior throughput and memory efficiency compared to existing offloading solutions.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05091
- Source paper: https://arxiv.org/abs/2604.05091
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05091v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05091v1.png
- GitHub: https://github.com/DLYuanGod/MegaTrain
- GitHub stars: 0
- Paper ID: 2604.05091
- Canonical ID: 2604.05091v1
- Paper group ID: 019d6ad2-a30f-7d76-9712-cf87fee3405c
- Version ID: 019d6ad2-a35f-74d6-b623-2441e2caf497
- Version: v1
- Version order: 1
- Published at: 2026-04-06T18:43:56+00:00
- First published at: 2026-04-06T18:43:56+00:00
- Updated at: 2026-04-08T02:01:22.447000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Zhengqing Yuan
- Hanchi Sun
- Lichao Sun
- Yanfang Ye

## Topics

- Computer Science
- cs.CL
- cs.DC
- cs.OS
- efficient-transformers
- hardware-aware-algorithms
- ml-systems
- optimization-methods
- training-orchestration
- transformers

## Metrics

- Visits (all): 312
- Visits (last 7 days): 312
- Total votes: 4
- Public total votes: 11
- X likes: 0

## Abstract

We present MegaTrain, a memory-centric system that efficiently trains 100B+ parameter large language models at full precision on a single GPU. Unlike traditional GPU-centric systems, MegaTrain stores parameters and optimizer states in host memory (CPU memory) and treats GPUs as transient compute engines. For each layer, we stream parameters in and compute gradients out, minimizing persistent device state. To battle the CPU-GPU bandwidth bottleneck, we adopt two key optimizations. 1) We introduce a pipelined double-buffered execution engine that overlaps parameter prefetching, computation, and gradient offloading across multiple CUDA streams, enabling continuous GPU execution. 2) We replace persistent autograd graphs with stateless layer templates, binding weights dynamically as they stream in, eliminating persistent graph metadata while providing flexibility in scheduling. On a single H200 GPU with 1.5TB host memory, MegaTrain reliably trains models up to 120B parameters. It also achieves 1.84$\times$ the training throughput of DeepSpeed ZeRO-3 with CPU offloading when training 14B models. MegaTrain also enables 7B model training with 512k token context on a single GH200.

## Problem

- Training Large Language Models (LLMs) exceeding tens of billions of parameters requires memory that often surpasses the capacity of a single GPU's high-bandwidth memory (HBM).
- Current offloading systems extend GPU capacity but treat host memory as a secondary spill buffer, leading to inefficiencies, redundant staging, and rapid GPU memory saturation.
- The high resource demands for fine-tuning large LLMs restrict access and broader participation in LLM development to institutions with substantial GPU infrastructure.

## Method

- MegaTrain implements a memory-centric approach, making host memory the authoritative store for all persistent training states (parameters, gradients, optimizer moments), while the GPU acts as a transient compute engine.
- It employs a pipelined double-buffered execution engine with three concurrent CUDA streams to orchestrate data transfers and computation, hiding CPU-GPU bandwidth latency.
- Model parameters are streamed to the GPU layer-by-layer for computation, and gradients are immediately offloaded to host memory, with optimizer updates performed entirely on the CPU.

## Results

- MegaTrain successfully trained models up to 120 billion parameters on a single H200 GPU, a scale at which competing offloading systems (DeepSpeed ZeRO-3 Offload, ZeRO-Infinity) experienced out-of-memory errors.
- The system achieved high sustained throughput, reaching 264 TFLOPS for a 14B parameter model on a GH200, demonstrating a 1.84x throughput improvement over DeepSpeed ZeRO-3 Offload, and maintained lower host memory consumption.
- It enabled full-precision training for ultra-long context lengths up to 512K tokens for a 7B model on a single GH200, maintaining stable memory usage (74-88 GB GPU memory) despite significant context expansion, and scaled 14B models on consumer-grade GPUs like the RTX 3090.

## Takeaways

- Decoupling model scale from limited GPU device memory is achievable by using host memory as the primary authoritative store for persistent training states.
- Effective overlap of data transfer (Host-to-Device and Device-to-Host) with computation is crucial to maximize GPU utilization and mitigate PCIe bandwidth bottlenecks for very large models.
- A stateless execution model with dynamic parameter binding and explicit memory management allows for fine-grained control over tensor lifecycles, avoiding fragmentation and enabling large-scale, long-context training.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6ad2-a30f-7d76-9712-cf87fee3405c/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ad2-a30f-7d76-9712-cf87fee3405c/transcript.json
- Transcript lines: 19
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/DLYuanGod/MegaTrain

## Similar Papers

- Reducing Activation Recomputation in Large Transformer Models (2205.05198v1): Researchers from NVIDIA developed sequence parallelism and selective activation recomputation to mitigate activation memory bottlenecks and enhance training throughput for large transformer models. These methods achieved approximately 5x reduction in activation memory and a 29-32% improvement in training throughput while reducing recomputation overhead to just 3%.
- ZeRO: Memory Optimizations Toward Training Trillion Parameter Models (1910.02054v3): ZeRO, developed by Microsoft, is a memory optimization strategy implemented within the DeepSpeed library that allows for efficient training of deep learning models with up to 170 billion parameters. This system optimizes memory use by partitioning model and residual states across devices, enabling unprecedented model scales while achieving high training throughput and powering models like Turing-NLG.
- ZO2: Scalable Zeroth-Order Fine-Tuning for Extremely Large Language  Models with Limited GPU Memory (2503.12668v1): KAUST researchers develop ZO2, a framework that enables fine-tuning of large language models on limited GPU memory through CPU offloading and zeroth-order optimization, allowing models like OPT-175B to be fine-tuned on a single 18GB GPU while maintaining accuracy comparable to traditional methods.
- MegaScale-MoE: Large-Scale Communication-Efficient Training of Mixture-of-Experts Models in Production (2505.11432v3): A production-grade system named MegaScale-MoE, developed by Peking University and ByteDance Seed, significantly improves the efficiency of large-scale Mixture-of-Experts (MoE) model training by mitigating communication bottlenecks. It achieves a 1.88x speedup over Megatron-LM for a 352B MoE model on 1,440 NVIDIA Hopper GPUs and has saved millions of GPU hours in ByteDance's data centers.
- SlimPipe: Memory-Thrifty and Efficient Pipeline Parallelism for  Long-Context LLM Training (2504.14519v1): Kuaishou Technology researchers present SlimPipe, a pipeline parallelism framework that enables training of large language models with ultra-long context lengths (up to 4096K tokens) while achieving 45.0% Model FLOPs Utilization on Llama 70B through uniform sequence slicing and workload redistribution techniques.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
