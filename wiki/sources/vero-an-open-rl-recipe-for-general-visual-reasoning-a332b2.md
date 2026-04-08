---
id: page:2026-04-06-alphaxiv-paper-vero-an-open-rl-recipe-for-general-visual-reason-80650390
page_type: source-note
title: Vero: An Open RL Recipe for General Visual Reasoning
aliases:
  - Vero: An Open RL Recipe for General Visual Reasoning
source_refs:
  - 2026-04-06-alphaxiv-paper-vero-an-open-rl-recipe-for-general-visual-reason-80650390
backlinks:
  - page:2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
  - page:2026-04-02-alphaxiv-paper-skill0-in-context-agentic-reinforcement-learning-9e84a0d6
  - page:2026-04-03-alphaxiv-paper-agentic-mme-what-agentic-capability-really-bring-688666ad
  - page:2026-04-03-alphaxiv-paper-self-distilled-rlvr-597ff1e6
  - page:2026-04-06-alphaxiv-paper-openworldlib-a-unified-codebase-and-definition-o-349dac12
  - page:2026-04-06-alphaxiv-paper-triattention-efficient-long-reasoning-with-trigo-0b3d9715
  - topic:agents
  - topic:computer-vision
  - topic:data-curation
  - topic:evaluations
  - topic:fine-tuning
  - topic:reasoning
updated_at: 2026-04-08T07:14:52.346153Z
managed: true
---
# Vero: An Open RL Recipe for General Visual Reasoning

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04917
- Document kind: paper
- Published at: 2026-04-06T17:56:25+00:00
- Authors: Gabriel Sarch, Linrong Cai, Qunzhong Wang, Haoyang Wu, Danqi Chen, Zhuang Liu
- Tags: paper, alphaxiv, research, agents, computer science, cs.ai, cs.cl, cs.cv, data-curation, fine-tuning
- Topics: [Agents](../topics/agents.md), [Computer Vision](../topics/computer-vision.md), [Fine-Tuning](../topics/fine-tuning.md), [Data Curation](../topics/data-curation.md), [Evaluations](../topics/evaluations.md), [Reasoning](../topics/reasoning.md)
- Trend score: 54.82
- Novelty score: 6.80

## Summary

# Vero: An Open RL Recipe for General Visual Reasoning ## alphaXiv Summary Princeton University researchers introduce Vero, an open reinforcement learning (RL) framework for training vision-language models (VLMs) that perform general visual reasoning across diverse tasks. Vero models, trained on a 600K diverse dataset and with task-routed rewards, achieved state-of-the-art average scores (e.g., 65.9-66.0) among 8B-parameter open-weight VLMs on a 30-benchmark evaluation suite, consistently outper

## Topic Map

- [Agents](../topics/agents.md)
- [Computer Vision](../topics/computer-vision.md)
- [Fine-Tuning](../topics/fine-tuning.md)
- [Data Curation](../topics/data-curation.md)
- [Evaluations](../topics/evaluations.md)
- [Reasoning](../topics/reasoning.md)

## Related Research

- [TriAttention: Efficient Long Reasoning with Trigonometric KV Compression](triattention-efficient-long-reasoning-with-trigonometric-kv-comp-d601e8.md) (shared topics: Computer Vision, Reasoning)
- [OpenWorldLib: A Unified Codebase and Definition of Advanced World Models](openworldlib-a-unified-codebase-and-definition-of-advanced-world-187d2a.md) (shared topics: Agents, Computer Vision)
- [Self-Distilled RLVR](self-distilled-rlvr-1944ab.md) (shared topics: Agents, Fine-Tuning)
- [Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?](agentic-mme-what-agentic-capability-really-brings-to-multimodal--78e741.md) (shared topics: Agents, Evaluations)
- [SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization](skill0-in-context-agentic-reinforcement-learning-for-skill-inter-b7a513.md) (shared topics: Agents, Fine-Tuning)
- [[Deprecated] Pixtral Large | Mistral AI](deprecated-pixtral-large-mistral-ai-0d8433.md) (shared topics: Computer Vision, Evaluations)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
- Curated Vero-600K, a 600,000-sample training dataset derived from 59 distinct datasets,
