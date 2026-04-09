---
id: 2026-03-09-jack-clark-import-ai-want-to-measure-ai-r-d-here-are-14-ways-to-do-it-d3211a88
kind: paper
title: Want to measure AI R&D, here are 14 ways to do it
source_url: https://arxiv.org/abs/2603.03992
source_name: Import AI
authors:
- GovAI
- University of Oxford
published_at: '2026-03-09T12:45:54Z'
ingested_at: '2026-04-09T20:15:57.158288Z'
content_hash: 6400d3cbf3eaef857b5ab5410cd09e16c38d798bd84411a13c8f790269aecfee
identity_hash: 56ec2e2ee8e5a49f575cef8508e8461ef3cce78fb344969480ab961c6f2fe648
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- ai r&d
- metrics
- governance
- automation
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/09/import-ai-448-ai-rd-bytedances-cuda-writing-agent-on-device-satellite-ai::story::2:https://arxiv.org/abs/2603.03992
canonical_url: https://arxiv.org/abs/2603.03992
doc_role: derived
parent_id: 2026-03-09-jack-clark-import-ai-import-ai-448-ai-r-d-bytedances-cuda-writing-age-45e7946b
index_visibility: visible
fetched_at: '2026-04-09T20:15:57.158293Z'
short_summary: Researchers have laid out 14 metrics to measure the success of AI companies in building and overseeing AI R&D Automation (AIRDA), which is a prerequisite for recursive self-improvement. The document suggests that AI measurement is essential for AI governance, requiring actions from companies, governments, and third parties.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:44.372565Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 6bdc1719cc9a4b896c58b899ac1a4ee168fba47704867fe35b3913488be8389a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 8a6e3501f0f45eab8d42eb0f69f6497cb3adf5e51e8d6f3a9c7618f2a8a77685
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.5
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses metrics and governance related to AI R&D, which aligns perfectly with the user's favorite topics of language models, evaluation, and reasoning.
  evidence_quotes:
  - Researchers have laid out 14 metrics to measure the success of AI companies in building and overseeing AI R&D Automation (AIRDA), which is a prerequisite for re
  - The document suggests that AI measurement is essential for AI governance, requiring actions from companies, governments, and third parties.
  - AI measurement is a prerequisite to AI governance.
---
# Want to measure AI R&D, here are 14 ways to do it

Source newsletter: Import AI 448: AI R&D; Bytedance’s CUDA-writing agent; on-device satellite AI
Source issue: https://jack-clark.net/2026/03/09/import-ai-448-ai-rd-bytedances-cuda-writing-agent-on-device-satellite-ai
Published At: 2026-03-09T12:45:54+00:00
Canonical URL: https://arxiv.org/abs/2603.03992

## Newsletter Context

…Generating metrics about the most significant property of AI… The biggest thing that could ever happen with artificial intelligence will be when it starts to build itself. This phenomenon which has been often termed recursive self-improvement is often seen by many as an event horizon, beyond which it’ll be increasingly hard to reason about the future. How would we know if we were approaching this point? Researchers with GovAI and the University of Oxford have written a paper laying out 14 distinct metrics which could be measured to help us figure out the extent to which AI companies are succeeding in building and overseeing AI R&D Automation (AIRDA) – getting AI to build AI, a necessary prerequisite for recursive self-improvement.

Why care about this : “AIRDA could accelerate AI progress, bringing forward AI’s benefits but also hastening the arrival of destructive capabilities, including those related to weapons of mass destruction, or other forms of disruption such as unemployment,” they write.

What are the 14 metrics?

- Measure AI performance on AI R&D
- Measure AI performance on AI R&D relative to humans and human-AI teams
- Measure ‘oversight red teaming’ – how well human teams can effectively supervise AI systems that are building themselves
- Measure misalignment in AIRDA
- Compute the rate of efficiency improvements on AI R&D tasks
- Survey staff on how they use AI and what this means for productivity
- Find out if and how often AI is used in high-stakes decisions
- Examine where AI researchers spend their time
- Meta-measure the effectiveness of how well companies can oversee AI development (e.g, the rate of bugs or undesired behaviors that make it through to production even with human oversight)
- Examine how often AI systems subvert the goals of their human developers
- Track the headcount of AI researchers at labs, as well as details of their performance
- Look at the distribution of compute used by AI companies across their AI R&D process and how this changes
- Examine compute as a share of AI R&D spending
- Understand the permissions AI systems have and how permissiveness changes over time

Governing AI R&D: The logical question implied by the above, I hope, is “wow that all sounds very high-stakes and important, what can we do about it”? As I write often in this newsletter, AI measurement is a prerequisite to AI governance. Therefore, with these measures, a few different actors should do a few different things. Specifically:

Companies should:

- Track differential progress between safety and capabilities research: Is capabilities research moving at a faster rate than oversight research?
- Track how AI R&D affects oversight: Automation could free up humans to invest more of their time in building systems for overseeing the work ofAI systems. On the other hand, AI-driven R&D might create systems which are innately harder for humans to understand, and the volume of activity being done by the AI systems could swamp any oversight systems.
- Track the actual extent of AI R&D: You can build metrics which work as proxies for AI R&D – e.g, many labs today test out how well AI systems can build AI kernels or train AI models. You can also test out how much AI R&D automation is being done in practice by your own organization. Another path is by doing qualitative and quantitative studies of human staff to understand how their own roles are changing, as well as how AI is being used in increasingly high-stakes decisions.

Governments should:

- Develop systems for confidential reporting, potentially in the form of industry-wide aggregates: Once companies are measuring this kind of data, governments should seek to gain access to it so they can understand the shape of AI progress.

Third parties should:

- Estimate metrics using public sources: Look at public reporting to create estimates for things that may relate to AI R&D, like the amount of compute companies have (e.g, both Epoch and SemiAnalysis do this quite well).
- Create tooling and design surveys: Builds tools that companies could use to generate more telemetry about AI R&D, and conduct surveys of people at companies to gather more insights.

Why this matters : “An actor has oversight over the AI R&D process to the extent that they (1) understand the process and (2) exercise informed control over it in order to produce desired outputs, such as by reviewing AI-generated outputs for errors”, they write. Therefore, for us as a species to have any ‘warning shots’ about recursive self-improvement and any hope of governing it, we need to be able to measure these aspects of it. Read more: Measuring AI R&D Automation (arXiv) .
