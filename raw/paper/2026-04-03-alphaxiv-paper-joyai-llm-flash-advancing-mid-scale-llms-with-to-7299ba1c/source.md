---
id: 2026-04-03-alphaxiv-paper-joyai-llm-flash-advancing-mid-scale-llms-with-to-7299ba1c
kind: paper
title: 'JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency'
source_url: https://www.alphaxiv.org/abs/2604.03044
source_name: alphaXiv Papers
authors:
- Aichen Cai
- Anmeng Zhang
- Anyu Li
- Bo Zhang
- Bohua Cai
- Chang Li
published_at: '2026-04-03T13:52:38Z'
ingested_at: '2026-04-07T21:43:00.761780Z'
content_hash: ed8fddf5e3a98d74dba05ff796f48bce97436ec60baa949093323c64fb7aaaf5
tags:
- paper
- alphaxiv
- research
- computer science
- cs.ai
- cs.cl
- efficient-transformers
- fine-tuning
- inference-optimization
- lightweight-models
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
external_key: https://www.alphaxiv.org/abs/2604.03044
canonical_url: https://www.alphaxiv.org/abs/2604.03044
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-07T21:43:00.761787Z'
short_summary: '# JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency ## alphaXiv Summary JoyAI-LLM Flash introduces an architecture and training methodology for mid-scale language models (sub-50B parameters) that prioritizes token and computational efficiency without compromising performance. The model, leveraging a Mixture-of-Experts design and novel policy optimization, consistently achieves competitive or superior benchmark results with significantly reduced token consumption compared to existin'
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:38:40.035042Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: ca0c6ab806c1c36141ec09c83644292028802554037acb4bf236f7cc944e3e0e
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: d9c6ff5e7cc85314fa0cd8f977b826f33e26fc68213935bb41c5e3cfd671b1ab
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.5
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses favorite topics like LLM architecture, efficiency, and optimization, making it highly relevant to the user's profile.
  evidence_quotes:
  - 'JoyAI-LLM Flash introduces an architecture and training methodology for mid-scale language models (sub-50B parameters) that prioritizes token and computational '
  - The model, leveraging a Mixture-of-Experts design and novel policy optimization, consistently achieves competitive or superior benchmark results with significan
  - Implemented a 48B-parameter Mixture-of-Experts (MoE) architecture, activating only 3.28B parameters per token for high sparsity and reduced computational cost.
---
# JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency

## alphaXiv Summary

JoyAI-LLM Flash introduces an architecture and training methodology for mid-scale language models (sub-50B parameters) that prioritizes token and computational efficiency without compromising performance. The model, leveraging a Mixture-of-Experts design and novel policy optimization, consistently achieves competitive or superior benchmark results with significantly reduced token consumption compared to existing state-of-the-art models.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03044
- Source paper: https://arxiv.org/abs/2604.03044
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03044v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03044v1.png
- Paper ID: 2604.03044
- Canonical ID: 2604.03044v1
- Paper group ID: 019d61b0-8a93-7b11-9434-8c366e558132
- Version ID: 019d61b0-8b6d-7c62-8d4c-b908acc13d79
- Version: v1
- Version order: 1
- Published at: 2026-04-03T13:52:38+00:00
- First published at: 2026-04-03T13:52:38+00:00
- Updated at: 2026-04-06T07:27:33.011000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Aichen Cai
- Anmeng Zhang
- Anyu Li
- Bo Zhang
- Bohua Cai
- Chang Li
- Changjian Jiang
- Changkai Lu
- Chao Xue
- Chaocai Liang
- Cheng Zhang
- Dongkai Liu
- Fei Wang
- Guoqiang Huang
- Haijian Ke
- Han Lin
- Hao Wang
- Ji Miao
- Jiacheng Zhang
- Jialong Shi
- Jifeng Zhu
- Jingjing Qian
- Junhui Luo
- Junwu Xiong
- Lam So
- Liang Huang
- Ming Ke
- Mingyang Li
- Panfeng Shi
- Peng Hao
- Qi Wang
- Qian Lai
- Qiaoqiao Yuan
- Qingyu Yin
- Qiong Cao
- Qixiang Wang
- Rongcheng Bian
- Rongduo Han
- Shaoqiang Zheng
- Shi Hu
- Shi Suo
- Shijie Ren
- Shijin Zhang
- Shiying Fan
- Shuai Xie
- Tianyi Zhang
- Wei Liu
- Wentao Tan
- Xianghan Meng
- Xiaodong He
- Xing Pan
- Xiran Wang
- Xuyang Peng
- Ya Zhang
- Yang Liu
- Yangyang Duan
- Yanxu Chen
- Yicheng Gong
- Yidan Huang
- Yifei Liu
- Yinhao Bai
- Yongqiang Liu
- Yuesong Zhang
- Yuqi Zhang
- Zerui Xie
- Zhenfang Wang
- Zhennan Shen
- Zheyuan Liu
- Zhuwei Zeng

## Topics

- Computer Science
- cs.AI
- cs.CL
- efficient-transformers
- fine-tuning
- inference-optimization
- lightweight-models
- model-compression
- optimization-methods
- parameter-efficient-training
- reinforcement-learning
- text-generation
- transformers

## Metrics

- Visits (all): 174
- Visits (last 7 days): 174
- Total votes: 0
- Public total votes: 14
- X likes: 0

## Abstract

We introduce JoyAI-LLM Flash, an efficient Mixture-of-Experts (MoE) language model designed to redefine the trade-off between strong performance and token efficiency in the sub-50B parameter regime. JoyAI-LLM Flash is pretrained on a massive corpus of 20 trillion tokens and further optimized through a rigorous post-training pipeline, including supervised fine-tuning (SFT), Direct Preference Optimization (DPO), and large-scale reinforcement learning (RL) across diverse environments. To improve token efficiency, JoyAI-LLM Flash strategically balances \emph{thinking} and \emph{non-thinking} cognitive modes and introduces FiberPO, a novel RL algorithm inspired by fibration theory that decomposes trust-region maintenance into global and local components, providing unified multi-scale stability control for LLM policy optimization. To enhance architectural sparsity, the model comprises 48B total parameters while activating only 2.7B parameters per forward pass, achieving a substantially higher sparsity ratio than contemporary industry leading models of comparable scale. To further improve inference throughput, we adopt a joint training-inference co-design that incorporates dense Multi-Token Prediction (MTP) and Quantization-Aware Training (QAT). We release the checkpoints for both JoyAI-LLM-48B-A3B Base and its post-trained variants on Hugging Face to support the open-source community.

## Problem

- Existing Large Language Models (LLMs) suffer from poor token efficiency and high computational costs during inference.
- Achieving a balance between strong model performance and operational efficiency has been a persistent challenge for LLM deployment.
- Current Reinforcement Learning from Human Feedback (RLHF) methods for LLM alignment face multi-scale instability issues, limiting effective policy optimization.

## Method

- Implemented a 48B-parameter Mixture-of-Experts (MoE) architecture, activating only 3.28B parameters per token for high sparsity and reduced computational cost.
- Developed a joint training-inference co-design incorporating Multi-Token Prediction (MTP) for speculative decoding and Quantization-Aware Training (QAT) for optimized deployment.
- Introduced FiberPO, a novel reinforcement learning algorithm based on fibration theory, to provide unified multi-scale stability control for LLM alignment during post-training.

## Results

- Demonstrated competitive or superior performance across various benchmarks, such as 65.6% accuracy on LiveCodeBench v6 while using 85% fewer tokens than GLM-4.7-Flash-Thinking.
- The FiberPO algorithm achieved stable RL training, reducing mean response length by 42% (from 7,902 to 4,543 tokens) while improving accuracy on AIME 2024.
- Inference optimizations yielded a 1.87x speedup using Multi-Token Prediction and up to a 28% throughput gain with W4AFP8 quantization, showing effective trade-offs between speed and accuracy.

## Takeaways

- Strategic design can balance "thinking" and "non-thinking" cognitive modes, enabling significantly reduced token consumption during inference.
- A sparse Mixture-of-Experts architecture can maintain strong performance while dramatically reducing the number of active parameters per forward pass.
- Decomposing trust-region maintenance in RL into global and local components, as with FiberPO, provides robust multi-scale stability control for LLM policy optimization.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d61b0-8a93-7b11-9434-8c366e558132/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d61b0-8a93-7b11-9434-8c366e558132/transcript.json
- Transcript lines: 21
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- DeepSeek-V3 Technical Report (2412.19437v2): DeepSeek-AI introduces DeepSeek-V3, a 671 billion parameter Mixture-of-Experts (MoE) model that achieves performance comparable to leading closed-source models such as GPT-4o and Claude-3.5-Sonnet, particularly excelling in coding and mathematics. This model was trained for an estimated $5.576 million, showcasing a high level of cost-efficiency through innovations in architecture, training objectives like multi-token prediction, and a highly optimized distributed training infrastructure.
- MiniMax-M1: Scaling Test-Time Compute Efficiently with Lightning  Attention (2506.13585v1): MiniMax developed MiniMax-M1, a large reasoning model leveraging a hybrid Mixture-of-Experts architecture with Lightning Attention to enable efficient scaling of test-time compute for extremely long contexts. It supports up to 1 million input tokens and 80,000 generation tokens while achieving substantial FLOPs reduction and competitive performance across various reasoning benchmarks.
- DeepSeek-V2: A Strong, Economical, and Efficient Mixture-of-Experts Language Model (2405.04434v5): DeepSeek-V2, developed by DeepSeek-AI, is a Mixture-of-Experts language model that demonstrates strong performance while achieving reduced training costs and improved inference efficiency. It delivers a 42.5% reduction in training costs and a 93.3% reduction in KV cache memory, showcasing its practicality for large-scale deployment and its top-tier capabilities in both English and Chinese.
- Kimi K2: Open Agentic Intelligence (2507.20534v2): Kimi K2, an open-source 1.04 trillion-parameter Mixture-of-Experts large language model from Moonshot AI, advances agentic intelligence by achieving state-of-the-art performance in competitive coding and tool use, significantly closing the gap with proprietary models. It introduces innovations in pre-training stability with the MuonClip optimizer and scales agentic capabilities through large-scale synthetic data generation and a robust reinforcement learning framework.
- MiniCPM4: Ultra-Efficient LLMs on End Devices (2506.07900v2): The OpenBMB/Tsinghua University team developed MiniCPM4, an ultra-efficient large language model engineered for resource-constrained end devices, integrating innovations in model architecture, training data, algorithms, and inference systems. This results in state-of-the-art performance for its size, an 8B model trained with 78% fewer tokens than comparable models, and a 7x decoding acceleration on edge GPUs for long-context tasks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
