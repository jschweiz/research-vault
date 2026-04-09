---
id: 2026-04-06-alphaxiv-paper-your-agent-their-asset-a-real-world-safety-analy-80bad67b
kind: paper
title: 'Your Agent, Their Asset: A Real-World Safety Analysis of OpenClaw'
source_url: https://www.alphaxiv.org/abs/2604.04759
source_name: alphaXiv Papers
authors:
- Zijun Wang
- Haoqin Tu
- Letian Zhang
- Hardy Chen
- Juncheng Wu
- Xiangyan Liu
- Zhenlong Yuan
- Tianyu Pang
- Michael Qizhe Shieh
- Fengze Liu
- Zeyu Zheng
- Huaxiu Yao
- Yuyin Zhou
- Cihang Xie
published_at: '2026-04-06T15:27:05Z'
ingested_at: '2026-04-09T09:56:12.362865Z'
content_hash: 521700ddf799acbdaeb6417f192113e5e39210e681079898af50a2e5c94c0812
identity_hash: b89266b2b51da6f2276ea2cac6372e41142fe5ba5c28083a32b9ab9e4a280b16
tags:
- paper
- alphaxiv
- research
- adversarial-attacks
- adversarial-robustness
- agentic-frameworks
- agents
- ai-for-cybersecurity
- Computer Science
- cs.AI
- cs.CL
- cs.CR
- cybersecurity
- ml-systems
- model-deployment-systems
- penetration-testing
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
external_key: https://www.alphaxiv.org/abs/2604.04759
canonical_url: https://www.alphaxiv.org/abs/2604.04759
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:56:12.362892Z'
short_summary: This study evaluates the real-world safety of OpenClaw, a personal AI agent, uncovering systematic vulnerabilities to 'state poisoning' across its persistent Capability, Identity, and Knowledge dimensions. It demonstrates that even advanced Large Language Models exhibit significantly increased attack success rates, up to 89.2% with Knowledge poisoning, suggesting these vulnerabilities are architectural rather than solely due to LLM limitations and exposing a tradeoff between agent evolution and security.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Your Agent, Their Asset: A Real-World Safety Analysis of OpenClaw

## alphaXiv Summary

This study evaluates the real-world safety of OpenClaw, a personal AI agent, uncovering systematic vulnerabilities to 'state poisoning' across its persistent Capability, Identity, and Knowledge dimensions. It demonstrates that even advanced Large Language Models exhibit significantly increased attack success rates, up to 89.2% with Knowledge poisoning, suggesting these vulnerabilities are architectural rather than solely due to LLM limitations and exposing a tradeoff between agent evolution and security.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04759
- Source paper: https://arxiv.org/abs/2604.04759
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04759v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04759v1.png
- GitHub: https://github.com/UCSC-VLAA/CIK-Bench
- GitHub stars: 16
- Paper ID: 2604.04759
- Canonical ID: 2604.04759v1
- Paper group ID: 019d65d8-c2a4-7b16-a0c4-266d583e19c2
- Version ID: 019d65d8-c2c3-71d9-87cc-9cec25330e97
- Version: v1
- Version order: 1
- Published at: 2026-04-06T15:27:05+00:00
- First published at: 2026-04-06T15:27:05+00:00
- Updated at: 2026-04-07T02:49:57.668000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Zijun Wang
- Haoqin Tu
- Letian Zhang
- Hardy Chen
- Juncheng Wu
- Xiangyan Liu
- Zhenlong Yuan
- Tianyu Pang
- Michael Qizhe Shieh
- Fengze Liu
- Zeyu Zheng
- Huaxiu Yao
- Yuyin Zhou
- Cihang Xie

## Topics

- adversarial-attacks
- adversarial-robustness
- agentic-frameworks
- agents
- ai-for-cybersecurity
- Computer Science
- cs.AI
- cs.CL
- cs.CR
- cybersecurity
- ml-systems
- model-deployment-systems
- penetration-testing

## Metrics

- Visits (all): 75
- Visits (last 7 days): 75
- Total votes: 1
- Public total votes: 9
- X likes: 0

## Abstract

OpenClaw, the most widely deployed personal AI agent in early 2026, operates with full local system access and integrates with sensitive services such as Gmail, Stripe, and the filesystem. While these broad privileges enable high levels of automation and powerful personalization, they also expose a substantial attack surface that existing sandboxed evaluations fail to capture. To address this gap, we present the first real-world safety evaluation of OpenClaw and introduce the CIK taxonomy, which unifies an agent's persistent state into three dimensions, i.e., Capability, Identity, and Knowledge, for safety analysis. Our evaluations cover 12 attack scenarios on a live OpenClaw instance across four backbone models (Claude Sonnet 4.5, Opus 4.6, Gemini 3.1 Pro, and GPT-5.4). The results show that poisoning any single CIK dimension increases the average attack success rate from 24.6% to 64-74%, with even the most robust model exhibiting more than a threefold increase over its baseline vulnerability. We further assess three CIK-aligned defense strategies alongside a file-protection mechanism; however, the strongest defense still yields a 63.8% success rate under Capability-targeted attacks, while file protection blocks 97% of malicious injections but also prevents legitimate updates. Taken together, these findings show that the vulnerabilities are inherent to the agent architecture, necessitating more systematic safeguards to secure personal AI agents. Our project page is this https URL.

## Problem

- Prior AI agent security research predominantly uses sandboxed environments and focuses on isolated attack dimensions, failing to assess the comprehensive real-world attack surface of deployed agents with external service integrations.
- Personal AI agents with extensive system access and integrations (e.g., Gmail, Stripe) present significant attack surfaces that are not adequately captured by theoretical or simulated assessments.
- A lack of a unified framework to categorize and evaluate the exploitation of all persistent state dimensions within live, operational personal AI agent systems.

## Method

- Introduced the CIK (Capability, Identity, Knowledge) taxonomy to provide a structured framework for categorizing an agent's persistent, evolving state and its attack surfaces.
- Conducted the first real-world safety evaluation of OpenClaw, a deployed personal AI agent, by integrating it with genuine external services and operating on a local machine to simulate actual usage conditions.
- Implemented a two-phase attack model (injection and trigger) to demonstrate how manipulating Capability, Identity, or Knowledge can lead to persistent, harmful actions across sessions.

## Results

- State poisoning consistently and substantially increased Attack Success Rates (ASR), with averages reaching 74.4% for Knowledge, 68.3% for Capability, and 64.3% for Identity attacks, up from a baseline ASR of 10.0-36.7%.
- Executable payloads in Capability attacks proved highly reliable, achieving ≥77% Phase 2 ASR across all models, often bypassing LLM content inspection.
- File protection effectively reduced malicious injection rates from 87.0% to 5.0% but could not reliably differentiate between malicious and benign updates, blocking legitimate personalization requests at similar rates (reducing them from 100% to below 13.2%).

## Takeaways

- State-poisoning vulnerabilities are systematic and fundamental to the architecture of personal AI agents that maintain persistent, evolving states, indicating that simply improving backbone LLM capabilities is insufficient for mitigation.
- There exists a fundamental tradeoff between agent evolution and security; the very mechanisms enabling personalization through persistent files also serve as primary attack surfaces.
- Current CIK-aligned and file-protection defense strategies are largely insufficient, especially against Capability attacks involving direct code execution, which often bypass LLM reasoning entirely.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d8-c2a4-7b16-a0c4-266d583e19c2/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d8-c2a4-7b16-a0c4-266d583e19c2/transcript.json

## Resources

- GitHub repository: https://github.com/UCSC-VLAA/CIK-Bench

## Similar Papers

- Real AI Agents with Fake Memories: Fatal Context Manipulation Attacks on Web3 Agents (2503.16248v3): A study by Princeton University and the Sentient Foundation formalized "memory injection" as a stealthy context manipulation attack against LLM-powered Web3 agents. The research empirically demonstrated that these attacks achieve higher success rates than prompt injection and bypass current prompt-level defenses, with fine-tuning showing improved robustness, particularly on the CrAIBench benchmark and ElizaOS.
- Security Challenges in AI Agent Deployment: Insights from a Large Scale Public Competition (2507.20526v1): Researchers conducted the largest public red-teaming competition against 22 frontier AI agents, revealing universal susceptibility to policy violations with an average 12.7% attack success rate. Indirect prompt injections were substantially more effective (27.1%) than direct methods (5.7%), and agent robustness showed no strong correlation with model capability or inference-time compute.
- Agent Security Bench (ASB): Formalizing and Benchmarking Attacks and  Defenses in LLM-based Agents (2410.02644v4): AGENT SECURITY BENCH (ASB) introduces a comprehensive benchmark for evaluating the security of LLM-based agents against various adversarial attacks, including a novel Plan-of-Thought Backdoor Attack. The research demonstrates that LLM-based agents are vulnerable across different operational stages and that current defense mechanisms are largely ineffective in mitigating these threats.
- InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Large Language Model Agents (2403.02691v3): Researchers at the University of Illinois Urbana-Champaign developed INJECAGENT, a benchmark to assess the vulnerability of tool-integrated large language model agents to indirect prompt injection attacks. Their evaluation revealed that prompted agents, even those based on advanced models, are highly susceptible to these attacks, while fine-tuned agents exhibit improved, but not complete, resilience.
- OS-Harm: A Benchmark for Measuring Safety of Computer Use Agents (2506.14866v2): Researchers from EPFL and Carnegie Mellon University developed OS-HARM, a benchmark for evaluating the safety of LLM-based computer use agents interacting with realistic operating system environments. The benchmark revealed that frontier agents are highly vulnerable to deliberate misuse (48-70% unsafe execution) and moderately susceptible to prompt injection attacks (2-20% unsafe execution).
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
