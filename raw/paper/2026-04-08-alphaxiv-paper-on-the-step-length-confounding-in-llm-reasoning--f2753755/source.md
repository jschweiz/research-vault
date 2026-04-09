---
id: 2026-04-08-alphaxiv-paper-on-the-step-length-confounding-in-llm-reasoning--f2753755
kind: paper
title: On the Step Length Confounding in LLM Reasoning Data Selection
source_url: https://www.alphaxiv.org/abs/2604.06834
source_name: alphaXiv Papers
authors:
- Bing Wang
- Rui Miao
- Chen Shen
- Shaotian Yan
- Kaiyuan Liu
- Ximing Li
- Xiaosong Yuan
- Sinan Fan
- Jun Zhang
- Jieping Ye
published_at: '2026-04-08T08:51:47Z'
ingested_at: '2026-04-09T10:02:31.957458Z'
content_hash: d74569d58196952496b0517a18c6cfc4cece4dad044a841d6c3ce611afeef914
identity_hash: a3b53299ba17cdb15b4b98be13b58b84e66748257aeffb689ad691e90c914068
tags:
- paper
- alphaxiv
- research
- causal-inference
- chain-of-thought
- Computer Science
- cs.AI
- cs.CL
- data-curation
- fine-tuning
- reasoning
- transformers
- audio
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06834
canonical_url: https://www.alphaxiv.org/abs/2604.06834
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:02:31.957463Z'
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
# On the Step Length Confounding in LLM Reasoning Data Selection

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06834
- Source paper: https://arxiv.org/abs/2604.06834
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06834v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06834v1.png
- Paper ID: 2604.06834
- Canonical ID: 2604.06834v1
- Paper group ID: 019d7019-7fd7-743d-a525-fbffde62b917
- Version ID: 019d7019-801e-7e7f-a6f0-ea51286e0420
- Version: v1
- Version order: 1
- Published at: 2026-04-08T08:51:47+00:00
- First published at: 2026-04-08T08:51:47+00:00
- Updated at: 2026-04-09T02:36:52.567000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Bing Wang
- Rui Miao
- Chen Shen
- Shaotian Yan
- Kaiyuan Liu
- Ximing Li
- Xiaosong Yuan
- Sinan Fan
- Jun Zhang
- Jieping Ye

## Topics

- causal-inference
- chain-of-thought
- Computer Science
- cs.AI
- cs.CL
- data-curation
- fine-tuning
- reasoning
- transformers

## Metrics

- Visits (all): 16
- Visits (last 7 days): 16
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Large reasoning models have recently demonstrated strong performance on complex tasks that require long chain-of-thought reasoning, through supervised fine-tuning on large-scale and high-quality datasets. To construct such datasets, existing pipelines generate long reasoning data from more capable Large Language Models (LLMs) and apply manually heuristic or naturalness-based selection methods to filter high-quality samples. Despite the proven effectiveness of naturalness-based data selection, which ranks data by the average log probability assigned by LLMs, our analysis shows that, when applied to LLM reasoning datasets, it systematically prefers samples with longer reasoning steps (i.e., more tokens per step) rather than higher-quality ones, a phenomenon we term step length confounding. Through quantitative analysis, we attribute this phenomenon to low-probability first tokens in reasoning steps; longer steps dilute their influence, thereby inflating the average log probabilities. To address this issue, we propose two variant methods: ASLEC-DROP, which drops first-token probabilities when computing average log probability, and ASLEC-CASL, which applies a causal debiasing regression to remove the first tokens' confounding effect. Experiments across four LLMs and five evaluation benchmarks demonstrate the effectiveness of our approach in mitigating the step length confounding problem.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d7019-7fd7-743d-a525-fbffde62b917/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7019-7fd7-743d-a525-fbffde62b917/transcript.json

## Similar Papers

- Stop Overthinking: A Survey on Efficient Reasoning for Large Language Models (2503.16419v4): Researchers from Rice University and the University of Houston present the first structured survey on efficient reasoning for Large Language Models, classifying methodologies that address the "overthinking phenomenon" by optimizing the length and necessity of generated reasoning sequences. This survey provides a comprehensive taxonomy and critical insights to guide the development of more practical and cost-effective LLM applications.
- LLMs Can Easily Learn to Reason from Demonstrations Structure, not  content, is what matters! (2502.07374v2): Research from UC Berkeley and Anyscale demonstrates that Large Language Models can efficiently acquire complex long chain-of-thought reasoning abilities through distillation, even with small datasets (as few as 17k samples) and parameter-efficient LoRA fine-tuning. The study reveals that the structural integrity and logical flow of reasoning demonstrations are more critical for learning than the specific content or numerical correctness of individual intermediate steps.
- DeepDistill: Enhancing LLM Reasoning Capabilities via Large-Scale  Difficulty-Graded Data Training (2504.17565v3): DeepDistill improves Large Language Model reasoning by employing a multi-stage supervised fine-tuning process with a large-scale, difficulty-graded dataset, reaching 79.2% on the AIME2024 mathematical reasoning benchmark.
- Long Is More Important Than Difficult for Training Reasoning Models (2503.18069v1): A comprehensive study reveals that the length of reasoning chains, rather than problem difficulty, is the primary factor in training effective reasoning models, with experiments showing comparable performance between models trained on lengthy but simpler problems versus complex single problems using the Qwen2.5 architecture family.
- Deconstructing Long Chain-of-Thought: A Structured Reasoning  Optimization Framework for Long CoT Distillation (2503.16385v1): A structured data processing framework optimizes Chain-of-Thought (CoT) reasoning in large language models through intelligent segmentation and redundancy elimination, achieving 5% improved token efficiency while maintaining or exceeding baseline accuracy across mathematical reasoning benchmarks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
