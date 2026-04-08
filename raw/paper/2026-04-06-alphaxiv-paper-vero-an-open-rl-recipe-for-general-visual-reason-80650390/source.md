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
published_at: 2026-04-07T15:20:05Z
ingested_at: 2026-04-07T21:42:30.794012Z
content_hash: 79a89c3dbdda88577df5c729b35c446c7f9d951511e0ea18422f794428c51fa9
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
  - Computer Science
  - cs.AI
  - cs.CL
  - cs.CV
  - generative-models
  - multi-modal-learning
  - reinforcement-learning
  - transfer-learning
  - vision-language-models
  - visual-reasoning
  - github
  - audio
  - transcript
  - summary
status: active
asset_paths:
  - alphaxiv-ai-detection.json
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
external_key: https://www.alphaxiv.org/abs/2604.04917
canonical_url: https://www.alphaxiv.org/abs/2604.04917
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:26:17.333701Z
short_summary: Princeton University researchers introduce Vero, a fully open reinforcement learning recipe and associated VLM family for general visual reasoning, demonstrating state-of-the-art performance among 8B-parameter models on a new 30-benchmark suite. The method consistently improved various base models' performance by 3.6 to 5.3 points across six diverse visual reasoning categories using a curated 600,000-sample dataset and task-routed reward functions.
lightweight_enrichment_status: failed
lightweight_enriched_at: null
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 79a89c3dbdda88577df5c729b35c446c7f9d951511e0ea18422f794428c51fa9
lightweight_enrichment_error: "Attempt to overwrite 'operation_run_id' in LogRecord"
---
# Vero: An Open RL Recipe for General Visual Reasoning

## alphaXiv Summary

Princeton University researchers introduce Vero, a fully open reinforcement learning recipe and associated VLM family for general visual reasoning, demonstrating state-of-the-art performance among 8B-parameter models on a new 30-benchmark suite. The method consistently improved various base models' performance by 3.6 to 5.3 points across six diverse visual reasoning categories using a curated 600,000-sample dataset and task-routed reward functions.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04917
- Source paper: https://arxiv.org/abs/2604.04917
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04917v2.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04917v2.png
- GitHub: https://github.com/zlab-princeton/vero
- GitHub stars: 0
- Paper ID: 2604.04917
- Canonical ID: 2604.04917v2
- Paper group ID: 019d65cf-fe30-789b-80f1-86b12f36f98a
- Version ID: 019d6ab8-7083-7b01-ba7d-9de854132e72
- Version: v2
- Version order: 2
- Published at: 2026-04-07T15:20:05+00:00
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

- Visits (all): 247
- Visits (last 7 days): 247
- Total votes: 6
- Public total votes: 13
- X likes: 0

## Abstract

What does it take to build a visual reasoner that works across charts, science, spatial understanding, and open-ended tasks? The strongest vision-language models (VLMs) show such broad visual reasoning is within reach, but the recipe behind them remains unclear, locked behind proprietary reinforcement learning (RL) pipelines with non-public data. We introduce Vero, a family of fully open VLMs that matches or exceeds existing open-weight models across diverse visual reasoning tasks. We scale RL data and rewards across six broad task categories, constructing Vero-600K, a 600K-sample dataset from 59 datasets, and designing task-routed rewards that handle heterogeneous answer formats. Vero achieves state-of-the-art performance, improving over four base models by 3.6-5.3 points on average across VeroEval, our suite of 30 challenging benchmarks. Starting from Qwen3-VL-8B-Instruct, Vero outperforms Qwen3-VL-8B-Thinking on 23 of 30 benchmarks without additional proprietary thinking data. When trained from the same base model, Vero-600K exceeds existing RL datasets across task categories. Systematic ablations reveal that different task categories elicit qualitatively distinct reasoning patterns that transfer poorly in isolation, suggesting that broad data coverage is the primary driver of strong RL scaling. All data, code, and models are released.

## Problem

- Lack of transparency in the development of state-of-the-art vision-language models (VLMs) that leverage proprietary RL pipelines, non-public data, and undisclosed reward designs.
- Challenges in applying reinforcement learning (RL) across a diverse range of visual reasoning tasks, including task interference, weak skill transfer, and optimization imbalances.
- Existing open RL efforts for VLMs often specialize in narrow task subsets, limiting their generalizability across broad visual understanding tasks.

## Method

- Developed Vero, a fully open-weight VLM family and a transparent, single-stage RL training recipe based on Group Relative Policy Optimization (GRPO).
- Curated Vero-600K, a large-scale dataset of 600,000 samples from 59 datasets, covering six broad visual reasoning task categories (STEM, Spatial & Action, Knowledge & Recognition, Chart & OCR, Grounding, Counting & Search, Captioning & Instruction Following).
- Designed a multi-route reward system with ten task-specific functions (e.g., string match, numeric tolerance, bounding box IoU, LLM-as-judge) to handle heterogeneous answer formats and evaluation criteria.

## Results

- Vero-Qwen3I-8B and Vero-Qwen3T-8B achieved average scores of 66.0 and 65.9 on the VeroEval suite, positioning them as top performers among evaluated 8B-parameter VLMs.
- The Vero training recipe consistently improved performance across four different base models, showing average gains of 3.6 to 5.3 points over 30 benchmarks, and outperformed proprietary RL-trained MiMo-VL-7B-RL on 3 out of 6 category averages.
- Demonstrated substantial performance improvements across all six task categories, with notable gains on benchmarks like ChartQA Pro (+15.9), MMMU-Pro Vision (+15.1), and MMERealWorld (+10.7).

## Takeaways

- A uniform mixture weighting across diverse task categories in the training data is crucial for achieving broad general visual reasoning capabilities and preventing negative cross-task transfer.
- Expressive, task-routed reward functions are necessary for effective reinforcement learning across heterogeneous answer formats in multi-domain visual reasoning tasks.
- Different visual task categories elicit distinct cognitive behavioral profiles and skill repertoires within VLMs, highlighting the multi-faceted nature of visual reasoning.

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
- Transcript lines: 22
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Mixed
- Headline: Mostly Human, AI Detected
- Fraction AI: 0.23242715
- Fraction AI-assisted: 0
- Fraction human: 0.7675728

## Resources

- GitHub repository: https://github.com/zlab-princeton/vero

## Similar Papers

- VLM-R1: A Stable and Generalizable R1-style Large Vision-Language Model (2504.07615v2): VLM-R1 introduces an open-source framework that applies rule-based reinforcement learning to Vision-Language Models (VLMs), enhancing their visual reasoning and generalization abilities on tasks like Referring Expression Comprehension and Open-Vocabulary Object Detection. The approach demonstrates improved out-of-domain performance compared to supervised fine-tuning and showcases emergent reasoning behaviors.
- Video-R1: Reinforcing Video Reasoning in MLLMs (2503.21776v4): Researchers introduced Video-R1, the first framework to apply a rule-based reinforcement learning paradigm for enhancing temporal reasoning capabilities in Multimodal Large Language Models (MLLMs) for video. Video-R1, leveraging a new temporal-aware RL algorithm and dedicated video reasoning datasets, consistently outperforms previous state-of-the-art models, achieving 37.1% accuracy on VSI-Bench, surpassing GPT-4o's 34.0%.
- SFT or RL? An Early Investigation into Training R1-Like Reasoning Large  Vision-Language Models (2504.11468v1): A comparative study examines the effectiveness of Supervised Fine-Tuning (SFT) versus Reinforcement Learning (RL) for training reasoning-capable vision-language models, revealing that SFT can impede subsequent RL performance by inducing superficial reasoning patterns, while direct RL training through Group Relative Policy Optimization achieves state-of-the-art performance on multimodal reasoning benchmarks.
- Molmo and PixMo: Open Weights and Open Data for State-of-the-Art Vision-Language Models (2409.17146v2): This work introduces Molmo, a family of state-of-the-art open-weight Vision-Language Models (VLMs), and PixMo, a comprehensive suite of VLM-independent training datasets. Molmo-72B achieves leading performance on academic benchmarks and human preference evaluations, demonstrating that high-performing VLMs can be built entirely from truly open data and models without relying on proprietary systems for data generation.
- OpenVLThinker: Complex Vision-Language Reasoning via Iterative SFT-RL Cycles (2503.17352v3): Researchers at UCLA developed OpenVLThinker, an open-source large vision-language model, leveraging an iterative supervised fine-tuning and reinforcement learning cycle to achieve complex, multi-step reasoning. This model demonstrates competitive performance with proprietary LVLMs and surpasses other open-source models on challenging benchmarks, showing data efficiency with 10x less data.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
