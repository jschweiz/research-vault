---
id: 2026-04-06-alphaxiv-paper-skillx-automatically-constructing-skill-knowledg-f4c5cea3
kind: paper
title: SkillX: Automatically Constructing Skill Knowledge Bases for Agents
source_url: https://www.alphaxiv.org/abs/2604.04804
source_name: alphaXiv Papers
authors:
  - Chenxi Wang
  - Zhuoyun Yu
  - Xin Xie
  - Wuguannan Yao
  - Runnan Fang
  - Shuofei Qiao
  - Kexin Cao
  - Guozhou Zheng
  - Xiang Qi
  - Peng Zhang
  - Shumin Deng
published_at: 2026-04-06T16:09:33Z
ingested_at: 2026-04-07T21:43:15.155557Z
content_hash: e04e774b5e9ae63671dec1a2b0acb23bf25ac08548568b0e8cc0de752fd52d34
tags:
  - paper
  - alphaxiv
  - research
  - agentic-frameworks
  - agents
  - computer science
  - cs.ai
  - cs.cl
  - cs.ir
  - cs.lg
  - Computer Science
  - cs.AI
  - cs.CL
  - cs.IR
  - cs.LG
  - cs.MA
  - generative-models
  - online-learning
  - reinforcement-learning
  - representation-learning
  - tool-use
  - transfer-learning
  - github
  - audio
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
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04804
canonical_url: https://www.alphaxiv.org/abs/2604.04804
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:27:04.053905Z
short_summary: SkillX is an automated framework that builds a plug-and-play skill knowledge base for LLM agents using a hierarchical representation of planning, functional, and atomic skills. This framework from Zhejiang University and Ant Digital Technologies improved task success rates by approximately 10% for weaker models and enhanced execution efficiency by reducing execution steps and input tokens across complex benchmarks.
lightweight_enrichment_status: failed
lightweight_enriched_at: null
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: e04e774b5e9ae63671dec1a2b0acb23bf25ac08548568b0e8cc0de752fd52d34
lightweight_enrichment_error: "Attempt to overwrite 'operation_run_id' in LogRecord"
---
# SkillX: Automatically Constructing Skill Knowledge Bases for Agents

## alphaXiv Summary

SkillX is an automated framework that builds a plug-and-play skill knowledge base for LLM agents using a hierarchical representation of planning, functional, and atomic skills. This framework from Zhejiang University and Ant Digital Technologies improved task success rates by approximately 10% for weaker models and enhanced execution efficiency by reducing execution steps and input tokens across complex benchmarks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04804
- Source paper: https://arxiv.org/abs/2604.04804
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04804v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04804v1.png
- GitHub: https://github.com/zjunlp/SkillX
- GitHub stars: 0
- Paper ID: 2604.04804
- Canonical ID: 2604.04804v1
- Paper group ID: 019d65bf-4671-7909-9268-425a0e1087c4
- Version ID: 019d65bf-46b9-7a61-89bb-767b91d8a074
- Version: v1
- Version order: 1
- Published at: 2026-04-06T16:09:33+00:00
- First published at: 2026-04-06T16:09:33+00:00
- Updated at: 2026-04-07T02:22:07.473000+00:00
- License: http://creativecommons.org/licenses/by-nc-sa/4.0/
- Citations: 0

## Authors

- Chenxi Wang
- Zhuoyun Yu
- Xin Xie
- Wuguannan Yao
- Runnan Fang
- Shuofei Qiao
- Kexin Cao
- Guozhou Zheng
- Xiang Qi
- Peng Zhang
- Shumin Deng

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.CL
- cs.IR
- cs.LG
- cs.MA
- generative-models
- online-learning
- reinforcement-learning
- representation-learning
- tool-use
- transfer-learning

## Metrics

- Visits (all): 124
- Visits (last 7 days): 124
- Total votes: 3
- Public total votes: 9
- X likes: 0

## Abstract

Learning from experience is critical for building capable large language model (LLM) agents, yet prevailing self-evolving paradigms remain inefficient: agents learn in isolation, repeatedly rediscover similar behaviors from limited experience, resulting in redundant exploration and poor generalization. To address this problem, we propose SkillX, a fully automated framework for constructing a \textbf{plug-and-play skill knowledge base} that can be reused across agents and environments. SkillX operates through a fully automated pipeline built on three synergistic innovations: \textit{(i) Multi-Level Skills Design}, which distills raw trajectories into three-tiered hierarchy of strategic plans, functional skills, and atomic skills; \textit{(ii) Iterative Skills Refinement}, which automatically revises skills based on execution feedback to continuously improve library quality; and \textit{(iii) Exploratory Skills Expansion}, which proactively generates and validates novel skills to expand coverage beyond seed training data. Using a strong backbone agent (GLM-4.6), we automatically build a reusable skill library and evaluate its transferability on challenging long-horizon, user-interactive benchmarks, including AppWorld, BFCL-v3, and $\tau^2$-Bench. Experiments show that SkillKB consistently improves task success and execution efficiency when plugged into weaker base agents, highlighting the importance of structured, hierarchical experience representations for generalizable agent learning. Our code will be publicly available soon at this https URL.

## Problem

- LLM agents learn inefficiently from isolated experiences, leading to repeated rediscovery of behaviors and poor generalization of learned knowledge, especially in complex, data-scarce environments.
- Existing experience representations lack simultaneous transferability, efficient retrieval, and direct executability, hindering effective reuse across tasks.
- Prior skill-based systems often demand extensive context management and progressive disclosure, which limits their robustness and practical application.

## Method

- SkillX, an automated framework, constructs a plug-and-play skill knowledge base to facilitate the reuse of learned behaviors across different agents and environments.
- It employs a multi-level hierarchical skill design (Planning, Functional, Atomic) for concise, composable, and robust experience representation.
- The framework includes an iterative process of skill extraction, refinement (merging and filtering), and an experience-guided exploratory expansion for continuous improvement and broader coverage.

## Results

- SkillX consistently boosted the performance of various base LLM agents, with weaker models like Qwen3-32B achieving approximately a 10% gain in task success rates.
- The multi-level skill representation proved more effective than other experience representations, leading to superior performance and transferability across different base models.
- The framework improved agent execution efficiency by reducing the number of execution steps and input tokens, and its experience-guided expansion generated more novel skills and performance gains compared to random exploration.

## Takeaways

- A multi-level hierarchical skill design provides a more advantageous and effective experience representation than direct trajectory retrieval or workflows, boosting agent performance.
- An iterative refinement process and experience-guided exploration strategy are crucial for continuously improving skill quality, coverage, and sample efficiency in complex environments.
- Distilling knowledge from a strong backbone agent into a structured skill base can effectively transfer capabilities to weaker inference models, expanding their operational boundaries.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65bf-4671-7909-9268-425a0e1087c4/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65bf-4671-7909-9268-425a0e1087c4/transcript.json

## AI Detection

- State: done
- Prediction: Human
- Headline: Fully Human Written
- Fraction AI: 0
- Fraction AI-assisted: 0
- Fraction human: 1

## Resources

- GitHub repository: https://github.com/zjunlp/SkillX

## Similar Papers

- SkillWeaver: Web Agents can Self-Improve by Discovering and Honing  Skills (2504.07079v1): Carnegie Mellon University and partner institutions develop SkillWeaver, a framework enabling web agents to autonomously discover and synthesize reusable API skills through environmental exploration, achieving 25-38% improvement in success rates on WebArena benchmarks and demonstrating effective skill transfer across different websites and agent capabilities.
- SkillRL: Evolving Agents via Recursive Skill-Augmented Reinforcement Learning (2602.08234v1): Researchers from the University of North Carolina at Chapel Hill and collaborators developed SKILLRL, a framework enabling Large Language Model (LLM) agents to learn and recursively evolve abstract skills from diverse experiences. SKILLRL achieves state-of-the-art performance with a 89.9% success rate on ALFWorld, 72.7% on WebShop, and an average score of 47.1% on search-augmented QA tasks, outperforming larger closed-source models and memory-augmented baselines.
- AgentEvolver: Towards Efficient Self-Evolving Agent System (2511.10395v1): AgentEvolver presents a self-evolving agent system that leverages large language models for autonomous task generation, efficient exploration, and fine-grained credit assignment. The framework demonstrated an average performance improvement of 29.4 percentage points for its 7B model and reduced training steps for convergence by up to 67% on standard benchmarks.
- ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory (2509.25140v2): Researchers from Google Cloud AI Research and the University of Illinois Urbana-Champaign developed ReasoningBank, a memory framework for LLM agents that distills generalizable reasoning strategies from self-judged successful and failed experiences, combined with Memory-aware Test-Time Scaling (MaTTS). This approach improved agent success rates by up to 8.3 percentage points and reduced interaction steps by up to 2.8 across web navigation and software engineering tasks, fostering continuous self-evolution.
- Memento-Skills: Let Agents Design Agents (2603.18743v1): Memento-Skills introduces a system for Large Language Model (LLM) agents to continually learn and improve without updating core model parameters, treating reusable skills as an external, evolving memory. The system achieved a 13.7 percentage-point increase in test accuracy on the GAIA benchmark and more than doubled the baseline performance on the HLE dataset, enabling autonomous agent design and adaptation.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
