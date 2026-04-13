---
id: page:2026-03-02-jack-clark-import-ai-llms-are-still-very-bad-at-videogames-4b8298cd
page_type: source-note
title: LLMs are still very bad at videogames
aliases:
- LLMs are still very bad at videogames
source_refs:
- 2026-03-02-jack-clark-import-ai-llms-are-still-very-bad-at-videogames-4b8298cd
backlinks:
- page:2026-02-02-jack-clark-import-ai-one-way-of-seeing-ai-progress-how-hard-its-getti-b88405ad
- page:2026-02-09-jack-clark-import-ai-ai-based-chip-design-is-harder-than-you-think-an-333f3a92
- page:2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
- page:2026-02-16-jack-clark-import-ai-can-ai-agents-independently-do-basic-ai-research-3ef778a6
- page:2026-02-16-jack-clark-import-ai-math-researchers-see-if-ai-can-help-solve-their--da564141
- page:2026-02-23-jack-clark-import-ai-chinese-researchers-try-to-build-a-truly-compreh-8bac5c2d
- page:2026-02-23-jack-clark-import-ai-llms-are-more-trigger-happy-than-humans-in-a-nuc-12330914
- page:2026-02-23-jack-clark-import-ai-want-to-make-ai-go-better-figure-out-how-to-meas-dcb9a008
- page:2026-03-02-jack-clark-import-ai-ais-can-teach-people-anything-including-how-to-g-39df0bb2
- page:2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
- page:2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
- page:2026-03-30-jack-clark-import-ai-how-long-will-a-new-math-benchmark-horizonmath-l-19e5f6c5
- topic:videogames
updated_at: '2026-04-09T23:10:02.694711Z'
managed: true
---
# LLMs are still very bad at videogames

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://p5.js/
- Document kind: article
- Published at: 2026-03-02T13:45:27+00:00
- Authors: MIT, Harvard, University of British Columbia, Princeton University, University of Cambridge, Universitat Politècnica de València
- Tags: newsletter, ai, analysis, policy, website, article, llms, videogames, benchmark, evaluation, sub-document
- Topics: [Evaluations](../topics/evaluations.md), [Llms](../topics/llms.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Sub Document](../topics/sub-document.md), [Videogames](../topics/videogames.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers developed AI GAMESTORE, a benchmark testing how well AI models perform compared to humans at playing simple games. The results show that state-of-the-art LLMs significantly underperform human baselines in these tasks.

## Topic Map

- [Evaluations](../topics/evaluations.md)
- [Llms](../topics/llms.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Sub Document](../topics/sub-document.md)
- [Videogames](../topics/videogames.md)

## Related Research

- [Can LLMs autonomously refine other LLMs for new tasks? Somewhat.](can-llms-autonomously-refine-other-llms-for-new-tasks-somewhat-738c53.md) (shared topics: Evaluations, Llms, Newsletter, Policy)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [AI-based chip design is harder than you think and benchmarks might be too easy](ai-based-chip-design-is-harder-than-you-think-and-benchmarks-mig-6b8331.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [One way of seeing AI progress – how hard it’s getting to design technical interviews](one-way-of-seeing-ai-progress-how-hard-its-getting-to-design-tec-cfca46.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [Good Taste the Only Real Moat Left](good-taste-the-only-real-moat-left-825f84.md) (shared topics: Llms, Newsletter, Sub Document)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy, Sub Document)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# LLMs are still very bad at videogames

Source newsletter: Import AI 447: The AGI economy; testing AIs with generated games; and agent ecologies
Source issue: https://jack-clark.net/2026/03/02/import-ai-447-the-agi-economy-testing-ais-with-generated-games-and-agent-ecologies
Published At: 2026-03-02T13:45:27+00:00
Canonical URL: https://p5.js/

## Newsletter Context

…GAMESTORE highlights a dumb side of modern AI, as well as suggesting a new way to build benchmarks… Researchers with MIT, Harvard, the University of British Columbia, Princeton University, the University of Cambridge, and the Universitat Politècnica de València, have built and released AI GAMESTORE, a benchmark that tests out how well AIs can do compared to humans at playing simple games found on the web. The results are pretty damning for the AI systems, with “state-of-the-art models achieving less than 30% of the human baseline on average, while taking 15-20x more time to compute than humans”.

What AI GAMESTORE is: AI GAMESTORE is a set of 100 games, which are simplified and recreated versions of popular games that people play. AI GAMESTORE was built by the authors sampling 7,500 games from the App Store, then filtering down to only those with 10,000+ reviews and a 4.5+ rating. After this, they further filtered the games using Gemini Flash 2.5, which assessed 1) whether the games can be played within a few minutes, 2) can be built in p5.js , 3) can have a quantifiable way of viewing performance, and 4) do not require extensive game-specific knowledge (e.g., poker). AI makes games to test AI: Following this, they use Claude 4.5 Sonnet to read the descriptions and other data to make a simplified version of each game in p5.js , then this game is tested for playability, then refined by a human playing the game and iteratively prompting an LLM to improve it. “Each refinement step takes about 2 minutes. On average, this process took 4.7 refinement steps for all 100 generated games,” they write. “The end-to-end process of generating and refining a new game with human-in-the-loop can be completed in approximately 30 minutes on average”.

Labeling for skills: Each finalized game is labeled by humans with a particular emphasis on the types of cognitive demand the games entail. These labels are: VP = Visual Processing; ST = Spatial-temporal Coordination; ME = Memory; PL = Planning; WM = World Model Learning; PH = Physical Reasoning; SO = Social Reasoning.

Cutting edge LLMs are very bad at this: The authors compare the performance of roughly ~100 humans against the performance of several cutting edge LLMs on the corpus. LLMs studied include: GPT-5.2, GPT-5-Mini, Gemini-2.5-Flash, Claude-Opus-4.5, Qwen-VL-32B, and LLama-4-Maverick. “While the evaluated models demonstrate the ability to navigate and interact with most game environments, a substantial performance gap remains between AI agents and human participants”, the researchers write. “State-of-the-art models like GPT-5.2, GEMINI-2.5-PRO, and CLAUDE-OPUS-4.5, all achieve geometric mean scores of less than 10% of the human baseline”. And it gets worse the more you look: The LLMs are also playing with advantages that humans don’t get – each human got 120 seconds to play each game, while each LLM got the same time, but they’re so bad at vision and low-latency control that the researchers gave them a crutch: “We pause the game every second to query the model to elicit five lists of actions to perform in the next second, with each action list corresponding to a 0.2 second segment of gameplay. Upon receiving the model response, the game is resumed and the actions are applied. The loop continues until the game is won or it reaches 2 minutes of game play (120 API calls). When you factor this in, the models look worse than humans on this dimension of time: “This is because the models spend a few minutes thinking, in addition to typically a few seconds of response latency per query; as a result, many models spend at least 20 mi
