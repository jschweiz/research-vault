---
id: 2026-02-09-jack-clark-import-ai-ai-based-chip-design-is-harder-than-you-think-an-333f3a92
kind: paper
title: AI-based chip design is harder than you think and benchmarks might be too easy
source_url: https://arxiv.org/abs/2601.21448
source_name: Import AI
authors:
- University of California at San Diego
- Columbia University
published_at: '2026-02-09T14:03:34Z'
ingested_at: '2026-04-09T20:16:51.909931Z'
content_hash: a63540318ddede0be432bc6e93a33f02ecabe48fa00f0fa07abb272191fd1351
identity_hash: 792afa15e7fa6774c2428bd2d9b58c30b3cbad55339e77f9bf64808406b637c5
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- chip design
- verilog
- benchmarks
- llm evaluation
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench::story::2:https://arxiv.org/abs/2601.21448
canonical_url: https://arxiv.org/abs/2601.21448
doc_role: derived
parent_id: 2026-02-09-jack-clark-import-ai-import-ai-444-llm-societies-huawei-makes-kernels-6922e476
index_visibility: visible
fetched_at: '2026-04-09T20:16:51.909937Z'
short_summary: Researchers developed ChipBench to evaluate how well modern AI systems can perform real-world chip design tasks in Verilog, finding that frontier models still struggle with general-purpose design.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:43.827303Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: dc0b25dd5fb6a430840d750e1ba273854605ec44d6e08abd534686396015a12a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 115eeafde5da9fe5be7df5e2a81b51c4c959089835b3c59bc887c66ab84dbfa9
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses LLM evaluation and reasoning in the context of complex, real-world tasks like chip design, aligning perfectly with the user's favorite topics.
  evidence_quotes:
  - Researchers developed ChipBench to evaluate how well modern AI systems can perform real-world chip design tasks in Verilog, finding that frontier models still s
  - ChipBench shows that no frontier model is great at real world Verilog yet… Researchers with the University of California at San Diego and Columbia University ha
  - The authors “identify three critical limitations of existing benchmarks that hinder accurate assessment of LLM capabilities for industrial deployment”.
---
# AI-based chip design is harder than you think and benchmarks might be too easy

Source newsletter: Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench
Source issue: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
Published At: 2026-02-09T14:03:34+00:00
Canonical URL: https://arxiv.org/abs/2601.21448

## Newsletter Context

…ChipBench shows that no frontier model is great at real world Verilog yet… Researchers with the University of California at San Diego and Columbia University have published ChipBench, a benchmark designed to test out how well modern AI systems can design chips in Verilog. The inspiration for ChipBench is dissatisfaction with current benchmarks, which they claim are too simple. When tested on ChipBench, no frontier model does particularly well, suggesting that open-ended, real world chip design is still a hard task for AI systems.

The deficiencies of current chip design: The authors “identify three critical limitations of existing benchmarks that hinder accurate assessment of LLM capabilities for industrial deployment”. These are that:

- Many Verilog benchmarks contain simple functional modules ranging from 10 to 76 lines. In real-world deployments, Verilog modules exceed 10,000 lines.
- Insufficient focus on debugging: Bugs cost a lot in physical hardware, so it may be better to concentrate on using LLMs for debugging chip designs.
- Verilog focus detracts from reference model evaluation: “In industrial workflows, reference model generation is even more resource-intensive than Verilog design, reflected in a 1:1 – 5:1 ratio of verification engineers (write reference model) to design engineers (write Verilog)”.

ChipBench : ChipBench tests out AI systems on three distinct competencies – writing Verilog code, debugging Verilog code, and writing reference models.

- Verilog writing: Based on 44 modules from real world hardware. “Our dataset features 3.8x longer code length and 13.9x more cells than VerilogEval.” These tests have three categories: self-contained module tests, hierarchical modules that are non-self-contained, and CPU IP modules sourced directly from open-source CPU projects.
- Verilog debugging : 89 test cases covering four error types: timing, arithmetic, assignment, and state machine bugs. These tests were built by manually injecting faults into known-good Verilog modules. Provides two types of debugging tests: zero-shot and one-shot. “The zero-shot test provides the model with the module description and buggy implementation, indicating that an error exists without providing localization details. The one-shot test provides identical information but supplements it with simulation waveform data (.vcd files)”.
- Reference model generation : 132 samples, enabling evaluation of reference model generation across Python, SystemC, and CXXRTL.

How well do modern systems do? The authors test out some decent frontier models from OpenAI (GPT 3.5, 4o, 5, and 5.2), Anthropic (Claude 4.5 Haiku, Sonnet, and Opus), Google (Gemini 2.5 Pro, and 3 Flash), Meta (LLaMa3.1 8B and 80B), and DeepSeek (V3.2). No model does well: “Despite testing on advanced models, the average pass@1 is relatively low,” they write.

- Verilog generation: CPU IP: Highest is 22.22% (Claude 4.5 Opus, Gemini 3 Flash, GPT 5.2) Non-Self-Contained: Highest is 50% (DeepSeek-Coder) Self-contained: Highest is 36.67% (Claude 4.5 Opus, Gemini 3 Flash)
- CPU IP: Highest is 22.22% (Claude 4.5 Opus, Gemini 3 Flash, GPT 5.2)
- Non-Self-Contained: Highest is 50% (DeepSeek-Coder)
- Self-contained: Highest is 36.67% (Claude 4.5 Opus, Gemini 3 Flash)

- Python reference model generation: CPU IP: 11.1% (Claude 4.5 Sonnet, Gemini 3 Flash) Non-Self-Contained: 0% (pass@1). Self-Contained: 40% (Claude-4.5 Haiku, Opus, Gemini 2.5 Pro, GPT-5)
- CPU IP: 11.1% (Claude 4.5 Sonnet, Gemini 3 Flash)
- Non-Self-Contained: 0% (pass@1).
- Self-Contained: 40% (Claude-4.5 Haiku, Opus, Gemini 2.5 Pro, GPT-5)

- Verilog debugging: Generally better performance, but still no model cracks 50% pass@1 when averaged across tasks.
- Generally better performance, but still no model cracks 50% pass@1 when averaged across tasks.

Why this matters : Though some AI systems have been used to build chips, they’ve been typically highly specialized, or stuck inside incredibly good scaffolds for eliciting good chip design behavior and stopping them from causing problems. What the researchers show here is that out-of-the-box LLMs are still pretty shitty at doing general purpose, real world chip design: “Current models have significant limitations in AI-aided chip design and remain far from ready for real industrial workflow integration.” At the same time, I can’t escape the feeling that there’s a scaffold for “being good at Verilog” which a contemporary AI system might be able to build if asked to and which would radically improve performance of systems on this benchmark. Read more: ChipBench: A Next-Step Benchmark for Evaluating LLM Performance in AI-Aided Chip Design (arXiv) . Get the code for ChipBench here (GitHub) .
