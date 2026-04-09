---
id: 2026-04-03-alphaxiv-paper-agentic-mme-what-agentic-capability-really-bring-688666ad
kind: paper
title: 'Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?'
source_url: https://www.alphaxiv.org/abs/2604.03016
source_name: alphaXiv Papers
authors:
- Qianshan Wei
- Yishan Yang
- Siyi Wang
- Jinglin Chen
- Binyu Wang
- Jiaming Wang
published_at: '2026-04-03T13:02:01Z'
ingested_at: '2026-04-07T21:43:35.459252Z'
content_hash: 4a81ac35e27bf8702b94edbeb3a0e691348134e23df370b118a9d55a2c644499
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- computer science
- cs.ai
- data-curation
- model-observability
- multi-modal-learning
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
external_key: https://www.alphaxiv.org/abs/2604.03016
canonical_url: https://www.alphaxiv.org/abs/2604.03016
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-07T21:43:35.459258Z'
short_summary: '# Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence? ## alphaXiv Summary Agentic-MME introduces a process-verified benchmark for assessing how multimodal large language models coordinate visual manipulation and open-web search tools to solve complex, real-world problems.'
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:38:14.553310Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: f7985cf1c46477ca452c616a897f57a4a5b137efa4e0a1331ba70c0a7695e8f1
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 4ced69fb8a39df97e17749fc8b28931384540817c8b65e3b69c89535aa996af5
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.7
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses favorite topics like LLM evaluation, multimodal intelligence, and agentic frameworks, making it highly relevant to the user's profile.
  evidence_quotes:
  - 'Agentic-MME introduces a process-verified benchmark for assessing how multimodal large language models coordinate visual manipulation and open-web search tools '
  - 'Agentic-MME introduces a process-verified benchmark for assessing how multimodal large language models coordinate visual manipulation and open-web search tools '
  - Experimental results show the best model, Gemini 3 Pro (Atm mode), achieved 56.3% overall accuracy and 33.3% on Level-3 tasks, significantly trailing human perf
---
# Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?

## alphaXiv Summary

Agentic-MME introduces a process-verified benchmark for assessing how multimodal large language models coordinate visual manipulation and open-web search tools to solve complex, real-world problems. Evaluation reveals a substantial performance gap, with leading models reaching 56.3% overall accuracy compared to human 93.8%, especially struggling with multi-step planning and reliable tool execution in intricately intertwined tasks.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.03016
- Source paper: https://arxiv.org/abs/2604.03016
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.03016v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.03016v1.png
- GitHub: https://github.com/ChoS3nE11ven/Agentic-MME
- GitHub stars: 0
- Paper ID: 2604.03016
- Canonical ID: 2604.03016v1
- Paper group ID: 019d6093-1ffe-77c5-a52b-160ccc7c316b
- Version ID: 019d6093-2048-7f2b-83a3-bacd32a8f7e6
- Version: v1
- Version order: 1
- Published at: 2026-04-03T13:02:01+00:00
- First published at: 2026-04-03T13:02:01+00:00
- Updated at: 2026-04-06T02:15:47.966000+00:00
- License: http://creativecommons.org/licenses/by-nc-sa/4.0/
- Citations: 0

## Authors

- Qianshan Wei
- Yishan Yang
- Siyi Wang
- Jinglin Chen
- Binyu Wang
- Jiaming Wang
- Shuang Chen
- Zechen Li
- Yang Shi
- Yuqi Tang
- Weining Wang
- Yi Yu
- Chaoyou Fu
- Qi Li
- Yi-Fan Zhang

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- data-curation
- model-observability
- multi-modal-learning
- reasoning
- tool-use
- vision-language-models
- visual-reasoning

## Metrics

- Visits (all): 134
- Visits (last 7 days): 134
- Total votes: 4
- Public total votes: 18
- X likes: 0

## Abstract

Multimodal Large Language Models (MLLMs) are evolving from passive observers into active agents, solving problems through Visual Expansion (invoking visual tools) and Knowledge Expansion (open-web search). However, existing evaluations fall short: they lack flexible tool integration, test visual and search tools separately, and evaluate primarily by final answers. Consequently, they cannot verify if tools were actually invoked, applied correctly, or used efficiently. To address this, we introduce Agentic-MME, a process-verified benchmark for Multimodal Agentic Capabilities. It contains 418 real-world tasks across 6 domains and 3 difficulty levels to evaluate capability synergy, featuring over 2,000 stepwise checkpoints that average 10+ person-hours of manual annotation per task. Each task includes a unified evaluation framework supporting sandboxed code and APIs, alongside a human reference trajectory annotated with stepwise checkpoints along dual-axis: S-axis and V-axis. To enable true process-level verification, we audit fine-grained intermediate states rather than just final answers, and quantify efficiency via an overthinking metric relative to human trajectories. Experimental results show the best model, Gemini3-pro, achieves 56.3% overall accuracy, which falls significantly to 23.0% on Level-3 tasks, underscoring the difficulty of real-world multimodal agentic problem solving.

## Problem

- Existing multimodal benchmarks lacked integrated evaluation of visual manipulation and open-web search tools, often treating them as separate functionalities.
- The synergistic interplay between visual and knowledge expansion in complex, real-world scenarios remained largely unexplored.
- Evaluations predominantly focused on final answer correctness, offering limited insight into intermediate steps, tool application accuracy, or specific failure modes.

## Method

- Developed Agentic-MME, a benchmark featuring 418 real-world tasks across 6 domains requiring the combined use of 13 visual operations and 4 open-web retrieval tools.
- Designed tasks with increasing difficulty, culminating in Level 3 scenarios demanding iterative, interleaved execution and synergistic coupling of visual and knowledge expansion.
- Implemented a process-verified evaluation methodology with granular step-wise human reference trajectories, dual-axis metrics (V_tool, V_true, S-axis), and an "Overthink" metric to diagnose intermediate failures and efficiency.

## Results

- The top-performing model, Gemini 3 Pro (Atm mode), achieved 56.3% overall accuracy and 33.3% on Level-3 tasks, significantly trailing human performance (93.8% overall, 82.3% on Level-3).
- Open-source models demonstrated lower performance, with some like Qwen3 VL-235B reaching 10.1% on Level-3 tasks, and exhibiting S-scores below 5% for effective knowledge expansion in certain cases.
- Structured function-calling (Atm) mode consistently matched or surpassed code generation (Gen) mode in tool invocation and accuracy, exemplified by a model's V_tool increasing from 7.6% to over 70% when switching modes.

## Takeaways

- Even leading MLLM agents exhibit a substantial performance disparity compared to human solvers, particularly in multi-step planning and reliable tool execution for complex, intertwined tasks.
- Open-source models demonstrate significant limitations in robust search planning and effective knowledge retrieval, hindering their ability to leverage external information.
- While flexible, code generation interfaces currently impose a higher cognitive load on models, leading to less reliable tool execution compared to structured function-calling APIs.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6093-1ffe-77c5-a52b-160ccc7c316b/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6093-1ffe-77c5-a52b-160ccc7c316b/transcript.json

## Resources

- GitHub repository: https://github.com/ChoS3nE11ven/Agentic-MME

## Similar Papers

- EmbodiedBench: Comprehensive Benchmarking Multi-modal Large Language  Models for Vision-Driven Embodied Agents (2502.09560v3): This paper presents EMBODIEDBENCH, a new comprehensive benchmark for evaluating Multi-modal Large Language Models (MLLMs) as vision-driven embodied agents. Experiments with 24 MLLMs reveal that while models perform strongly on high-level planning tasks, they significantly struggle with low-level physical interactions like precise manipulation and long-horizon tasks, with GPT-4o achieving only 28.9% on manipulation.
- MCP-Bench: Benchmarking Tool-Using LLM Agents with Complex Real-World Tasks via MCP Servers (2508.20453v1): Accenture and UC Berkeley researchers developed MCP-Bench, a benchmark for evaluating LLM agents on complex, multi-step real-world tasks using production-grade Model Context Protocol (MCP) servers and fuzzy instructions. The evaluation of 20 LLMs revealed that while basic tool execution is robust, advanced models still face challenges in long-horizon planning, cross-domain orchestration, and information grounding.
- \$OneMillion-Bench: How Far are Language Agents from Human Experts? (2603.07980v1): A new benchmark, $OneMillion-Bench, evaluates language agents on complex, economically consequential professional tasks across five high-stakes domains, revealing a "reliability gap" between current AI agents and human experts. It quantifies the economic value delivered by agents, showing varied impacts of web search and providing detailed diagnostic insights.
- MM-BrowseComp: A Comprehensive Benchmark for Multimodal Browsing Agents (2508.13186v1): ByteDance, alongside Nanjing University and other institutions, introduced MM-BrowseComp, a new benchmark that evaluates multimodal browsing agents' ability to retrieve and reason over information across text, images, and videos on the web. Evaluations show that even state-of-the-art models achieve low accuracy, highlighting significant limitations in current AI agents' multimodal comprehension and proactive visual analysis.
- MMIE: Massive Multimodal Interleaved Comprehension Benchmark for Large  Vision-Language Models (2410.10139v2): A new benchmark, MMIE, comprising over 20,000 multimodal queries, measures large vision-language models' ability to comprehend and generate interleaved text and images across diverse knowledge domains. The research also introduces MMIE-Score, an automated evaluation metric that demonstrates superior alignment with human judgment compared to existing methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
