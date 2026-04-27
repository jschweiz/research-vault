---
id: 2026-03-15-alphaxiv-paper-ai-can-learn-scientific-taste-d070f2ad
kind: paper
title: AI Can Learn Scientific Taste
source_url: https://www.alphaxiv.org/abs/2603.14473
source_name: alphaXiv Papers
authors:
- Jingqi Tong
- Mingzhe Li
- Hangcheng Li
- Yongzhuo Yang
- Yurong Mou
- Weijie Ma
- Zhiheng Xi
- Hongji Chen
- Xiaoran Liu
- Qinyuan Cheng
- Ming Zhang
- Qiguang Chen
- Weifeng Ge
- Qipeng Guo
- Tianlei Ying
- Tianxiang Sun
- Yining Zheng
- Xinchi Chen
- Jun Zhao
- Ning Ding
- Xuanjing Huang
- Yugang Jiang
- Xipeng Qiu
published_at: '2026-03-15T16:31:51Z'
ingested_at: '2026-04-09T23:36:20.503612Z'
content_hash: c9a26b90956efb4eda476a106daaf6f158203f7caf7af3727970e91ca1dc5125
identity_hash: 9a2bdfba3b53d035cc31631849cd953caf7f99061adac4c8cf840d629417c08f
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.CL
- github
- audio
- transcript
- summary
status: active
asset_paths:
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
external_key: https://www.alphaxiv.org/abs/2603.14473
canonical_url: https://www.alphaxiv.org/abs/2603.14473
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T23:36:20.503619Z'
short_summary: Researchers from Fudan University and collaborators developed OpenMOSS, an AI framework designed to acquire "scientific taste" for judging and generating high-impact research ideas. Their Reinforcement Learning from Community Feedback (RLCF) approach, which uses citation data as supervision, yielded a Scientific Judge model that surpassed leading proprietary LLMs in predicting paper impact and a Scientific Thinker model capable of generating research ideas with superior win rates against strong LLMs.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:42:59.250105Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: b6b1ee3b586d94365aa1bd326295fdf3edefe4a1c81a05bf3dc5b8bdf910a24b
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b+alphaxiv-metrics-v1
lightweight_scoring_input_hash: 1c8530e01c6b4bdda143a817fbbe305b3842436e1b40f11b40840f8b192301a8
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 1.0
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: 'This paper directly addresses post-training methods, reasoning, and evaluation for LLMs using Reinforcement Learning from Community Feedback. alphaXiv engagement signals: 195 public votes, 48 total votes, 301 visits in the last 7 days.'
  evidence_quotes:
  - Their Reinforcement Learning from Community Feedback (RLCF) approach, which uses citation data as supervision, yielded a Scientific Judge model that surpassed l
  - Scientific Judge models, such as SciJudge-Qwen3-30B, achieved an 80.6% accuracy on the in-domain SciJudgeBench, outperforming proprietary LLM baselines includin
  - The models demonstrated significant generalization, showing up to 55.1 percentage point accuracy improvements on temporal out-of-domain data and up to 72.0 perc
---
# AI Can Learn Scientific Taste

## alphaXiv Summary

Researchers from Fudan University and collaborators developed OpenMOSS, an AI framework designed to acquire "scientific taste" for judging and generating high-impact research ideas. Their Reinforcement Learning from Community Feedback (RLCF) approach, which uses citation data as supervision, yielded a Scientific Judge model that surpassed leading proprietary LLMs in predicting paper impact and a Scientific Thinker model capable of generating research ideas with superior win rates against strong LLMs.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2603.14473
- Source paper: https://arxiv.org/abs/2603.14473
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2603.14473v1.pdf
- Cover image: https://www.alphaxiv.org/image/2603.14473v1.png
- GitHub: https://github.com/tongjingqi/AI-Can-Learn-Scientific-Taste
- GitHub stars: 7
- Paper ID: 2603.14473
- Canonical ID: 2603.14473v1
- Paper group ID: 019cf974-5d41-74f8-ae60-26cc02fec05f
- Version ID: 019cf974-5d91-7504-ad4a-89cd6d24f626
- Version: v1
- Version order: 1
- Published at: 2026-03-15T16:31:51+00:00
- First published at: 2026-03-15T16:31:51+00:00
- Updated at: 2026-03-17T01:41:18.785000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Jingqi Tong
- Mingzhe Li
- Hangcheng Li
- Yongzhuo Yang
- Yurong Mou
- Weijie Ma
- Zhiheng Xi
- Hongji Chen
- Xiaoran Liu
- Qinyuan Cheng
- Ming Zhang
- Qiguang Chen
- Weifeng Ge
- Qipeng Guo
- Tianlei Ying
- Tianxiang Sun
- Yining Zheng
- Xinchi Chen
- Jun Zhao
- Ning Ding
- Xuanjing Huang
- Yugang Jiang
- Xipeng Qiu

## Topics

- Computer Science
- cs.CL

## Metrics

- Visits (all): 3024
- Visits (last 7 days): 301
- Total votes: 48
- Public total votes: 195
- X likes: 0

## Abstract

Great scientists have strong judgement and foresight, closely tied to what we call scientific taste. Here, we use the term to refer to the capacity to judge and propose research ideas with high potential impact. However, most relative research focuses on improving an AI scientist's executive capability, while enhancing an AI's scientific taste remains underexplored. In this work, we propose Reinforcement Learning from Community Feedback (RLCF), a training paradigm that uses large-scale community signals as supervision, and formulate scientific taste learning as a preference modeling and alignment problem. For preference modeling, we train Scientific Judge on 700K field- and time-matched pairs of high- vs. low-citation papers to judge ideas. For preference alignment, using Scientific Judge as a reward model, we train a policy model, Scientific Thinker, to propose research ideas with high potential impact. Experiments show Scientific Judge outperforms SOTA LLMs (e.g., GPT-5.2, Gemini 3 Pro) and generalizes to future-year test, unseen fields, and peer-review preference. Furthermore, Scientific Thinker proposes research ideas with higher potential impact than baselines. Our findings show that AI can learn scientific taste, marking a key step toward reaching human-level AI scientists.

## Problem

- Existing AI agents for scientific research primarily focus on executive tasks like literature search or automated experimentation, lacking the "scientific taste" to discern high-impact research ideas.
- Current large language models (LLMs) struggle to consistently differentiate between truly impactful research concepts and those that are superficially novel yet trivial.
- Traditional reinforcement learning methods (RLHF, RLVR) are limited by the high cost of human annotation or the lack of objective, verifiable ground-truth rewards in open-ended scientific domains.

## Method

- Introduced Reinforcement Learning from Community Feedback (RLCF), a three-stage training paradigm that leverages large-scale, naturally occurring community feedback (citations) as a supervisory signal.
- Developed SciJudgeBench, a dataset comprising 700,000 field- and time-matched paper abstract pairs with citation-based preference labels for training scientific judgment models.
- Trained "Scientific Judge" using Group Relative Policy Optimization (GRPO) to predict paper impact and "Scientific Thinker" using Scientific Judge as a generative reward model to generate high-impact research ideas via Comparison-Based GRPO.

## Results

- Scientific Judge models, such as SciJudge-Qwen3-30B, achieved an 80.6% accuracy on the in-domain SciJudgeBench, outperforming proprietary LLM baselines including GPT-5.2 and Gemini 3 Pro.
- The models demonstrated significant generalization, showing up to 55.1 percentage point accuracy improvements on temporal out-of-domain data and up to 72.0 percentage point gains on ICLR peer-review preferences.
- Scientific Thinker, trained with Scientific Judge, generated research ideas with higher potential impact, achieving an 81.5% in-domain win rate against its base policy and an average win rate of 54.2% when competing against ideas from strong proprietary LLMs.

## Takeaways

- "Scientific taste," encompassing the capacity to judge and propose high-impact research, is an empirically learnable objective for AI systems, extending beyond human intuition.
- Large-scale community feedback, specifically citation data, provides a scalable and effective supervisory signal for aligning AI with scientific values in complex, open-ended research domains.
- The learned scientific judgment capability generalizes robustly across different time periods (predicting future paper preferences), diverse scientific fields, and even aligns with independent peer-review evaluation metrics.

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

- MP3: https://paper-podcasts.alphaxiv.org/019cf974-5d41-74f8-ae60-26cc02fec05f/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019cf974-5d41-74f8-ae60-26cc02fec05f/transcript.json
- Transcript lines: 16
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Resources

- GitHub repository: https://github.com/tongjingqi/AI-Can-Learn-Scientific-Taste

## Similar Papers

- J1: Incentivizing Thinking in LLM-as-a-Judge via Reinforcement Learning (2505.10320v3): FAIR at Meta developed J1, an online reinforcement learning framework that explicitly optimizes chain-of-thought reasoning in LLMs acting as judges for other LLM responses. J1 models achieve state-of-the-art performance across five diverse benchmarks using only synthetic data, demonstrating robust generalizability and effectively mitigating positional bias.
- AI Idea Bench 2025: AI Research Idea Generation Benchmark (2504.14191v3): AI Idea Bench 2025 introduces a benchmark framework for quantitatively evaluating AI research ideas generated by Large Language Models, using a dataset of papers published after mainstream LLM knowledge cutoffs to mitigate data leakage. The framework employs diverse metrics to assess idea quality against ground truth and external references, revealing strengths and weaknesses of current idea generation approaches.
- DeepScientist: Advancing Frontier-Pushing Scientific Findings Progressively (2509.26603v1): DeepScientist, developed by WestlakeNLP, is an autonomous AI system that successfully surpassed human state-of-the-art on three frontier AI tasks within a month-long cycle, including a 142.8% improvement in agent failure attribution and a 7.9% higher AUROC for AI text detection. The system employs a goal-driven Bayesian optimization approach and a multi-agent architecture to conduct large-scale, iterative scientific exploration and validate findings.
- Alternating Reinforcement Learning for Rubric-Based Reward Modeling in Non-Verifiable LLM Post-Training (2602.01511v2): Rubric-ARM is a framework that jointly optimizes a rubric generator and a judge using alternating reinforcement learning for Large Language Model (LLM) post-training in complex, non-verifiable domains. It achieved an average reward modeling performance of 74.8% and enabled downstream policy models to reach up to 80.8% on instruction following benchmarks.
- Robust Reinforcement Learning from Human Feedback for Large Language Models Fine-Tuning (2504.03784v6): Variance-Reduced Preference Optimization (VRPO) enhances the robustness and sample efficiency of reinforcement learning from human feedback (RLHF) algorithms by leveraging a known reference policy and an auxiliary preference model. This framework, which addresses both preference and reward model misspecification, consistently achieves higher expected rewards and win rates across LLM fine-tuning tasks, alongside theoretical guarantees for variance reduction and double robustness.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
