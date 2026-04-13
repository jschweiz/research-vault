---
id: page:2026-02-16-jack-clark-import-ai-can-ai-agents-independently-do-basic-ai-research-3ef778a6
page_type: source-note
title: Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes
aliases:
- Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes
source_refs:
- 2026-02-16-jack-clark-import-ai-can-ai-agents-independently-do-basic-ai-research-3ef778a6
backlinks:
- page:2026-02-02-jack-clark-import-ai-import-a-idea-6783b26f
- page:2026-02-02-jack-clark-import-ai-one-way-of-seeing-ai-progress-how-hard-its-getti-b88405ad
- page:2026-02-09-jack-clark-import-ai-ai-based-chip-design-is-harder-than-you-think-an-333f3a92
- page:2026-02-16-jack-clark-import-ai-facebook-makes-a-better-recommender-system-and-f-e7ec92ff
- page:2026-02-16-jack-clark-import-ai-math-researchers-see-if-ai-can-help-solve-their--da564141
- page:2026-03-02-jack-clark-import-ai-llms-are-still-very-bad-at-videogames-4b8298cd
- page:2026-03-02-jack-clark-import-ai-what-happens-when-humans-try-to-mess-with-ai-age-c6091226
- page:2026-03-09-jack-clark-import-ai-bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-480da18e
- page:2026-03-23-jack-clark-import-ai-china-builds-a-dataset-and-ai-model-for-electron-a67bef0c
- page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
updated_at: '2026-04-09T23:10:02.615258Z'
managed: true
---
# Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://x.com/j_foerst/status/2021524537662210204
- Document kind: article
- Published at: 2026-02-16T14:01:19+00:00
- Tags: newsletter, ai, analysis, policy, website, article, benchmark, machine learning, agents, research, sub-document
- Topics: [Agents](../topics/agents.md), [Evaluations](../topics/evaluations.md), [Machine Learning](../topics/machine-learning.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Sub Document](../topics/sub-document.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

The AI Research Science Benchmark (AIRS-BENCH) tests how well AI agents can complete diverse machine learning tasks, ranging from code generation to time series forecasting. The benchmark explores potential scaling laws regarding how agent solutions relate to model size and human performance.

## Topic Map

- [Agents](../topics/agents.md)
- [Evaluations](../topics/evaluations.md)
- [Machine Learning](../topics/machine-learning.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Sub Document](../topics/sub-document.md)

## Related Research

- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [AI-based chip design is harder than you think and benchmarks might be too easy](ai-based-chip-design-is-harder-than-you-think-and-benchmarks-mig-6b8331.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [One way of seeing AI progress – how hard it’s getting to design technical interviews](one-way-of-seeing-ai-progress-how-hard-its-getting-to-design-tec-cfca46.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [Feedback Flywheel](feedback-flywheel-c22a0d.md) (shared topics: Machine Learning, Newsletter, Sub Document)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy, Sub Document)
- [Work With Us](work-with-us-b67b8e.md) (shared topics: Agents, Newsletter, Sub Document)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes

Source newsletter: Import AI 445: Timing superintelligence; AIs solve frontier math proofs; a new ML research benchmark
Source issue: https://jack-clark.net/2026/02/16/import-ai-445-timing-superintelligence-ais-solve-frontier-math-proofs-a-new-ml-research-benchmark
Published At: 2026-02-16T14:01:19+00:00
Canonical URL: https://x.com/j_foerst/status/2021524537662210204

## Newsletter Context

…And we can expect today’s models to be much better at this than the paper suggests… Researchers with Meta, the University of Oxford, and University College London, have built and released the AI Research Science Benchmark (AIRS-BENCH), a way of testing out how well AI systems can complete contemporary machine learning tasks.

What AIRS-BENCH is made of: AIRS-BENCH tests out how well agents can solve 20 distinct tasks, sourced from 17 recent machine learning papers. The tasks span a variety of technical genres, including: molecules and proteins machine learning, question answering, text extraction and matching, time series, text classification, code, and math.

Some example tasks:

- CodeGenerationAPPSPassAt5: Solve coding problems by generating five distinct Python programs for each problem.
- CoreferenceResolutionWinograndeAccuracy : Identify which of two possible options a pronoun in a sentence refers to. It uses the Winogrande dataset, which contains sentences with an ambiguous pronoun and two possible answers.
- TimeSeriesForecastingRideshareMAE: Perform time series forecasting over the Rideshare dataset, which is part of the Monash Time Series Forecasting Repository.

Results: Real problems, crappy models: This is a somewhat perplexing benchmark – the tasks are interesting and wrap in a lot of complexity. But the paper only tests out relatively bad models, such as the Code World Model, o3-mini, gpt-oss-20b, gpt-oss-120b, GPT-4o, and Devstral-Small 24B. This is a very funny set of models, and none of them are true frontier ones – one of the paper authors wrote on twitter “ this took some time to get out “, so this could just be an artifact of slow publishing timelines. In tests, none of the models are on par with the elo rating of a best-in-class human – but I’m not sure what to make of this till I see results with more powerful models.

Why this matters – models might produce different solutions to humans, and this is a cool way of studying if there’s a ‘scaling law’ here : One way this could be interesting is understanding the different ways models might solve tasks relative to humans. In one example, TextualClassificationSickAccuracy, models had to determine whether a pair of sentences have a relationship involving either entailment, contradiction, or no relationship. SOTA from the literature is a person fine-tuning RoBERTa on the underlying training set and testing on the test set. By comparison, the best tested AIRS-BENCH agent, GPT-OSS-120B, “produces a two-level stacked ensemble that combines multiple transformer models and a meta-learner. RoBERTa-large and DeBERTa-v3-large are independently fine-tuned on the SICK training set. Each model processes sentence pairs and outputs logits for each class. The training is performed using 5-fold stratified cross-validation, ensuring robust out-of-fold (OOF) predictions and preventing overfitting. The logits from both base models are concatenated to form a feature vector for each example.” This is extremely complicated! But it’s also interesting in that perhaps we can learn something about the progression in agents by looking at how the simplicity of their solutions to tasks might scale with size, where naively I’d expect more powerful models to arrive at simpler solutions. As Blaise Pascal once apocryphally said ““I have only made this letter longer because I have not had the time to make it shorter”. Read more : AIRS-Bench: a Suite of Tasks for Frontier AI Research Science Agents (arXiv) .
