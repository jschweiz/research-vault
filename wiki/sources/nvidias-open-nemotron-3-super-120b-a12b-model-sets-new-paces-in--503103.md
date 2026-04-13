---
id: page:2026-03-27-the-batch-research-nvidias-open-nemotron-3-super-120b-a12b-model-se-7cf0f41a
page_type: source-note
title: Nvidia’s Open Nemotron 3 Super 120B-A12B Model Sets New Paces In Its Class
aliases:
- Nvidia’s Open Nemotron 3 Super 120B-A12B Model Sets New Paces In Its Class
source_refs:
- 2026-03-27-the-batch-research-nvidias-open-nemotron-3-super-120b-a12b-model-se-7cf0f41a
backlinks: []
updated_at: '2026-04-09T23:08:05.636939Z'
managed: true
---
# Nvidia’s Open Nemotron 3 Super 120B-A12B Model Sets New Paces In Its Class

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/nvidias-open-nemotron-3-super-120b-a12b-model-sets-new-paces-in-its-class
- Document kind: blog-post
- Published at: 2026-03-27T07:06:06-07:00
- Authors: Nvidia
- Tags: deeplearning-ai, official, research, website, blog-post, large language model, open source, agentic applications, nvidia, deep learning
- Topics: [Agentic Applications](../topics/agentic-applications.md), [Deep Learning](../topics/deep-learning.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Large Language Model](../topics/large-language-model.md), [Nvidia](../topics/nvidia.md), [Official](../topics/official.md)
- Trend score: 68.20
- Novelty score: 3.20

## Summary

Nvidia released Nemotron 3 Super, a competitive open-source large language model designed for agentic applications, featuring a hybrid architecture and extensive training data. The model demonstrates fast performance and strong results in agentic tasks compared to other open-weights models.

## Topic Map

- [Agentic Applications](../topics/agentic-applications.md)
- [Deep Learning](../topics/deep-learning.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Large Language Model](../topics/large-language-model.md)
- [Nvidia](../topics/nvidia.md)
- [Official](../topics/official.md)

## Related Research

- [Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window](recursive-language-models-offer-path-to-dramatically-expand-beyo-eade39.md) (shared topics: Deep Learning, Deeplearning Ai, Official)
- [Alibaba’s Latest Flagship Qwen3.5 Models Are Open-Weights MoE Performers In Sizes from Less than 1B Parameters](alibabas-latest-flagship-qwen3-5-models-are-open-weights-moe-per-be882e.md) (shared topics: Deep Learning, Deeplearning Ai, Official)
- [Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs](test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to--b1f1bd.md) (shared topics: Deeplearning Ai, Official)
- [Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs](google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30--7835fb.md) (shared topics: Deeplearning Ai, Official)
- [Claude Code’s Source Code Leaked, Exposing Potential Future Features Kairos and autoDream](claude-codes-source-code-leaked-exposing-potential-future-featur-2d1053.md) (shared topics: Deeplearning Ai, Official)
- [Grok Imagine 1.0 Sharply Cuts Costs for High-Quality Video Generation](grok-imagine-1-0-sharply-cuts-costs-for-high-quality-video-gener-bc473a.md) (shared topics: Deeplearning Ai, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Nvidia, the dominant supplier of AI chips, released a competitive open-source large language model whose speed tops its size class — the first open-weights leader to come from the United States since last year, when Meta delivered Llama 4.
What’s new: Nvidia [released](https://developer.nvidia.com/blog/introducing-nemotron-3-super-an-open-hybrid-mamba-transformer-moe-for-agentic-reasoning/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz) Nemotron 3 Super 120B-A12B, a large language model designed for agentic applications, including not only weights but also training datasets and recipes. It is the second in a planned family of three: Nvidia [released](https://developer.nvidia.com/blog/inside-nvidia-nemotron-3-techniques-tools-and-data-that-make-it-efficient-and-accurate/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz) Nemotron 3 Nano-39B-A3B in December 2025, and Nemotron 3 Ultra-500B-A50B is forthcoming.
- Input/output: Text in (up to 1 million tokens), text out (up to 1 million tokens)
- Knowledge cutoff: June 2025 (pretraining data), February 2026 (fine-tuning data)
- Architecture: Hybrid mamba-2/transformer/mixture-of-experts with multi-token prediction layers (120 billion parameters, 12 billion active per token)
- Training data: 25 trillion tokens of curated data scraped from the web and synthesized in 20 natural languages and 43 programming languages
- Features: Tool calling, structured outputs, seven languages (Chinese, English, French, German, Italian, Japanese, Spanish), reasoning modes (off, low, regular)
- Performance: Fastest open-weights model of its size (442 output tokens per second), leads open-weights models on PinchBench test of agentic tasks
- Availability/price: Weights and datasets free to
[download](https://huggingface.co/collections/nvidia/nvidia-nemotron-v3?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz)under a license that permits noncommercial and commercial uses (rights terminate if safety guardrails are removed without replacement or if the user files patent or copyright litigation against Nvidia), free chat via[Nvidia](https://build.nvidia.com/nvidia/nemotron-3-super-120b-a12b?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz)and OpenRouter, API around $0.30/$0.80 per 1 million tokens of input/output via third-party providers
How it works: Nemotron 3 Super’s hybrid architecture interleaves mamba-2, attention, and modified MoE layers with multi-token prediction heads that generate a number of tokens per forward pass.
- Most of Nemotron 3 Super’s layers are
[mamba-2](https://arxiv.org/pdf/2405.21060?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz)layers. Unlike attention layers, which consume quadratically more processing power as input length increases, mamba-2 layers compress earlier context into a compact representation at each step. Nemotron 3 Super interleaves attention layers selectively to handle tasks that require precise retrieval from distant parts of an input, which mamba-2 layers struggle with. - The MoE layers use Nvidia’s
[LatentMoE](https://arxiv.org/abs/2601.18089?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9o2Recq645Sh94dkQERF-s-TPwoF7fmy7Bw20yk8Bg7em33UUSAF9nnQ3hCwDYUj56R_zz)design that compresses each token's representation to 1/4 its usual size before the MoE router decides which experts to activate. This compression enables the model to actiate 22 experts per token using roughly the same amount of processing power as five or six experts typically would requ
