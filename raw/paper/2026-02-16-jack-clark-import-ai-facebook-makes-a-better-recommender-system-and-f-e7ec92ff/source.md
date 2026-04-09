---
id: 2026-02-16-jack-clark-import-ai-facebook-makes-a-better-recommender-system-and-f-e7ec92ff
kind: paper
title: Facebook makes a better recommender system, and figures out some recommender scaling laws
source_url: https://arxiv.org/abs/2602.10016
source_name: Import AI
authors: []
published_at: '2026-02-16T14:01:19Z'
ingested_at: '2026-04-09T20:16:40.069938Z'
content_hash: a08644e539e17d683dd1e0205e2019adcb42e128998299720f190bde423a79d8
identity_hash: cf99a87f350e49cd732e3530208da046ed28690ac0905655386acb4bc6f6f343
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/16/import-ai-445-timing-superintelligence-ais-solve-frontier-math-proofs-a-new-ml-research-benchmark::story::2:https://arxiv.org/abs/2602.10016
canonical_url: https://arxiv.org/abs/2602.10016
doc_role: derived
parent_id: 2026-02-16-jack-clark-import-ai-import-ai-445-timing-superintelligence-ais-solve-74f2ca81
index_visibility: visible
fetched_at: '2026-04-09T20:16:40.069943Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Facebook makes a better recommender system, and figures out some recommender scaling laws

Source newsletter: Import AI 445: Timing superintelligence; AIs solve frontier math proofs; a new ML research benchmark
Source issue: https://jack-clark.net/2026/02/16/import-ai-445-timing-superintelligence-ais-solve-frontier-math-proofs-a-new-ml-research-benchmark
Published At: 2026-02-16T14:01:19+00:00
Canonical URL: https://arxiv.org/abs/2602.10016

## Newsletter Context

…Kunlun is another nice example of what industrial AI looks like… Facebook has published details on Kunlun, a recommendation system which is more efficient than previous ones developed by the ad behemoth. Along with this, Facebook has also figured out a predictable ‘scaling law’ for Kunlun models, making it easier for the company to invest hitherto unprecedented compute in these models for a more predictable return. This is a big deal because recommendation systems are what companies like Facebook use for advertising, which is both a) how they make the vast majority of their money, and b) has a tremendous impact on the buying and attention habits of the billions of people that use Facebook and other social platforms.

Recommenders are different to LLMs: We’ve had scaling laws for LLMs like Claude and ChatGPT for a while, but it’s been harder to develop the same scaling laws for recommender models. This is because recommender models work quite differently to LLMs, and so building scaling models here is “an open challenge for systems that jointly model both sequential user behaviors and non-sequential context features”. Recommender models also tend to be a lot less efficient than LLMs: Recommendation systems achieve only 3-15% Model FLOPs Utilization (MFU), compared to 40-60% for LLMs, due to heterogeneous feature spaces resulting in small embedding dimensions, irregular tensor shapes, and memory-bound operations

Kunlun: The bulk of the paper involves a discussion of the design of Kunlun, which is basically a well optimized recommender system with resulting better MFU. Kunlun contains a Kunlun Transformer Block for context-aware sequence modeling via GDPA-enhanced personalized feed-forward networks and multi-head self-attention, as well as a Kunlun Interaction Block “for bidirectional information exchange through personalized weight generation, hierarchical sequence summarization, and global feature interaction”. There are a bunch of other tricks Facebook used to build Kunlun and you can read the paper to learn more. Ultimately, Kunlun improves MFU from 17% to 37% on NVIDIA B200 GPUs.

Why this matters – a scaling law for money: The key insight in the paper is that Kunlun models scale predictably, exhibiting the kind of power-law scaling behavior that language models exhibit. But where with LLMs scaling laws are typically assessed via a reduction in loss on an underlying dataset, here its normalized entropy (NE). In Facebook experiments, they discover reliable scaling laws for both NE gains in terms of the amount of gigaflops dumped into training the model, as well as related scaling laws for improvement in NE according to the number of layers used. The Kunlun models have been “deployed across major Meta Ads models, delivering a 1.2% improvement in topline metrics”. What we’re seeing here is the optimization of some of the most societally significant AI systems in the world – ones which direct billions of eyeballs towards a variety of products and online information – colliding with a greater degree of performance predictability; by developing these scaling laws, Meta has made it easier for it to spend even more compute on making these models even better, by making the investments in them more predictable in terms of the intelligence return on capital investment. Read more : Kunlun: Establishing Scaling Laws for Massive-Scale Recommendation Systems through Unified Architecture Design (arXiv) .
