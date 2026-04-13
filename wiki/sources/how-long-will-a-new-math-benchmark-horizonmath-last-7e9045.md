---
id: page:2026-03-30-jack-clark-import-ai-how-long-will-a-new-math-benchmark-horizonmath-l-19e5f6c5
page_type: source-note
title: How long will a new math benchmark, HorizonMath, last?
aliases:
- How long will a new math benchmark, HorizonMath, last?
source_refs:
- 2026-03-30-jack-clark-import-ai-how-long-will-a-new-math-benchmark-horizonmath-l-19e5f6c5
backlinks:
- topic:automated-verification
- topic:evaluations
- topic:gpt-5-4-pro
- topic:math-benchmark
- topic:mathematics
updated_at: '2026-04-09T23:10:03.844937Z'
managed: true
---
# How long will a new math benchmark, HorizonMath, last?

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2603.15617
- Document kind: paper
- Published at: 2026-03-30T12:28:13+00:00
- Authors: University of Oxford, Harvard University, Princeton University, Ellison Institute of Technology
- Tags: newsletter, ai, analysis, policy, website, paper, math benchmark, mathematics, automated verification, gpt 5.4 pro, sub-document
- Topics: [Math Benchmark](../topics/math-benchmark.md), [Evaluations](../topics/evaluations.md), [Automated Verification](../topics/automated-verification.md), [Gpt 5 4 Pro](../topics/gpt-5-4-pro.md), [Mathematics](../topics/mathematics.md), [Newsletter](../topics/newsletter.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

HorizonMath is a new math benchmark designed to test AI systems on solving unknown mathematical problems, featuring automated verification and covering various mathematical domains.

## Topic Map

- [Math Benchmark](../topics/math-benchmark.md)
- [Evaluations](../topics/evaluations.md)
- [Automated Verification](../topics/automated-verification.md)
- [Gpt 5 4 Pro](../topics/gpt-5-4-pro.md)
- [Mathematics](../topics/mathematics.md)
- [Newsletter](../topics/newsletter.md)

## Related Research

- [The Mathematical Memory of AI: Understanding Vector Databases and Embedding Pipelines](the-mathematical-memory-of-ai-understanding-vector-databases-and-ddb3fb.md) (shared topics: Mathematics, Newsletter)
- [Can LLMs autonomously refine other LLMs for new tasks? Somewhat.](can-llms-autonomously-refine-other-llms-for-new-tasks-somewhat-738c53.md) (shared topics: Evaluations, Newsletter)
- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Evaluations, Newsletter)
- [Want to make AI go better? Figure out how to measure it](want-to-make-ai-go-better-figure-out-how-to-measure-it-5bd5b9.md) (shared topics: Evaluations, Newsletter)
- [Chinese researchers try to build a truly comprehensive LLM evaluation system](chinese-researchers-try-to-build-a-truly-comprehensive-llm-evalu-063f83.md) (shared topics: Evaluations, Newsletter)
- [Math researchers see if AI can help solve their private solutions to frontier problems. The answer: Kind of.](math-researchers-see-if-ai-can-help-solve-their-private-solution-0b0950.md) (shared topics: Evaluations, Newsletter)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# How long will a new math benchmark, HorizonMath, last?

Source newsletter: Import AI 451: Political superintelligence; Google’s society of minds, and a robot drummer
Source issue: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer
Published At: 2026-03-30T12:28:13+00:00
Canonical URL: https://arxiv.org/abs/2603.15617

## Newsletter Context

…New test challenges AI systems to solve unknown problems, then automatically verifies the answers… Another day brings another hard math benchmark that I imagine will crumple in the face of ongoing AI progress in the coming year. This time it’s HorizonMath, a benchmark containing 100 “predominantly unsolved” problems across 8 domains in applied and computational mathematics. The benchmark was built by researchers with the University of Oxford, Harvard University, Princeton University, and the Ellison Institute of Technology.

Special features about HorizonMath:

- Contamination-Proof: “Because the solutions are unknown, they do not exist in any training corpus, and any correct solution produced by a model would therefore signal genuine reasoning ability and autonomous discovery.”
- Automated verification : “A core feature of our benchmark is its fully automated, reproducible, and human-free evaluation pipeline”, the authors write. “We automate verification using high-precision numeric comparison and deterministic constraint-checkers”.

What HorizonMath contains: HorizonMath’s 100 problems are classified along three axes: output types, which specifies how the model needs to solve the task ranging from identifying an exact closed-form expression for a numerically approximated target value, to the production of discrete mathematical objects; solvability levels, which span ‘level 0’ (problems with known closed forms) to ‘level 3’ (problems that could be conjectured unsolvable or lack finite closed forms); and mathematical domains, which specifies the type of domain ranging from number theory to discrete geometry to mathematical constants.

Reassuringly hard: On the full dataset, the highest scoring model is GPT 5.4 Pro with 7%, followed by Opus 4.6 and Gemini 3.1 Pro which both tie at 3%. On the “Level 0” (aka, the easiest) problems, GPT 5.4 Pro leads at 50% completion, with both Opus 4.6 and Gemini 3.1 in a tie again at 30% each.

Next steps: They will expand the benchmark in two ways, first by liberalizing the sorts of solutions that they will take in, as well as by “extending beyond the three current problem categories to include open problems that require proof-based verification, integrating with formal systems such as Lean”.

Why this matters – perhaps the first truly creative AI systems will show up in mathematics: AI systems are pushing on the frontiers of math today, with systems like Gemini already helping humans to come up with seemingly original math proofs ( Import AI 441 ), and tests like “First Proof” emerging which examine how well AI systems can handle problems that have never been talked about publicly let alone solved ( Import AI 445 ). With HorizonMath, we have another useful benchmark to help us see if AI is about to cross some ‘creativity rubicon’ and begin solving unsolved problems. Read more : HorizonMath: Measuring AI Progress Toward Mathematical Discovery with Automatic Verification (arXiv) . Get the benchmark here : HorizonMath (GitHub) .

Tech Tales:

Site report [2029]

Percentage of compute and power below ground: 70% (+50 absolute points). Number of staff living fully onsite: 300 (+250). Estimated duration of ‘hard seal’ based on current supplies and a projected population of ~500: 4 months (+3 months). Estimated lead of the project relative to others in-country: 6 months. Capability estimates: 90%-110% of our own leading system.

Recommendation: Based on the substantial increase in resources allocated to hardening the facility for closed-loop development, we believe additional measures must b
