---
id: 2026-04-06-alphaxiv-paper-rosclaw-a-hierarchical-semantic-physical-framewo-b48d0d1c
kind: paper
title: 'ROSClaw: A Hierarchical Semantic-Physical Framework for Heterogeneous Multi-Agent Collaboration'
source_url: https://www.alphaxiv.org/abs/2604.04664
source_name: alphaXiv Papers
authors:
- Rongfeng Zhao
- Xuanhao Zhang
- Zhaochen Guo
- Xiang Shao
- Zhongpan Zhu
- Bin He
- Jie Chen
published_at: '2026-04-06T13:16:24Z'
ingested_at: '2026-04-09T10:00:08.388604Z'
content_hash: bfd1967076187db3ca337990142ad3881e47ae21a7cbc65ad9134d0a052338f1
identity_hash: a8b2e21f980ee85628ae2a735c65ff41a913e8f4283fdd04fc2f9d359ff87b65
tags:
- paper
- alphaxiv
- research
- agents
- Computer Science
- continual-learning
- cs.AI
- cs.MA
- cs.RO
- multi-agent-learning
- reinforcement-learning
- robotic-control
- robotics-perception
- tool-use
- vision-language-models
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
external_key: https://www.alphaxiv.org/abs/2604.04664
canonical_url: https://www.alphaxiv.org/abs/2604.04664
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:00:08.388607Z'
short_summary: Researchers from Shanghai Research Institute for Intelligent Autonomous Systems developed ROSClaw, a hierarchical semantic-physical framework that integrates high-level AI reasoning with low-level robot control for heterogeneous multi-agent collaboration. The framework uses a vision-language model controller, incorporates physical constraints via e-URDF, and features a closed-loop data collection mechanism, enabling robust task execution and safe motion generation across diverse robotic platforms.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# ROSClaw: A Hierarchical Semantic-Physical Framework for Heterogeneous Multi-Agent Collaboration

## alphaXiv Summary

Researchers from Shanghai Research Institute for Intelligent Autonomous Systems developed ROSClaw, a hierarchical semantic-physical framework that integrates high-level AI reasoning with low-level robot control for heterogeneous multi-agent collaboration. The framework uses a vision-language model controller, incorporates physical constraints via e-URDF, and features a closed-loop data collection mechanism, enabling robust task execution and safe motion generation across diverse robotic platforms.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04664
- Source paper: https://arxiv.org/abs/2604.04664
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04664v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04664v1.png
- Paper ID: 2604.04664
- Canonical ID: 2604.04664v1
- Paper group ID: 019d65b8-3aac-7d87-a83d-1a8f997dabb7
- Version ID: 019d65b8-3adc-7480-a52c-56a98f5bd470
- Version: v1
- Version order: 1
- Published at: 2026-04-06T13:16:24+00:00
- First published at: 2026-04-06T13:16:24+00:00
- Updated at: 2026-04-07T02:14:25.708000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Rongfeng Zhao
- Xuanhao Zhang
- Zhaochen Guo
- Xiang Shao
- Zhongpan Zhu
- Bin He
- Jie Chen

## Topics

- agents
- Computer Science
- continual-learning
- cs.AI
- cs.MA
- cs.RO
- multi-agent-learning
- reinforcement-learning
- robotic-control
- robotics-perception
- tool-use
- vision-language-models

## Metrics

- Visits (all): 57
- Visits (last 7 days): 57
- Total votes: 1
- Public total votes: 8
- X likes: 0

## Abstract

The integration of large language models (LLMs) with embodied agents has improved high-level reasoning capabilities; however, a critical gap remains between semantic understanding and physical execution. While vision-language-action (VLA) and vision-language-navigation (VLN) systems enable robots to perform manipulation and navigation tasks from natural language instructions, they still struggle with long-horizon sequential and temporally structured tasks. Existing frameworks typically adopt modular pipelines for data collection, skill training, and policy deployment, resulting in high costs in experimental validation and policy optimization. To address these limitations, we propose ROSClaw, an agent framework for heterogeneous robots that integrates policy learning and task execution within a unified vision-language model (VLM) controller. The framework leverages e-URDF representations of heterogeneous robots as physical constraints to construct a sim-to-real topological mapping, enabling real-time access to the physical states of both simulated and real-world agents. We further incorporate a data collection and state accumulation mechanism that stores robot states, multimodal observations, and execution trajectories during real-world execution, enabling subsequent iterative policy optimization. During deployment, a unified agent maintains semantic continuity between reasoning and execution, and dynamically assigns task-specific control to different agents, thereby improving robustness in multi-policy execution. By establishing an autonomous closed-loop framework, ROSClaw minimizes the reliance on robot-specific development workflows. The framework supports hardware-level validation, automated generation of SDK-level control programs, and tool-based execution, enabling rapid cross-platform transfer and continual improvement of robotic skills. Ours project page: this https URL.

## Problem

- Existing embodied intelligence systems face a semantic-physical gap, struggling to connect high-level reasoning with explicit physical dynamics and control constraints, often leading to infeasible or unsafe plans.
- Hardware heterogeneity, with fragmented SDKs and non-standardized interfaces across diverse robotic platforms, impedes unified control and efficient coordination.
- Current frameworks are often static, open-loop pipelines, limiting continuous learning, adaptation from physical interactions, and effective generalization across dynamic environments for multi-agent systems.

## Method

- A three-layer semantic-physical architecture (Cognitive, Coordination Automation via OpenClaw, and ROSClaw Physical World) unifies high-level reasoning, abstract task logic, and high-frequency robot control for heterogeneous agents.
- An e-URDF-based physical interception and scheduling mechanism (a "physical firewall") uses digital twin simulation to validate the physical feasibility and safety of generated commands before execution.
- A resource-driven closed-loop process continuously collects real-time robot states, multimodal observations, and execution trajectories into a Local Resource Pool, enabling self-organizing learning and continual policy refinement.

## Results

- The framework successfully orchestrated a complex, long-horizon collaborative task involving a mobile robotic arm, a humanoid robot, and a fixed robotic arm from different manufacturers in a smart home environment.
- The e-URDF-based physical safeguarding mechanism validated automatically generated multi-gimbal dance choreographies through pre-execution simulation and collision detection, reducing generation time to approximately three minutes.
- The system continuously recorded robot states and environmental perception data, enabling real-time interaction, structured environmental understanding via VLM, and the accumulation of reusable skill representations for continuous learning.

## Takeaways

- Effective integration of high-level semantic reasoning with low-level physical control is achieved through asynchronous decoupling across a hierarchical architecture, maintaining stability and coherence.
- A unified abstraction layer, the Online Tool Pool, successfully bridges diverse hardware SDKs and APIs, enabling cross-platform generalization and automated program synthesis from abstract instructions.
- Proactive physical safeguarding via e-URDF and digital twin simulation is critical for ensuring the safety and feasibility of AI-generated actions, preventing physically impossible or unsafe commands from reaching real robots.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65b8-3aac-7d87-a83d-1a8f997dabb7/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65b8-3aac-7d87-a83d-1a8f997dabb7/transcript.json

## Similar Papers

- HybridVLA: Collaborative Diffusion and Autoregression in a Unified Vision-Language-Action Model (2503.10631v3): HybridVLA introduces a unified Vision-Language-Action model that integrates both diffusion-based continuous action prediction and autoregressive reasoning within a shared Large Language Model backbone. This approach achieves state-of-the-art performance in robotic manipulation, demonstrating up to 19% higher success rates over prior methods in real-world tasks and strong generalization to unseen conditions.
- Being-0: A Humanoid Robotic Agent with Vision-Language Models and  Modular Skills (2503.12533v2): Being-0, a full-sized humanoid robot agent, successfully performs complex, multi-step tasks in real-world environments. Its framework integrates a high-level Foundation Model with robust modular skills via a novel VLM-based "Connector" module, which enhances embodied scene understanding, real-time control, and efficient task execution.
- Embodied Long Horizon Manipulation with Closed-loop Code Generation and Incremental Few-shot Adaptation (2503.21969v3): The DAHLIA framework enables robots to perform complex, multi-step manipulation tasks by generating executable code directly from natural language instructions. It employs a closed-loop dual-tunnel system with incremental few-shot adaptation, achieving high success rates on various benchmarks and demonstrating robust error recovery in real-world scenarios without relying on extensive pre-trained policies.
- CLEA: Closed-Loop Embodied Agent for Enhancing Task Execution in Dynamic  Environments (2503.00729v1): Researchers from CUHK-Shenzhen and Shanghai Jiao Tong University introduce CLEA, a groundbreaking closed-loop framework that enables robust LLM-based robotic task planning through four specialized language models working in concert, achieving a 67.3% improvement in success rate over baseline systems while demonstrating practical deployment in dynamic real-world environments.
- RoboClaw: An Agentic Framework for Scalable Long-Horizon Robotic Tasks (2603.11558v3): RoboClaw introduces an agentic framework that unifies data collection, policy learning, and execution for long-horizon robotic tasks, leveraging a Vision-Language Model as a meta-controller. This framework decreased human time for data collection by 53.7% and improved long-horizon task success rates by 25% compared to baseline methods on real-world manipulation tasks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
