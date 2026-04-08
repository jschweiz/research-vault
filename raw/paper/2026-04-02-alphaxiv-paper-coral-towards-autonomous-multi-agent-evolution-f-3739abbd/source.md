---
id: 2026-04-02-alphaxiv-paper-coral-towards-autonomous-multi-agent-evolution-f-3739abbd
kind: paper
title: CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery
source_url: https://www.alphaxiv.org/abs/2604.01658
source_name: alphaXiv Papers
authors:
  - Ao Qu
  - Han Zheng
  - Zijian Zhou
  - Yihao Yan
  - Yihong Tang
  - Shao Yong Ong
  - Fenglu Hong
  - Kaichen Zhou
  - Chonghe Jiang
  - Minwei Kong
  - Jiacheng Zhu
  - Xuan Jiang
  - Sirui Li
  - Cathy Wu
  - Bryan Kian Hsiang Low
  - Jinhua Zhao
  - Paul Pu Liang
published_at: 2026-04-02T05:59:06Z
ingested_at: 2026-04-07T21:41:46.384262Z
content_hash: ed9a00331ef07eca6b8e4b7cb9f380ed13e8c9551dd070bcefba9e9f37142a12
tags:
  - paper
  - alphaxiv
  - research
  - agentic-frameworks
  - agents
  - computer science
  - cs.ai
  - deep-reinforcement-learning
  - evolutionary-algorithms
  - multi-agent-learning
  - Computer Science
  - cs.AI
  - optimization-methods
  - reasoning
  - tool-use
  - transformers
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
external_key: https://www.alphaxiv.org/abs/2604.01658
canonical_url: https://www.alphaxiv.org/abs/2604.01658
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:26:41.561079Z
short_summary: The CORAL framework introduces an autonomous multi-agent evolutionary system, empowering Large Language Model agents to control their discovery process and collaborate indirectly through shared persistent memory. This approach achieved new state-of-the-art results on 8 out of 11 mathematical and systems optimization tasks, exhibiting a 3-10x higher improvement rate and an 18.3% cycle reduction in kernel engineering.
lightweight_enrichment_status: failed
lightweight_enriched_at: null
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: ed9a00331ef07eca6b8e4b7cb9f380ed13e8c9551dd070bcefba9e9f37142a12
lightweight_enrichment_error: "Attempt to overwrite 'operation_run_id' in LogRecord"
---
# CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery

## alphaXiv Summary

The CORAL framework introduces an autonomous multi-agent evolutionary system, empowering Large Language Model agents to control their discovery process and collaborate indirectly through shared persistent memory. This approach achieved new state-of-the-art results on 8 out of 11 mathematical and systems optimization tasks, exhibiting a 3-10x higher improvement rate and an 18.3% cycle reduction in kernel engineering.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.01658
- Source paper: https://arxiv.org/abs/2604.01658
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.01658v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.01658v1.png
- GitHub: https://github.com/Human-Agent-Society/CORAL
- GitHub stars: 306
- Paper ID: 2604.01658
- Canonical ID: 2604.01658v1
- Paper group ID: 019d5134-3e7c-759e-b352-329b5c646f37
- Version ID: 019d5134-3eb5-7678-b628-0fa53333a99a
- Version: v1
- Version order: 1
- Published at: 2026-04-02T05:59:06+00:00
- First published at: 2026-04-02T05:59:06+00:00
- Updated at: 2026-04-03T02:37:51.612000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Ao Qu
- Han Zheng
- Zijian Zhou
- Yihao Yan
- Yihong Tang
- Shao Yong Ong
- Fenglu Hong
- Kaichen Zhou
- Chonghe Jiang
- Minwei Kong
- Jiacheng Zhu
- Xuan Jiang
- Sirui Li
- Cathy Wu
- Bryan Kian Hsiang Low
- Jinhua Zhao
- Paul Pu Liang

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- deep-reinforcement-learning
- evolutionary-algorithms
- multi-agent-learning
- optimization-methods
- reasoning
- tool-use
- transformers

## Metrics

- Visits (all): 924
- Visits (last 7 days): 924
- Total votes: 12
- Public total votes: 55
- X likes: 0

## Abstract

Large language model (LLM)-based evolution is a promising approach for open-ended discovery, where progress requires sustained search and knowledge accumulation. Existing methods still rely heavily on fixed heuristics and hard-coded exploration rules, which limit the autonomy of LLM agents. We present CORAL, the first framework for autonomous multi-agent evolution on open-ended problems. CORAL replaces rigid control with long-running agents that explore, reflect, and collaborate through shared persistent memory, asynchronous multi-agent execution, and heartbeat-based interventions. It also provides practical safeguards, including isolated workspaces, evaluator separation, resource management, and agent session and health management. Evaluated on diverse mathematical, algorithmic, and systems optimization tasks, CORAL sets new state-of-the-art results on 10 tasks, achieving 3-10 times higher improvement rates with far fewer evaluations than fixed evolutionary search baselines across tasks. On Anthropic's kernel engineering task, four co-evolving agents improve the best known score from 1363 to 1103 cycles. Mechanistic analyses further show how these gains arise from knowledge reuse and multi-agent exploration and communication. Together, these results suggest that greater agent autonomy and multi-agent evolution can substantially improve open-ended discovery. Code is available at this https URL.

## Problem

- Existing LLM-powered evolutionary search relies on fixed heuristics and external rules, limiting agent autonomy and adaptability in complex, open-ended problem spaces where optimal search strategies are unknown.
- Current multi-agent LLM systems often use 'vertical scaling' with human-defined roles and rigid communication, which is restrictive for truly open-ended discovery where optimal task decomposition and interaction patterns are not known in advance.

## Method

- CORAL implements autonomous multi-agent evolution by empowering LLM agents with control over the retrieve, propose, evaluate, and update stages of the evolutionary loop, rather than relying on fixed external rules.
- A shared persistent memory, structured as a file system, enables asynchronous multi-agent organization where agents explore solution spaces in parallel and indirectly exchange discoveries, notes, and reusable skills.
- Heartbeat-based interventions (e.g., periodic consolidation, stagnation redirection) are incorporated to prevent agents from getting stuck, encourage knowledge contribution, and dynamically reorient search strategies.

## Results

- A single CORAL agent outperformed fixed evolutionary search baselines on all 11 mathematical and systems optimization tasks, achieving new state-of-the-art results on 8 tasks and demonstrating a 3-10x higher improvement rate.
- Multi-agent CORAL (4 agents) extended search performance on challenging stress-test problems, achieving an 18.3% cycle reduction in kernel engineering (a new SOTA) and a 5.0% score increase in polyominoes packing.
- Analysis revealed that multi-agent gains stem from cross-agent information transfer (e.g., 36% of attempts on Kernel Engineering used cross-agent parents with higher improvement rates) and increased exploration diversity (low Jaccard similarity of strategies across agents).

## Takeaways

- Granting LLM agents autonomy over evolutionary decisions and facilitating local verification steps leads to substantially more efficient search and higher improvement rates compared to fixed evolutionary algorithms.
- Asynchronous multi-agent organization with shared persistent memory fosters emergent collaboration and diverse exploration, extending the search frontier beyond what single autonomous agents can achieve.
- The systematic accumulation and sharing of knowledge, via agent-generated notes and reusable skills, is critical for driving successful and sustained discovery, especially in complex open-ended tasks.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d5134-3e7c-759e-b352-329b5c646f37/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d5134-3e7c-759e-b352-329b5c646f37/transcript.json
- Transcript lines: 19
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Mixed
- Headline: Mostly Human, AI Detected
- Fraction AI: 0.24912539
- Fraction AI-assisted: 0
- Fraction human: 0.75087464

## Resources

- GitHub repository: https://github.com/Human-Agent-Society/CORAL

## Similar Papers

- MemEvolve: Meta-Evolution of Agent Memory Systems (2512.18746v1): OPPO AI Agent Team and LV-NUS lab developed MemEvolve, a meta-evolutionary framework that allows large language model agents to adaptively refine their memory architectures. This approach enables agents to consistently improve task performance by up to 17.06% and generalize across various tasks, LLMs, and agent frameworks.
- AVO: Agentic Variation Operators for Autonomous Evolutionary Search (2603.24517v1): Agentic Variation Operators (AVO) empower large language models to function as autonomous, iterative optimizers in evolutionary search for high-performance code. This framework successfully discovered multi-head attention kernels on NVIDIA Blackwell B200 GPUs that achieved up to 3.5% higher throughput than cuDNN and 10.5% higher than FlashAttention-4, alongside effective transferability to grouped-query attention.
- SE-Agent: Self-Evolution Trajectory Optimization in Multi-Step Reasoning with LLM-Based Agents (2508.02085v6): A collaborative effort introduces SE-Agent, a self-evolutionary framework for LLM-based agents that optimizes multi-step reasoning trajectories via iterative revision, recombination, and refinement. This approach achieved state-of-the-art performance on SWE-bench Verified, improving Pass@1 by up to 112% for Llama-3.1-70b-Instruct and reaching 61.2% with Claude-3.7-Sonnet.
- ShinkaEvolve: Towards Open-Ended And Sample-Efficient Program Evolution (2509.19349v1): ShinkaEvolve combines large language models with advanced evolutionary computation to create an open-source framework for efficient, open-ended program discovery. This approach achieves state-of-the-art performance across diverse tasks while dramatically reducing the number of computational evaluations required.
- EvoScientist: Towards Multi-Agent Evolving AI Scientists for End-to-End Scientific Discovery (2603.08127v1): Researchers from Huawei Technologies Co., Ltd. developed EvoScientist, a multi-agent framework that enables AI scientists to continuously improve their idea generation and experiment execution strategies by learning from past outcomes. The system produced higher-quality scientific ideas and demonstrated increased code execution success rates, leading to accepted research papers at an AI conference, including a Best Paper Award.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
