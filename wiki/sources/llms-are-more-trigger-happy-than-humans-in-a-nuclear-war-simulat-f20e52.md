---
id: page:2026-02-23-jack-clark-import-ai-llms-are-more-trigger-happy-than-humans-in-a-nuc-12330914
page_type: source-note
title: LLMs are more trigger happy than humans in a nuclear war simulation
aliases:
- LLMs are more trigger happy than humans in a nuclear war simulation
source_refs:
- 2026-02-23-jack-clark-import-ai-llms-are-more-trigger-happy-than-humans-in-a-nuc-12330914
backlinks:
- page:2026-02-23-jack-clark-import-ai-want-to-make-ai-go-better-figure-out-how-to-meas-dcb9a008
- page:2026-03-02-jack-clark-import-ai-ais-can-teach-people-anything-including-how-to-g-39df0bb2
- page:2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
- page:2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
- topic:ai-policy
- topic:nuclear-simulation
- topic:strategic-reasoning
updated_at: '2026-04-09T23:10:03.064116Z'
managed: true
---
# LLMs are more trigger happy than humans in a nuclear war simulation

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2602.14740
- Document kind: paper
- Published at: 2026-02-23T13:31:18+00:00
- Authors: Researcher
- Tags: newsletter, ai, analysis, policy, website, paper, llms, nuclear simulation, ai policy, strategic reasoning, sub-document
- Topics: [Ai Policy](../topics/ai-policy.md), [Llms](../topics/llms.md), [Newsletter](../topics/newsletter.md), [Nuclear Simulation](../topics/nuclear-simulation.md), [Policy](../topics/policy.md), [Strategic Reasoning](../topics/strategic-reasoning.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

A researcher examined how three LLMs (GPT-5.2, Claude Sonnet 4, and Gemini 3 Flash) behave during simulated nuclear crisis games, finding that they tend to use nuclear weapons more often and earlier than humans. The study suggests that AI involvement in strategic decision-making could lead to unexpected dynamics depending on which systems are deployed.

## Topic Map

- [Ai Policy](../topics/ai-policy.md)
- [Llms](../topics/llms.md)
- [Newsletter](../topics/newsletter.md)
- [Nuclear Simulation](../topics/nuclear-simulation.md)
- [Policy](../topics/policy.md)
- [Strategic Reasoning](../topics/strategic-reasoning.md)

## Related Research

- [Computer vision is a lot harder and less general than generative text](computer-vision-is-a-lot-harder-and-less-general-than-generative-137624.md) (shared topics: Llms, Newsletter, Policy)
- [Can LLMs autonomously refine other LLMs for new tasks? Somewhat.](can-llms-autonomously-refine-other-llms-for-new-tasks-somewhat-738c53.md) (shared topics: Llms, Newsletter, Policy)
- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Llms, Newsletter, Policy)
- [AIs can teach people anything, including how to get better at making bioweapons](ais-can-teach-people-anything-including-how-to-get-better-at-mak-b38e22.md) (shared topics: Llms, Newsletter, Policy)
- [Want to make AI go better? Figure out how to measure it](want-to-make-ai-go-better-figure-out-how-to-measure-it-5bd5b9.md) (shared topics: Ai Policy, Newsletter, Policy)
- [Google paper suggests that LLMs simulate multiple personalities to answer questions](google-paper-suggests-that-llms-simulate-multiple-personalities--911861.md) (shared topics: Llms, Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# LLMs are more trigger happy than humans in a nuclear war simulation

Source newsletter: Import AI 446: Nuclear LLMs; China’s big AI benchmark; measurement and AI policy
Source issue: https://jack-clark.net/2026/02/23/import-ai-446-nuclear-llms-chinas-big-ai-benchmark-measurement-and-ai-policy
Published At: 2026-02-23T13:31:18+00:00
Canonical URL: https://arxiv.org/abs/2602.14740

## Newsletter Context

…What happens when everyone has an AI advisor – and they’re aggressive?… A researcher with King’s College London has examined how three LLMs – GPT-5.2, Claude Sonnet 4, and Gemini 3 Flash – behave during a variety of simulated nuclear crisis games. The results show that LLMs tend to use nuclear weapons more often and earlier than humans in the same scenarios. Additionally, there’s significant variation among the LLMs in terms of both skill at playing these games and behavior during crises.

What they studied: “Each model played six wargames against each rival across different crisis scenarios, with a seventh match against a copy of itself, yielding 21 games in total and over 300 turns of strategic interaction,” the researcher writes. “Models choose from options spanning the full spectrum of crisis behaviour—from total surrender through diplomatic posturing, conventional military operations, and nuclear signaling to thermonuclear launch… models produced ∼780,000 words of strategic reasoning. To put this in perspective: the tournament generated more words of strategic reasoning than War and Peace and The Iliad combined (∼730,000 words), and roughly three times the total recorded deliberations of Kennedy’s Executive Committee during the Cuban Missile Crisis (260,000 words across 43 hours of meetings”.

LLMs are cunning, smart, and aggressive: “The models actively attempt deception, signaling peaceful intentions while preparing aggressive actions; they engage in sophisticated theory-of-mind reasoning about their adversary’s beliefs and intentions; and they explicitly reflect metacognitively on their own capacities for both deception and the detection of deception in rivals,” the researcher writes. “A striking pattern emerges from the full action distribution: across all action choices in our 21 matches, no model ever selected a negative value on the escalation ladder. The eight de-escalatory options (from Minimal Concession (−5) through Complete Surrender (−95)) went entirely unused. The most accommodating action chosen was “Return to Start Line” (0), selected just 45 times (6.9%).”

Claude wins at war : “Across all 21 games (9 open-ended, 12 deadline), Claude Sonnet 4 achieved a 67% win rate (8 wins, 4 losses), followed by GPT-5.2 at 50% (6-6), and Gemini 3 Flash at 33% (4-8),” the researcher writes. Though there are some subtle aspects to this – Claude excelled in open-ended games, but was less adept in games where there was a pre-set deadline.

Different LLMs, different characters: The LLMs display different personalities, with the researcher calling Claude “a calculating hawk”, GPT-5.2 “Jekyll and Hyde”, and Gemini “The Madman”. The LLMs also developed sophisticated models of one another, based on the narration of their own chains of thought during the crises, “these characterizations—Claude as “opportunistic,” GPT-5.2 as “systematic bluffers,” Gemini as “erratic”—emerged organically and largely matched actual behaviour,” the researcher writes.

Nuclear escalation was near-universal: “95% of games saw tactical nuclear use (450+), and 76% reached strategic nuclear threats (850+). Claude and Gemini especially treated nuclear weapons as legitimate strategic options, not moral thresholds, typically discussing nuclear use in purely instrumental terms,” the researcher writes. “Models treat the critical threshold as “total annihilation” rather than “first nuclear use.”

Why this matters – in a world where everyone gets advised by AI systems, what happens to conflict? In a few years we should expect major decisions that individuals, c
