---
id: 2026-04-06-alphaxiv-paper-search-do-not-guess-teaching-small-language-mode-ae1bd71c
kind: paper
title: 'Search, Do not Guess: Teaching Small Language Models to Be Effective Search Agents'
source_url: https://www.alphaxiv.org/abs/2604.04651
source_name: alphaXiv Papers
authors:
- Yizhou Liu
- Qi Sun
- Yulin Chen
- Siyue Zhang
- Chen Zhao
published_at: '2026-04-06T13:00:38Z'
ingested_at: '2026-04-09T09:58:15.153071Z'
content_hash: ba1307aa5cf4e3defaa3b5015acd147f24daa94d8d980b19a89012879ee4b76e
identity_hash: 9217d4d08f8855b4d0e475cecffd44b41ab9049fcc76e140b672ffe1019c7eb1
tags:
- paper
- alphaxiv
- research
- agents
- Computer Science
- cs.AI
- fine-tuning
- information-extraction
- knowledge-distillation
- lightweight-models
- reasoning
- text-generation
- tool-use
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
external_key: https://www.alphaxiv.org/abs/2604.04651
canonical_url: https://www.alphaxiv.org/abs/2604.04651
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:58:15.153076Z'
short_summary: Researchers from New York University and Nanyang Technological University introduce the "Always-Search Policy" (ASP), a distillation approach that explicitly trains small language models (SLMs) to consistently invoke external search tools and ground their answers in retrieved evidence. This enables SLMs to achieve performance comparable to large language models on complex knowledge-intensive QA tasks, while reducing inference latency by approximately three times, by effectively addressing parametric hallucination and insufficient search tool invocation.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Search, Do not Guess: Teaching Small Language Models to Be Effective Search Agents

## alphaXiv Summary

Researchers from New York University and Nanyang Technological University introduce the "Always-Search Policy" (ASP), a distillation approach that explicitly trains small language models (SLMs) to consistently invoke external search tools and ground their answers in retrieved evidence. This enables SLMs to achieve performance comparable to large language models on complex knowledge-intensive QA tasks, while reducing inference latency by approximately three times, by effectively addressing parametric hallucination and insufficient search tool invocation.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04651
- Source paper: https://arxiv.org/abs/2604.04651
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04651v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04651v1.png
- GitHub: https://github.com/yizhou0409/Agentic-Rag
- GitHub stars: 0
- Paper ID: 2604.04651
- Canonical ID: 2604.04651v1
- Paper group ID: 019d6679-9bee-75ef-9b34-2727092d4707
- Version ID: 019d6679-9c17-75c6-a31e-f560a13572dc
- Version: v1
- Version order: 1
- Published at: 2026-04-06T13:00:38+00:00
- First published at: 2026-04-06T13:00:38+00:00
- Updated at: 2026-04-07T05:45:39.054000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yizhou Liu
- Qi Sun
- Yulin Chen
- Siyue Zhang
- Chen Zhao

## Topics

- agents
- Computer Science
- cs.AI
- fine-tuning
- information-extraction
- knowledge-distillation
- lightweight-models
- reasoning
- text-generation
- tool-use

## Metrics

- Visits (all): 73
- Visits (last 7 days): 73
- Total votes: 1
- Public total votes: 9
- X likes: 0

## Abstract

Agents equipped with search tools have emerged as effective solutions for knowledge-intensive tasks. While Large Language Models (LLMs) exhibit strong reasoning capabilities, their high computational cost limits practical deployment for search agents. Consequently, recent work has focused on distilling agentic behaviors from LLMs into Small Language Models (SLMs). Through comprehensive evaluation on complex multi-hop reasoning tasks, we find that despite possessing less parametric knowledge, SLMs invoke search tools less frequently and are more prone to hallucinations. To address this issue, we propose \policy, a lightweight fine-tuning approach that explicitly trains SLMs to reliably retrieve and generate answers grounded in retrieved evidence. Compared to agent distillation from LLMs, our approach improves performance by 17.3 scores on Bamboogle and 15.3 scores on HotpotQA, achieving LLM-level results across benchmarks. Our further analysis reveals that adaptive search strategies in SLMs often degrade performance, highlighting the necessity of consistent search behavior for reliable reasoning.

## Problem

- Large Language Models (LLMs) are computationally expensive for search agent tasks, hindering practical deployment due to high latency and cost.
- Small Language Models (SLMs) struggle with knowledge-intensive tasks, exhibiting "parametric hallucination" by relying on limited internal knowledge and "under-searching" by failing to invoke external tools frequently.
- Traditional agentic distillation methods for SLMs yield only marginal improvements, as LLM-generated trajectories implicitly depend on parametric knowledge unavailable to smaller models.

## Method

- Introduced the "Always-Search Policy" (ASP), a distillation paradigm that explicitly trains Small Language Models (SLMs) to consistently invoke external search tools.
- Implemented ASP through Supervised Fine-Tuning (SFT-ASP) and On-Policy Distillation (OPD with ASP), filtering teacher trajectories to enforce evidence grounding and tool usage.
- Designed specific system prompts to instruct SLMs to behave as "Knowledge-Free" agents, always searching for and grounding essential information externally.

## Results

- The "Always-Search Policy" (ASP) improved Small Language Model (SLM) performance, increasing String-F1 on Bamboogle by 17.4 points (from 53.2 to 70.6) and on HotpotQA by 9.7 points (from 47.9 to 57.6) for Qwen3-1.7B, achieving performance comparable to Qwen3-8B.
- ASP-trained SLMs demonstrated an approximately three-fold reduction in end-to-end inference latency compared to a Qwen3-32B Large Language Model, while closing the performance gap to within roughly 2.5 F1 points on benchmarks like Bamboogle.
- ASP effectively increased search tool invocation frequency (e.g., up to 2.84 searches per question for OPD-ASP) and enhanced robustness to noisy retrieval, resulting in smaller performance drops (2.3 vs. 12.1 points) than standard-distilled models.

## Takeaways

- The primary bottlenecks for Small Language Models (SLMs) in agentic search are parametric hallucination and insufficient search tool invocation, rather than reasoning ability once evidence is provided.
- Explicitly enforcing an "Always-Search Policy" during distillation, rather than merely imitating teacher trajectories, is crucial for SLMs to effectively ground answers in external evidence.
- Adaptive search strategies, where SLMs attempt to self-answer based on internal confidence, are detrimental to their performance due to unreliable internal knowledge, unlike for larger models.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6679-9bee-75ef-9b34-2727092d4707/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6679-9bee-75ef-9b34-2727092d4707/transcript.json

## Resources

- GitHub repository: https://github.com/yizhou0409/Agentic-Rag

## Similar Papers

- ZeroSearch: Incentivize the Search Capability of LLMs without Searching (2505.04588v2): A framework called ZEROSEARCH enables training large language models (LLMs) to leverage search capabilities by replacing costly real-world search engine APIs with a simulated LLM environment. This approach from Alibaba Group's Tongyi Lab achieves superior performance while substantially reducing training costs.
- R1-Searcher: Incentivizing the Search Capability in LLMs via  Reinforcement Learning (2503.05592v2): R1-Searcher, from Renmin University of China, introduces a two-stage outcome-based reinforcement learning framework that enables Large Language Models to autonomously invoke and leverage external search systems. This approach significantly outperforms strong RAG baselines on multi-hop question answering benchmarks and demonstrates robust generalization to out-of-domain and online search scenarios.
- Distilling LLM Agent into Small Models with Retrieval and Code Tools (2505.17612v2): Researchers from KAIST, University of Wisconsin-Madison, and KRAFTON developed Agent Distillation, a framework that transfers advanced tool-using and interactive reasoning capabilities from large language model agents to small language models. This approach enables sLMs to achieve performance comparable to much larger models on complex factual and mathematical tasks.
- SSRL: Self-Search Reinforcement Learning (2508.10874v1): Self-Search Reinforcement Learning (SSRL) allows large language models to act as internal search engines during training, significantly reducing the reliance on costly external search engines. This method improves training efficiency by 5.53x compared to prior approaches and demonstrates effective generalization to real-world search scenarios during inference.
- Reinforced Internal-External Knowledge Synergistic Reasoning for  Efficient Adaptive Search Agent (2505.07596v1): A reinforcement learning framework enables large language models to efficiently combine internal and external knowledge through adaptive search strategies, reducing retrieval frequency while maintaining or improving performance across multiple knowledge-intensive reasoning tasks through a novel knowledge-boundary aware reward function.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
