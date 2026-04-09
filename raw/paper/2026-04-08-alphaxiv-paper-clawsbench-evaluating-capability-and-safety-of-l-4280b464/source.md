---
id: 2026-04-08-alphaxiv-paper-clawsbench-evaluating-capability-and-safety-of-l-4280b464
kind: paper
title: 'ClawsBench: Evaluating Capability and Safety of LLM Productivity Agents in Simulated Workspaces'
source_url: https://www.alphaxiv.org/abs/2604.05172
source_name: alphaXiv Papers
authors:
- Xiangyi Li
- Kyoung Whan Choe
- Yimin Liu
- Xiaokun Chen
- Chujun Tao
- Bingran You
- Wenbo Chen
- Zonglin Di
- Jiankai Sun
- Shenghan Zheng
- Jiajun Bao
- Yuanli Wang
- Weixiang Yan
- Yiyuan Li
- Han-chung Lee
published_at: '2026-04-08T09:27:21Z'
ingested_at: '2026-04-09T09:58:24.001737Z'
content_hash: 02608a46a85def42d101fa5101db992157fe0970fdbd9c726db40b7637f9452a
identity_hash: d7045507767aa74dc68a355c14e921dcfc55eb280633fd3f92b1f0b2e17572e5
tags:
- paper
- alphaxiv
- research
- adversarial-robustness
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- reasoning
- tool-use
- audio
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.05172
canonical_url: https://www.alphaxiv.org/abs/2604.05172
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:58:24.001744Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# ClawsBench: Evaluating Capability and Safety of LLM Productivity Agents in Simulated Workspaces

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05172
- Source paper: https://arxiv.org/abs/2604.05172
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05172v2.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05172v2.png
- Paper ID: 2604.05172
- Canonical ID: 2604.05172v2
- Paper group ID: 019d6b24-3b0a-7e90-ae27-9fae8a48aaa8
- Version ID: 019d70fa-bee9-799c-b67a-e7d67519eab2
- Version: v2
- Version order: 2
- Published at: 2026-04-08T09:27:21+00:00
- First published at: 2026-04-06T21:09:06+00:00
- Updated at: 2026-04-08T03:30:29.770000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Xiangyi Li
- Kyoung Whan Choe
- Yimin Liu
- Xiaokun Chen
- Chujun Tao
- Bingran You
- Wenbo Chen
- Zonglin Di
- Jiankai Sun
- Shenghan Zheng
- Jiajun Bao
- Yuanli Wang
- Weixiang Yan
- Yiyuan Li
- Han-chung Lee

## Topics

- adversarial-robustness
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- reasoning
- tool-use

## Metrics

- Visits (all): 28
- Visits (last 7 days): 28
- Total votes: 0
- Public total votes: 1
- X likes: 0

## Abstract

Large language model (LLM) agents are increasingly deployed to automate productivity tasks (e.g., email, scheduling, document management), but evaluating them on live services is risky due to potentially irreversible changes. Existing benchmarks rely on simplified environments and fail to capture realistic, stateful, multi-service workflows. We introduce ClawsBench, a benchmark for evaluating and improving LLM agents in realistic productivity settings. It includes five high-fidelity mock services (Gmail, Slack, Google Calendar, Google Docs, Google Drive) with full state management and deterministic snapshot/restore, along with 44 structured tasks covering single-service, cross-service, and safety-critical scenarios. We decompose agent scaffolding into two independent levers (domain skills that inject API knowledge via progressive disclosure, and a meta prompt that coordinates behavior across services) and vary both to measure their separate and combined effects. Experiments across 6 models, 4 agent harnesses, and 33 conditions show that with full scaffolding, agents achieve task success rates of 39-64% but exhibit unsafe action rates of 7-33%. On OpenClaw, the top five models fall within a 10 percentage-point band on task success (53-63%), with unsafe action rates from 7% to 23% and no consistent ordering between the two metrics. We identify eight recurring patterns of unsafe behavior, including multi-step sandbox escalation and silent contract modification. We release the trajectories and future dataset at this https URL.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6b24-3b0a-7e90-ae27-9fae8a48aaa8/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b24-3b0a-7e90-ae27-9fae8a48aaa8/transcript.json

## Similar Papers

- SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks (2602.12670v3): Researchers introduced SkillsBench, a benchmark to evaluate how effectively "Agent Skills" augment large language model (LLM) agents, measuring performance across diverse tasks and agent-model configurations. The benchmark found that curated Skills improved average agent performance by +16.2 percentage points and can enable smaller LLMs to match the performance of larger models operating without Skills.
- REAL: Benchmarking Autonomous Agents on Deterministic Simulations of  Real Websites (2504.11543v2): Researchers developed REAL, a benchmark featuring 11 deterministic, high-fidelity simulations of real-world websites and 112 multi-turn tasks to evaluate autonomous web agents. The evaluation of frontier language models on REAL revealed that no agent achieved higher than a 41.07% success rate, indicating significant limitations in current capabilities.
- MCP-Bench: Benchmarking Tool-Using LLM Agents with Complex Real-World Tasks via MCP Servers (2508.20453v1): Accenture and UC Berkeley researchers developed MCP-Bench, a benchmark for evaluating LLM agents on complex, multi-step real-world tasks using production-grade Model Context Protocol (MCP) servers and fuzzy instructions. The evaluation of 20 LLMs revealed that while basic tool execution is robust, advanced models still face challenges in long-horizon planning, cross-domain orchestration, and information grounding.
- AgentBench: Evaluating LLMs as Agents (2308.03688v3): AGENTBENCH introduces a multi-dimensional benchmark with 8 interactive environments to systematically evaluate Large Language Models (LLMs) as agents. The benchmark reveals a significant performance gap between commercial and open-source LLMs, identifying predominant failure modes in long-term reasoning and instruction following.
- The Tool Decathlon: Benchmarking Language Agents for Diverse, Realistic, and Long-Horizon Task Execution (2510.25726v2): The Tool Decathlon (TOOLATHLON) is introduced as a new benchmark for evaluating language agents on diverse, realistic, and long-horizon tasks spanning 32 real-world applications. Evaluations reveal that state-of-the-art models, including Claude-4.5-Sonnet, achieve only up to a 38.6% success rate, underscoring significant limitations in current agent capabilities for complex, multi-step operations.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
