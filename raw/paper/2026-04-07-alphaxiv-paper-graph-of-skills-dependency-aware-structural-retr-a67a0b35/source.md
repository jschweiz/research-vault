---
id: 2026-04-07-alphaxiv-paper-graph-of-skills-dependency-aware-structural-retr-a67a0b35
kind: paper
title: 'Graph of Skills: Dependency-Aware Structural Retrieval for Massive Agent Skills'
source_url: https://www.alphaxiv.org/abs/2604.05333
source_name: alphaXiv Papers
authors:
- Dawei Li
- Zongxia Li
- Hongyang Du
- Xiyang Wu
- Shihang Gui
- Yongbei Kuang
- Lichao Sun
published_at: '2026-04-07T02:09:11Z'
ingested_at: '2026-04-09T10:02:14.376052Z'
content_hash: 45b2cc829f954d442b8f88e781e1da41cc10dca14d722f26ac97d5c0352e8db4
identity_hash: e9c91c74185a2d12abdbebba21c7e0ab06cda040f40be78a2fbdc1825bb3aba8
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- Computer Science
- cs.AI
- graph-neural-networks
- inference-optimization
- optimization-methods
- tool-use
- transformers
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
external_key: https://www.alphaxiv.org/abs/2604.05333
canonical_url: https://www.alphaxiv.org/abs/2604.05333
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:02:14.376056Z'
short_summary: Graph of Skills (GoS) improves the performance and efficiency of Large Language Model agents when utilizing extensive skill libraries by implementing a dependency-aware structural retrieval layer. This method consistently yielded a 43.6% higher average reward and 37.8% reduction in input tokens compared to full-loading baselines, effectively overcoming limitations like context window saturation and the 'prerequisite gap' in semantic skill retrieval.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Graph of Skills: Dependency-Aware Structural Retrieval for Massive Agent Skills

## alphaXiv Summary

Graph of Skills (GoS) improves the performance and efficiency of Large Language Model agents when utilizing extensive skill libraries by implementing a dependency-aware structural retrieval layer. This method consistently yielded a 43.6% higher average reward and 37.8% reduction in input tokens compared to full-loading baselines, effectively overcoming limitations like context window saturation and the 'prerequisite gap' in semantic skill retrieval.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05333
- Source paper: https://arxiv.org/abs/2604.05333
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05333v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05333v1.png
- GitHub: https://github.com/davidliuk/graph-of-skills
- GitHub stars: 3
- Paper ID: 2604.05333
- Canonical ID: 2604.05333v1
- Paper group ID: 019d6b83-5091-782b-b8e7-6c70a2cb0ca0
- Version ID: 019d6b83-50c2-7f93-afaf-05135067013e
- Version: v1
- Version order: 1
- Published at: 2026-04-07T02:09:11+00:00
- First published at: 2026-04-07T02:09:11+00:00
- Updated at: 2026-04-08T05:14:21.201000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Dawei Li
- Zongxia Li
- Hongyang Du
- Xiyang Wu
- Shihang Gui
- Yongbei Kuang
- Lichao Sun

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.AI
- graph-neural-networks
- inference-optimization
- optimization-methods
- tool-use
- transformers

## Metrics

- Visits (all): 18
- Visits (last 7 days): 18
- Total votes: 2
- Public total votes: 3
- X likes: 0

## Abstract

Skill usage has become a core component of modern agent systems and can substantially improve agents' ability to complete complex tasks. In real-world settings, where agents must monitor and interact with numerous personal applications, web browsers, and other environment interfaces, skill libraries can scale to thousands of reusable skills. Scaling to larger skill sets introduces two key challenges. First, loading the full skill set saturates the context window, driving up token costs, hallucination, and latency.
In this paper, we present Graph of Skills (GoS), an inference-time structural retrieval layer for large skill libraries. GoS constructs an executable skill graph offline from skill packages, then at inference time retrieves a bounded, dependency-aware skill bundle through hybrid semantic-lexical seeding, reverse-weighted Personalized PageRank, and context-budgeted hydration. On SkillsBench and ALFWorld, GoS improves average reward by 43.6% over the vanilla full skill-loading baseline while reducing input tokens by 37.8%, and generalizes across three model families: Claude Sonnet, GPT-5.2 Codex, and MiniMax. Additional ablation studies across skill libraries ranging from 200 to 2,000 skills further demonstrate that GoS consistently outperforms both vanilla skills loading and simple vector retrieval in balancing reward, token efficiency, and runtime.

## Problem

- Large skill libraries lead to context window saturation, increased token costs, and higher latency for LLM agents when the entire library is loaded.
- Purely semantic skill retrieval often suffers from a 'prerequisite gap,' failing to retrieve all functionally necessary skills (e.g., parsers, converters) that are semantically distant from the primary task query.
- Agents struggle with multi-step tasks when provided with incomplete or noisy skill sets, leading to lower task completion rates and inefficient planning.

## Method

- An offline phase constructs a typed directed graph from the local skill corpus, normalizing skills into nodes and inducing dependency, workflow, semantic, and alternative relations as edges.
- An online structural retrieval phase employs hybrid seed retrieval (combining semantic and lexical scores) and reverse-aware typed diffusion on the graph to identify relevant skills.
- A budgeted reranking and hydration step materializes a compact, execution-complete skill bundle, prioritizing skills based on combined diffusion and query evidence scores, while adhering to context limits.

## Results

- GoS consistently achieved the highest average reward across all benchmarks and LLM models, improving average reward by 43.6% compared to the Vanilla Skills baseline and outperforming Vector Skills in every tested scenario.
- The method significantly enhanced efficiency, reducing input token usage by 37.8% on average compared to Vanilla Skills while maintaining similar token efficiency to Vector Skills, and also reduced agent runtime in most configurations.
- GoS demonstrated improved scalability, with its performance advantage over baselines increasing with skill library size, notably between 500 and 2,000 skills, confirming its effectiveness for large-scale agent skill management.

## Takeaways

- Explicitly modeling and leveraging dependency and workflow structures via a graph is crucial for retrieving functionally complete skill bundles, overcoming the 'prerequisite gap' of semantic-only methods.
- A hybrid approach combining both semantic and lexical signals for initial skill seeding significantly improves the quality of candidate skills before graph-based expansion.
- Reverse-aware graph diffusion effectively propagates relevance from high-level matched skills back to their essential prerequisites, ensuring that necessary but semantically weak skills are included.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b83-5091-782b-b8e7-6c70a2cb0ca0/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b83-5091-782b-b8e7-6c70a2cb0ca0/transcript.json

## Resources

- GitHub repository: https://github.com/davidliuk/graph-of-skills

## Similar Papers

- SkillRL: Evolving Agents via Recursive Skill-Augmented Reinforcement Learning (2602.08234v1): Researchers from the University of North Carolina at Chapel Hill and collaborators developed SKILLRL, a framework enabling Large Language Model (LLM) agents to learn and recursively evolve abstract skills from diverse experiences. SKILLRL achieves state-of-the-art performance with a 89.9% success rate on ALFWorld, 72.7% on WebShop, and an average score of 47.1% on search-augmented QA tasks, outperforming larger closed-source models and memory-augmented baselines.
- InstructRAG: Leveraging Retrieval-Augmented Generation on Instruction  Graphs for LLM-Based Task Planning (2504.13032v1): A multi-agent meta-reinforcement learning framework called InstructRAG enhances LLM-based task planning through graph-structured instruction paths and specialized agents for path retrieval and prompt generation, improving success rates across datasets like HotpotQA, ALFWorld, and Webshop while enabling effective transfer to new tasks.
- SkillsBench: Benchmarking How Well Agent Skills Work Across Diverse Tasks (2602.12670v3): Researchers introduced SkillsBench, a benchmark to evaluate how effectively "Agent Skills" augment large language model (LLM) agents, measuring performance across diverse tasks and agent-model configurations. The benchmark found that curated Skills improved average agent performance by +16.2 percentage points and can enable smaller LLMs to match the performance of larger models operating without Skills.
- Inducing Programmatic Skills for Agentic Tasks (2504.06821v2): Agent Skill Induction (ASI) is a framework that allows large language model (LLM) agents to autonomously learn and verify executable programmatic skills directly from successful task completions in web environments. This method significantly enhances task success rates and operational efficiency compared to agents relying on static instructions or unverified textual skills.
- SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization (2604.02268v1): The SKILL0 framework introduces In-Context Reinforcement Learning (ICRL) to enable Large Language Model (LLM) agents to internalize skills into their parameters, thereby achieving autonomous behavior without external skill descriptions at inference time. This approach yielded superior performance, such as an 87.9% success rate on ALFWorld (+9.7% over AgentOCR), while substantially reducing context token costs by over 5 times compared to skill-augmented methods.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
