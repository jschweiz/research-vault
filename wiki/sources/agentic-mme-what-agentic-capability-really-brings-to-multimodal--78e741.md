---
id: page:2026-04-03-alphaxiv-paper-agentic-mme-what-agentic-capability-really-bring-688666ad
page_type: source-note
title: Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?
aliases:
  - Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?
source_refs:
  - 2026-04-03-alphaxiv-paper-agentic-mme-what-agentic-capability-really-bring-688666ad
backlinks:
updated_at: 2026-04-08T07:14:48.047158Z
managed: true
---
# Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence?

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.03016
- Document kind: paper
- Published at: 2026-04-03T13:02:01+00:00
- Authors: Qianshan Wei, Yishan Yang, Siyi Wang, Jinglin Chen, Binyu Wang, Jiaming Wang
- Tags: paper, alphaxiv, research, agentic-frameworks, agents, computer science, cs.ai, data-curation, model-observability, multi-modal-learning
- Topics: [Agents](../topics/agents.md), [Evaluations](../topics/evaluations.md), [Search](../topics/search.md), [Multimodal](../topics/multimodal.md), [Agentic Frameworks](../topics/agentic-frameworks.md), [Artificial Intelligence](../topics/artificial-intelligence.md)
- Trend score: 54.82
- Novelty score: 6.80

## Summary

# Agentic-MME: What Agentic Capability Really Brings to Multimodal Intelligence? ## alphaXiv Summary Agentic-MME introduces a process-verified benchmark for assessing how multimodal large language models coordinate visual manipulation and open-web search tools to solve complex, real-world problems.

## Topic Map

- [Agents](../topics/agents.md)
- [Evaluations](../topics/evaluations.md)
- [Search](../topics/search.md)
- [Multimodal](../topics/multimodal.md)
- [Agentic Frameworks](../topics/agentic-frameworks.md)
- [Artificial Intelligence](../topics/artificial-intelligence.md)

## Related Research

- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Agentic Frameworks, Agents, Artificial Intelligence)
- [Memory Intelligence Agent](memory-intelligence-agent-7ffa81.md) (shared topics: Agentic Frameworks, Agents, Artificial Intelligence)
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](coral-towards-autonomous-multi-agent-evolution-for-open-ended-di-462c70.md) (shared topics: Agentic Frameworks, Agents, Artificial Intelligence)
- [Vero: An Open RL Recipe for General Visual Reasoning](vero-an-open-rl-recipe-for-general-visual-reasoning-a332b2.md) (shared topics: Agents, Evaluations)
- [OpenWorldLib: A Unified Codebase and Definition of Advanced World Models](openworldlib-a-unified-codebase-and-definition-of-advanced-world-187d2a.md) (shared topics: Agents, Multimodal)
- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Agents, Artificial Intelligence)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
- Designed tasks with increasing difficulty, culminating in Level 3 scenarios demanding iterative, interleaved execution and synergistic coupling of visua
