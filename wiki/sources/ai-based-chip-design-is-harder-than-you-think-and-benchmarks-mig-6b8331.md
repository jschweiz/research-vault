---
id: page:2026-02-09-jack-clark-import-ai-ai-based-chip-design-is-harder-than-you-think-an-333f3a92
page_type: source-note
title: AI-based chip design is harder than you think and benchmarks might be too easy
aliases:
- AI-based chip design is harder than you think and benchmarks might be too easy
source_refs:
- 2026-02-09-jack-clark-import-ai-ai-based-chip-design-is-harder-than-you-think-an-333f3a92
backlinks:
- page:2026-02-02-jack-clark-import-ai-one-way-of-seeing-ai-progress-how-hard-its-getti-b88405ad
- page:2026-02-16-jack-clark-import-ai-can-ai-agents-independently-do-basic-ai-research-3ef778a6
- page:2026-02-23-jack-clark-import-ai-chinese-researchers-try-to-build-a-truly-compreh-8bac5c2d
- page:2026-03-02-jack-clark-import-ai-llms-are-still-very-bad-at-videogames-4b8298cd
- topic:chip-design
- topic:llm-evaluation
updated_at: '2026-04-09T23:10:02.222126Z'
managed: true
---
# AI-based chip design is harder than you think and benchmarks might be too easy

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2601.21448
- Document kind: paper
- Published at: 2026-02-09T14:03:34+00:00
- Authors: University of California at San Diego, Columbia University
- Tags: newsletter, ai, analysis, policy, website, paper, chip design, verilog, benchmarks, llm evaluation, sub-document
- Topics: [Evaluations](../topics/evaluations.md), [Chip Design](../topics/chip-design.md), [Llm Evaluation](../topics/llm-evaluation.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Sub Document](../topics/sub-document.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers developed ChipBench to evaluate how well modern AI systems can perform real-world chip design tasks in Verilog, finding that frontier models still struggle with general-purpose design.

## Topic Map

- [Evaluations](../topics/evaluations.md)
- [Chip Design](../topics/chip-design.md)
- [Llm Evaluation](../topics/llm-evaluation.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Sub Document](../topics/sub-document.md)

## Related Research

- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [Chinese researchers try to build a truly comprehensive LLM evaluation system](chinese-researchers-try-to-build-a-truly-comprehensive-llm-evalu-063f83.md) (shared topics: Evaluations, Llm Evaluation, Newsletter, Policy)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [One way of seeing AI progress – how hard it’s getting to design technical interviews](one-way-of-seeing-ai-progress-how-hard-its-getting-to-design-tec-cfca46.md) (shared topics: Evaluations, Newsletter, Policy, Sub Document)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy, Sub Document)
- [AI might let us build “political superintelligence”](ai-might-let-us-build-political-superintelligence-25b211.md) (shared topics: Newsletter, Policy, Sub Document)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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
- Self-Contained: 40% (Claude-4.5 Haiku, Opus, Gemini 2.5 Pro
