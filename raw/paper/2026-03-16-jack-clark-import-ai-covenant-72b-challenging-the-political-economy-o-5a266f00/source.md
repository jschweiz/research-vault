---
id: 2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
kind: paper
title: 'COVENANT-72B: Challenging the political economy of AI via distributed training'
source_url: https://arxiv.org/abs/2603.08163
source_name: Import AI
authors:
- Covenant AI
published_at: '2026-03-16T12:30:50Z'
ingested_at: '2026-04-09T20:15:46.484507Z'
content_hash: 26c0c1af974c64e5777adfd88ad3a0ce1edb3e81952a016609ba21ee8ff4827b
identity_hash: fc7e5465b5f29f0e78c0546e8ce8b969768196cf37c39124da4457231b09f260
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- llm
- distributed training
- blockchain
- model training
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text::story::2:https://arxiv.org/abs/2603.08163
canonical_url: https://arxiv.org/abs/2603.08163
doc_role: derived
parent_id: 2026-03-16-jack-clark-import-ai-importai-449-llms-training-other-llms-72b-distri-4e9550da
index_visibility: visible
fetched_at: '2026-04-13T18:14:58.281991Z'
short_summary: Covenant-72B is a 72B parameter LLM trained via a distributed process using blockchain coordination, demonstrating that democratized training is feasible at scale. The training involved ~1.1T tokens and was coordinated by ~20 peers running distributed GPU setups.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:34.731980Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: c2733862b0396e7ddb8cfd4e556d62d75b11a2ea349681f799374ccda0e1b392
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 35c62a77ef88b14bcfb2a1311f0cf6fa0abedeef01612c857185150188ff9ed6
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses distributed training methods for LLMs, which aligns perfectly with the user's favorite topics of LLM training, efficiency, and research tooling.
  evidence_quotes:
  - Covenant-72B is a 72B parameter LLM trained via a distributed process using blockchain coordination, demonstrating that democratized training is feasible at sca
  - The training involved ~1.1T tokens and was coordinated by ~20 peers running distributed GPU setups.
  - Distributed training is a technique that can change the political economy of AI by shifting the people at the frontier from monolithic ‘compute singletons’ (lik
---
# COVENANT-72B: Challenging the political economy of AI via distributed training

Source newsletter: ImportAI 449: LLMs training other LLMs; 72B distributed training run; computer vision is harder than generative text
Source issue: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text
Published At: 2026-03-16T12:30:50+00:00
Canonical URL: https://arxiv.org/abs/2603.08163

## Newsletter Context

…Distributed training via the blockchain notches up a meaningful win… A bunch of people have used the blockchain to coordinate the distributed training run of a 72B parameter model which matches the performance of LLaMA2, a model trained and released by Facebook in 2023. The model, Covenant 72B, is a dense decoder-only Transformer architecture model built in the LLaMA-3 style. “Our model, pre-trained on approximately 1.1T tokens, performs competitively with fully centralized models pre-trained on similar or higher compute budgets, demonstrating that fully democratized, non-whitelisted participation is not only feasible, but can be achieved at unprecedented scale for a globally distributed pre-training run,” writes Covenant AI, an organization dedicated to doing AI development on top of the blockchain.

Further details about the model and how it was trained : The model itself is basically a standard LLM that you would’ve been pleased to play with in 2023 or 2024, though might be a bit old fashioned in 2026. The truly unique aspect of it comes from it being trained in a distributed way, where ~20 distinct peers, each running 8xB200 GPUs, helped train it. Training was coordinated via Gauntlet, software developed by Covenant that runs on top of the Bittensor blockchain under Subnet 3. Gauntlet “enables permissionless training coordinated using a blockchain protocol by introducing a validator that scores submitted pseudo-gradients and selects which participants contribute to the global aggregation each round and broadcasts them to the network”. “In COVENANT-72B, each peer runs a SparseLoCo replica and the cross-peer communications occur through SparseLoCo’s heavily compressed pseudo-gradients,” the authors write. “Within each peer, 8×B200 GPUs use dynamic FSDP to shard model parameters, gradients, and training states across local GPUs.”

Data : “The training data comprises ∼1.1T tokens in total, split between the main and annealing phases. The main phase (∼1.09T tokens) consists of web text from DCLM, while the annealing phase uses higher-quality data [3, 5] (∼14.2B tokens). Specifically, the annealing phase uses a curated blend of instruction (∼27%), synthetic web (∼20%), code (15%), math (13%), and ~25% pre-training replay data from natural web text to mitigate forgetting”.

Performance: On MMLU, Covenant-72B gets a score of 67.1, versus 32.7 for INTELLECT-1 (a smaller AI model built via distributed training by Prime Intellect), and 65.7 for LLaMA-2-70B. A version of Covenant-72B that has been fine-tuned on ~15B tokens for conversational interaction has similarly good scores, getting 67.4 on MMLU versus 67.9 for K2-Chat (an open source model developed in 2025) and 63.1 for LLaMA-2-70B-Chat. For MATH, it gets 26.3, versus 19.1 for K2-Chat, and 10.7 for LLaMA-2-70B. “Compared to centralized-cluster training runs of similar parameter count, COVENANT-72B is broadly competitive. Notably, these centralized baselines were trained with conventional datacenter infrastructure and, in the case of LLaMA-2-70B, on substantially more tokens (2T vs. ∼1.1T,” they write.

Why this matters – who owns the future?: Distributed training is a technique that can change the political economy of AI by shifting the people at the frontier from monolithic ‘compute singletons’ (like labs such as Anthropic and OpenAI, and clouds like Google) to a larger federated collective. But for that to be true, distributed training needs to catch up to the frontier (more discussion from Epoch report in Import AI 439 ) – as impressive as Covenant is, it’s mostly a demonstration that distributed training can build some non-trivial models that have vague utility, but that’s a long way from the frontier – modern frontier models are trained on tens to hundreds of thousands of chips, whereas this was trained on perhaps ~160 or so (20 peers * 8 chips apiece). Nonetheless, it’s an important technology to track, and I could imagine a world where on-device AI features a lot of models developed via distributed training techniques, while on-cloud AI mostly runs on proprietary models trained on huge amounts of compute. Read more: Covenant-72B: Pre-Training a 72B LLM with Trustless Peers Over-the-Internet (arXiv) . Get the model here: Covenant, (HuggingFace) .
