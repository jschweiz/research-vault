---
id: 2026-04-07-alphaxiv-paper-can-large-language-models-reinvent-foundational--425cd036
kind: paper
title: Can Large Language Models Reinvent Foundational Algorithms?
source_url: https://www.alphaxiv.org/abs/2604.05716
source_name: alphaXiv Papers
authors:
- Jian Zhao
- Haoren Luo
- Yu Wang
- Yuhan Cao
- Pingyue Sheng
- Tianxing He
published_at: '2026-04-07T11:15:22Z'
ingested_at: '2026-04-09T09:59:36.280908Z'
content_hash: f27aa0e9d6cd93d47acf6647def5cc9a258d6d5f801c89c12e50a486abc10ee8
identity_hash: 97c85170b41d9b27ce3a3d9d775b5a3c51202cc28fbbb7a1eb57170e5c9f3499
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.AI
- deep-reinforcement-learning
- generative-models
- human-ai-interaction
- model-interpretation
- reasoning
- reasoning-verification
- test-time-inference
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
external_key: https://www.alphaxiv.org/abs/2604.05716
canonical_url: https://www.alphaxiv.org/abs/2604.05716
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:59:36.280914Z'
short_summary: Researchers from Xiongan AI Institute and Tsinghua University introduce an "Unlearn-and-Reinvent" pipeline to evaluate whether Large Language Models can invent foundational algorithms after explicitly forgetting them. The strongest unlearned model successfully reinvented 50% of ten target algorithms without hints, demonstrating an inherent capacity for algorithmic invention beyond memorization.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Can Large Language Models Reinvent Foundational Algorithms?

## alphaXiv Summary

Researchers from Xiongan AI Institute and Tsinghua University introduce an "Unlearn-and-Reinvent" pipeline to evaluate whether Large Language Models can invent foundational algorithms after explicitly forgetting them. The strongest unlearned model successfully reinvented 50% of ten target algorithms without hints, demonstrating an inherent capacity for algorithmic invention beyond memorization.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05716
- Source paper: https://arxiv.org/abs/2604.05716
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05716v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05716v1.png
- GitHub: https://github.com/Algo-Reinvention/algo-reinvention
- GitHub stars: 0
- Paper ID: 2604.05716
- Canonical ID: 2604.05716v1
- Paper group ID: 019d6b79-9003-7bda-90e4-99639829fd8c
- Version ID: 019d6b79-9017-75fc-a000-6d8ed947e783
- Version: v1
- Version order: 1
- Published at: 2026-04-07T11:15:22+00:00
- First published at: 2026-04-07T11:15:22+00:00
- Updated at: 2026-04-08T05:03:42.083000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Jian Zhao
- Haoren Luo
- Yu Wang
- Yuhan Cao
- Pingyue Sheng
- Tianxing He

## Topics

- Computer Science
- cs.AI
- deep-reinforcement-learning
- generative-models
- human-ai-interaction
- model-interpretation
- reasoning
- reasoning-verification
- test-time-inference
- transformers

## Metrics

- Visits (all): 25
- Visits (last 7 days): 25
- Total votes: 0
- Public total votes: 3
- X likes: 0

## Abstract

LLMs have shown strong potential to advance scientific discovery. Whether they possess the capacity for foundational innovation, however, remains an open question. In this work, we focus on a prerequisite for foundational innovation: can LLMs reinvent foundational algorithms in computer science? Our \textit{Unlearn-and-Reinvent} pipeline applies LLM unlearning to remove a specific foundational algorithm, such as Dijkstra's or Euclid's algorithm, from an LLM's pretrained knowledge, and then tests whether the model can reinvent it in a controlled environment. To enable effective unlearning, we adopt a GRPO-based, on-policy unlearning method. Across 10 target algorithms, 3 strong open-weight models, and 3 hint levels, our experiments demonstrate that (1) the strongest model Qwen3-4B-Thinking-2507 successfully reinvents 50% of the algorithms with no hint, 70% at hint level 1, and 90% at hint level 2; (2) a few high-level hints can enhance the reinvention success rate, but even step-by-step hints fail for those complicated algorithms; and (3) test-time reinforcement learning enables successful reinvention for the Strassen algorithm at hint level 2. Through analyses of output trajectories and ablation studies, we find that generative verifier in the reinvention phase plays a critical role in sustaining models' reasoning strength, helping to avoid the ``thought collapse'' phenomenon. These findings offer insights into both the potential and current limits of LLMs' innovative thinking.

## Problem

- It is challenging to distinguish if Large Language Models (LLMs) truly invent algorithms or merely recall them from vast training data, which inherently contains knowledge of foundational algorithms.
- Retraining LLMs from scratch on data explicitly excluding target algorithms is computationally prohibitive for testing pure invention.
- A controlled and computationally efficient experimental setup is needed to assess LLMs' intrinsic capacity for foundational algorithmic discovery.

## Method

- The "Unlearn-and-Reinvent" pipeline was developed, consisting of an unlearning phase to remove specific algorithmic knowledge and a reinvention phase to assess independent discovery.
- A Group Relative Policy Optimization (GRPO)-based unlearning method with a multi-dimensional reward function was employed to achieve near-complete forgetting while preserving the LLM's general utility.
- The reinvention phase featured an interactive coding environment with a generative verifier providing diagnostic feedback, coupled with hierarchical hint levels and test-time reinforcement learning to aid exploration and optimization.

## Results

- The best-performing unlearned model, Qwen3-4B-Thinking-2507, reinvented 50% of the 10 target algorithms with no hints, achieving an average Reinvention Success Rate (RSR) of 21.8%.
- External hints significantly improved reinvention, with high-level hints increasing RSR to 48.5% and step-by-step hints raising it to 80.9% for the top model.
- Test-time reinforcement learning enabled the reinvention of Strassen's algorithm at 62.5% success for correct outputs and improved solution efficiency for other algorithms, even for those not fully reinvented from zero success.
- The GRPO-based unlearning method achieved an average forgetting rate between 96.0% and 100.0% while largely preserving the models' general utility on standard benchmarks.

## Takeaways

- LLMs possess a genuine capacity for algorithmic invention, as evidenced by successfully reinventing foundational algorithms after their knowledge was explicitly unlearned.
- The ability of LLMs to invent new algorithms is bounded by complexity, performing better with algorithms reachable via incremental search but struggling with those requiring non-intuitive design or complex invariants.
- Interactive diagnostic feedback from a generative verifier and test-time reinforcement learning are crucial for sustaining LLM reasoning, preventing "thought collapse," and enabling discovery of complex or efficient solutions.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b79-9003-7bda-90e4-99639829fd8c/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b79-9003-7bda-90e4-99639829fd8c/transcript.json

## Resources

- GitHub repository: https://github.com/Algo-Reinvention/algo-reinvention

## Similar Papers

- Does Reinforcement Learning Really Incentivize Reasoning Capacity in LLMs Beyond the Base Model? (2504.13837v5): Research from Tsinghua University reveals that current Reinforcement Learning with Verifiable Rewards (RLVR) primarily enhances the sampling efficiency of Large Language Models for already existing reasoning patterns. This optimization often narrows the models' overall reasoning capacity at higher pass@k values, contrasting with distillation, which effectively expands their problem-solving scope.
- DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning (2501.12948v2): DeepSeek-AI developed DeepSeek-R1, an LLM demonstrating that sophisticated reasoning capabilities can emerge through pure outcome-based reinforcement learning without reliance on human-annotated reasoning trajectories. The model achieved an AIME 2024 pass@1 accuracy of 77.9% with R1-Zero, and the multi-stage DeepSeek-R1 surpassed state-of-the-art models on numerous math, coding, and STEM benchmarks while exhibiting emergent self-reflection and dynamic strategy adaptation.
- Combinatorial Optimization for All: Using LLMs to Aid Non-Experts in Improving Optimization Algorithms (2503.10968v2): Researchers at the Artificial Intelligence Research Institute (IIIA-CSIC) investigated the ability of Large Language Models (LLMs) to enhance existing combinatorial optimization algorithms for non-expert users, using a simple prompting strategy across ten diverse algorithms. Their methodology improved the performance of nine out of ten tested algorithms, with the best LLM-generated code outperforming originals in solution quality or convergence time, sometimes also reducing code complexity.
- Learning to Discover at Test Time (2601.16175v2): TTT-Discover introduces a reinforcement learning approach that trains large language models during testing to achieve new state-of-the-art solutions in complex scientific and engineering problems. This method leverages an open-source LLM to adapt and learn iteratively, surpassing previous benchmarks in mathematics, GPU kernel optimization, and algorithm design.
- Algorithm Discovery With LLMs: Evolutionary Search Meets Reinforcement Learning (2504.05108v4): Researchers at EPFL developed EvoTune, an iterative framework that tightly integrates large language model (LLM) based evolutionary search with reinforcement learning (RL) for algorithm discovery. This approach continuously refines the LLM's generative policy, leading to faster and more efficient discovery of high-performing and robust algorithms across various tasks, including combinatorial optimization, symbolic regression, and competitive programming.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
