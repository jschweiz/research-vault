---
id: 2026-04-02-alphaxiv-paper-evoskills-self-evolving-agent-skills-via-co-evol-34083480
kind: paper
title: 'EvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification'
source_url: https://www.alphaxiv.org/abs/2604.01687
source_name: alphaXiv Papers
authors:
- Hanrong Zhang
- Shicheng Fan
- Henry Peng Zou
- Yankai Chen
- Zhenting Wang
- Jiayu Zhou
- Chengze Li
- Wei-Chieh Huang
- Yifei Yao
- Kening Zheng
- Xue Liu
- Xiaoxiao Li
- Philip S. Yu
published_at: '2026-04-02T06:43:20Z'
ingested_at: '2026-04-09T09:56:43.038282Z'
content_hash: 765fa6495018790d076b6ef0f787347935bd2fcae3f156b30ce5756a25e57339
identity_hash: 2553ff2a5dc82ec9eebbd4b17d0f4042b738e4c9b481f910f950b0615456dac9
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- evolutionary-algorithms
- generative-models
- meta-learning
- multi-agent-learning
- tool-use
- transformers
- audio
- transcript
- summary
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
external_key: https://www.alphaxiv.org/abs/2604.01687
canonical_url: https://www.alphaxiv.org/abs/2604.01687
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:56:43.038292Z'
short_summary: EvoSkills enables large language model agents to autonomously generate and iteratively refine complex, multi-file skill packages through a co-evolutionary verification framework. This approach yields skills that surpass human-authored versions and exhibit strong transferability across different LLM architectures, effectively bridging the cognitive gap between human-designed workflows and agent execution.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# EvoSkills: Self-Evolving Agent Skills via Co-Evolutionary Verification

## alphaXiv Summary

EvoSkills enables large language model agents to autonomously generate and iteratively refine complex, multi-file skill packages through a co-evolutionary verification framework. This approach yields skills that surpass human-authored versions and exhibit strong transferability across different LLM architectures, effectively bridging the cognitive gap between human-designed workflows and agent execution.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.01687
- Source paper: https://arxiv.org/abs/2604.01687
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.01687v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.01687v1.png
- Paper ID: 2604.01687
- Canonical ID: 2604.01687v1
- Paper group ID: 019d5133-23a8-7777-89af-96ec890f30cb
- Version ID: 019d5133-23fb-7e56-9026-bf5a2b6a5923
- Version: v1
- Version order: 1
- Published at: 2026-04-02T06:43:20+00:00
- First published at: 2026-04-02T06:43:20+00:00
- Updated at: 2026-04-03T02:36:39.208000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Hanrong Zhang
- Shicheng Fan
- Henry Peng Zou
- Yankai Chen
- Zhenting Wang
- Jiayu Zhou
- Chengze Li
- Wei-Chieh Huang
- Yifei Yao
- Kening Zheng
- Xue Liu
- Xiaoxiao Li
- Philip S. Yu

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- evolutionary-algorithms
- generative-models
- meta-learning
- multi-agent-learning
- tool-use
- transformers

## Metrics

- Visits (all): 395
- Visits (last 7 days): 395
- Total votes: 8
- Public total votes: 39
- X likes: 0

## Abstract

Anthropic proposes the concept of skills for LLM agents to tackle multi-step professional tasks that simple tool invocations cannot address. A tool is a single, self-contained function, whereas a skill is a structured bundle of interdependent multi-file artifacts. Currently, skill generation is not only label-intensive due to manual authoring, but also may suffer from human--machine cognitive misalignment, which can lead to degraded agent performance, as evidenced by evaluations on SkillsBench. Therefore, we aim to enable agents to autonomously generate skills. However, existing self-evolving methods designed for tools cannot be directly applied to skills due to their increased complexity. To address these issues, we propose EvoSkills, a self-evolving skills framework that enables agents to autonomously construct complex, multi-file skill packages. Specifically, EvoSkills couples a Skill Generator that iteratively refines skills with a Surrogate Verifier that co-evolves to provide informative and actionable feedback without access to ground-truth test content. On SkillsBench, EvoSkills achieves the highest pass rate among five baselines on both Claude Code and Codex, and also exhibits strong generalization capabilities to six additional LLMs.

## Problem

- Manual human authoring of 'agent skills' is labor-intensive, difficult to scale, and often leads to inconsistent performance due to 'human-machine cognitive misalignment'.
- Existing self-evolving methods for LLM agents focus primarily on atomic tools or function APIs, lacking the capability to generate and refine complex, structured, multi-file skill packages.
- Many self-evolution approaches require ground-truth supervision for failure diagnosis, limiting their applicability in real-world scenarios where such detailed feedback is unavailable.

## Method

- The EvoSkills framework introduces a co-evolutionary approach, employing a Skill Generator and an information-isolated Surrogate Verifier that iteratively refine skills and their verification mechanisms.
- The Skill Generator autonomously generates and refines multi-file skill bundles by processing task instructions and structured failure diagnostics from the verifier.
- The Surrogate Verifier independently generates and refines a suite of deterministic test assertions, providing dense, actionable feedback and escalating its tests when ground-truth failures occur despite surrogate success.

## Results

- EvoSkills achieved a 71.1% pass rate on SkillsBench with Claude Opus 4.6, outperforming the no-skill baseline (30.6%) by +40.5 percentage points and human-curated skills (53.5%) by +17.6 percentage points.
- Ablation studies confirmed that removing the surrogate verifier led to a substantial drop in pass rate by -30.0 percentage points, highlighting its critical role in targeted repairs.
- Skills evolved by Claude Opus 4.6 showed strong transferability across six other LLM models, improving their respective no-skill baselines by +36 to +44 percentage points.
- Self-evolved skills outperformed human-curated skills in 9 out of 11 professional domains, including significant gains in Finance (+56.9 pp) and Cybersecurity (+23.2 pp), and corrected degraded performance in Natural Science.

## Takeaways

- LLM agents can autonomously generate more effective and reliable skills than human experts, as these self-evolved skills better align with the agent's intrinsic reasoning and execution patterns.
- A co-evolutionary framework, especially with an information-isolated surrogate verifier, provides crucial, actionable feedback for skill refinement without requiring direct ground-truth supervision.
- Self-evolved skills demonstrate strong cross-model transferability, suggesting they encode reusable task structures rather than model-specific artifacts, making them broadly portable.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d5133-23a8-7777-89af-96ec890f30cb/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d5133-23a8-7777-89af-96ec890f30cb/transcript.json
- Transcript lines: 24
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- SkillWeaver: Web Agents can Self-Improve by Discovering and Honing  Skills (2504.07079v1): Carnegie Mellon University and partner institutions develop SkillWeaver, a framework enabling web agents to autonomously discover and synthesize reusable API skills through environmental exploration, achieving 25-38% improvement in success rates on WebArena benchmarks and demonstrating effective skill transfer across different websites and agent capabilities.
- SkillRL: Evolving Agents via Recursive Skill-Augmented Reinforcement Learning (2602.08234v1): Researchers from the University of North Carolina at Chapel Hill and collaborators developed SKILLRL, a framework enabling Large Language Model (LLM) agents to learn and recursively evolve abstract skills from diverse experiences. SKILLRL achieves state-of-the-art performance with a 89.9% success rate on ALFWorld, 72.7% on WebShop, and an average score of 47.1% on search-augmented QA tasks, outperforming larger closed-source models and memory-augmented baselines.
- AgentEvolver: Towards Efficient Self-Evolving Agent System (2511.10395v1): AgentEvolver presents a self-evolving agent system that leverages large language models for autonomous task generation, efficient exploration, and fine-grained credit assignment. The framework demonstrated an average performance improvement of 29.4 percentage points for its 7B model and reduced training steps for convergence by up to 67% on standard benchmarks.
- Agent-as-a-Judge: Evaluate Agents with Agents (2410.10934v2): The Agent-as-a-Judge framework and the DevAI benchmark provide a scalable and reliable method for evaluating AI agents, demonstrating a superior alignment with human judgment compared to LLM-as-a-Judge. This approach achieves substantial cost and time reductions in evaluating complex, real-world AI application development tasks.
- MemSkill: Learning and Evolving Memory Skills for Self-Evolving Agents (2602.02474v1): MemSkill introduces an approach for Large Language Model (LLM) agents where memory operations are learned and evolve over time, moving beyond static, human-engineered mechanisms. This system, developed by Nanyang Technological University and collaborators, achieves superior performance in conversational and embodied tasks by continually refining a dynamic skill bank and a skill-selection policy.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
