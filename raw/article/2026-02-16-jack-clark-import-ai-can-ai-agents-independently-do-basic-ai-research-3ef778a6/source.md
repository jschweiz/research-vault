---
id: 2026-02-16-jack-clark-import-ai-can-ai-agents-independently-do-basic-ai-research-3ef778a6
kind: article
title: Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes
source_url: https://x.com/j_foerst/status/2021524537662210204
source_name: Import AI
authors: []
published_at: '2026-02-16T14:01:19Z'
ingested_at: '2026-04-09T20:16:41.205010Z'
content_hash: da96aea1f7dbfdce357f5a87c0b177bf8692fd6eb25774dd4b3212af5d1e500a
identity_hash: eef181977eb523d9794cf38a904e3000a2aa3c1d583e9e40b77bda087053dbd6
tags:
- newsletter
- ai
- analysis
- policy
- website
- article
- benchmark
- machine learning
- agents
- research
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/16/import-ai-445-timing-superintelligence-ais-solve-frontier-math-proofs-a-new-ml-research-benchmark::story::4:https://x.com/j_foerst/status/2021524537662210204
canonical_url: https://x.com/j_foerst/status/2021524537662210204
doc_role: derived
parent_id: 2026-02-16-jack-clark-import-ai-import-ai-445-timing-superintelligence-ais-solve-74f2ca81
index_visibility: visible
fetched_at: '2026-04-13T18:16:17.570329Z'
short_summary: The AI Research Science Benchmark (AIRS-BENCH) tests how well AI agents can complete various machine learning tasks sourced from recent papers. The benchmark explores potential scaling laws regarding how agent solutions relate to model size and human performance.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:53:59.246003Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: aa9c4f4bbc1cf731744bdd7c3e23379a60a360f56943576d425148f3cb6311a1
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: e22c0d169921ecfebb4267e1be399c2fac028306e2267bced753d3cfd673d516
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: This document directly addresses frontier LLM evaluation and research methods, which aligns perfectly with the user's focus on evaluation, reasoning, and research tooling.
  evidence_quotes:
  - The AI Research Science Benchmark (AIRS-BENCH) tests how well AI agents can complete various machine learning tasks sourced from recent papers.
  - 'Why this matters – models might produce different solutions to humans, and this is a cool way of studying if there’s a ‘scaling law’ here : One way this could b'
  - As Blaise Pascal once apocryphally said “I have only made this letter longer because I have not had the time to make it shorter”.
---
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
