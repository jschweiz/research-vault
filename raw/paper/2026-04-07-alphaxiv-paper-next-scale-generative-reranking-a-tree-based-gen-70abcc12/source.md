---
id: 2026-04-07-alphaxiv-paper-next-scale-generative-reranking-a-tree-based-gen-70abcc12
kind: paper
title: 'Next-Scale Generative Reranking: A Tree-based Generative Rerank Method at Meituan'
source_url: https://www.alphaxiv.org/abs/2604.05314
source_name: alphaXiv Papers
authors:
- Shuli Wang
- Changhao Li
- Ke Fan
- Senjie Kou Junwei Yin
- Chi Wang
- Yinhua Zhu
- Haitao Wang
- Xingxing Wang
published_at: '2026-04-07T01:35:20Z'
ingested_at: '2026-04-09T09:58:33.967538Z'
content_hash: a3ae29d1de2a0dc71a4fd501d8415f10dce156a1a9b70a53cea5f4671c25a880
identity_hash: ad2e363844831b449f922098ccca08164c37902562dc9f307d725d8169a0a308
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.IR
- audio
- summary
status: active
asset_paths:
- alphaxiv-ai-detection.json
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.05314
canonical_url: https://www.alphaxiv.org/abs/2604.05314
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:58:33.967542Z'
short_summary: Meituan researchers developed Next-Scale Generative Reranking (NSGR), a tree-based framework for recommendation systems that generates item lists hierarchically and uses multi-scale guidance to resolve goal inconsistency between its generator and evaluator. The framework achieved superior offline performance, including absolute gains of 0.0153 AUC and 0.0160 GAUC on a large industrial dataset, and in online A/B tests on Meituan's food delivery platform, it increased CTR by 2.89%, CVR by 0.58%, and GMV by 3.15% for 20 candidate items.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Next-Scale Generative Reranking: A Tree-based Generative Rerank Method at Meituan

## alphaXiv Summary

Meituan researchers developed Next-Scale Generative Reranking (NSGR), a tree-based framework for recommendation systems that generates item lists hierarchically and uses multi-scale guidance to resolve goal inconsistency between its generator and evaluator. The framework achieved superior offline performance, including absolute gains of 0.0153 AUC and 0.0160 GAUC on a large industrial dataset, and in online A/B tests on Meituan's food delivery platform, it increased CTR by 2.89%, CVR by 0.58%, and GMV by 3.15% for 20 candidate items.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05314
- Source paper: https://arxiv.org/abs/2604.05314
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05314v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05314v1.png
- Paper ID: 2604.05314
- Canonical ID: 2604.05314v1
- Paper group ID: 019d6aeb-4548-735d-adbb-e39a765ca041
- Version ID: 019d6aeb-458e-73c6-8c93-c9197e1a939f
- Version: v1
- Version order: 1
- Published at: 2026-04-07T01:35:20+00:00
- First published at: 2026-04-07T01:35:20+00:00
- Updated at: 2026-04-08T02:28:16.840000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Shuli Wang
- Changhao Li
- Ke Fan
- Senjie Kou Junwei Yin
- Chi Wang
- Yinhua Zhu
- Haitao Wang
- Xingxing Wang

## Topics

- Computer Science
- cs.IR

## Metrics

- Visits (all): 38
- Visits (last 7 days): 38
- Total votes: 0
- Public total votes: 4
- X likes: 0

## Abstract

In modern multi-stage recommendation systems, reranking plays a critical role by modeling contextual information. Due to inherent challenges such as the combinatorial space complexity, an increasing number of methods adopt the generative paradigm: the generator produces the optimal list during inference, while an evaluator guides the generator's optimization during the training phase. However, these methods still face two problems. Firstly, these generators fail to produce optimal generation results due to the lack of both local and global perspectives, regardless of whether the generation strategy is autoregressive or non-autoregressive. Secondly, the goal inconsistency problem between the generator and the evaluator during training complicates the guidance signal and leading to suboptimal performance. To address these issues, we propose the \textbf{N}ext-\textbf{S}cale \textbf{G}eneration \textbf{R}eranking (NSGR), a tree-based generative framework. Specifically, we introduce a next-scale generator (NSG) that progressively expands a recommendation list from user interests in a coarse-to-fine manner, balancing global and local perspectives. Furthermore, we design a multi-scale neighbor loss, which leverages a tree-based multi-scale evaluator (MSE) to provide scale-specific guidance to the NSG at each scale. Extensive experiments on public and industrial datasets validate the effectiveness of NSGR. And NSGR has been successfully deployed on the Meituan food delivery platform.

## Problem

- Existing reranking methods struggle with the combinatorial explosion of the permutation space, making exhaustive evaluation computationally infeasible in large-scale industrial settings.
- Prior generative reranking paradigms (autoregressive, one-step, multi-step) face limitations in balancing global and local contextual understanding during list generation or are prone to local optima.
- A "goal inconsistency problem" exists between the generator (which seeks optimal lists) and the evaluator (trained to estimate list utility), hindering effective guidance signals.

## Method

- Introduced Next-Scale Generative Reranking (NSGR), a tree-based framework comprising a Next-Scale Generator (NSG) and a Multi-Scale Evaluator (MSE).
- The NSG generates recommendation lists hierarchically, following a coarse-to-fine, tree-based expansion to balance global and local context.
- A Multi-Scale Neighbor Loss (MSNL) mechanism provides scale-specific guidance to the NSG during training, using relative rewards from the MSE to resolve goal inconsistency.

## Results

- NSGR achieved absolute gains of 0.0153 AUC and 0.0160 GAUC over the best baseline (YOLOR) on a large industrial Meituan dataset.
- The framework demonstrated superior generator performance, achieving Hit Ratios of 0.861 (HR@1%) and 0.987 (HR@10%) on the Meituan dataset.
- Online A/B tests on Meituan's platform showed a 2.89% increase in CTR, 0.58% increase in CVR, and 3.15% increase in GMV when using 20 candidate items, demonstrating significant business impact.

## Takeaways

- A hierarchical, tree-based generation approach allows for effectively capturing both global list structure and fine-grained local item interactions within the recommendation list.
- Providing the generator with scale-specific relative rewards, derived from an evaluator's assessment of neighboring lists, directly addresses the goal inconsistency problem, leading to more robust generator training.
- Modeling multi-scale contextual relationships within the evaluator significantly enhances its ability to accurately predict the overall utility of a recommendation list.

## Full Overview

Saved in `alphaxiv-overview.md` and `alphaxiv-overview.json`.

## Overview Languages

- de
- en
- es
- fr
- hi
- ja
- ko
- ru
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6aeb-4548-735d-adbb-e39a765ca041/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6aeb-4548-735d-adbb-e39a765ca041/transcript.json

## AI Detection

- State: done
- Prediction: Human
- Headline: Mostly Human Written
- Fraction AI: 0.013434284
- Fraction AI-assisted: 0
- Fraction human: 0.9865657

## Similar Papers

- A Generative Re-ranking Model for List-level Multi-objective  Optimization at Taobao (2505.07197v1): SORT-Gen, a generative re-ranking model developed by Alibaba's Taobao & Tmall Group, addresses list-level multi-objective optimization by generating entire item lists. It achieved a +4.13% increase in clicks and +8.10% in GMV in online A/B tests on Taobao, with 19 ms latency, demonstrating a powerful and efficient solution for optimizing multiple business objectives simultaneously.
- Towards Large-scale Generative Ranking (2505.04180v2): Xiaohongshu Inc. developed GenRank, an efficient generative ranking architecture, to investigate and deploy generative recommendation in large-scale industrial settings. The system improved online user satisfaction metrics by up to 1.25% in A/B tests and achieved over 25% better P99 response time compared to the production model.
- EAGER: Two-Stream Generative Recommender with Behavior-Semantic Collaboration (2406.14017v2): EAGER, developed by Zhejiang University and Huawei Noah’s Ark Lab, introduces a two-stream generative recommender system that integrates behavioral and semantic information through a unique architecture for enhanced personalization. This framework consistently outperforms state-of-the-art generative baselines, achieving up to 31.49% higher Recall@5 on benchmark datasets.
- Comprehensive List Generation for Multi-Generator Reranking (2504.15625v1): Researchers at Kuaishou Technology develop a Multi-Generator-Evaluator (MG-E) framework for recommendation reranking that combines multiple list generators with an evaluator, introducing a List Comprehensiveness metric and Complementary List Generation technique to improve recommendation diversity and accuracy across both offline benchmarks and live A/B tests.
- Sparse Meets Dense: Unified Generative Recommendations with Cascaded  Sparse-Dense Representations (2503.02453v1): COBRA (Cascaded sparsE-dense RepresentAtion) is a framework that combines sparse IDs with dense vectors for generative recommendation, improving recommendation performance and offering control over diversity. The approach achieved a 3.8% increase in conversion rate and a 2.7% increase in Average Revenue Per User (ARPU) in online A/B tests on a large-scale industrial platform.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
