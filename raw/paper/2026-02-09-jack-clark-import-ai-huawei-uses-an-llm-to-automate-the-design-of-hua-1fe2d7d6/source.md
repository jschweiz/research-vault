---
id: 2026-02-09-jack-clark-import-ai-huawei-uses-an-llm-to-automate-the-design-of-hua-1fe2d7d6
kind: paper
title: Huawei uses an LLM to automate the design of Huawei chip kernels
source_url: https://arxiv.org/abs/2601.22760
source_name: Import AI
authors:
- Researchers with Nanjing University
- Huawei
published_at: '2026-02-09T14:03:34Z'
ingested_at: '2026-04-09T20:16:53.047731Z'
content_hash: 9549f998cc1e76a9f3e6143d670f6b979ce81af8181c94e43b2aff39be72affb
identity_hash: e2b337992d0e2bf0f248f5f1763fc4a442cd016898a743830ddc46986d3147e5
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- llm
- huawei
- kernel design
- npu
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench::story::4:https://arxiv.org/abs/2601.22760
canonical_url: https://arxiv.org/abs/2601.22760
doc_role: derived
parent_id: 2026-02-09-jack-clark-import-ai-import-ai-444-llm-societies-huawei-makes-kernels-6922e476
index_visibility: visible
fetched_at: '2026-04-09T20:16:53.047736Z'
short_summary: Researchers used LLMs to automate the design of kernels for Huawei chip kernels by developing a two-stage pipeline called AscendCraft. This method achieved high compilation success and functional correctness, demonstrating AI's potential to accelerate hardware kernel development.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:43.942798Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 8479aad0f90e54b71f6be56dee79972b3ebfa9b765f2e97f10e602ef1c8eff02
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 684f9bf6a1f2e791dff4ca05678f29e6e210f85cdba16d0e8f25f22d76cfcb1f
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 0.95
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses the user's favorite topics of LLMs and research tooling in the context of hardware kernel design.
  evidence_quotes:
  - Researchers used LLMs to automate the design of kernels for Huawei chip kernels by developing a two-stage pipeline called AscendCraft.
  - This method achieved high compilation success and functional correctness, demonstrating AI's potential to accelerate hardware kernel development.
  - 'Nonetheless, the signs are clear: we can use AI to accelerate the optimizing of AI hardware, even for systems which are relatively new and/or underdiscussed in '
---
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
