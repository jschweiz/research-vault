---
id: page:2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
page_type: source-note
title: Mistral Small 3 | Mistral AI
aliases:
- Mistral Small 3 | Mistral AI
source_refs:
- 2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
backlinks:
- page:2025-03-17-mistral-research-mistral-small-3-1-mistral-ai-8a888094
- page:2025-07-30-mistral-research-announcing-codestral-25-08-and-the-complete-mist-98053d11
- topic:3-mistral-ai
updated_at: '2026-04-09T12:15:42.550703Z'
managed: true
---
# Mistral Small 3 | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/mistral-small-3
- Document kind: blog-post
- Published at: 2025-01-30T12:00:00+00:00
- Tags: mistral, official, research, website, blog-post
- Topics: [Evaluations](../topics/evaluations.md), [Mistral](../topics/mistral.md), [Official](../topics/official.md), [Website](../topics/website.md), [Inference](../topics/inference.md), [3 Mistral Ai](../topics/3-mistral-ai.md)
- Trend score: 56.46
- Novelty score: 1.80

## Topic Map

- [Evaluations](../topics/evaluations.md)
- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Inference](../topics/inference.md)
- [3 Mistral Ai](../topics/3-mistral-ai.md)

## Related Research

- [Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI](announcing-codestral-25-08-and-the-complete-mistral-coding-stack-cdf219.md) (shared topics: Evaluations, Inference, Mistral, Official, Website)
- [Mistral Small 3.1 | Mistral AI](mistral-small-3-1-mistral-ai-5dc4fa.md) (shared topics: Evaluations, Inference, Mistral, Official, Website)
- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Evaluations, Mistral, Official, Website)
- [Introducing Mistral Small 4 | Mistral AI](introducing-mistral-small-4-mistral-ai-2b9baa.md) (shared topics: Inference, Mistral, Official, Website)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Evaluations, Mistral, Official, Website)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Evaluations, Mistral, Official, Website)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Today we’re introducing Mistral Small 3, a latency-optimized 24B-parameter model released under the Apache 2.0 license.
Mistral Small 3 is competitive with larger models such as Llama 3.3 70B or Qwen 32B, and is an excellent open replacement for opaque proprietary models like GPT4o-mini. Mistral Small 3 is on par with Llama 3.3 70B instruct, while being more than 3x faster on the same hardware.
Mistral Small 3 is a pre-trained and instructed model catered to the ‘80%’ of generative AI tasks—those that require robust language and instruction following performance, with very low latency.
We designed this new model to saturate performance at a size suitable for local deployment. Particularly, Mistral Small 3 has far fewer layers than competing models, substantially reducing the time per forward pass. At over 81% accuracy on MMLU and 150 tokens/s latency, Mistral Small is currently the most efficient model of its category.
We’re releasing both a pretrained and instruction-tuned checkpoint under Apache 2.0. The checkpoints can serve as a powerful base for accelerating progress. Note that Mistral Small 3 is neither trained with RL nor synthetic data, so is earlier in the model production pipeline than models like Deepseek R1 (a great and complementary piece of open-source technology!). It can serve as a great base model for building accrued reasoning capacities. We look forward to seeing how the open-source community adopts and customizes it.
Performance
Human Evaluations
We conducted side by side evaluations with an external third-party vendor, on a set of over 1k proprietary coding and generalist prompts. Evaluators were tasked with selecting their preferred model response from anonymized generations produced by Mistral Small 3 vs another model. We are aware that in some cases the benchmarks on human judgement starkly differ from publicly available benchmarks, but have taken extra caution in verifying a fair evaluation. We are confident that the above benchmarks are valid.
Instruct performance
Our instruction tuned model performs competitively with open weight models three times its size and with proprietary GPT4o-mini model across Code, Math, General knowledge and Instruction following benchmarks.
Performance accuracy on all benchmarks were obtained through the same internal evaluation pipeline - as such, numbers may vary slightly from previously reported performance ([Qwen2.5-32B-Instruct](https://qwenlm.github.io/blog/qwen2.5-llm/), [Llama-3.3-70B-Instruct](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct), [Gemma-2-27B-IT](https://huggingface.co/google/gemma-2-27b-it)). Judge based evals such as Wildbench, Arena hard and MTBench were based on gpt-4o-2024-05-13.
Pretraining performance
Mistral Small 3, a 24B model, offers the best performance for its size class and rivals with models three times larger such as Llama 3.3 70B.
When to use Mistral Small 3
Across our customers and community, we are seeing several distinct use cases emerge for pre-trained models of this size:
- Fast-response conversational assistance: Mistral Small 3 excels in scenarios where quick, accurate responses are critical. This includes virtual assistants in many scenarios where users expect immediate feedback and near real-time interactions.
- Low-latency function calling: Mistral Small 3 is able to handle rapid function execution when used as part of automated or agentic workflows.
- Fine-tuning to create subject matter experts: Mistral Small 3 can be fine-tuned to specialize in specific domains, creating highly accurate subject matter experts. This is particularly useful in fields like legal advice, medical diagnostics, and technical support, where domain-specific knowledge is essential.
- Local inference: Particularly beneficial for hobbyists and organizations handling sensitive or proprietary information. When quantized, Mistral Small 3 can be run privately on a single RTX 4090 or a Macbook with 32GB RAM.
Our customers are evaluating Mistral Sm
