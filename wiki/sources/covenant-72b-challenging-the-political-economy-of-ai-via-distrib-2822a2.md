---
id: page:2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
page_type: source-note
title: 'COVENANT-72B: Challenging the political economy of AI via distributed training'
aliases:
- 'COVENANT-72B: Challenging the political economy of AI via distributed training'
source_refs:
- 2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
backlinks:
- page:2026-02-09-jack-clark-import-ai-gemini-solves-some-erdos-problems-and-illustrate-f0eb84fe
- page:2026-02-09-jack-clark-import-ai-huawei-uses-an-llm-to-automate-the-design-of-hua-1fe2d7d6
- page:2026-03-02-jack-clark-import-ai-the-agi-economy-most-labor-goes-to-the-machines--5bc18134
- page:2026-03-09-jack-clark-import-ai-bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-480da18e
- page:2026-03-16-jack-clark-import-ai-if-ai-writes-all-the-worlds-software-we-should-i-e3751112
- page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
- topic:blockchain
- topic:model-training
updated_at: '2026-04-09T23:10:03.127110Z'
managed: true
---
# COVENANT-72B: Challenging the political economy of AI via distributed training

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2603.08163
- Document kind: paper
- Published at: 2026-03-16T12:30:50+00:00
- Authors: Covenant AI
- Tags: newsletter, ai, analysis, policy, website, paper, llm, distributed training, blockchain, model training, sub-document
- Topics: [Infrastructure](../topics/infrastructure.md), [Blockchain](../topics/blockchain.md), [Llm](../topics/llm.md), [Model Training](../topics/model-training.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Covenant-72B is a 72B parameter LLM trained via a distributed run involving 20 peers, demonstrating that fully democratized, non-whitelisted participation is feasible for large-scale pre-training.

## Topic Map

- [Infrastructure](../topics/infrastructure.md)
- [Blockchain](../topics/blockchain.md)
- [Llm](../topics/llm.md)
- [Model Training](../topics/model-training.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)

## Related Research

- [Meta uses a harness to coax Anthropic’s models into self-improvement](meta-uses-a-harness-to-coax-anthropics-models-into-self-improvem-032241.md) (shared topics: Llm, Newsletter, Policy)
- [If AI writes all the world’s software, we should invest more in verification](if-ai-writes-all-the-worlds-software-we-should-invest-more-in-ve-0b8f88.md) (shared topics: Infrastructure, Newsletter, Policy)
- [ByteDance finetunes a Seed1.6 model to be a CUDA-writing agent](bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-writing-agent-49e5e1.md) (shared topics: Infrastructure, Llm, Newsletter)
- [The AGI economy – most labor goes to the machines, and humans shift to verification](the-agi-economy-most-labor-goes-to-the-machines-and-humans-shift-fbc912.md) (shared topics: Infrastructure, Newsletter, Policy)
- [Huawei uses an LLM to automate the design of Huawei chip kernels](huawei-uses-an-llm-to-automate-the-design-of-huawei-chip-kernels-b40808.md) (shared topics: Llm, Newsletter, Policy)
- [Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI](gemini-solves-some-erdos-problems-and-illustrates-the-challenges-c4e0ea.md) (shared topics: Llm, Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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

Why this matters – who owns the future?: Distributed training is a technique that can change the political economy of AI by shifting the people at the frontier from monolithic ‘compute singletons’ (like labs such as Anthropic and OpenAI, and clouds like Google) to a larger federated collective. But for that to be true, distributed training needs to catch up to the frontier (more discussion from E
