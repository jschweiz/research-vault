---
id: page:2026-02-27-the-batch-research-stanford-and-together-ai-researchers-chart-edge--37b43f41
page_type: source-note
title: Stanford and Together.AI Researchers Chart Edge Models’ Performance in Intelligence Per Watt
aliases:
- Stanford and Together.AI Researchers Chart Edge Models’ Performance in Intelligence Per Watt
source_refs:
- 2026-02-27-the-batch-research-stanford-and-together-ai-researchers-chart-edge--37b43f41
backlinks:
- topic:cloud-computing
- topic:hardware-performance
- topic:intelligence-per-watt
- topic:large-language-models
- topic:local-computing
updated_at: '2026-04-09T23:08:05.939479Z'
managed: true
---
# Stanford and Together.AI Researchers Chart Edge Models’ Performance in Intelligence Per Watt

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/stanford-and-together-ai-researchers-chart-edge-models-performance-in-intelligence-per-watt
- Document kind: blog-post
- Published at: 2026-02-27T07:14:44-08:00
- Authors: Jon Saad-Falcon, Avanika Narayan
- Tags: deeplearning-ai, official, research, website, blog-post, large language models, intelligence per watt, local computing, cloud computing, hardware performance
- Topics: [Cloud Computing](../topics/cloud-computing.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Hardware Performance](../topics/hardware-performance.md), [Intelligence Per Watt](../topics/intelligence-per-watt.md), [Large Language Models](../topics/large-language-models.md), [Local Computing](../topics/local-computing.md)
- Trend score: 25.71
- Novelty score: 0.45

## Summary

Researchers found that while cloud systems are currently more energy-efficient per user, local systems are rapidly improving in intelligence per watt. This trend suggests that smaller, high-performance models running on local devices could enable significant energy savings by shifting AI workloads from the cloud.

## Topic Map

- [Cloud Computing](../topics/cloud-computing.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Hardware Performance](../topics/hardware-performance.md)
- [Intelligence Per Watt](../topics/intelligence-per-watt.md)
- [Large Language Models](../topics/large-language-models.md)
- [Local Computing](../topics/local-computing.md)

## Related Research

- [Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs](test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to--b1f1bd.md) (shared topics: Deeplearning Ai)
- [Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs](google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30--7835fb.md) (shared topics: Deeplearning Ai)
- [Claude Code’s Source Code Leaked, Exposing Potential Future Features Kairos and autoDream](claude-codes-source-code-leaked-exposing-potential-future-featur-2d1053.md) (shared topics: Deeplearning Ai)
- [Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window](recursive-language-models-offer-path-to-dramatically-expand-beyo-eade39.md) (shared topics: Deeplearning Ai)
- [Grok Imagine 1.0 Sharply Cuts Costs for High-Quality Video Generation](grok-imagine-1-0-sharply-cuts-costs-for-high-quality-video-gener-bc473a.md) (shared topics: Deeplearning Ai)
- [Nvidia’s Open Nemotron 3 Super 120B-A12B Model Sets New Paces In Its Class](nvidias-open-nemotron-3-super-120b-a12b-model-sets-new-paces-in--503103.md) (shared topics: Deeplearning Ai)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Projected demand for output from large language models is spurring a massive buildout of data centers. Researchers asked whether smaller models running on local devices could meaningfully lighten that load.
What’s new: Jon Saad-Falcon, Avanika Narayan, and colleagues at Stanford University and Together AI, a provider of software development and training, found that laptops are increasingly capable of substituting for cloud computing, based on a metric they call [intelligence per watt](https://arxiv.org/abs/2511.07885v2?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41).
Key insight: Cloud systems are typically more energy-efficient per user than local systems, but smaller, high-performance models increasingly enable local systems to run more efficiently. In a previous era, processing shifted from mainframes to personal computers when personal computers could perform well enough while using the same or less energy. Similarly, AI workloads can shift from data centers to personal devices if smaller models running on laptops can provide sufficient accuracy while using less energy per query. We can measure the viability of local versus cloud computing by computing intelligence per watt: the accuracy on a given task divided by the power consumed to achieve it. Assuming local and cloud systems achieve similar accuracy, the one with the higher intelligence per watt is a more efficient choice.
How it works: The authors ran various open-weights large language models on hardware designed for laptops and data-center servers. To measure the trend in intelligence per watt over time, they included both recent models (from the Qwen3, GPT-OSS, Gemma3, and IBM Granite 4.0 families, late-2025 vintage) and older models (Mixtral-8x7B and Llama -3.1-8B, circa 2023-2024), recent processors (including the Apple M4 Max laptop chip and Nvidia H100 data-center chip) and older processors (like the 2018-vintage Nvidia Quadro RTX 6000). They fed the models 1 million queries from [real-world conversations](https://arxiv.org/abs/2409.03753?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41), [science](https://arxiv.org/abs/2502.13124?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41), and [academic](https://arxiv.org/abs/2406.01574?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41) [disciplines](https://arxiv.org/abs/2502.14739?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41).
- To measure accuracy, the authors compared fixed outputs to ground truth and used GPT-4o to evaluate open-ended responses.
- Simultaneously, they recorded power consumption.
- The authors used this data to simulate an ideal system for routing the queries to models: For each query, they tracked the model — whether hosted locally or in the cloud — that responded correctly while using the least power, and assumed that model processed the query.
Results: Local systems don’t yet match cloud systems for intelligence per watt, but they are improving as researchers develop smaller models that achieve higher performance. If local systems are as accurate as cloud systems, routing queries to them could save substantial amounts of energy.
- Cloud-computing systems are more intelligent per watt. Smaller models that ran on the Nvidia B200 chip achieved at least 1.4x higher intelligence per watt than the same models running on local chips.
- However, in local systems, intelligence per watt has risen dramatically. Intelligence per watt rose 5.3 times between 2023 and 2025, driven by algorithmic advances and hardware im
