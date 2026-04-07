---
id: 2026-04-06-alphaxiv-paper-vero-an-open-rl-recipe-for-general-visual-reason-80650390
kind: paper
title: Vero: An Open RL Recipe for General Visual Reasoning
source_url: https://www.alphaxiv.org/abs/2604.04917
source_name: alphaXiv Papers
authors:
  - Gabriel Sarch
  - Linrong Cai
  - Qunzhong Wang
  - Haoyang Wu
  - Danqi Chen
  - Zhuang Liu
published_at: 2026-04-06T17:56:25Z
ingested_at: 2026-04-07T21:42:30.794012Z
content_hash: 6ccc8b65b78bb38992ed89ecc9edb658b6470c4e184274b76df4cb0b03e725fb
tags:
  - paper
  - alphaxiv
  - research
  - agents
  - computer science
  - cs.ai
  - cs.cl
  - cs.cv
  - data-curation
  - fine-tuning
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
external_key: https://www.alphaxiv.org/abs/2604.04917
canonical_url: https://www.alphaxiv.org/abs/2604.04917
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-07T21:42:30.794017Z
short_summary: # Vero: An Open RL Recipe for General Visual Reasoning ## alphaXiv Summary Princeton University researchers introduce Vero, an open reinforcement learning (RL) framework for training vision-language models (VLMs) that perform general visual reasoning across diverse tasks. Vero models, trained on a 600K diverse dataset and with task-routed rewards, achieved state-of-the-art average scores (e.g., 65.9-66.0) among 8B-parameter open-weight VLMs on a 30-benchmark evaluation suite, consistently outper
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-07T21:48:13.434935Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 6ccc8b65b78bb38992ed89ecc9edb658b6470c4e184274b76df4cb0b03e725fb
lightweight_enrichment_error: null
---
# Vero: An Open RL Recipe for General Visual Reasoning

## alphaXiv Summary

Princeton University researchers introduce Vero, an open reinforcement learning (RL) framework for training vision-language models (VLMs) that perform general visual reasoning across diverse tasks. Vero models, trained on a 600K diverse dataset and with task-routed rewards, achieved state-of-the-art average scores (e.g., 65.9-66.0) among 8B-parameter open-weight VLMs on a 30-benchmark evaluation suite, consistently outperforming proprietary RL recipes and demonstrating broad improvements across six visual reasoning categories.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04917
- Source paper: https://arxiv.org/abs/2604.04917
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04917v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04917v1.png
- GitHub: https://github.com/zlab-princeton/vero
- GitHub stars: 0
- Paper ID: 2604.04917
- Canonical ID: 2604.04917v1
- Paper group ID: 019d65cf-fe30-789b-80f1-86b12f36f98a
- Version ID: 019d65cf-fe5f-7f9c-b461-e85e5f739c88
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:56:25+00:00
- First published at: 2026-04-06T17:56:25+00:00
- Updated at: 2026-04-07T02:40:23.088000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Gabriel Sarch
- Linrong Cai
- Qunzhong Wang
- Haoyang Wu
- Danqi Chen
- Zhuang Liu

## Topics

- agents
- Computer Science
- cs.AI
- cs.CL
- cs.CV
- data-curation
- fine-tuning
- generative-models
- multi-modal-learning
- reinforcement-learning
- transfer-learning
- vision-language-models
- visual-reasoning

## Metrics

- Visits (all): 109
- Visits (last 7 days): 109
- Total votes: 4
- Public total votes: 11
- X likes: 0

## Abstract

What does it take to build a visual reasoner that works across charts, science, spatial understanding, and open-ended tasks? The strongest vision-language models (VLMs) show such broad visual reasoning is within reach, but the recipe behind them remains unclear, locked behind proprietary reinforcement learning (RL) pipelines with non-public data. We introduce Vero, a family of fully open VLMs that matches or exceeds existing open-weight models across diverse visual reasoning tasks. We scale RL data and rewards across six broad task categories, constructing Vero-600K, a 600K-sample dataset from 59 datasets, and designing task-routed rewards that handle heterogeneous answer formats. Vero achieves state-of-the-art performance, improving over four base models by 3.7-5.5 points on average across VeroEval, our suite of 30 challenging benchmarks. Starting from Qwen3-VL-8B-Instruct, Vero outperforms Qwen3-VL-8B-Thinking on 23 of 30 benchmarks without additional proprietary thinking data. When trained from the same base model, Vero-600K exceeds existing RL datasets across task categories. Systematic ablations reveal that different task categories elicit qualitatively distinct reasoning patterns that transfer poorly in isolation, suggesting that broad data coverage is the primary driver of strong RL scaling. All data, code, and models are released.

## Problem

- Most advanced vision-language models (VLMs) rely on proprietary RL pipelines with undisclosed data and reward designs, limiting transparency, analysis, and reproducibility for the research community.
- Existing open-source RL efforts for VLMs typically focus on narrow domains (e.g., visual mathematics) and struggle to generalize effectively to a broader range of visual reasoning tasks.
- Applying RL across diverse and heterogeneous visual reasoning tasks introduces challenges such as interference, weak skill transfer, and optimization imbalances.

## Method

- Developed Vero, a fully open, single-stage reinforcement learning (RL) recipe including code, data (Vero-600K), and models, designed for general visual reasoning across a broad spectrum of tasks.
- Curated Vero-600K, a 600,000-sample training dataset derived from 59 distinct datasets, categorized into six broad visual reasoning categories with careful filtering and uniform mixing strategies.
- Implemented a multi-faceted reward system utilizing Group Relative Policy Optimization (GRPO) with GSPO advancements, combining task-routed accuracy rewards (ten distinct functions), format penalties, and an overlong penalty, including an LLM-as-judge for open-ended responses.

## Results

- Vero models (Vero-Qwen3T-8B, Vero-Qwen3I-8B) achieved state-of-the-art overall average scores (65.9-66.0) among 8B-parameter open-weight VLMs on the 30-benchmark VeroEval suite, surpassing base models on 23-24 out of 30 benchmarks.
- Vero training consistently improved performance across four different base models, with average gains ranging from +3.7 to +5.5 points, and Vero-MiMo-7B outperformed a proprietary MiMo-VL-7B-RL on 3 of 6 category averages.
- Ablation studies confirmed the superiority of multi-route reward design (+5.4 points overall, +36.3 on Captioning) over unified baselines, and demonstrated RL's more substantial and uniform gains (+4.8 points) compared to SFT (+0.4 points) across task categories.

## Takeaways

- A fully open and transparent RL recipe, leveraging diverse data and task-specific rewards, can achieve performance competitive with or superior to proprietary RL pipelines for general visual reasoning.
- Broad data diversity and balanced multi-task mixing are crucial for positive cross-task transfer and preventing catastrophic performance degradation in multi-task reinforcement learning for VLMs, effectively addressing interference challenges.
- Carefully designed, task-routed reward functions and strategic inclusion of open-ended tasks are essential for both achieving high accuracy on diverse benchmarks and maintaining/improving general visual chat quality, while mitigating reward hacking.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65cf-fe30-789b-80f1-86b12f36f98a/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65cf-fe30-789b-80f1-86b12f36f98a/transcript.json

## Resources

- GitHub repository: https://github.com/zlab-princeton/vero

## Similar Papers

- VLM-R1: A Stable and Generalizable R1-style Large Vision-Language Model (2504.07615v2): VLM-R1 introduces an open-source framework that applies rule-based reinforcement learning to Vision-Language Models (VLMs), enhancing their visual reasoning and generalization abilities on tasks like Referring Expression Comprehension and Open-Vocabulary Object Detection. The approach demonstrates improved out-of-domain performance compared to supervised fine-tuning and showcases emergent reasoning behaviors.
- Video-R1: Reinforcing Video Reasoning in MLLMs (2503.21776v4): Researchers introduced Video-R1, the first framework to apply a rule-based reinforcement learning paradigm for enhancing temporal reasoning capabilities in Multimodal Large Language Models (MLLMs) for video. Video-R1, leveraging a new temporal-aware RL algorithm and dedicated video reasoning datasets, consistently outperforms previous state-of-the-art models, achieving 37.1% accuracy on VSI-Bench, surpassing GPT-4o's 34.0%.
- SFT or RL? An Early Investigation into Training R1-Like Reasoning Large  Vision-Language Models (2504.11468v1): A comparative study examines the effectiveness of Supervised Fine-Tuning (SFT) versus Reinforcement Learning (RL) for training reasoning-capable vision-language models, revealing that SFT can impede subsequent RL performance by inducing superficial reasoning patterns, while direct RL training through Group Relative Policy Optimization achieves state-of-the-art performance on multimodal reasoning benchmarks.
- Molmo and PixMo: Open Weights and Open Data for State-of-the-Art Vision-Language Models (2409.17146v2): This work introduces Molmo, a family of state-of-the-art open-weight Vision-Language Models (VLMs), and PixMo, a comprehensive suite of VLM-independent training datasets. Molmo-72B achieves leading performance on academic benchmarks and human preference evaluations, demonstrating that high-performing VLMs can be built entirely from truly open data and models without relying on proprietary systems for data generation.
- OpenVLThinker: Complex Vision-Language Reasoning via Iterative SFT-RL Cycles (2503.17352v3): Researchers at UCLA developed OpenVLThinker, an open-source large vision-language model, leveraging an iterative supervised fine-tuning and reinforcement learning cycle to achieve complex, multi-step reasoning. This model demonstrates competitive performance with proprietary LVLMs and surpasses other open-source models on challenging benchmarks, showing data efficiency with 10x less data.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
