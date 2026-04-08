---
id: 2026-04-02-alphaxiv-paper-skill0-in-context-agentic-reinforcement-learning-9e84a0d6
kind: paper
title: SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization
source_url: https://www.alphaxiv.org/abs/2604.02268
source_name: alphaXiv Papers
authors:
  - Zhengxi Lu
  - Zhiyuan Yao
  - Jinyang Wu
  - Chengcheng Han
  - Qi Gu
  - Xunliang Cai
published_at: 2026-04-02T17:03:05Z
ingested_at: 2026-04-07T21:41:39.019232Z
content_hash: 958846b513262026ffbdbe7312d0d9010f72eee25a81f8a48ca5587d42747e87
tags:
  - paper
  - alphaxiv
  - research
  - agentic-frameworks
  - agents
  - computer science
  - cs.lg
  - deep-reinforcement-learning
  - fine-tuning
  - multi-modal-learning
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
external_key: https://www.alphaxiv.org/abs/2604.02268
canonical_url: https://www.alphaxiv.org/abs/2604.02268
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:26:08.802153Z
short_summary: # SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization ## alphaXiv Summary The SKILL0 framework introduces In-Context Reinforcement Learning (ICRL) to enable Large Language Model (LLM) agents to internalize skills into their parameters, thereby achieving autonomous behavior without external skill descriptions at inference time. This approach yielded superior performance, such as an 87.9% success rate on ALFWorld (+9.7% over AgentOCR), while substantially reducing context t
lightweight_enrichment_status: succeeded
lightweight_enriched_at: 2026-04-08T10:09:19.955599Z
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 958846b513262026ffbdbe7312d0d9010f72eee25a81f8a48ca5587d42747e87
lightweight_enrichment_error: null
---
# SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization

## alphaXiv Summary

The SKILL0 framework introduces In-Context Reinforcement Learning (ICRL) to enable Large Language Model (LLM) agents to internalize skills into their parameters, thereby achieving autonomous behavior without external skill descriptions at inference time. This approach yielded superior performance, such as an 87.9% success rate on ALFWorld (+9.7% over AgentOCR), while substantially reducing context token costs by over 5 times compared to skill-augmented methods.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.02268
- Source paper: https://arxiv.org/abs/2604.02268
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.02268v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.02268v1.png
- GitHub: https://github.com/ZJU-REAL/SkillZero
- GitHub stars: 19
- Paper ID: 2604.02268
- Canonical ID: 2604.02268v1
- Paper group ID: 019d511d-d065-788f-bb15-a8562d561925
- Version ID: 019d511d-d09e-7393-8942-1927dfb3aa94
- Version: v1
- Version order: 1
- Published at: 2026-04-02T17:03:05+00:00
- First published at: 2026-04-02T17:03:05+00:00
- Updated at: 2026-04-03T02:13:21.637000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Zhengxi Lu
- Zhiyuan Yao
- Jinyang Wu
- Chengcheng Han
- Qi Gu
- Xunliang Cai
- Weiming Lu
- Jun Xiao
- Yueting Zhuang
- Yongliang Shen

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.LG
- deep-reinforcement-learning
- fine-tuning
- multi-modal-learning
- tool-use
- transfer-learning
- transformers
- zero-shot-learning

## Metrics

- Visits (all): 1635
- Visits (last 7 days): 1635
- Total votes: 40
- Public total votes: 114
- X likes: 0

## Abstract

Agent skills, structured packages of procedural knowledge and executable resources that agents dynamically load at inference time, have become a reliable mechanism for augmenting LLM agents. Yet inference-time skill augmentation is fundamentally limited: retrieval noise introduces irrelevant guidance, injected skill content imposes substantial token overhead, and the model never truly acquires the knowledge it merely follows. We ask whether skills can instead be internalized into model parameters, enabling zero-shot autonomous behavior without any runtime skill retrieval. We introduce SKILL0, an in-context reinforcement learning framework designed for skill internalization. SKILL0 introduces a training-time curriculum that begins with full skill context and progressively withdraws it. Skills are grouped offline by category and rendered with interaction history into a compact visual context, teaching he model tool invocation and multi-turn task completion. A Dynamic Curriculum then evaluates each skill file's on-policy helpfulness, retaining only those from which the current policy still benefits within a linearly decaying budget, until the agent operates in a fully zero-shot setting. Extensive agentic experiments demonstrate that SKILL0 achieves substantial improvements over the standard RL baseline (+9.7\% for ALFWorld and +6.6\% for Search-QA), while maintaining a highly efficient context of fewer than 0.5k tokens per step. Our code is available at this https URL.

## Problem

- Existing inference-time skill augmentation methods suffer from retrieval noise, where irrelevant or misleading guidance can corrupt the agent's contextual understanding.
- Injected skill content creates high token overhead in the context window, leading to increased computational costs and limiting scalability in multi-turn interactions.
- Current LLM agents merely follow explicit skill descriptions, remaining perpetually dependent on external guidance rather than truly internalizing knowledge into their model parameters.

## Method

- SKILL0 employs an In-Context Reinforcement Learning (ICRL) framework where skills are provided as in-context guidance during training, but are entirely removed during inference to promote internalization.
- An Adaptive Curriculum Learning mechanism progressively reduces the active skill budget and dynamically selects beneficial skills based on a 'helpfulness' metric, compelling agents to internalize knowledge over time.
- The system utilizes visual context modeling to map textual interaction history and skills into compact RGB images, significantly reducing token overhead, alongside a composite reward incentivizing both task success and context compression.

## Results

- SKILL0 achieved superior performance, with a 3B model reaching an 87.9% success rate on ALFWorld (+9.7% over AgentOCR) and 40.8% on Search-QA (+6.6%), demonstrating its ability to internalize skills effectively.
- The framework significantly reduced context token costs during inference, consuming over 5 times fewer tokens per step compared to text-based or skill-augmented methods like SkillRL.
- Validation accuracy tracked during training provided empirical evidence of skill internalization, as models evaluated without skill prompts eventually surpassed skill-augmented variants by the end of optimization.

## Takeaways

- Skill internalization is a viable and advantageous alternative to inference-time skill augmentation, allowing LLM agents to transition from context-dependent execution to truly autonomous, memory-based behavior.
- A dynamically decaying skill budget, combined with filtering and ranking skills by their 'helpfulness,' is crucial for successful internalization, preventing agents from over-relying on external prompts.
- Providing skills as transient scaffolding during training, and then gradually withdrawing them, effectively guides the agent to consolidate knowledge within its parameters, leading to superior skill-free inference performance.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d511d-d065-788f-bb15-a8562d561925/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d511d-d065-788f-bb15-a8562d561925/transcript.json
- Transcript lines: 19
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Human
- Headline: Mostly Human Written
- Fraction AI: 0.06914828
- Fraction AI-assisted: 0
- Fraction human: 0.9308517

## Resources

- GitHub repository: https://github.com/ZJU-REAL/SkillZero

## Similar Papers

- SkillRL: Evolving Agents via Recursive Skill-Augmented Reinforcement Learning (2602.08234v1): Researchers from the University of North Carolina at Chapel Hill and collaborators developed SKILLRL, a framework enabling Large Language Model (LLM) agents to learn and recursively evolve abstract skills from diverse experiences. SKILLRL achieves state-of-the-art performance with a 89.9% success rate on ALFWorld, 72.7% on WebShop, and an average score of 47.1% on search-augmented QA tasks, outperforming larger closed-source models and memory-augmented baselines.
- Memento-Skills: Let Agents Design Agents (2603.18743v1): Memento-Skills introduces a system for Large Language Model (LLM) agents to continually learn and improve without updating core model parameters, treating reusable skills as an external, evolving memory. The system achieved a 13.7 percentage-point increase in test accuracy on the GAIA benchmark and more than doubled the baseline performance on the HLE dataset, enabling autonomous agent design and adaptation.
- SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks (2602.12670v3): Researchers introduced SkillsBench, a benchmark to evaluate how effectively "Agent Skills" augment large language model (LLM) agents, measuring performance across diverse tasks and agent-model configurations. The benchmark found that curated Skills improved average agent performance by +16.2 percentage points and can enable smaller LLMs to match the performance of larger models operating without Skills.
- AgentGym-RL: Training LLM Agents for Long-Horizon Decision Making through Multi-Turn Reinforcement Learning (2509.08755v1): An open-source framework, AgentGym-RL, facilitates the training of large language model agents for long-horizon decision-making through multi-turn reinforcement learning and a progressive interaction scaling strategy called ScalingInter-RL. This approach enables a 7B parameter model to achieve an average success rate comparable to or exceeding larger proprietary models across diverse environments, highlighting the impact of RL training on agentic intelligence.
- Remember Me, Refine Me: A Dynamic Procedural Memory Framework for Experience-Driven Agent Evolution (2512.10696v1): ReMe introduces a dynamic procedural memory framework for LLM agents, enabling continuous learning and adaptation through a closed-loop system of experience acquisition, reuse, and refinement. This framework allows smaller language models to achieve performance comparable to or surpassing larger, memory-less models, demonstrating a memory-scaling effect and improving agent robustness.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
