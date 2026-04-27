---
id: 2026-04-13-jack-clark-import-ai-ai-can-reverse-engineer-software-that-contains-t-d57e49d9
kind: blog-post
title: AI can reverse engineer software that contains thousands of lines of code
source_url: https://epoch.ai/blog/mirrorcode-preliminary-results
source_name: Import AI
authors:
- Import AI
published_at: '2026-04-13T10:02:22Z'
ingested_at: '2026-04-13T18:12:31.816619Z'
content_hash: 556b83db1f965311def0e8aefab21896bb97fa8e1474a85dd32fb6cff5e81ce3
identity_hash: 222193d60e771c2e56ca3ede3d5ea51e19d7885c2ee4af83b569e932245e0d13
tags:
- newsletter
- ai
- analysis
- policy
- website
- blog-post
- sub-document
- mirrorcode
- software
- reverse engineering
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/04/13/import-ai-453-breaking-ai-agents-mirrorcode-and-ten-views-on-gradual-disempowerment::story::1:https://epoch.ai/blog/mirrorcode-preliminary-results
canonical_url: https://epoch.ai/blog/mirrorcode-preliminary-results
doc_role: derived
parent_id: 2026-04-13-jack-clark-import-ai-import-ai-453-breaking-ai-agents-mirrorcode-and--91e156f4
index_visibility: visible
fetched_at: '2026-04-13T18:12:31.816624Z'
short_summary: AI systems, using benchmarks like MirrorCode, demonstrate long-horizon capabilities in autonomously reimplementing complex software. This suggests AI progress in coding tasks may be significantly faster than previously estimated.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:25.052500Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 1523ef342dc017039f22c6e8baabc8634250a918922b339b1e3ba83e502d06fe
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: e0fc60570cbf5b7326d26e01e3a3740fdf98511893c7eac3402c4399b5c453f1
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.5
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses post-training methods and reasoning capabilities relevant to frontier LLM research, using a relevant benchmark.
  evidence_quotes:
  - AI systems, using benchmarks like MirrorCode, demonstrate long-horizon capabilities in autonomously reimplementing complex software.
  - The results show that AI systems are more capable than most people think at certain types of coding task, suggesting AI progress may be even faster than we prev
  - 'Today’s AI models are extremely capable at some of these tasks: “Claude Opus 4.6 successfully reimplemented gotree — a bioinformatics toolkit with ~16,000 lines'
---
# AI can reverse engineer software that contains thousands of lines of code

Source newsletter: Import AI 453: Breaking AI agents; MirrorCode; and ten views on gradual disempowerment
Source issue: https://jack-clark.net/2026/04/13/import-ai-453-breaking-ai-agents-mirrorcode-and-ten-views-on-gradual-disempowerment
Published At: 2026-04-13T10:02:22+00:00
Canonical URL: https://epoch.ai/blog/mirrorcode-preliminary-results

## Newsletter Context

…MirrorCode demonstrates some of the long-horizon capabilities of modern AI systems… AI measurement organizations METR and Epoch have built MirrorCode, a benchmark meant to test out how well AI models can autonomously reimplement complex existing software. The results show that AI systems are more capable than most people think at certain types of coding task, suggesting AI progress may be even faster than we previously thought.

What is MirrorCode: “Each MirrorCode task consists of a command-line (CLI) program that an agent is tasked to reimplement exactly. The AI agent is given execute-only access to the original program and a set of visible test cases, but does not have access to the original source code,” the researchers write. “The full MirrorCode benchmark includes more than 20 target programs spanning different areas of computing: Unix utilities, data serialization and query tools, bioinformatics, interpreters, static analysis, cryptography, and compression.”

The results: Today’s AI models are extremely capable at some of these tasks: “Claude Opus 4.6 successfully reimplemented gotree — a bioinformatics toolkit with ~16,000 lines of Go and 40+ commands. We guess this same task would take a human engineer without AI assistance 2–17 weeks. We see continued gains from inference scaling on larger projects, suggesting they may be solvable given enough tokens.” Additionally, they also found that performance can scale with inference, so the more compute you give a model, the better it’ll do.

Caveats: Now, this benchmark isn’t quite like normal coding tests. It’s better to think of it as a proofpoint for AI systems being able to generate systems which imitate the function of other systems when they get a lot of help: AI systems tested out here are asked to clone programs which produce a canonical output (and therefore can naturally generate a specification), there may be some cases of memorization on the basic programs, and this only covers a slice of the large universe of potential software projects.

Why this matters – for some tasks, AI is already as good as a fulltime sophisticated employee: Imagine you gave a talented software programmer a CLI interface to a complicated program and asked them to write the underlying program without seeing its source code. I’d wager only a fraction of them could do it if the program was quite sophisticated. And the ones that could would likely spend many days working on it. The fact AI can do this task autonomously is remarkable and a testament to the skill of these models. Read more : MirrorCode: Evidence that AI can already do some weeks-long coding tasks (Epoch AI) .
