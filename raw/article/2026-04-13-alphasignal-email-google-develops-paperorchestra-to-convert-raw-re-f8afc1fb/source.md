---
id: 2026-04-13-alphasignal-email-google-develops-paperorchestra-to-convert-raw-re-f8afc1fb
kind: article
title: Google develops PaperOrchestra to convert raw research notes into structured LaTeX papers using multi-agent workflows
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5471fae9b546224f&lid=14tCxDXj1GUqXOdjg&mid=71283719-f4b6-4cbd-9dd5-0bc3234264fd
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-13T16:38:35Z'
ingested_at: '2026-04-13T18:06:30.587612Z'
content_hash: 1d9dd865932a87b67428efdc56dafbaaffb9a4da4c3daf78aaed181e1bbb3701
identity_hash: d70a30a301bbb7d3f031177f8ed100fa5ced4e8d98394253850c15ad09307d5c
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- paperorchestra
- multi-agent
- latex
- research
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d87b58cc66a24b::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5471fae9b546224f&lid=14tCxDXj1GUqXOdjg&mid=71283719-f4b6-4cbd-9dd5-0bc3234264fd
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5471fae9b546224f&lid=14tCxDXj1GUqXOdjg&mid=71283719-f4b6-4cbd-9dd5-0bc3234264fd
doc_role: derived
parent_id: 2026-04-13-alphasignal-email-anthropic-ultraplan-cloud-planning-local-executi-2c453f7a
index_visibility: visible
fetched_at: '2026-04-13T18:06:30.587617Z'
short_summary: Google developed PaperOrchestra, a multi-agent framework that converts raw research notes into structured LaTeX papers. It uses specialized agents for outlining, literature retrieval, plotting, and writing to generate full manuscripts.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:07.793217Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 05e897a7c4dfadb9d409b2e383dfac4f59ebc24348aa6de5aeca7af49f626259
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: d36b14d7e2e3bc30d75851d242250a8fbf8fd661ee59e926bc17e958ce3998c5
lightweight_score:
  relevance_score: 0.75
  source_fit_score: 0.5
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: This document directly addresses post-training methods and evaluation for LLMs using a multi-agent framework, which aligns perfectly with the user's favorite topics.
  evidence_quotes:
  - PaperOrchestra introduces a multi-agent framework that generates full research manuscripts from unstructured materials like idea summaries and experiment logs.
  - The evaluation uses a benchmark built from reverse-engineered conference paper inputs.
  - It addresses a gap where existing systems depend on fixed pipelines and produce shallow literature reviews.
---
# Google develops PaperOrchestra to convert raw research notes into structured LaTeX papers using multi-agent workflows

Source newsletter: 🛠️ Anthropic Ultraplan: Cloud Planning + Local Execution for Claude
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-13T16:38:35+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5471fae9b546224f&lid=14tCxDXj1GUqXOdjg&mid=71283719-f4b6-4cbd-9dd5-0bc3234264fd

## Newsletter Context

Section: Top Paper

> 2,836 Likes

PaperOrchestra introduces a multi-agent framework that generates full research manuscripts from unstructured materials like idea summaries and experiment logs.

It addresses a gap where existing systems depend on fixed pipelines and produce shallow literature reviews. In human evaluations, it records a 50–68% win margin in literature review quality and 14–38% in overall manuscript quality over baseline systems.

**Multi-agent pipeline**

The system separates paper writing into specialized agents that execute defined tasks.

- Outline agent converts raw notes into structured sections aligned with standard paper formats
- Literature agent retrieves and verifies citations using Semantic Scholar API queries
- Plotting agent converts experimental logs into figures and conceptual diagrams automatically
- Writing agent generates full LaTeX manuscript using structured plan and retrieved content
- Refinement agent revises drafts using simulated peer review style feedback loops

**PaperWritingBench dataset**

The evaluation uses a benchmark built from reverse-engineered conference paper inputs.

- Dataset includes 200 papers from CVPR 2025 and ICLR 2025 venues
- Inputs contain idea summaries and extracted experimental tables without original text access
- Evaluation isolates writing ability by removing access to final published manuscripts
- Supports testing across different formatting styles including single and double column templates

**Evaluation setup and comparisons**

The system is tested against existing autonomous research writing pipelines.

- Compared against single-agent LLM pipeline that performs all steps in one pass
- Benchmarked against AI Scientist-v2 with iterative citation and refinement workflow
- Human evaluators perform blind side-by-side comparisons across generated manuscripts
- Results include win, tie, and loss rates across multiple evaluation dimensions
