---
id: page:2026-03-09-jack-clark-import-ai-bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-480da18e
page_type: source-note
title: ByteDance finetunes a Seed1.6 model to be a CUDA-writing agent
aliases:
- ByteDance finetunes a Seed1.6 model to be a CUDA-writing agent
source_refs:
- 2026-03-09-jack-clark-import-ai-bytedance-finetunes-a-seed1-6-model-to-be-a-cuda-480da18e
backlinks:
- page:2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
- page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
- topic:cuda
updated_at: '2026-04-09T23:10:03.608548Z'
managed: true
---
# ByteDance finetunes a Seed1.6 model to be a CUDA-writing agent

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://profile.py/
- Document kind: article
- Published at: 2026-03-09T12:45:54+00:00
- Authors: ByteDance, Tsinghua University
- Tags: newsletter, ai, analysis, policy, website, article, cuda, llm, agent, machine learning, sub-document
- Topics: [Agents](../topics/agents.md), [Infrastructure](../topics/infrastructure.md), [Cuda](../topics/cuda.md), [Llm](../topics/llm.md), [Machine Learning](../topics/machine-learning.md), [Newsletter](../topics/newsletter.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

ByteDance researchers fine-tuned a Seed1.6 LLM to create a CUDA-writing agent called CUDA Agent. This agent demonstrated state-of-the-art performance in CUDA kernel development, significantly boosting performance over baseline models.

## Topic Map

- [Agents](../topics/agents.md)
- [Infrastructure](../topics/infrastructure.md)
- [Cuda](../topics/cuda.md)
- [Llm](../topics/llm.md)
- [Machine Learning](../topics/machine-learning.md)
- [Newsletter](../topics/newsletter.md)

## Related Research

- [What Is an LLM? A No-Jargon Introduction](what-is-an-llm-a-no-jargon-introduction-9f47cf.md) (shared topics: Llm, Machine Learning, Newsletter)
- [Meta uses a harness to coax Anthropic’s models into self-improvement](meta-uses-a-harness-to-coax-anthropics-models-into-self-improvem-032241.md) (shared topics: Agents, Llm, Newsletter)
- [COVENANT-72B: Challenging the political economy of AI via distributed training](covenant-72b-challenging-the-political-economy-of-ai-via-distrib-2822a2.md) (shared topics: Infrastructure, Llm, Newsletter)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Agents, Machine Learning, Newsletter)
- [Perplexity rolls out startup competition focused on building companies powered entirely by Computer agents](perplexity-rolls-out-startup-competition-focused-on-building-com-6788e5.md) (shared topics: Agents, Newsletter)
- [Cursor enables running agents on any machine while controlling them remotely from your phone](cursor-enables-running-agents-on-any-machine-while-controlling-t-27a349.md) (shared topics: Agents, Newsletter)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# ByteDance finetunes a Seed1.6 model to be a CUDA-writing agent

Source newsletter: Import AI 448: AI R&D; Bytedance’s CUDA-writing agent; on-device satellite AI
Source issue: https://jack-clark.net/2026/03/09/import-ai-448-ai-rd-bytedances-cuda-writing-agent-on-device-satellite-ai
Published At: 2026-03-09T12:45:54+00:00
Canonical URL: https://profile.py/

## Newsletter Context

…Using AI to finetune AI to write code to train future AI systems… Researchers with ByteDance and Tsinghua University have built CUDA Agent, a fine-tuned AI model for writing GPU programming code. The research is another sign of how people are increasingly using AI to speedup core aspects of AI development. It’s also vaguely notable for the fact that a major Chinese lab and university continues to use US-made chips (NVIDIA H20s) versus homegrown ones.

What CUDA Agent is: CUDA agent is a finetuned Seed 1.6 LLM, an MOE model with 23B active parameters and 230B total parameters. Finetuning took place on a cluster of 128 NVIDIA H20 GPUs. CUDA Agent has been developed specifically for writing GPU code by being fine-tuned on a dataset refined out of the underlying PyTorch ‘torch’ and ‘transformers’ software libraries. “The filtered synthesized training dataset contains 6,000 samples, forming CUDA-Agent-Ops-6K, a curated operator-level dataset for training CUDA-capable agents,” the authors write.

Turning a model into an agent: In the last year or so, researchers have repeatedly shown that you can increase the performance of an LLM for a given task by giving it access to some specialized tools and some specialized instructions, then letting it operate over time – this is essentially an AI agent. The CUDA agent here is the fine-tuned model that has been turned into an agent by adopting the OpenHands framework, then given tools including BashTool, GlobTool, MultiEditTool, TodoWriteTool. The agent runs in a four stage loop:

- Analyze performance of the native PyTorch implementation of a given bit of CUDA code using the provided profile.py script
- Implement custom CUDA operators by rewriting the model in model_new.py
- Compile and evaluate the optimized model in the provided GPU sandbox environment
- Repeat the optimization process until the implementation achieves a 5% speedup over the torch.compile baseline

Results: The resulting agent is very good at CUDA kernel development: “CUDA Agent successfully scales to a context length of 128k tokens and supports up to 200 interaction turns, achieving state-of-the-art performance,” they write. Their finetuning massively boosts performance from a base rate of 74% for Seed1.6, to “100%, 100%, and 92% over torch.compile on the Level-1, Level-2, and Level-3 splits of KernelBench, outperforming advanced proprietary models such as Claude Opus 4.5 and Gemini 3 Pro by approximately 40% in the Level-3 split.” However, comparing against other base models paints a different story: Claude Opus 4.5 and Gemini 3 Pro base models get 95.2% and 91.2% respectively, suggesting that if they were finetuned, you’d increase their performance as well, and they start from a much stronger baseline.

Why this matters – building AI that builds AI: These results show how modern AI systems are increasingly good at the tasks required to develop and deploy AI systems themselves. This suggests we’re at the beginning of a compounding speedup where new AI models will be used to increase the efficiency of the infrastructure with which their successors will be trained. Read more: CUDA Agent: Large-Scale Agentic RL for High-Performance CUDA Kernel Generation (arXiv) .
