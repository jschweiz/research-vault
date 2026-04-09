---
id: 2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
kind: paper
title: Embarrassingly Simple Self-Distillation Improves Code Generation
source_url: https://www.alphaxiv.org/abs/2604.01193
source_name: alphaXiv Papers
authors:
- Ruixiang Zhang
- Richard He Bai
- Huangjie Zheng
- Navdeep Jaitly
- Ronan Collobert
- Yizhe Zhang
published_at: '2026-04-01T17:39:50Z'
ingested_at: '2026-04-09T12:08:39.392812Z'
content_hash: a00bee4eab073eaa48cd5c054d29eb90384e71cc874e0ac82f397d89665dfd48
identity_hash: 8176b3cc8ba2c31a31484efef1cf9221d59eaca66cce3febb10ebd02b3858bf8
tags:
- paper
- alphaxiv
- research
- computer science
- cs.cl
- fine-tuning
- generative-models
- instruction-tuning
- knowledge-distillation
- model-interpretation
status: active
asset_paths:
- alphaxiv-ai-detection.json
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-podcast.mp3
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.01193
canonical_url: https://www.alphaxiv.org/abs/2604.01193
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:08:39.392818Z'
short_summary: Simple Self-Distillation (SSD) improves code generation by training large language models exclusively on self-generated solutions, leading to performance gains without external supervision. This method reshapes token distributions to balance precision and exploration in LLM decoding.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T15:00:27.122555Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 379d3589722369fb82cc2c936e4110cbf2d909b2abc4d2adb6328dbac2b9deff
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 73e3a21f8a3f38f8aad85f4d9296420cd184be16fbd5cbb6021d814af86848b1
lightweight_score:
  relevance_score: 0.616
  source_fit_score: 0.55
  topic_fit_score: 0.62
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on 2 favorite-topic matches.
  evidence_quotes:
  - 'Simple Self-Distillation (SSD) improves code generation by training large language models exclusively on self-generated solutions, leading to performance gains '
---
# Embarrassingly Simple Self-Distillation Improves Code Generation

## alphaXiv Summary

A method called Simple Self-Distillation (SSD) enables large language models to enhance their code generation performance by training exclusively on self-generated, unverified solutions. This approach improved the Qwen3-30B-Instruct model's pass@1 score on LiveCodeBench v6 from 42.4% to 55.3%, demonstrating its efficacy without external supervision or complex verification.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.01193
- Source paper: https://arxiv.org/abs/2604.01193
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.01193v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.01193v1.png
- GitHub: https://github.com/apple/ml-ssd
- GitHub stars: 2
- Paper ID: 2604.01193
- Canonical ID: 2604.01193v1
- Paper group ID: 019d4bff-833f-7d1e-bb18-25fb1ef24565
- Version ID: 019d4bff-8374-72cf-a6d5-e902fd357539
- Version: v1
- Version order: 1
- Published at: 2026-04-01T17:39:50+00:00
- First published at: 2026-04-01T17:39:50+00:00
- Updated at: 2026-04-02T02:22:09.727000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Ruixiang Zhang
- Richard He Bai
- Huangjie Zheng
- Navdeep Jaitly
- Ronan Collobert
- Yizhe Zhang

## Topics

- Computer Science
- cs.CL
- fine-tuning
- generative-models
- instruction-tuning
- knowledge-distillation
- model-interpretation
- self-supervised-learning
- text-generation
- transformers

## Metrics

- Visits (all): 3772
- Visits (last 7 days): 3764
- Total votes: 75
- Public total votes: 207
- X likes: 0

## Abstract

Can a large language model (LLM) improve at code generation using only its own raw outputs, without a verifier, a teacher model, or reinforcement learning? We answer in the affirmative with simple self-distillation (SSD): sample solutions from the model with certain temperature and truncation configurations, then fine-tune on those samples with standard supervised fine-tuning. SSD improves Qwen3-30B-Instruct from 42.4% to 55.3% pass@1 on LiveCodeBench v6, with gains concentrating on harder problems, and it generalizes across Qwen and Llama models at 4B, 8B, and 30B scale, including both instruct and thinking variants. To understand why such a simple method can work, we trace these gains to a precision-exploration conflict in LLM decoding and show that SSD reshapes token distributions in a context-dependent way, suppressing distractor tails where precision matters while preserving useful diversity where exploration matters. Taken together, SSD offers a complementary post-training direction for improving LLM code generation.

## Problem

- High cost and difficulty of obtaining high-quality supervised training signals for LLM code generation, limiting scalability.
- Limitations of existing self-improvement methods, including performance ceilings for teacher-based distillation and operational complexities or instabilities in RL and unsupervised intrinsic reward systems.
- An inherent "precision-exploration conflict" in LLM decoding for code, where a single global temperature setting struggles to balance precise token generation at constrained points with necessary exploration for diverse algorithmic choices.

## Method

- Introduce Simple Self-Distillation (SSD), where a frozen base LLM generates a single candidate solution for each problem prompt using specific training-time decoding configurations, without any external verification.
- Fine-tune the base LLM on this self-generated, unverified dataset using standard supervised fine-tuning with a cross-entropy loss function.
- Deploy the resulting fine-tuned model with optimized evaluation-time decoding settings, designed to leverage the reshaped token distributions for improved performance.

## Results

- SSD consistently increased pass@1 scores across five evaluated models, with Qwen3-30B-Instruct improving by 12.9 percentage points (from 42.4% to 55.3%) on LiveCodeBench v6.
- Performance gains were disproportionately higher for more challenging problems, showing pass@1 gains of up to 15.3pp and pass@5 gains of 23.0pp on hard problems for Qwen3-30B-Instruct.
- The SSD-trained model substantially outperformed the best-tuned base model configuration by 11.8pp for Qwen3-30B-Instruct pass@1, indicating that SSD's changes are not achievable through decoding parameter adjustments alone.

## Takeaways

- Simple Self-Distillation (SSD) alleviates the "precision-exploration conflict" by context-dependently reshaping the model's token distributions, suppressing distractors at "locks" while maintaining useful diversity at "forks."
- SSD induces fundamental changes within the model's learned distributions that cannot be replicated by merely adjusting inference-time decoding parameters on the original model.
- The method's benefits stem from distributional reshaping (support compression and within-support smoothing) rather than the superficial correctness of individual self-generated training samples, as improvements persist even with intentionally degraded training data.

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
- ro
- ru
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d4bff-833f-7d1e-bb18-25fb1ef24565/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d4bff-833f-7d1e-bb18-25fb1ef24565/transcript.json
- Transcript lines: 15
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Mixed
- Headline: Mostly Human, AI Detected
- Fraction AI: 0.16347297
- Fraction AI-assisted: 0.04946369
- Fraction human: 0.78706336

## Resources

- GitHub repository: https://github.com/apple/ml-ssd

## Similar Papers

- Reinforcement Learning via Self-Distillation (2601.20802v2): Researchers from ETH Zurich, Max Planck Institute, MIT, and Stanford developed Self-Distillation Policy Optimization (SDPO), an on-policy algorithm that trains large language models by transforming rich environmental feedback into dense, token-level learning signals. This method yields a 10x speedup in training time, requires 4x fewer generations to reach baseline accuracy on competitive programming tasks, and enables solution discovery for hard problems with 3x fewer generations.
- Teaching Language Models to Critique via Reinforcement Learning (2502.03492v2): Researchers from The University of Hong Kong and ByteDance introduced CTRL, a reinforcement learning framework for training a specialized LLM critic to provide effective and actionable feedback, particularly for code generation. This framework achieved up to 106.1% relative Pass@1 improvements on code benchmarks and demonstrated weak-to-strong generalization, where a weaker critic guides a stronger generator, without relying on human-annotated critiques.
- Integrating Symbolic Execution into the Fine-Tuning of Code-Generating LLMs (2504.15210v2): Researchers at TU Darmstadt developed a method to integrate symbolic execution into the fine-tuning process of code-generating Large Language Models. This approach significantly enhanced the accuracy of reward models, demonstrating a 37.19% improvement over the baseline, though its direct impact on the code-generating actor models' pass@5 scores was limited.
- QueST: Incentivizing LLMs to Generate Difficult Problems (2510.17715v1): QueST, a framework from the University of Zurich and Microsoft Research, trains large language models to generate difficult competitive coding problems at an unprecedented scale. This enables an 8B model, fine-tuned on the generated synthetic data, to achieve code reasoning performance on par with a 671B model, establishing a new Pareto optimum.
- Teaching Large Language Models to Self-Debug (2304.05128v2): Researchers from Google DeepMind and UC Berkeley developed SELF-DEBUGGING, an iterative prompting framework that enables large language models to autonomously identify and correct errors in their generated code. This approach, which incorporates 'rubber duck debugging' through self-explanation and external execution feedback, achieves state-of-the-art performance and significantly improves sample efficiency across various coding tasks like text-to-SQL and code translation.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
