---
id: 2026-02-27-the-batch-research-stanford-and-together-ai-researchers-chart-edge--37b43f41
kind: blog-post
title: Stanford and Together.AI Researchers Chart Edge Models’ Performance in Intelligence Per Watt
source_url: https://www.deeplearning.ai/the-batch/stanford-and-together-ai-researchers-chart-edge-models-performance-in-intelligence-per-watt
source_name: The Batch Research
authors:
- Jon Saad-Falcon
- Avanika Narayan
published_at: '2026-02-27T07:14:44-08:00'
ingested_at: '2026-04-09T20:54:57.537965Z'
content_hash: 3da41d334a7eb56bad96810ddbf881520090be4730442ac40240e14f9b791d33
identity_hash: 3f1bbd9b683ac9cbf5e82a3c18c6fe9c5de222fbf81fc643ba60852d9d800710
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- large language models
- intelligence per watt
- local computing
- cloud computing
- hardware performance
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/stanford-and-together-ai-researchers-chart-edge-models-performance-in-intelligence-per-watt
canonical_url: https://www.deeplearning.ai/the-batch/stanford-and-together-ai-researchers-chart-edge-models-performance-in-intelligence-per-watt
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T21:59:46.529421Z'
short_summary: Researchers found that while cloud systems are currently more energy-efficient per user, local systems are rapidly improving in intelligence per watt. This trend suggests that smaller, high-performance models running on local devices could enable significant energy savings by shifting AI workloads from the cloud.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:48.042146Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 2d14f4ce672adfd1280afda299e557a374c79a526998db617b6ce6720a24203d
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: c096b79e2dd121ec48a1776b96534ce7c6ae2c264b1b01e97552556a5afdea67
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.9
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: This document directly addresses efficiency and performance trade-offs in LLM deployment, which aligns perfectly with the user's favorite topics of efficiency, reasoning, and architecture.
  evidence_quotes:
  - Researchers found that while cloud systems are currently more energy-efficient per user, local systems are rapidly improving in intelligence per watt.
  - 'We can measure the viability of local versus cloud computing by computing intelligence per watt: the accuracy on a given task divided by the power consumed to a'
  - In simulated hybrid scenarios, power savings exceeded 80 percent.
---
Projected demand for output from large language models is spurring a massive buildout of data centers. Researchers asked whether smaller models running on local devices could meaningfully lighten that load.
What’s new: Jon Saad-Falcon, Avanika Narayan, and colleagues at Stanford University and Together AI, a provider of software development and training, found that laptops are increasingly capable of substituting for cloud computing, based on a metric they call [intelligence per watt](https://arxiv.org/abs/2511.07885v2?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41).
Key insight: Cloud systems are typically more energy-efficient per user than local systems, but smaller, high-performance models increasingly enable local systems to run more efficiently. In a previous era, processing shifted from mainframes to personal computers when personal computers could perform well enough while using the same or less energy. Similarly, AI workloads can shift from data centers to personal devices if smaller models running on laptops can provide sufficient accuracy while using less energy per query. We can measure the viability of local versus cloud computing by computing intelligence per watt: the accuracy on a given task divided by the power consumed to achieve it. Assuming local and cloud systems achieve similar accuracy, the one with the higher intelligence per watt is a more efficient choice.
How it works: The authors ran various open-weights large language models on hardware designed for laptops and data-center servers. To measure the trend in intelligence per watt over time, they included both recent models (from the Qwen3, GPT-OSS, Gemma3, and IBM Granite 4.0 families, late-2025 vintage) and older models (Mixtral-8x7B and Llama -3.1-8B, circa 2023-2024), recent processors (including the Apple M4 Max laptop chip and Nvidia H100 data-center chip) and older processors (like the 2018-vintage Nvidia Quadro RTX 6000). They fed the models 1 million queries from [real-world conversations](https://arxiv.org/abs/2409.03753?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41), [science](https://arxiv.org/abs/2502.13124?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41), and [academic](https://arxiv.org/abs/2406.01574?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41) [disciplines](https://arxiv.org/abs/2502.14739?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--_6hmb3DGhckxFQ9Gf4Kr2IIQwrEhiiAuElBhJrqd3pK_MzbJGcrUQx3Cg7YhH_DLqBP41).
- To measure accuracy, the authors compared fixed outputs to ground truth and used GPT-4o to evaluate open-ended responses.
- Simultaneously, they recorded power consumption.
- The authors used this data to simulate an ideal system for routing the queries to models: For each query, they tracked the model — whether hosted locally or in the cloud — that responded correctly while using the least power, and assumed that model processed the query.
Results: Local systems don’t yet match cloud systems for intelligence per watt, but they are improving as researchers develop smaller models that achieve higher performance. If local systems are as accurate as cloud systems, routing queries to them could save substantial amounts of energy.
- Cloud-computing systems are more intelligent per watt. Smaller models that ran on the Nvidia B200 chip achieved at least 1.4x higher intelligence per watt than the same models running on local chips.
- However, in local systems, intelligence per watt has risen dramatically. Intelligence per watt rose 5.3 times between 2023 and 2025, driven by algorithmic advances and hardware improvements.
- In the authors’ analysis of single-turn chat and reasoning queries, local systems that ran smaller models were able to answer approximately 88.7 percent of queries correctly relative to cloud systems while consuming substantially less power. In simulated hybrid scenarios, power savings exceeded 80 percent.
Yes, but: The authors did not assess the intelligence per watt of proprietary models like OpenAI GPT-5, likely because it’s unclear how much power they use. However, they did compare the accuracy of proprietary models. The most accurate local model (Qwen3-14B) trailed behind GPT-5, Gemini-2.5-Pro, and Claude Sonnet 4.5 by 11 percent accuracy to 13 percent accuracy.
Why it matters: Researchers are improving large language models rapidly, making higher performing models for the same amount of power usage. Tracking this performance increase reveals the relative trade-off between power and performance over time. As that tradeoff tilts more and more towards low-power devices, people have more options. These options offer the potential to spread the computational load and enable machine intelligence to be distributed more widely.
We’re thinking: Privacy often drives the conversation around local AI. The prospect of rising intelligence per watt creates an intriguing economic argument.
