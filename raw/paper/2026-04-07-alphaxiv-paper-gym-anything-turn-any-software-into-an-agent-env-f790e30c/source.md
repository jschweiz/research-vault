---
id: 2026-04-07-alphaxiv-paper-gym-anything-turn-any-software-into-an-agent-env-f790e30c
kind: paper
title: 'Gym-Anything: Turn any Software into an Agent Environment'
source_url: https://www.alphaxiv.org/abs/2604.06126
source_name: alphaXiv Papers
authors:
- Pranjal Aggarwal
- Graham Neubig
- Sean Welleck
published_at: '2026-04-07T17:38:15Z'
ingested_at: '2026-04-09T08:12:24.759665Z'
content_hash: 1ac4a0c8d142eab3a57517674ca2f9ff31e87656706ba888a69666ae12460c0c
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.LG
- data-curation
- deep-reinforcement-learning
- multi-agent-learning
- reasoning-verification
- tool-use
- vision-language-models
- github
- audio
- summary
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
external_key: https://www.alphaxiv.org/abs/2604.06126
canonical_url: https://www.alphaxiv.org/abs/2604.06126
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:12:24.759673Z'
short_summary: Carnegie Mellon University researchers introduced Gym-Anything, a framework that automates the creation of interactive software environments and over 10,000 long-horizon tasks for computer-use agents. This system enables the scalable development of benchmarks like CUA-World, which spans 200 economically relevant software applications and supports evaluation across diverse occupational domains.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Gym-Anything: Turn any Software into an Agent Environment

## alphaXiv Summary

Carnegie Mellon University researchers introduced Gym-Anything, a framework that automates the creation of interactive software environments and over 10,000 long-horizon tasks for computer-use agents. This system enables the scalable development of benchmarks like CUA-World, which spans 200 economically relevant software applications and supports evaluation across diverse occupational domains.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06126
- Source paper: https://arxiv.org/abs/2604.06126
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06126v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06126v1.png
- GitHub: https://github.com/cmu-l3/gym-anything
- GitHub stars: 2
- Paper ID: 2604.06126
- Canonical ID: 2604.06126v1
- Paper group ID: 019d6b51-c355-7a97-bf19-abce43625816
- Version ID: 019d6b51-c377-7c58-878c-4252cbde3756
- Version: v1
- Version order: 1
- Published at: 2026-04-07T17:38:15+00:00
- First published at: 2026-04-07T17:38:15+00:00
- Updated at: 2026-04-08T04:20:13.781000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Pranjal Aggarwal
- Graham Neubig
- Sean Welleck

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- cs.LG
- data-curation
- deep-reinforcement-learning
- multi-agent-learning
- reasoning-verification
- tool-use
- vision-language-models

## Metrics

- Visits (all): 118
- Visits (last 7 days): 118
- Total votes: 5
- Public total votes: 8
- X likes: 0

## Abstract

Computer-use agents hold the promise of assisting in a wide range of digital economic activities. However, current research has largely focused on short-horizon tasks over a limited set of software with limited economic value, such as basic e-commerce and OS-configuration tasks. A key reason is that creating environments for complex software requires significant time and human effort, and therefore does not scale. To address this, we introduce Gym-Anything, a framework for converting any software into an interactive computer-use environment. We frame environment creation itself as a multi-agent task: a coding agent writes setup scripts, downloads real-world data, and configures the software, while producing evidence of correct setup. An independent audit agent then verifies evidence for the environment setup against a quality checklist. Using a taxonomy of economically valuable occupations grounded in U.S. GDP data, we apply this pipeline to 200 software applications with broad occupational coverage. The result is CUA-World, a collection of over 10K long-horizon tasks spanning domains from medical science and astronomy to engineering and enterprise systems, each configured with realistic data along with train and test splits. CUA-World also includes CUA-World-Long, a challenging long-horizon benchmark with tasks often requiring over 500 steps, far exceeding existing benchmarks. Distilling successful trajectories from the training split into a 2B vision-language model outperforms models 2$\times$ its size. We also apply the same auditing principle at test time: a separate VLM reviews completed trajectories and provides feedback on what remains, improving Gemini-3-Flash on CUA-World-Long from 11.5% to 14.0%. We release all code, infrastructure, and benchmark data to facilitate future research in realistic computer-use agents.

## Problem

- Computer-use agent (CUA) research focused on short-horizon tasks within a limited selection of software, failing to reflect complex, real-world professional workflows.
- Prohibitive cost and time investment were required for manual creation of realistic, interactive environments and diverse tasks for complex software applications.
- Existing benchmarks led to unfaithful agent evaluation and provided limited training signals for long-horizon, multi-step tasks in heterogeneous environments.

## Method

- Developed Gym-Anything, a framework standardizing environment creation with setup scripts and a declarative configuration, handling container orchestration and providing a Gymnasium-style API.
- Implemented a multi-agent creation-audit loop, where a Creation Agent builds environments and an adversarial Audit Agent verifies setup, significantly automating the process.
- Employed a propose-and-amplify strategy for task generation, creating seed tasks with an expensive agent and amplifying them with a cheaper model, followed by VLM-based filtering and a robust checklist verifier with integrity checks.

## Results

- Created CUA-World, a benchmark comprising over 10,000 long-horizon tasks across 200 economically relevant software applications, covering all 22 major U.S. occupation groups.
- Frontier models achieved moderate pass rates (e.g., Gemini 3 Flash: 22.6% on CUA-World-Test, 11.5% on CUA-World-Long with extended steps), indicating substantial room for improvement in handling complex tasks.
- Distilling successful trajectories from CUA-World-Train into a 2B vision-language model boosted its pass rate from 1.6% to 4.4%, demonstrating the utility of the dataset for agent supervision; Test-Time Auditing further improved Gemini 3 Flash's pass rate on CUA-World-Long from 11.5% to 14.0%.

## Takeaways

- Automating interactive environment creation via a multi-agent pipeline, enhanced by adversarial auditing, is key to scaling computer-use agent research beyond existing limitations.
- Grounding software and task selection in economic value (GDP attribution) ensures the relevance and impact of benchmarks for real-world professional automation.
- Granular, VLM-based task verification, leveraging privileged information and integrity checks, is essential for accurately evaluating agent performance on complex, long-horizon tasks and preventing workflow bypasses.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b51-c355-7a97-bf19-abce43625816/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b51-c355-7a97-bf19-abce43625816/transcript.json

## Resources

- GitHub repository: https://github.com/cmu-l3/gym-anything

## Similar Papers

- Agent S2: A Compositional Generalist-Specialist Framework for Computer  Use Agents (2504.00906v1): Researchers at Simular Research developed Agent S2, a compositional generalist-specialist framework for computer use agents that achieves new state-of-the-art performance on OSWorld, WindowsAgentArena, and AndroidWorld benchmarks. This framework utilizes a Mixture of Grounding experts for precise GUI interaction and Proactive Hierarchical Planning for robust, adaptive long-horizon task completion.
- Agent World Model: Infinity Synthetic Environments for Agentic Reinforcement Learning (2602.10090v2): The Agent World Model (AWM) introduces an open-source, code-driven pipeline that synthesizes 1,000 diverse, executable tool-use environments with database-backed state for large-scale reinforcement learning of autonomous agents. Agents trained on these synthetic environments, developed collaboratively by UNC Chapel Hill and Snowflake, demonstrate strong out-of-distribution generalization across various real-world benchmarks, validating the approach for developing robust LLM agents.
- OpenCUA: Open Foundations for Computer-Use Agents (2508.09123v3): The OPENCUA framework provides open foundations for computer-use agents, releasing tools for data collection, a large-scale dataset of 22,625 trajectories across multiple operating systems, and models. Its OPENCUA-72B model achieved 45.0% success on the OSWorld-Verified benchmark, representing a new state-of-the-art for open-source systems and reducing the performance gap with proprietary agents.
- Scaling Agents for Computer Use (2510.02250v2): Simular Research introduces Behavior Judge (BJudge), a framework enabling effective wide scaling for Computer-Use Agents (CUAs) by generating and evaluating multiple execution trajectories. BJudge achieved a 72.6% success rate on the OSWorld benchmark, establishing a new state-of-the-art and surpassing human-level performance of 72.36%.
- Terminal-Bench: Benchmarking Agents on Hard, Realistic Tasks in Command Line Interfaces (2601.11868v1): Terminal-Bench 2.0 introduces a benchmark to evaluate AI agents on 89 hard, realistic tasks within command-line environments, revealing that even frontier models achieve a resolution rate of less than 65%. This work establishes a challenging standard for assessing agent capabilities in complex technical workflows.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
