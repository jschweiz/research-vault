---
id: page:2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
page_type: source-note
title: Google paper suggests that LLMs simulate multiple personalities to answer questions
aliases:
- Google paper suggests that LLMs simulate multiple personalities to answer questions
source_refs:
- 2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
backlinks:
- page:2026-02-02-jack-clark-import-ai-import-a-idea-6783b26f
- page:2026-02-23-jack-clark-import-ai-llms-are-more-trigger-happy-than-humans-in-a-nuc-12330914
- page:2026-03-02-jack-clark-import-ai-ais-can-teach-people-anything-including-how-to-g-39df0bb2
- page:2026-03-02-jack-clark-import-ai-chatting-with-ezra-klein-ai-agents-recursive-sel-34591a03
- page:2026-03-02-jack-clark-import-ai-what-happens-when-humans-try-to-mess-with-ai-age-c6091226
- page:2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
- page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
- topic:societies-thought
updated_at: '2026-04-09T23:10:02.632112Z'
managed: true
---
# Google paper suggests that LLMs simulate multiple personalities to answer questions

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2601.10825
- Document kind: paper
- Published at: 2026-02-09T14:03:34+00:00
- Authors: Google
- Tags: newsletter, ai, analysis, policy, website, paper, llms, reasoning, multi-agent, societies of thought, sub-document
- Topics: [Reasoning](../topics/reasoning.md), [Agents](../topics/agents.md), [Llms](../topics/llms.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Societies Thought](../topics/societies-thought.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Google researchers found that LLMs simulate multiple personalities and form 'societies of thought' when solving hard problems, suggesting they develop multi-agent-like interactions in their reasoning chains.

## Topic Map

- [Reasoning](../topics/reasoning.md)
- [Agents](../topics/agents.md)
- [Llms](../topics/llms.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Societies Thought](../topics/societies-thought.md)

## Related Research

- [Meta uses a harness to coax Anthropic’s models into self-improvement](meta-uses-a-harness-to-coax-anthropics-models-into-self-improvem-032241.md) (shared topics: Agents, Newsletter, Policy)
- [Computer vision is a lot harder and less general than generative text](computer-vision-is-a-lot-harder-and-less-general-than-generative-137624.md) (shared topics: Llms, Newsletter, Policy)
- [Can LLMs autonomously refine other LLMs for new tasks? Somewhat.](can-llms-autonomously-refine-other-llms-for-new-tasks-somewhat-738c53.md) (shared topics: Llms, Newsletter, Policy)
- [What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs](what-happens-when-humans-try-to-mess-with-ai-agents-a-lot-of-con-d0dd0e.md) (shared topics: Agents, Newsletter, Policy)
- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Llms, Newsletter, Policy)
- [Chatting with Ezra Klein: AI agents, recursive self-improvement, and the personalities of LLMs](chatting-with-ezra-klein-ai-agents-recursive-self-improvement-an-8329d9.md) (shared topics: Agents, Llms, Newsletter)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Google paper suggests that LLMs simulate multiple personalities to answer questions

Source newsletter: Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench
Source issue: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
Published At: 2026-02-09T14:03:34+00:00
Canonical URL: https://arxiv.org/abs/2601.10825

## Newsletter Context

…The smarter we make language models, the more they tend towards building and manipulating rich, multi-agent world models… When thinking about hard problems, I often find it’s helpful to try and view them from multiple perspectives, especially when it comes to checking my own assumptions and biases. Now, researchers with Google, the University of Chicago, and the Santa Fe Institute, have studied how AI reasoning models work and have concluded they do the same thing, with LLMs seeming to invoke multiple different perspectives in their chains of thought when solving hard problems.

The key finding: In tests on DeepSeek-R1 and QwQ-32B (one wonders why the Google researchers didn’t touch Google models here…) they find that “enhanced reasoning emerges not from extended computation alone, but from the implicit simulation of complex, multi-agent-like interactions—a society of thought—which enables the deliberate diversification and debate among internal cognitive perspectives characterized by distinct personality traits and domain expertise.”

How it works: It appears that different forms of persona and discussion style modeling emerge as a consequence of training models through RL to do reasoning – the results don’t show up on base pre-trained models like DeepSeek v3. The authors find that models embody a variety of conversational styles, including question and answering, perspective shifts, reconciliation, and conflict of perspectives. “In an organic chemistry problem requiring multistep reaction analysis to identify the final product’s structure (i.e., multi-step Diels-Alder synthesis), DeepSeek-R1 exhibits perspective shifts and conflict, expressed through socio-emotional roles such as disagreement, giving opinion, and giving orientation,” they find. Similarly, “In a creative writing trace where the model rewrites the sentence “I flung my hatred into the burning fire,” seven perspectives emerge, including a creative ideator (highest Openness and Extraversion) who generates stylistic alternatives and a semantic fidelity checker (low agreeableness, high neuroticism) who prevents scope creep—“But that adds ‘deep-seated’ which wasn’t in the original”. And in a mathematical puzzle “at step 40, the model produces mechanical, enumerative chain-of-thought-style reasoning, whereas by step 120, two distinctive simulated personas have appeared, recognizing their collectivity with the pronoun “we”— expressing uncertainty (“Again no luck”), considering alternatives (“Maybe we can try using negative numbers”), and reflecting on problem constraints.”

Why this matters: Janus strikes again: Back in September 2022 janus wrote a post on LessWrong saying the correct way to view LLMs was as “simulators”. The post correctly called out many of the phenomena we now experience, where LLMs seem to be coming alive with all kinds of wild behaviors which are best explained by the LLMs learning to model and represent rich concepts to themselves to help them compute answers to our questions. “Calling GPT a simulator gets across that in order to do anything, it has to simulate something,” Janus wrote. “Training a model to predict diverse trajectories seems to make it internalize general laws underlying the distribution, allowing it to simulate counterfactuals that can be constructed from the distributional semantics.”. This Google paper lines up with this, along with other recent findings that as we make LLMs more advanced they both develop richer and more powerful representations of reality, as well as exhibiting a greater ability to model a theory of mind. It all
