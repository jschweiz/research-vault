---
id: page:2026-02-23-jack-clark-import-ai-chinese-researchers-try-to-build-a-truly-compreh-8bac5c2d
page_type: source-note
title: Chinese researchers try to build a truly comprehensive LLM evaluation system
aliases:
- Chinese researchers try to build a truly comprehensive LLM evaluation system
source_refs:
- 2026-02-23-jack-clark-import-ai-chinese-researchers-try-to-build-a-truly-compreh-8bac5c2d
backlinks:
- page:2026-02-09-jack-clark-import-ai-ai-based-chip-design-is-harder-than-you-think-an-333f3a92
- page:2026-02-16-jack-clark-import-ai-math-researchers-see-if-ai-can-help-solve-their--da564141
- page:2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
- page:2026-03-30-jack-clark-import-ai-how-long-will-a-new-math-benchmark-horizonmath-l-19e5f6c5
- topic:llm-evaluation
- topic:risk-assessment
updated_at: '2026-04-09T23:10:02.657555Z'
managed: true
---
# Chinese researchers try to build a truly comprehensive LLM evaluation system

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2602.14135v1
- Document kind: paper
- Published at: 2026-02-23T13:31:18+00:00
- Authors: Beijing Institute of AI Safety and Governance, Beijing Key Laboratory of Safe AI and Superalignment, Chinese Academy of Sciences
- Tags: newsletter, ai, analysis, policy, website, paper, llm evaluation, ai safety, benchmark, risk assessment, sub-document
- Topics: [Evaluations](../topics/evaluations.md), [Ai Safety](../topics/ai-safety.md), [Llm Evaluation](../topics/llm-evaluation.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Risk Assessment](../topics/risk-assessment.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Chinese institutions built the ForesightSafety Bench, a large-scale AI safety evaluation framework covering 94 risk subcategories. The benchmark highlights common AI safety concerns and shows Anthropic models leading in defensive resilience.

## Topic Map

- [Evaluations](../topics/evaluations.md)
- [Ai Safety](../topics/ai-safety.md)
- [Llm Evaluation](../topics/llm-evaluation.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Risk Assessment](../topics/risk-assessment.md)

## Related Research

- [AI-based chip design is harder than you think and benchmarks might be too easy](ai-based-chip-design-is-harder-than-you-think-and-benchmarks-mig-6b8331.md) (shared topics: Evaluations, Llm Evaluation, Newsletter, Policy)
- [Can LLMs autonomously refine other LLMs for new tasks? Somewhat.](can-llms-autonomously-refine-other-llms-for-new-tasks-somewhat-738c53.md) (shared topics: Evaluations, Newsletter, Policy)
- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Evaluations, Newsletter, Policy)
- [Want to make AI go better? Figure out how to measure it](want-to-make-ai-go-better-figure-out-how-to-measure-it-5bd5b9.md) (shared topics: Evaluations, Newsletter, Policy)
- [Superintelligence could save and extend lives, so we should go for it](superintelligence-could-save-and-extend-lives-so-we-should-go-fo-9572f3.md) (shared topics: Ai Safety, Newsletter, Policy)
- [Math researchers see if AI can help solve their private solutions to frontier problems. The answer: Kind of.](math-researchers-see-if-ai-can-help-solve-their-private-solution-0b0950.md) (shared topics: Evaluations, Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Chinese researchers try to build a truly comprehensive LLM evaluation system

Source newsletter: Import AI 446: Nuclear LLMs; China’s big AI benchmark; measurement and AI policy
Source issue: https://jack-clark.net/2026/02/23/import-ai-446-nuclear-llms-chinas-big-ai-benchmark-measurement-and-ai-policy
Published At: 2026-02-23T13:31:18+00:00
Canonical URL: https://arxiv.org/abs/2602.14135v1

## Newsletter Context

…ForesightSafety Bench shows the surprising overlap between East and West on AI safety issues… For all the differences between China and the USA, it’s worth occasionally looking into the cultures of AI evaluation in the two countries and here you tend to discover surprising similarities. This is especially true of ForesightSafety Bench, a large-scale AI safety evaluation framework built by a variety of Chinese institutions that includes the same categories you’d expect to see in any large-scale Western testing framework.

Who built ForesightSafety Bench? The benchmark was built by the Beijing Institute of AI Safety and Governance, the Beijing Key Laboratory of Safe AI and Superalignment, and the Chinese Academy of Sciences.

What it is: ForesightSafety Bench “comprehensively covers 7 major fundamental safety risk categories, 5 extended safety pillars, and 8 key industrial safety domains, forming a total of 94 refined risk subcategories. To date, the benchmark has accumulated tens of thousands of structured risk data points and assessment results, establishing a widely encompassing, hierarchically clear, and data-driven framework for AI safety evaluation and analysis.” Coverage areas include education and research, employment and workplace, government and public services, information and media, industry and infrastructure, finance and economy, healthcare and medicine, law and regulation, embodied AI safety, social AI safety, environmental AI safety, AI4Science safety, and catastrophic and existential risks. Some of the benchmark comes from taking in evaluations built by other groups, like GPQA, while other parts come from the authors of the benchmark. Existential risk and alignment: Perhaps most surprisingly, the benchmark includes a lot of tests relating to the further afield AI safety concerns which fascinate Western frontier labs, including evaluations for things like: alignment faking, sandbagging, deception and unfaithful reasoning, sycophancy, psychological manipulation, feints, bluffing, loss of control and power seeking, malicious self replication, goal misalignment and value drift, emergent agency and unintended autonomy, ai-enabled mass harm, autonomous weapons and strategic instability, and loss of human agency.

Results – Anthropic wins: For the general leaderboard as well as most sub-category breakdowns, Anthropic’s models lead, with the 4.5 series (Haiku and Sonnet), generally leading the competition, followed by Gemini-3-Flash. “Leading models, epitomized by the Claude series, demonstrate exceptional defensive resilience across critical dimensions—including Fundamental Safety, Extended Safety, and Industrial Safety—establishing remarkably high safety thresholds. Ranking alongside or closely following are the DeepSeek and GPT series, which achieve a robust balance between task efficacy and safety compliance through mature alignment mechanisms, all while maintaining high level capabilities”.

Why this matters – AI policy has some common tools : As we discuss elsewhere in this issue, measurement is a basic prerequisite for being able to do most forms of AI governance. It’s worth reminding ourselves that despite the larger geopolitical differences between the countries, AI scientists in each one are dealing with common problems – how to assess the properties of their systems for societally relevant aspects. And it’s even more encouraging that people in China are worried about some of the existential risk aspects that frontier labs in the US also worry about. Read more : ForesightSafety Bench: A Frontier Ri
