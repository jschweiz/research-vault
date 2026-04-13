---
id: 2026-02-23-jack-clark-import-ai-chinese-researchers-try-to-build-a-truly-compreh-8bac5c2d
kind: paper
title: Chinese researchers try to build a truly comprehensive LLM evaluation system
source_url: https://arxiv.org/abs/2602.14135v1
source_name: Import AI
authors:
- Beijing Institute of AI Safety and Governance
- Beijing Key Laboratory of Safe AI and Superalignment
- Chinese Academy of Sciences
published_at: '2026-02-23T13:31:18Z'
ingested_at: '2026-04-09T20:16:29.269229Z'
content_hash: 8925ebf66441b13d9bd6f60abfd5004efac4692b5b67d9f68847912ee4fa4b04
identity_hash: 832f81feed9ac39b6b34091d952b1a1c36a8786d098a3eb21833a80434546125
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- llm evaluation
- ai safety
- benchmark
- risk assessment
- sub-document
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/23/import-ai-446-nuclear-llms-chinas-big-ai-benchmark-measurement-and-ai-policy::story::3:https://arxiv.org/abs/2602.14135v1
canonical_url: https://arxiv.org/abs/2602.14135v1
doc_role: derived
parent_id: 2026-02-23-jack-clark-import-ai-import-ai-446-nuclear-llms-chinas-big-ai-benchma-74d04bde
index_visibility: visible
fetched_at: '2026-04-13T18:15:55.689004Z'
short_summary: Chinese institutions built the ForesightSafety Bench, a large-scale AI safety evaluation framework covering 94 risk subcategories. The benchmark highlights common AI safety concerns and shows Anthropic models leading in defensive resilience.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
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

Why this matters – AI policy has some common tools : As we discuss elsewhere in this issue, measurement is a basic prerequisite for being able to do most forms of AI governance. It’s worth reminding ourselves that despite the larger geopolitical differences between the countries, AI scientists in each one are dealing with common problems – how to assess the properties of their systems for societally relevant aspects. And it’s even more encouraging that people in China are worried about some of the existential risk aspects that frontier labs in the US also worry about. Read more : ForesightSafety Bench: A Frontier Risk Evaluation and Governance Framework towards Safe AI (arXiv) . Get the benchmark here : ForesightSafety-Bench (GitHub) . View the leaderboard here : ForesightSafety Bench Leaderboard (official site) .
