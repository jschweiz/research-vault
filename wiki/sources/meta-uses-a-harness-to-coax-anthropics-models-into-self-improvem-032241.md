---
id: page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
page_type: source-note
title: Meta uses a harness to coax Anthropic’s models into self-improvement
aliases:
- Meta uses a harness to coax Anthropic’s models into self-improvement
source_refs:
- 2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
backlinks:
- page:2026-02-02-jack-clark-import-ai-import-a-idea-6783b26f
- page:2026-02-09-jack-clark-import-ai-gemini-solves-some-erdos-problems-and-illustrate-f0eb84fe
- page:2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
- page:2026-02-09-jack-clark-import-ai-huawei-uses-an-llm-to-automate-the-design-of-hua-1fe2d7d6
- page:2026-03-02-jack-clark-import-ai-what-happens-when-humans-try-to-mess-with-ai-age-c6091226
- page:2026-03-09-jack-clark-import-ai-bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-480da18e
- page:2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
- page:2026-04-06-jack-clark-import-ai-startups-that-adopt-ai-for-internal-use-are-more-1de6e70d
- topic:hyperagent
- topic:self-improvement
updated_at: '2026-04-09T23:10:03.830389Z'
managed: true
---
# Meta uses a harness to coax Anthropic’s models into self-improvement

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2603.19461
- Document kind: paper
- Published at: 2026-03-30T12:28:13+00:00
- Authors: University of British Columbia, Vector Institute, University of Edinburgh, New York University, CIFAR, Meta
- Tags: newsletter, ai, analysis, policy, website, paper, llm, self-improvement, hyperagent, agent, sub-document
- Topics: [Agents](../topics/agents.md), [Hyperagent](../topics/hyperagent.md), [Llm](../topics/llm.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Self Improvement](../topics/self-improvement.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers developed a 'hyperagent' harness that allows Large Language Models (LLMs) to self-improve performance across various tasks by iteratively modifying their prompts and system mechanisms.

## Topic Map

- [Agents](../topics/agents.md)
- [Hyperagent](../topics/hyperagent.md)
- [Llm](../topics/llm.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Self Improvement](../topics/self-improvement.md)

## Related Research

- [COVENANT-72B: Challenging the political economy of AI via distributed training](covenant-72b-challenging-the-political-economy-of-ai-via-distrib-2822a2.md) (shared topics: Llm, Newsletter, Policy)
- [ByteDance finetunes a Seed1.6 model to be a CUDA-writing agent](bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-writing-agent-49e5e1.md) (shared topics: Agents, Llm, Newsletter)
- [What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs](what-happens-when-humans-try-to-mess-with-ai-agents-a-lot-of-con-d0dd0e.md) (shared topics: Agents, Newsletter, Policy)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Agents, Newsletter, Policy)
- [Huawei uses an LLM to automate the design of Huawei chip kernels](huawei-uses-an-llm-to-automate-the-design-of-huawei-chip-kernels-b40808.md) (shared topics: Llm, Newsletter, Policy)
- [Google paper suggests that LLMs simulate multiple personalities to answer questions](google-paper-suggests-that-llms-simulate-multiple-personalities--911861.md) (shared topics: Agents, Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Meta uses a harness to coax Anthropic’s models into self-improvement

Source newsletter: Import AI 451: Political superintelligence; Google’s society of minds, and a robot drummer
Source issue: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer
Published At: 2026-03-30T12:28:13+00:00
Canonical URL: https://arxiv.org/abs/2603.19461

## Newsletter Context

…Give an LLM some tools and a recursive loop and the ability to edit its harness, step back, and let the magic happen… Researchers with the University of British Columbia, Vector Institute, University of Edinburgh, New York University, CIFAR, and Meta have built a harness for LLMs that has the ability to self-improve performance for arbitrary tasks. The approach is called a hyperagent, and it means giving an LLM a scaffold that can iteratively improve the prompts it uses to bootstrap its performance on tasks as well as the system it uses to get better at generating future prompts. Hyperagents work over generations, so one hyperagent begets a few hyperagents and the ones which do the best on the task will themselves spawn some more hyperagents, forming multiple layers of AI genealogy until performance is saturated.

Cyberpunk name of the year award: Hyperagent is actually short for “Darwin Godel Machine Hyperagents”: Besides the research being cool, my congratulations to the authors on coming up with a name I’d love to see chiseled into the moon by a laserbeam wielded by a superintelligence.

How hyperagents work : Hyperagents are “self-referential agents that integrate a task agent (which solves the target task) and a meta agent (which modifies itself and the task agent) into a single editable program. Crucially, the meta-level modification procedure is itself editable, enabling metacognitive self-modification, improving not only task-solving behavior, but also the mechanism that generates future improvements,” the researchers write. “This initial hyperagent is equipped with two tools: a bash tool for executing shell commands, and a specialized tool for inspecting and modifying files.”

Testing the agents in four different domains: The authors test out hyperagents by applying them to four problems – coding (polyglot), prediction (paper review), robotics (robotics reward design), and math understanding (olympiad-level math grading). For most problems, the Hyperagents use Claude Sonnet 4.5 as their base model, with one exception (Polyglot). Evaluations are done via several different models: o3-mini (Polyglot), GPT-4o (paper review), Claude Sonnet 4.5 (robotics reward design), and o4-mini (IMO-level grading). In all cases, the hyperagent approach improves performance significantly above the baseline.

- Polyglot: “the agent is given a code repository and a natural language instruction describing a desired change, and must modify the repository accordingly”. Results: “Across 5 runs, the DGM-H improves its training performance on the 50-task Polyglot subset from 0.140 (the initial agent) to 0.340 (CI: 0.300 – 0.380).”

- Paper review: “For each task, the agent is given the full text of an AI research paper and must predict a binary accept/reject decision”. Results: “On test tasks, DGM-H improves paper review performance from 0.0 (the initial agent) to 0.710 (CI: 0.590 – 0.750)”

- Robotics reward design: “Given a natural language description of a robotics task, an agent must generate a suitable reward function. This reward function is then used to train a quadruped robot in simulation using RL” Results : “DGM-H improves performance from 0.060 (the initial agent) to 0.372 (CI: 0.355 – 0.436), surpassing the default reward function that directly optimizes the evaluation metric (0.348)”

Why this matters – bootstrapping the singularity: Papers like this show that today’s AI systems are already capable of autonomously improving their performance when given the right scaffold and starting ingredients. An interesting
