---
id: page:2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
page_type: source-note
title: Embarrassingly Simple Self-Distillation Improves Code Generation
aliases:
  - Embarrassingly Simple Self-Distillation Improves Code Generation
source_refs:
  - 2026-04-01-alphaxiv-paper-embarrassingly-simple-self-distillation-improves-93a70f44
backlinks:
  - page:2026-04-03-alphaxiv-paper-self-distilled-rlvr-597ff1e6
  - page:2026-04-06-alphaxiv-paper-a-frame-is-worth-one-token-efficient-generative--a948963c
  - topic:fine-tuning
  - topic:generative-models
  - topic:instruction-tuning
  - topic:knowledge-distillation
  - topic:language-modeling
updated_at: 2026-04-08T07:14:52.333865Z
managed: true
---
# Embarrassingly Simple Self-Distillation Improves Code Generation

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.01193
- Document kind: paper
- Published at: 2026-04-01T17:39:50+00:00
- Authors: Ruixiang Zhang, Richard He Bai, Huangjie Zheng, Navdeep Jaitly, Ronan Collobert, Yizhe Zhang
- Tags: paper, alphaxiv, research, computer science, cs.cl, fine-tuning, generative-models, instruction-tuning, knowledge-distillation, model-interpretation
- Topics: [Fine-Tuning](../topics/fine-tuning.md), [Computer Science](../topics/computer-science.md), [Generative Models](../topics/generative-models.md), [Instruction Tuning](../topics/instruction-tuning.md), [Knowledge Distillation](../topics/knowledge-distillation.md), [Language Modeling](../topics/language-modeling.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# Embarrassingly Simple Self-Distillation Improves Code Generation ## alphaXiv Summary A method called Simple Self-Distillation (SSD) enables large language models to enhance their code generation performance by training exclusively on self-generated, unverified solutions. This approach improved the Qwen3-30B-Instruct model's pass@1 score on LiveCodeBench v6 from 42.4% to 55.3%, demonstrating its efficacy without external supervision or complex verification.

## Topic Map

- [Fine-Tuning](../topics/fine-tuning.md)
- [Computer Science](../topics/computer-science.md)
- [Generative Models](../topics/generative-models.md)
- [Instruction Tuning](../topics/instruction-tuning.md)
- [Knowledge Distillation](../topics/knowledge-distillation.md)
- [Language Modeling](../topics/language-modeling.md)

## Related Research

- [Self-Distilled RLVR](self-distilled-rlvr-1944ab.md) (shared topics: Computer Science, Fine-Tuning, Knowledge Distillation)
- [A Frame is Worth One Token: Efficient Generative World Modeling with Delta Tokens](a-frame-is-worth-one-token-efficient-generative-world-modeling-w-98472f.md) (shared topics: Computer Science, Generative Models)
- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Computer Science, Language Modeling)
- [MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale](mineru2-5-pro-pushing-the-limits-of-data-centric-document-parsin-394662.md) (shared topics: Computer Science, Language Modeling)
- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Computer Science, Language Modeling)
- [JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency](joyai-llm-flash-advancing-mid-scale-llms-with-token-efficiency-ea0c5b.md) (shared topics: Computer Science, Fine-Tuning)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Embarrassingly Simple Self-Distillation Improves Code Generation

## alphaXiv Summary

A method called Simple Self-Distillation (SSD) enables large language models to enhance their code generation performance by training exclusively on self-generated, unverified solutions. This approach improved the Qwen3-30B-Instruct model's pass@1 score on LiveCodeBench v6 from 42.4% to 55.3%, demonstrating its efficacy without external supervision or complex verification.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.01193
- Source paper: https://arxiv.org/abs/2604.01193
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.01193v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.01193v1.png
- GitHub: https://github.com/apple/ml-ssd
- GitHub stars: 2
- Paper ID: 2604.01193
- Canonical ID: 2604.01193v1
- Paper group ID: 019d4bff-833f-7d1e-bb18-25fb1ef24565
- Version ID: 019d4bff-8374-72cf-a6d5-e902fd357539
- Version: v1
- Version order: 1
- Published at: 2026-04-01T17:39:50+00:00
- First published at: 2026-04-01T17:39:50+00:00
- Updated at: 2026-04-02T02:22:09.727000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Ruixiang Zhang
- Richard He Bai
- Huangjie Zheng
- Navdeep Jaitly
- Ronan Collobert
- Yizhe Zhang

## Topics

- Computer Science
- cs.CL
- fine-tuning
- generative-models
- instruction-tuning
- knowledge-distillation
- model-interpretation
- self-supervised-learning
- text-generation
- transformers

## Metrics

- Visits (all): 3248
- Visits (last 7 days): 3248
- Total votes: 60
- Public total votes: 173
- X likes: 0

## Abstract

Can a large language model (LLM) improve at code generation using only its own raw outputs, without a verifier, a teacher model, or reinforcement learning? We answer in the affirmative with simple self-distillation (SSD): sample solutions from the model with certain temperature and truncation configurations, then fine-tune on those samples with standard supervised fine-tuning. SSD improves Qwen3-30B-Instruct from 42.4% to 55.3% pass@1 on LiveCodeBench v6, with gains concentrating on harder problems, and it generalizes across Qwen and Llama models at 4B, 8B, and 30B scale, including both instruct and thinking variants. To understand why such a simple method can work, we trace these gains to a precision-exploration conflict in LLM decoding and show that SSD reshapes token distributions in a context-dependent way, suppressing distractor tails where precision matters while preserving useful diversity where exploration matters. Taken together, SSD offers a complementary post-training direction for improving LLM code generation.

## Problem

- High cost and difficulty of obtaining high-quality supervised training signals for LLM code generation, limiting scalability.
- Limitations of existing self-improvement methods, including performance ceilings for teacher-based distillation and operational complexities or instabilities in RL and unsupervised intrinsic reward systems.
- An inherent "precision-exploration conflict" in LLM decoding for code, where a single global temperature setting struggles to balance precise token generation at constrained points with necessary exploration for diverse algorithmic choices.

## Method

- Introduce Simple Self-Distillation (SSD), where a frozen base LLM generates a single candidate solution for each problem prompt using specific training-time decoding configurations, without any external verification.
- Fine-tune the base LLM on this self-generated, unverified dataset using standard supervised fine-tuning with a cross-entropy loss function.
- Deploy the resulting fine-tuned model with optimized evaluation-time decoding settings, designed to leverage the reshaped token distributions for improved performance.

## Results

- SSD consistently increased pass@1 scores across five evaluated models, with Qwen3-30B-Instruct improving by 12.9 percentage points (from 42.4% to 55.3%) on LiveCodeBench v6.
- Performance
