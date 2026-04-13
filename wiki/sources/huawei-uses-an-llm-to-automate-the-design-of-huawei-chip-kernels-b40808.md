---
id: page:2026-02-09-jack-clark-import-ai-huawei-uses-an-llm-to-automate-the-design-of-hua-1fe2d7d6
page_type: source-note
title: Huawei uses an LLM to automate the design of Huawei chip kernels
aliases:
- Huawei uses an LLM to automate the design of Huawei chip kernels
source_refs:
- 2026-02-09-jack-clark-import-ai-huawei-uses-an-llm-to-automate-the-design-of-hua-1fe2d7d6
backlinks:
- page:2026-02-09-jack-clark-import-ai-gemini-solves-some-erdos-problems-and-illustrate-f0eb84fe
- page:2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
- page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
- topic:huawei
- topic:kernel-design
- topic:npu
updated_at: '2026-04-09T23:10:03.314509Z'
managed: true
---
# Huawei uses an LLM to automate the design of Huawei chip kernels

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2601.22760
- Document kind: paper
- Published at: 2026-02-09T14:03:34+00:00
- Authors: Researchers with Nanjing University, Huawei
- Tags: newsletter, ai, analysis, policy, website, paper, llm, huawei, kernel design, npu, sub-document
- Topics: [Huawei](../topics/huawei.md), [Kernel Design](../topics/kernel-design.md), [Llm](../topics/llm.md), [Newsletter](../topics/newsletter.md), [Npu](../topics/npu.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers used LLMs to automate the design of kernels for Huawei chip kernels by developing a two-stage pipeline called AscendCraft. This method achieved high compilation success and functional correctness, demonstrating AI's potential to accelerate hardware kernel development.

## Topic Map

- [Huawei](../topics/huawei.md)
- [Kernel Design](../topics/kernel-design.md)
- [Llm](../topics/llm.md)
- [Newsletter](../topics/newsletter.md)
- [Npu](../topics/npu.md)
- [Policy](../topics/policy.md)

## Related Research

- [Meta uses a harness to coax Anthropic’s models into self-improvement](meta-uses-a-harness-to-coax-anthropics-models-into-self-improvem-032241.md) (shared topics: Llm, Newsletter, Policy)
- [COVENANT-72B: Challenging the political economy of AI via distributed training](covenant-72b-challenging-the-political-economy-of-ai-via-distrib-2822a2.md) (shared topics: Llm, Newsletter, Policy)
- [Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI](gemini-solves-some-erdos-problems-and-illustrates-the-challenges-c4e0ea.md) (shared topics: Llm, Newsletter, Policy)
- [OpenAI #16: A History and a Proposal](openai-16-a-history-and-a-proposal-a6e162.md) (shared topics: Newsletter, Policy)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy)
- [Startups that adopt AI for internal use are more successful than those that don’t](startups-that-adopt-ai-for-internal-use-are-more-successful-than-b0b397.md) (shared topics: Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Huawei uses an LLM to automate the design of Huawei chip kernels

Source newsletter: Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench
Source issue: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
Published At: 2026-02-09T14:03:34+00:00
Canonical URL: https://arxiv.org/abs/2601.22760

## Newsletter Context

…LLMs need scaffolds for more obscure chips… Researchers with Nanjing University and Huawei have used LLMs to help automate the design of kernels for AscendC Huawei chips, as a further symptom of how modern AI systems can accelerate their own development.

AscendCraft: AscendCraft is software for automating the generation of code for Huawei kernels. Modern LLMs can generate quite good kernel code for widely used chips like NVIDIA GPUs, but relatively obscure chips like Huawei are less well understood by LLMs, mostly due to data availability. “Publicly available NPU kernel implementations are far scarcer than GPU counterparts, limiting the training corpus for LLMs,” the authors write. “The lack of largescale, high-quality NPU code makes it difficult for LLMs to generate correct and efficient kernels”.

What they did: To build AscendCraft, the authors developed a two stage pipeline. In stage one, they have an LLM build “a high-level DSL program that describes the kernel’s core computation, tiling strategy, and on-chip dataflow.” The DSL is “designed to be LLM-friendly, appropriately abstracted, and sufficiently expressive to capture high-performance NPU kernel designs” – I think of it as basically a scaffold to focus the LLM around the specifics of building kernels for Huawei hardware. In the second stage, they “”transcompile the DSL into AscendC code through a sequence of structured LLM-based lowering passes, each responsible for translating a specific aspect of the DSL into valid and efficient AscendC constructs”.

Slightly odd thing: Strangely, the paper doesn’t disclose precisely which LLM is used here.

The results: They test out a range of kernels built in this way on MultiKernelBench. In their tests, they find that “AscendCraft achieves 98.1% compilation success and 90.4% functional correctness. Moreover, 46.2% of generated kernels match or exceed PyTorch eager execution performance”. This is promising enough performance that it’s going to be worth them continuing with this research, but not so good that it instantly knocks things out of the park and revolutionizes how kernels for Huawei chips get made. Nonetheless, the signs are clear: we can use AI to accelerate the optimizing of AI hardware, even for systems which are relatively new and/or underdiscussed in the pre-training corpus LLMs are trained on. Read more : AscendCraft: Automatic Ascend NPU Kernel Generation via DSL-Guided Transcompilation (arXiv) .
