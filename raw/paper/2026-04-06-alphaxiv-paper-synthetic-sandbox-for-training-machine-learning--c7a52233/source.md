---
id: 2026-04-06-alphaxiv-paper-synthetic-sandbox-for-training-machine-learning--c7a52233
kind: paper
title: Synthetic Sandbox for Training Machine Learning Engineering Agents
source_url: https://www.alphaxiv.org/abs/2604.04872
source_name: alphaXiv Papers
authors:
- Yuhang Zhou
- Lizhu Zhang
- Yifan Wu
- Jiayi Liu
- Xiangjun Fan
- Zhuokai Zhao
published_at: '2026-04-06T17:19:29Z'
ingested_at: '2026-04-09T12:07:30.998655Z'
content_hash: bab9375e1882b278ad65dd2981791c6ac41347e5e96d20036c40b5a7ea54fafa
identity_hash: 6e689d26ab49e41bc13f647d9360998237dfca9d0a7763a6e4c53e0f6fd49585
tags:
- paper
- alphaxiv
- research
- agentic-frameworks
- agents
- computer science
- cs.cl
- cs.lg
- fine-tuning
- ml-systems
status: active
asset_paths:
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
external_key: https://www.alphaxiv.org/abs/2604.04872
canonical_url: https://www.alphaxiv.org/abs/2604.04872
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:07:30.998660Z'
short_summary: SandMLE is a framework that creates synthetic, micro-scale machine learning engineering environments to enable practical on-policy reinforcement learning for training LLM agents. This approach significantly reduces execution time and improves performance on MLE benchmarks compared to existing methods.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T14:34:23.207762Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 21e3750ee6503ba31e971c695a9d6dc76ad8ad62e34934e663a56c25fffeb1ec
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 4c951b56d4477eb0eaa33290d0063c5ad913ae3dbf240e5d495bbf82c2d6418d
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.5
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses the user's favorite topics of LLM agents, evaluation, and reinforcement learning in the context of machine learning engineering.
  evidence_quotes:
  - SandMLE is a framework that creates synthetic, micro-scale machine learning engineering environments to enable practical on-policy reinforcement learning for tr
  - SandMLE reduces average code execution time by 13.7 times, enabling Qwen3 models to achieve up to a 100.7% relative improvement in "Any Medal" rates on MLE-Benc
  - We observe that sandbox data size is the primary source of this bottleneck.
---
# Synthetic Sandbox for Training Machine Learning Engineering Agents

## alphaXiv Summary

SandMLE is a framework that creates synthetic, micro-scale machine learning engineering environments, making on-policy trajectory-wise reinforcement learning practical for training LLM agents. This approach reduces average code execution time by 13.7 times, enabling Qwen3 models to achieve up to a 100.7% relative improvement in "Any Medal" rates on MLE-Bench-Lite compared to baseline methods.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04872
- Source paper: https://arxiv.org/abs/2604.04872
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04872v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04872v1.png
- Paper ID: 2604.04872
- Canonical ID: 2604.04872v1
- Paper group ID: 019d65d7-7578-7816-83a9-18e52c67232c
- Version ID: 019d65d7-75b7-7cd6-8911-58cd23ba0104
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:19:29+00:00
- First published at: 2026-04-06T17:19:29+00:00
- Updated at: 2026-04-07T02:48:32.376000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Yuhang Zhou
- Lizhu Zhang
- Yifan Wu
- Jiayi Liu
- Xiangjun Fan
- Zhuokai Zhao
- Hong Yan

## Topics

- agentic-frameworks
- agents
- Computer Science
- cs.CL
- cs.LG
- fine-tuning
- ml-systems
- multi-agent-learning
- reinforcement-learning
- synthetic-data
- tool-use
- transformers

## Metrics

- Visits (all): 90
- Visits (last 7 days): 90
- Total votes: 3
- Public total votes: 13
- X likes: 0

## Abstract

As large language model agents advance beyond software engineering (SWE) tasks toward machine learning engineering (MLE), verifying agent behavior becomes orders of magnitude more expensive: while SWE tasks can be verified via fast-executing unit tests, MLE verification requires running full ML pipelines -- data preprocessing, model training, and metric evaluation -- on large datasets at each rollout step, rendering trajectory-wise on-policy reinforcement learning (RL) prohibitively slow. Existing approaches retreat to supervised fine-tuning (SFT) or offline proxy rewards, sacrificing the exploration and generalization benefits of on-policy RL. We observe that sandbox data size is the primary source of this bottleneck. Based on this insight, we introduce SandMLE, a multi-agent framework that generates diverse, verifiable synthetic MLE environments from a small number of seed tasks, preserving the structural and technical complexity of real-world problems while constraining datasets to micro-scale (each task is paired with only 50-200 training samples). Through extensive experiments, we show that SandMLE reduces execution time by over 13 times, enabling large-scale, on-policy trajectory-wise RL for the first time in the MLE domain. On MLE-bench-lite, SandMLE yields significant gains over SFT baselines across Qwen3-8B, 14B, and 30B-A3B, with relative medal rate improvements ranging from 20.3% to 66.9%. Furthermore, the trained policy generalizes across unseen agentic scaffolds, achieving up to 32.4% better HumanRank score on MLE-Dojo.

## Problem

- Applying on-policy trajectory-wise Reinforcement Learning (RL) to Machine Learning Engineering (MLE) tasks is computationally infeasible due to the long execution times of full ML pipelines.
- Each MLE code execution takes around 200 seconds, making the large-scale rollouts required for on-policy RL impractical.
- Existing methods like supervised fine-tuning (SFT) or step-wise RL with proxy rewards for MLE agents fail to leverage the exploration and generalization benefits of on-policy RL.

## Method

- Developed a multi-agent framework to autonomously generate diverse, verifiable synthetic MLE environments with micro-scale datasets (50-200 samples).
- Constrained synthetic datasets drastically reduce execution latency from approximately 200 seconds to about 14 seconds per task.
- Applied trajectory-wise Group Relative Policy Optimization (GRPO) with a dense, milestone-based reward function to train LLM agents effectively.

## Results

- Achieved a 13.7x speedup in average code execution time (from 196.17s to 14.31s) by using synthetic micro-datasets.
- SandMLE-trained Qwen3 models showed up to 100.7% relative improvement in "Any Medal" rates over base models on MLE-Bench-Lite and surpassed SFT baselines.
- Demonstrated robust generalization across various agent scaffolds and benchmarks, indicating transferable reasoning capabilities for trained LLM agents.

## Takeaways

- The primary bottleneck for applying on-policy RL to MLE tasks is the execution latency caused by dataset size, which can be overcome with micro-scale synthetic data.
- A multi-agent system can effectively generate a diverse curriculum of structurally complex yet computationally light synthetic MLE tasks.
- Dense, milestone-based reward functions are critical for stable and effective policy optimization in long-horizon, complex agentic tasks.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d7-7578-7816-83a9-18e52c67232c/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d7-7578-7816-83a9-18e52c67232c/transcript.json

## Similar Papers

- Agent World Model: Infinity Synthetic Environments for Agentic Reinforcement Learning (2602.10090v2): The Agent World Model (AWM) introduces an open-source, code-driven pipeline that synthesizes 1,000 diverse, executable tool-use environments with database-backed state for large-scale reinforcement learning of autonomous agents. Agents trained on these synthetic environments, developed collaboratively by UNC Chapel Hill and Snowflake, demonstrate strong out-of-distribution generalization across various real-world benchmarks, validating the approach for developing robust LLM agents.
- From Word to World: Can Large Language Models be Implicit Text-based World Models? (2512.18832v2): This research systematically explores whether large language models (LLMs) can serve as implicit text-based world models for agents, demonstrating that supervised fine-tuning enables them to reliably simulate multi-turn interactions. Fine-tuned LLMs achieved up to 99.87% exact match accuracy in structured environments and over 90% consistency for multi-step rollouts, showing utility in action verification, synthetic data generation, and policy warm-starting.
- SWE-Synth: Synthesizing Verifiable Bug-Fix Data to Enable Large Language Models in Resolving Real-World Bugs (2504.14757v2): SWE-Synth introduces a framework for synthesizing verifiable, process-aware bug-fix datasets at the repository level, enabling Large Language Models to learn iterative debugging strategies. Models fine-tuned on SWE-Synth data achieved a 15.3% resolve rate on SWE-Bench Lite, surpassing performance from manually curated datasets, with synthetic bugs often indistinguishable from real ones by human developers.
- Simulating Environments with Reasoning Models for Agent Training (2511.01824v1): This research introduces a method for training large language model (LLM) agents using other LLMs as environment simulators, achieving up to 14.4 point average score improvements on benchmarks like OfficeBench for open models compared to seed-tuned baselines. This approach enables scalable generation of high-quality training data and facilitates reinforcement learning without dedicated environment engineering.
- SWE-Universe: Scale Real-World Verifiable Environments to Millions (2602.02361v1): Alibaba Group's Qwen Team developed SWE-Universe, a framework to automatically construct over 800,000 real-world, multilingual, verifiable software engineering environments from GitHub PRs. This massive dataset significantly enhances coding agent capabilities, with the Qwen3-Max-Thinking model achieving 75.3% accuracy on SWE-Bench Verified and substantial gains on multilingual benchmarks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
