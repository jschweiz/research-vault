---
id: page:2026-04-03-alphaxiv-paper-joyai-llm-flash-advancing-mid-scale-llms-with-to-7299ba1c
page_type: source-note
title: JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency
aliases:
  - JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency
source_refs:
  - 2026-04-03-alphaxiv-paper-joyai-llm-flash-advancing-mid-scale-llms-with-to-7299ba1c
backlinks:
  - page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-7bb194d2
  - page:2026-03-30-alphaxiv-paper-meta-harness-end-to-end-optimization-of-model-ha-be1d870e
  - page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
  - page:2026-04-04-alphaxiv-paper-lightthinker-from-reasoning-compression-to-memor-0d96ca8a
  - page:2026-04-06-alphaxiv-paper-muon-dynamics-as-a-spectral-wasserstein-flow-bfacf3b1
  - page:2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
  - page:2026-04-07-anthropic-research-alignment-faking-in-large-language-models-anthro-c2cfd72b
  - topic:artificial-intelligence
  - topic:efficiency
  - topic:efficient-transformers
  - topic:fine-tuning
  - topic:reinforcement-learning
updated_at: 2026-04-08T07:14:52.361956Z
managed: true
---
# JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.03044
- Document kind: paper
- Published at: 2026-04-03T13:52:38+00:00
- Authors: Aichen Cai, Anmeng Zhang, Anyu Li, Bo Zhang, Bohua Cai, Chang Li
- Tags: paper, alphaxiv, research, computer science, cs.ai, cs.cl, efficient-transformers, fine-tuning, inference-optimization, lightweight-models
- Topics: [Fine-Tuning](../topics/fine-tuning.md), [Efficiency](../topics/efficiency.md), [Reinforcement Learning](../topics/reinforcement-learning.md), [Artificial Intelligence](../topics/artificial-intelligence.md), [Computer Science](../topics/computer-science.md), [Efficient Transformers](../topics/efficient-transformers.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency ## alphaXiv Summary JoyAI-LLM Flash introduces an architecture and training methodology for mid-scale language models (sub-50B parameters) that prioritizes token and computational efficiency without compromising performance. The model, leveraging a Mixture-of-Experts design and novel policy optimization, consistently achieves competitive or superior benchmark results with significantly reduced token consumption compared to existin

## Topic Map

- [Fine-Tuning](../topics/fine-tuning.md)
- [Efficiency](../topics/efficiency.md)
- [Reinforcement Learning](../topics/reinforcement-learning.md)
- [Artificial Intelligence](../topics/artificial-intelligence.md)
- [Computer Science](../topics/computer-science.md)
- [Efficient Transformers](../topics/efficient-transformers.md)

## Related Research

- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Artificial Intelligence, Computer Science, Efficiency)
- [Meta-Harness: End-to-End Optimization of Model Harnesses](meta-harness-end-to-end-optimization-of-model-harnesses-1e9809.md) (shared topics: Artificial Intelligence, Computer Science, Efficient Transformers)
- [Meta-Harness: End-to-End Optimization of Model Harnesses](meta-harness-end-to-end-optimization-of-model-harnesses-ebb80b.md) (shared topics: Artificial Intelligence, Computer Science, Efficient Transformers)
- [TriAttention: Efficient Long Reasoning with Trigonometric KV Compression](triattention-efficient-long-reasoning-with-trigonometric-kv-comp-d601e8.md) (shared topics: Computer Science, Efficiency)
- [Muon Dynamics as a Spectral Wasserstein Flow](muon-dynamics-as-a-spectral-wasserstein-flow-55bdcb.md) (shared topics: Artificial Intelligence, Computer Science)
- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Artificial Intelligence, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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

- Existing Large Language Models (LLMs) suffer from poor token efficiency and high co
