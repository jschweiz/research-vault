---
id: 2026-03-25-alphaxiv-paper-avo-agentic-variation-operators-for-autonomous-e-0c30946e
kind: paper
title: 'AVO: Agentic Variation Operators for Autonomous Evolutionary Search'
source_url: https://www.alphaxiv.org/abs/2603.24517
source_name: alphaXiv Papers
authors:
- Terry Chen
- Zhifan Ye
- Bing Xu
- Zihao Ye
- Timmy Liu
- Ali Hassani
- Tianqi Chen
- Andrew Kerr
- Haicheng Wu
- Yang Xu
- Yu-Jung Chen
- Hanfeng Chen
- Aditya Kane
- Ronny Krashinsky
- Ming-Yu Liu
- Vinod Grover
- Luis Ceze
- Roger Bringmann
- John Tran
- Wei Liu
- Fung Xie
- Michael Lightstone
- Humphrey Shi
published_at: '2026-03-25T16:55:04Z'
ingested_at: '2026-04-09T23:38:18.372661Z'
content_hash: 31ce3afe32f5522e9e75c158f054aad2f6f5690ab4f7ffa7099a76ad69c64a42
identity_hash: 4eef74c71a2926b9d31393a7c1689a26ec88793f6d03d961e18ef58610b4fef1
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- Computer Science
- cs.LG
- efficient-transformers
- evolutionary-algorithms
- hardware-aware-algorithms
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-podcast.mp3
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2603.24517
canonical_url: https://www.alphaxiv.org/abs/2603.24517
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T23:38:18.372667Z'
short_summary: Agentic Variation Operators (AVO) empower large language models to function as autonomous, iterative optimizers in evolutionary search for high-performance code. This framework successfully discovered multi-head attention kernels on NVIDIA Blackwell B200 GPUs that achieved up to 3.5% higher throughput than cuDNN and 10.5% higher than FlashAttention-4, alongside effective transferability to grouped-query attention.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:42:59.499323Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: e95dc82b7d637235ab8a782a5fde3e52ac0b22cfe3230e3b2ee40d9b347c174b
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# AVO: Agentic Variation Operators for Autonomous Evolutionary Search

## alphaXiv Summary

Agentic Variation Operators (AVO) empower large language models to function as autonomous, iterative optimizers in evolutionary search for high-performance code. This framework successfully discovered multi-head attention kernels on NVIDIA Blackwell B200 GPUs that achieved up to 3.5% higher throughput than cuDNN and 10.5% higher than FlashAttention-4, alongside effective transferability to grouped-query attention.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.24517
- Source paper: https://arxiv.org/abs/2603.24517
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.24517v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.24517v1.png
- Paper ID: 2603.24517
- Canonical ID: 2603.24517v1
- Paper group ID: 019d27c8-58f8-7fce-9fa4-284e66418945
- Version ID: 019d27c8-5976-7351-9aff-acb9f4e1028e
- Version: v1
- Version order: 1
- Published at: 2026-03-25T16:55:04+00:00
- First published at: 2026-03-25T16:55:04+00:00
- Updated at: 2026-03-26T01:35:34.648000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Terry Chen
- Zhifan Ye
- Bing Xu
- Zihao Ye
- Timmy Liu
- Ali Hassani
- Tianqi Chen
- Andrew Kerr
- Haicheng Wu
- Yang Xu
- Yu-Jung Chen
- Hanfeng Chen
- Aditya Kane
- Ronny Krashinsky
- Ming-Yu Liu
- Vinod Grover
- Luis Ceze
- Roger Bringmann
- John Tran
- Wei Liu
- Fung Xie
- Michael Lightstone
- Humphrey Shi

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.LG
- efficient-transformers
- evolutionary-algorithms
- hardware-aware-algorithms
- inference-optimization
- optimization-methods
- transformers

## Metrics

- Visits (all): 2322
- Visits (last 7 days): 754
- Total votes: 33
- Public total votes: 167
- X likes: 0

## Abstract

Agentic Variation Operators (AVO) are a new family of evolutionary variation operators that replace the fixed mutation, crossover, and hand-designed heuristics of classical evolutionary search with autonomous coding agents. Rather than confining a language model to candidate generation within a prescribed pipeline, AVO instantiates variation as a self-directed agent loop that can consult the current lineage, a domain-specific knowledge base, and execution feedback to propose, repair, critique, and verify implementation edits. We evaluate AVO on attention, among the most aggressively optimized kernel targets in AI, on NVIDIA Blackwell (B200) GPUs. Over 7 days of continuous autonomous evolution on multi-head attention, AVO discovers kernels that outperform cuDNN by up to 3.5% and FlashAttention-4 by up to 10.5% across the evaluated configurations. The discovered optimizations transfer readily to grouped-query attention, requiring only 30 minutes of additional autonomous adaptation and yielding gains of up to 7.0% over cuDNN and 9.3% over FlashAttention-4. Together, these results show that agentic variation operators move beyond prior LLM-in-the-loop evolutionary pipelines by elevating the agent from candidate generator to variation operator, and can discover performance-critical micro-architectural optimizations that produce kernels surpassing state-of-the-art expert-engineered attention implementations on today's most advanced GPU hardware.

## Problem

- Existing LLM-augmented evolutionary search methods restrict LLMs to single-turn candidate generation, limiting their capacity for complex, iterative optimization workflows.
- Optimizing performance-critical computational targets, such as GPU kernels for deep learning, demands intricate, multi-step engineering, which current LLM approaches do not fully support.
- Achieving further performance gains on already aggressively optimized implementations like FlashAttention-4 and cuDNN requires deep, sustained, and iterative interaction with hardware specifics and development environments.

## Method

- Introduce Agentic Variation Operators (AVO), which replace traditional evolutionary variation with an autonomous LLM-powered agent, granting it full agency over the optimization process.
- The AVO agent is equipped with planning capabilities, persistent memory, and tool use (e.g., code editing, shell execution, documentation retrieval) to perform self-directed, multi-step optimization loops.
- The agent continuously evolves solutions, performing internal edit-evaluate-diagnose cycles, and commits improved versions to a lineage, guided by a self-supervision mechanism to maintain progress over extended periods.

## Results

- AVO-discovered multi-head attention (MHA) kernels on NVIDIA Blackwell B200 GPUs achieved up to 3.5% higher throughput than cuDNN and 10.5% higher than FlashAttention-4 for causal attention configurations.
- The evolved MHA kernel was autonomously adapted to grouped-query attention (GQA) in approximately 30 minutes, showing up to 7.0% gains over cuDNN and 9.3% over FlashAttention-4 for causal GQA.
- The agent identified specific micro-architectural optimizations, such as branchless accumulator rescaling, correction/MMA pipeline overlap, and register rebalancing across warp groups, illustrating its capacity for fine-grained hardware tuning.

## Takeaways

- Elevating LLMs to autonomous "Agentic Variation Operators" enables them to engage in complex, iterative engineering workflows, moving beyond mere candidate generation to genuine code optimization.
- Autonomous agents can perform deep hardware-level reasoning, including understanding synchronization, memory ordering, instruction pipeline scheduling, and register allocation, to achieve performance gains.
- Continuous, self-directed evolution over extended durations can uncover highly optimized solutions that surpass expert-engineered baselines and are transferable to related computational tasks.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d27c8-58f8-7fce-9fa4-284e66418945/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d27c8-58f8-7fce-9fa4-284e66418945/transcript.json
- Transcript lines: 17
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- CUDA Agent: Large-Scale Agentic RL for High-Performance CUDA Kernel Generation (2602.24286v1): Researchers from ByteDance Seed and Tsinghua University developed CUDA Agent, a large-scale agentic reinforcement learning system that autonomously generates high-performance CUDA kernels. This system achieves superior optimization capabilities on the KernelBench benchmark, yielding substantial speedups over traditional compilers and other advanced language models.
- AlphaEvolve: A coding agent for scientific and algorithmic discovery (2506.13131v1): AlphaEvolve, from Google DeepMind, combines large language models with an evolutionary search framework to autonomously discover novel algorithms and optimize code. This system identified a faster procedure for 4x4 complex matrix multiplication, improved state-of-the-art for several open mathematical problems, and delivered tangible optimizations for Google's computing ecosystem, including recovering 0.7% of fleet-wide compute resources.
- CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery (2604.01658v1): The CORAL framework introduces an autonomous multi-agent evolutionary system, empowering Large Language Model agents to control their discovery process and collaborate indirectly through shared persistent memory. This approach achieved new state-of-the-art results on 8 out of 11 mathematical and systems optimization tasks, exhibiting a 3-10x higher improvement rate and an 18.3% cycle reduction in kernel engineering.
- EvoCUA: Evolving Computer Use Agents via Learning from Scalable Synthetic Experience (2601.15876v2): Meituan, in collaboration with Fudan, Tongji, and HKUST, developed EvoCUA, an evolutionary framework for computer-use agents that learns from scalable synthetic experience instead of static datasets. This approach achieved a 56.7% success rate on the OSWorld benchmark, establishing a new open-source state-of-the-art and nearing the performance of leading closed-source models.
- Group-Evolving Agents: Open-Ended Self-Improvement via Experience Sharing (2602.04837v1): Researchers at the University of California, Santa Barbara developed Group-Evolving Agents (GEA), a framework enabling open-ended self-improvement for AI systems by evolving groups of agents that share experiences. This group-centric approach led to a 71.0% success rate on SWE-bench Verified and 88.3% on Polyglot, surpassing individual-centric self-evolving methods and matching human-designed agent performance.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
