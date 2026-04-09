---
id: 2026-04-07-alphaxiv-paper-qimeng-prepair-precise-code-repair-via-edit-awar-1ae2d9d9
kind: paper
title: 'QiMeng-PRepair: Precise Code Repair via Edit-Aware Reward Optimization'
source_url: https://www.alphaxiv.org/abs/2604.05963
source_name: alphaXiv Papers
authors:
- Changxin Ke
- Rui Zhang
- Jiaming Guo
- Yuanbo Wen
- Li Ding
- Shuo Wang
- Xuyuan Zhu
- Xiong Peng
- Di Huang
- Zidong Du
- Xing Hu
- Qi Guo
- Yunji Chen
published_at: '2026-04-07T14:56:38Z'
ingested_at: '2026-04-09T09:57:28.144478Z'
content_hash: 21d764a03956ef2d508cc74b9f2387812258f8087f73256ba3c7624339359f2b
identity_hash: aee896b4bcbde041e065fe7923f2f6b06819edc62a843a225137cece04becd75
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.LG
- cs.SE
- fine-tuning
- inference-optimization
- optimization-methods
- reinforcement-learning
- sequence-modeling
- synthetic-data
- transformers
- github
- audio
- summary
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
external_key: https://www.alphaxiv.org/abs/2604.05963
canonical_url: https://www.alphaxiv.org/abs/2604.05963
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:57:28.144485Z'
short_summary: Researchers from the Chinese Academy of Sciences developed the PRepair framework to mitigate "over-editing" in large language model-based code repair, improving both the accuracy and precision of modifications. The framework, which utilizes a novel edit-aware reward optimization, increases repair precision ($fix_1@1$) by up to 31.41% on Verilog and accelerates inference by up to 15%.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# QiMeng-PRepair: Precise Code Repair via Edit-Aware Reward Optimization

## alphaXiv Summary

Researchers from the Chinese Academy of Sciences developed the PRepair framework to mitigate "over-editing" in large language model-based code repair, improving both the accuracy and precision of modifications. The framework, which utilizes a novel edit-aware reward optimization, increases repair precision ($fix_1@1$) by up to 31.41% on Verilog and accelerates inference by up to 15%.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05963
- Source paper: https://arxiv.org/abs/2604.05963
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05963v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05963v1.png
- GitHub: https://github.com/kcxain/QiMeng-PRepair
- GitHub stars: 0
- Paper ID: 2604.05963
- Canonical ID: 2604.05963v1
- Paper group ID: 019d6b07-3cd2-704b-8851-c142e79a56e3
- Version ID: 019d6b07-3d01-7834-900b-897743c460a5
- Version: v1
- Version order: 1
- Published at: 2026-04-07T14:56:38+00:00
- First published at: 2026-04-07T14:56:38+00:00
- Updated at: 2026-04-08T02:58:49.682000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Changxin Ke
- Rui Zhang
- Jiaming Guo
- Yuanbo Wen
- Li Ding
- Shuo Wang
- Xuyuan Zhu
- Xiong Peng
- Di Huang
- Zidong Du
- Xing Hu
- Qi Guo
- Yunji Chen

## Topics

- Computer Science
- cs.LG
- cs.SE
- fine-tuning
- inference-optimization
- optimization-methods
- reinforcement-learning
- sequence-modeling
- synthetic-data
- transformers

## Metrics

- Visits (all): 70
- Visits (last 7 days): 70
- Total votes: 1
- Public total votes: 9
- X likes: 0

## Abstract

Large Language Models (LLMs) achieve strong program repair performance but often suffer from over-editing, where excessive modifications overwrite correct code and hinder bug localization. We systematically quantify its impact and introduce precise repair task, which maximizes reuse of correct code while fixing only buggy parts. Building on this insight, we propose PRepair, a framework that mitigates over-editing and improves repair accuracy. PRepair has two components: Self-Breaking, which generates diverse buggy programs via controlled bug injection and min-max sampling, and Self-Repairing, which trains models with Edit-Aware Group Relative Policy Optimization (EA-GRPO) using an edit-aware reward to encourage minimal yet correct edits. Experiments show that PRepair improves repair precision by up to 31.4% under $\mathrm{fix}_1@1$, a metric that jointly considers repair correctness and extent, and significantly increases decoding throughput when combined with speculative editing, demonstrating its potential for precise and practical code repair.

## Problem

- Large Language Models (LLMs) for code repair frequently "over-edit" by regenerating extensive code, hindering bug localization and maintainability.
- Existing LLM-based repair methods struggle with data scarcity for precise, minimal fixes and lack mechanisms to preserve correct code during training.
- Over-editing degrades code quality, increases developer cognitive load during review, and negatively impacts the efficiency of inference mechanisms like speculative decoding.

## Method

- The PRepair framework employs a "Self-Breaking" stage to generate high-quality, diverse buggy programs with preserved correct logic.
- An "Edit-Aware Group Relative Policy Optimization" (EA-GRPO) is introduced, dynamically applying an edit penalty based on group accuracy to balance repair correctness with minimal modifications.
- A new metric, $fix_p@k$, quantifies repair performance by simultaneously assessing correctness and the precision of modifications relative to the theoretical minimum edit cost.

## Results

- PRepair with EA-GRPO increased $fix_1@1$ by up to 20.95% (Python) and 31.41% (Verilog), demonstrating a marked reduction in over-editing compared to baseline models.
- The framework preserved or enhanced repair correctness (pass@k) and showed improved cross-domain generalization, unlike naive correctness-only training which often led to degradation.
- Precise repairs from EA-GRPO led to up to 15% faster inference throughput via speculative decoding, contrasting with throughput degradation observed from over-editing models.

## Takeaways

- Optimizing LLMs for repair correctness alone leads to an "over-editing" phenomenon where models make extensive, unnecessary changes.
- Incorporating dynamic, edit-aware reward shaping into policy optimization can guide LLMs to perform precise repairs while sustaining or improving overall correctness.
- Precise code repair, characterized by minimal edits, inherently enhances inference efficiency in speculative decoding by increasing draft token acceptance rates.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b07-3cd2-704b-8851-c142e79a56e3/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b07-3cd2-704b-8851-c142e79a56e3/transcript.json

## Resources

- GitHub repository: https://github.com/kcxain/QiMeng-PRepair

## Similar Papers

- ContrastRepair: Enhancing Conversation-Based Automated Program Repair via Contrastive Test Case Pairs (2403.01971v2)
- SWE-Synth: Synthesizing Verifiable Bug-Fix Data to Enable Large Language Models in Resolving Real-World Bugs (2504.14757v2): SWE-Synth introduces a framework for synthesizing verifiable, process-aware bug-fix datasets at the repository level, enabling Large Language Models to learn iterative debugging strategies. Models fine-tuned on SWE-Synth data achieved a 15.3% resolve rate on SWE-Bench Lite, surpassing performance from manually curated datasets, with synthetic bugs often indistinguishable from real ones by human developers.
- Teaching Large Language Models to Self-Debug (2304.05128v2): Researchers from Google DeepMind and UC Berkeley developed SELF-DEBUGGING, an iterative prompting framework that enables large language models to autonomously identify and correct errors in their generated code. This approach, which incorporates 'rubber duck debugging' through self-explanation and external execution feedback, achieves state-of-the-art performance and significantly improves sample efficiency across various coding tasks like text-to-SQL and code translation.
- Fully Autonomous Programming using Iterative Multi-Agent Debugging with  Large Language Models (2503.07693v1): Researchers at Simula, University of Oslo, TU Eindhoven, and Philips Research developed SEIDR, a multi-agent framework for iterative debugging of LLM-generated code. This approach significantly increases the success rate of autonomous programming tasks by addressing the "near-miss syndrome" in LLM outputs, demonstrating improved problem-solving capabilities across Python and C++.
- FGIT: Fault-Guided Fine-Tuning for Code Generation (2503.16913v4)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
