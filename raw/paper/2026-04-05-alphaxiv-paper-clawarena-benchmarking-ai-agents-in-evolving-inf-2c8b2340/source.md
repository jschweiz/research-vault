---
id: 2026-04-05-alphaxiv-paper-clawarena-benchmarking-ai-agents-in-evolving-inf-2c8b2340
kind: paper
title: 'ClawArena: Benchmarking AI Agents in Evolving Information Environments'
source_url: https://www.alphaxiv.org/abs/2604.04202
source_name: alphaXiv Papers
authors:
- Haonian Ji
- Kaiwen Xiong
- Siwei Han
- Peng Xia
- Shi Qiu
- Yiyang Zhou
published_at: '2026-04-05T17:55:23Z'
ingested_at: '2026-04-08T09:28:01.511188Z'
content_hash: 7ac427d23b86e05c5abb9827bc9c4f38596d0f9e85778252cc0dcd35968e38bb
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- computer science
- continual-learning
- cs.ai
- cs.cl
- cs.lg
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
external_key: https://www.alphaxiv.org/abs/2604.04202
canonical_url: https://www.alphaxiv.org/abs/2604.04202
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:12:55.652167Z'
short_summary: ClawArena is a benchmark for evaluating AI agents in dynamic information environments, focusing on multi-source conflict reasoning, dynamic belief revision, and implicit personalization. Experiments show that underlying language model capabilities are more critical than agent framework design for overall performance.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:39:37.841143Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 5d6b8e562a3d98b9f69fd32addb26e0d628e94bd4ca21688f9a27e5ac2f224ce
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 9022f8396a0e77e4ca6c19cc8fba153d60cb77efa063cc53ef580e1562b3c3f7
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.5
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses the user's favorite topics of language models, evaluation, and reasoning by introducing a benchmark for AI agents and analyzing the role of model capabilities versus framework design.
  evidence_quotes:
  - Experiments on five agent frameworks and five language models show that both model capability (15.4% range) and framework design (9.2%) substantially affect per
  - The intrinsic capabilities of the base language model have a more dominant impact on overall agent performance (0.154 range) compared to the design of the agent
  - ClawArena introduces a benchmark for evaluating AI agents in complex, dynamic information environments, focusing on multi-source conflict reasoning, dynamic bel
---
# ClawArena: Benchmarking AI Agents in Evolving Information Environments

## alphaXiv Summary

ClawArena introduces a benchmark for evaluating AI agents in complex, dynamic information environments, focusing on multi-source conflict reasoning, dynamic belief revision, and implicit personalization. Experiments indicate that underlying language model capabilities more significantly impact overall performance (0.154 range) than agent framework design, though sophisticated frameworks like MetaClaw can enhance execution-oriented tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04202
- Source paper: https://arxiv.org/abs/2604.04202
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04202v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04202v1.png
- GitHub: https://github.com/aiming-lab/ClawArena
- GitHub stars: 3
- Paper ID: 2604.04202
- Canonical ID: 2604.04202v1
- Paper group ID: 019d65dc-b043-70b0-8cb7-b5cdacb96183
- Version ID: 019d65dc-b081-7036-b3bf-27189cb11a51
- Version: v1
- Version order: 1
- Published at: 2026-04-05T17:55:23+00:00
- First published at: 2026-04-05T17:55:23+00:00
- Updated at: 2026-04-07T02:54:15.107000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Haonian Ji
- Kaiwen Xiong
- Siwei Han
- Peng Xia
- Shi Qiu
- Yiyang Zhou
- Jiaqi Liu
- Jinlong Li
- Bingzhou Li
- Zeyu Zheng
- Cihang Xie
- Huaxiu Yao

## Topics

- agentic-frameworks
- agents
- Computer Science
- continual-learning
- cs.AI
- cs.CL
- cs.LG
- human-ai-interaction
- reasoning
- test-time-inference

## Metrics

- Visits (all): 144
- Visits (last 7 days): 144
- Total votes: 4
- Public total votes: 20
- X likes: 0

## Abstract

AI agents deployed as persistent assistants must maintain correct beliefs as their information environment evolves. In practice, evidence is scattered across heterogeneous sources that often contradict one another, new information can invalidate earlier conclusions, and user preferences surface through corrections rather than explicit instructions. Existing benchmarks largely assume static, single-authority settings and do not evaluate whether agents can keep up with this complexity. We introduce ClawArena, a benchmark for evaluating AI agents in evolving information environments. Each scenario maintains a complete hidden ground truth while exposing the agent only to noisy, partial, and sometimes contradictory traces across multi-channel sessions, workspace files, and staged updates. Evaluation is organized around three coupled challenges: multi-source conflict reasoning, dynamic belief revision, and implicit personalization, whose interactions yield a 14-category question taxonomy. Two question formats, multi-choice (set-selection) and shell-based executable checks, test both reasoning and workspace grounding. The current release contains 64 scenarios across 8 professional domains, totaling 1{,}879 evaluation rounds and 365 dynamic updates. Experiments on five agent frameworks and five language models show that both model capability (15.4% range) and framework design (9.2%) substantially affect performance, that self-evolving skill frameworks can partially close model-capability gaps, and that belief revision difficulty is determined by update design strategy rather than the mere presence of updates. Code is available at this https URL.

## Problem

- Existing AI agent benchmarks operate on simplified assumptions, typically using static environments with a single source of truth, failing to mirror real-world complexities.
- Agents struggle with resolving conflicting information originating from multiple heterogeneous sources (e.g., chat, files) and discerning source reliability.
- Current evaluation methods do not adequately assess an agent's ability to revise prior beliefs in response to new, evolving information or to learn and apply implicit user preferences over time.

## Method

- ClawArena provides a benchmark of 64 scenarios across 8 professional domains, featuring a hidden ground truth and noisy, partial, and potentially contradictory observable information via multi-channel histories and files.
- It integrates evaluation across multi-source conflict reasoning, dynamic belief revision, and implicit personalization, using a 14-category question taxonomy to capture diverse failure modes.
- Scenarios are constructed with empirical distributions to ensure authenticity and include both multi-choice set-selection questions and shell-based executable checks for comprehensive assessment of abstract reasoning and workspace grounding.

## Results

- MetaClaw, a skill-driven self-evolving framework built on OpenClaw, achieved the highest overall score of 0.603 with GPT-5.1, surpassing OpenClaw by 4.1% and demonstrating superior Execution Evaluation.
- Language models showed a clear capability gradient with OpenClaw, from Claude Opus 4.6 (0.735) as the top performer, followed by Sonnet 4.6 (0.708), Haiku 4.5 (0.614), and GPT-5.2 (0.581).
- Error analysis revealed that workspace grounding capabilities (executable checks) are largely uncorrelated with abstract reasoning (multi-choice scores), indicating distinct challenges, and model-level biases like narrative anchoring can propagate across frameworks.

## Takeaways

- The intrinsic capabilities of the base language model have a more dominant impact on overall agent performance (0.154 range) compared to the design of the agent framework (0.092 range).
- Self-evolving agent frameworks, exemplified by MetaClaw, can improve performance, especially in execution-oriented tasks and during mid-scenario updates, potentially mitigating some underlying model limitations.
- Belief revision difficulty is primarily driven by the strategic design of updates, with concentrated and targeted contradictions leading to greater performance drops than merely a high volume of distributed updates.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65dc-b043-70b0-8cb7-b5cdacb96183/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65dc-b043-70b0-8cb7-b5cdacb96183/transcript.json

## Resources

- GitHub repository: https://github.com/aiming-lab/ClawArena

## Similar Papers

- REAL: Benchmarking Autonomous Agents on Deterministic Simulations of  Real Websites (2504.11543v2): Researchers developed REAL, a benchmark featuring 11 deterministic, high-fidelity simulations of real-world websites and 112 multi-turn tasks to evaluate autonomous web agents. The evaluation of frontier language models on REAL revealed that no agent achieved higher than a 41.07% success rate, indicating significant limitations in current capabilities.
- ARE: Scaling Up Agent Environments and Evaluations (2509.17158v2): Meta's research introduces ARE (Agents Research Environments), a scalable, event-based platform for developing and evaluating LLM agents in dynamic, asynchronous simulations. The accompanying Gaia2 benchmark reveals critical limitations in current frontier LLMs, particularly their performance on tasks requiring adaptability, temporal awareness, and ambiguity resolution, while demonstrating the potential of multi-agent collaboration.
- \$OneMillion-Bench: How Far are Language Agents from Human Experts? (2603.07980v1): A new benchmark, $OneMillion-Bench, evaluates language agents on complex, economically consequential professional tasks across five high-stakes domains, revealing a "reliability gap" between current AI agents and human experts. It quantifies the economic value delivered by agents, showing varied impacts of web search and providing detailed diagnostic insights.
- AgentBench: Evaluating LLMs as Agents (2308.03688v3): AGENTBENCH introduces a multi-dimensional benchmark with 8 interactive environments to systematically evaluate Large Language Models (LLMs) as agents. The benchmark reveals a significant performance gap between commercial and open-source LLMs, identifying predominant failure modes in long-term reasoning and instruction following.
- AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents (2406.13352v3): ETH Zurich researchers developed AgentDojo, a dynamic and extensible evaluation framework to measure the adversarial robustness of LLM agents against prompt injection attacks in realistic, tool-calling environments. The framework revealed that even highly capable LLMs struggle with complex benign tasks and are susceptible to prompt injection attacks, with more capable models often being easier to attack. While existing defenses show mixed results, simple tool isolation mechanisms proved most effective at mitigating attacks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
