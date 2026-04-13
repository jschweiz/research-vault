---
id: page:2026-02-16-jack-clark-import-ai-facebook-makes-a-better-recommender-system-and-f-e7ec92ff
page_type: source-note
title: Facebook makes a better recommender system, and figures out some recommender scaling laws
aliases:
- Facebook makes a better recommender system, and figures out some recommender scaling laws
source_refs:
- 2026-02-16-jack-clark-import-ai-facebook-makes-a-better-recommender-system-and-f-e7ec92ff
backlinks: []
updated_at: '2026-04-09T23:08:05.987767Z'
managed: true
---
# Facebook makes a better recommender system, and figures out some recommender scaling laws

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2602.10016
- Document kind: paper
- Published at: 2026-02-16T14:01:19+00:00
- Authors: Facebook
- Tags: newsletter, ai, analysis, policy, website, paper, recommender systems, scaling laws, machine learning, facebook, sub-document
- Topics: [Pretraining](../topics/pretraining.md), [Facebook](../topics/facebook.md), [Machine Learning](../topics/machine-learning.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Recommender Systems](../topics/recommender-systems.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Facebook developed a recommendation system called Kunlun and discovered scaling laws for these models, making it easier to invest compute for better results. This work demonstrates predictable scaling behavior for recommender systems, which are crucial for advertising and social platforms.

## Topic Map

- [Pretraining](../topics/pretraining.md)
- [Facebook](../topics/facebook.md)
- [Machine Learning](../topics/machine-learning.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Recommender Systems](../topics/recommender-systems.md)

## Related Research

- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy, Pretraining)
- [UK government finds a scaling law for AI cyberattacks – and it’s going up and to the right!](uk-government-finds-a-scaling-law-for-ai-cyberattacks-and-its-go-be9e3f.md) (shared topics: Newsletter, Policy, Pretraining)
- [China builds a dataset and AI model for electronic warfare](china-builds-a-dataset-and-ai-model-for-electronic-warfare-ba06a0.md) (shared topics: Machine Learning, Newsletter, Policy)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Machine Learning, Newsletter, Policy)
- [Feedback Flywheel](feedback-flywheel-c22a0d.md) (shared topics: Machine Learning, Newsletter)
- [Build Self-Learning Agents Without Any Fine-Tuning](build-self-learning-agents-without-any-fine-tuning-7c2f7d.md) (shared topics: Machine Learning, Newsletter)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
