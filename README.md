# Research Vault

This repository is the durable knowledge vault for Research Center.

It is a file-native content store, not an application codebase and not a database dump.
The Mac-hosted backend writes into this repo, commits changes, and syncs them to GitHub.
Humans and agents should treat the Markdown and JSON files here as the source of truth for durable knowledge.

This repo is meant to support an **LLM-maintained knowledge base** workflow:

1. collect raw source material,
2. compile it into a linked Markdown wiki,
3. ask complex questions against that wiki,
4. render persistent outputs such as notes, slides, and charts,
5. file the best results back into the knowledge base so future work compounds.

## Staged Workflow

The ingest pipeline is intentionally split into separate stages.
Agents and operators should keep these boundaries sharp:

1. `fetching`
   Discover source material, normalize raw content, write vault files, and perform deterministic decomposition only.
   No LLM generation is allowed here.
2. `lightweight enrichment`
   Run a small one-time-per-content-hash local Ollama pass for minor metadata only: short summary, missing authors, and lightweight tags.
3. `enrichment`
   Deeper Codex-agent work such as cross-links, richer synthesis, wiki maintenance, Q&A, and health checks.
   This stage is intentionally separate from fetch and indexing, and it runs only when explicitly triggered.
4. `indexing`
   Rebuild helper indexes from durable vault files only.
   Indexing must never invent summaries, scores, insights, or derived facts.

The default Mac ingest path is: `fetch -> lightweight enrich stale docs -> rebuild items index -> single Git sync`.
Wiki compile, brief generation, audio generation, and viewer publishing are downstream actions, not part of the default ingest chain.

## Advanced Enrichment Jobs

The Codex-driven advanced layer is split into four explicit job types:

- `compile`
  Incrementally maintain `wiki/` from `raw/`.
  Codex edits wiki pages directly, then the backend deterministically rebuilds `system/indexes/pages.json` and `system/indexes/graph.json`.
- `health_check`
  Inspect the vault for consistency gaps, missing metadata, broken links, stale pages, duplicate concepts, and follow-up questions.
  Write durable reports under `outputs/health-checks/`.
- `answer`
  Answer research questions against the vault and write durable outputs under `outputs/answers/`, `outputs/slides/`, or `outputs/charts/`.
- `file_output`
  Take an existing durable output and distill its reusable insight back into `wiki/`.

These jobs are intentionally separate from default ingest.
Fetching and lightweight enrichment should keep generating raw evidence and small metadata.
Codex jobs are where the knowledge base itself compounds.

### Codex Run Bundles

Every advanced run creates a local run bundle outside the synced vault under the app's local state:

- `.local-state/codex-enrichment/runs/<run-id>/manifest.json`
- `.local-state/codex-enrichment/runs/<run-id>/prompt.md`
- `.local-state/codex-enrichment/runs/<run-id>/final-schema.json`
- `.local-state/codex-enrichment/runs/<run-id>/events.jsonl`
- `.local-state/codex-enrichment/runs/<run-id>/final.json`
- `.local-state/codex-enrichment/runs/<run-id>/stderr.log`

Compile staleness also lives outside the synced vault:

- `.local-state/codex-enrichment/compile-state.json`

This keeps operational state local while preserving the vault as the durable knowledge surface.

## What Lives Here

- `raw/`: source documents, notes, images, and attached originals
- `wiki/`: compiled or curated knowledge pages generated from `raw/`
- `briefs/`: dated daily brief artifacts, including markdown, JSON, and audio
- `outputs/`: persistent query answers, slides, charts, health checks, and viewer bundles
- `system/config/`: durable configuration that belongs with the vault, especially `sources.json`

These directories are rebuildable runtime state and are intentionally ignored from Git:

- `system/indexes/`
- `system/runs/`
- `system/leases/`

Local secrets, pairing tokens, caches, and machine-only auth material do not belong in this repo.

## Operating Model

### Raw Ingest

The `raw/` tree is the intake layer for evidence:

- articles
- papers
- repositories
- datasets
- images
- notes derived from any of the above

The preferred pattern is:

- `raw/<kind>/<doc-id>/source.md` for the canonical text representation
- `raw/<kind>/<doc-id>/assets/` or sibling files for local originals, images, PDFs, and related material

Local copies of images and original files are useful because agents can reference them directly while compiling or answering questions.

The main automated raw kinds currently used by the backend are:

- `blog-post` for official/company blog content
- `article` for general written pieces
- `news` for news-style updates and newsroom items
- `newsletter` for canonical email issues
- `paper` for research-paper sources such as alphaXiv or similar paper indexes

### Readable Raw IDs

New raw document folders use readable IDs:

- `YYYY-MM-DD-source-slug-title-slug-hash8`

Example shape:

- `2026-04-07-openai-website-openai-test-launch-a1b2c3d4`

These IDs are created from the stable external key plus a readable title slug.
They are meant to stay browseable in Obsidian, Finder, and GitHub.

### Raw Document Contract

Each canonical raw document lives in:

- `raw/<kind>/<doc-id>/source.md`

`source.md` holds YAML frontmatter plus the canonical text body.
Important frontmatter fields include:

- `id`
- `kind`
- `title`
- `source_id`
- `source_pipeline_id`
- `external_key`
- `source_url`
- `canonical_url`
- `authors`
- `published_at`
- `ingested_at`
- `fetched_at`
- `content_hash`
- `tags`
- `doc_role`
- `parent_id`
- `index_visibility`
- `short_summary`
- `lightweight_enrichment_status`

Raw metadata belongs in frontmatter, not in a separate database.

### Newsletter Parent / Child Modeling

Newsletter sources are modeled in two layers:

- a canonical parent `newsletter` raw doc for the original issue
- optional derived child docs for clearly extractable stories or linked entries

The parent newsletter doc:

- preserves the full email body and provenance
- uses `doc_role = primary`
- may use `index_visibility = hidden` when child docs were emitted

Derived child docs:

- use `doc_role = derived`
- point back to the parent with `parent_id`
- are classified as `blog-post`, `article`, or `news`
- are the items that should usually appear in inbox-style views

This keeps the original email intact while preventing duplicate coverage in the UI.

### Wiki Compile

The `wiki/` tree is not just a set of hand-authored notes. It is the compiled knowledge layer.
Agents should incrementally maintain:

- summaries of important source documents
- concept pages and category pages
- backlinks and cross-references
- synthesized articles that connect multiple sources

Humans may inspect and guide the wiki, but the default assumption is that the LLM maintains most of it.
The backend no longer writes wiki content directly in compile mode.
Codex writes or updates `wiki/**`, and the backend only rebuilds deterministic indexes afterward.

### Obsidian as Frontend

This repo is intended to work well inside Obsidian:

- browse `raw/`, `wiki/`, `briefs/`, and `outputs/`
- read Markdown answers and reports directly
- view slide decks in Marp-compatible Markdown
- inspect generated images and charts

The webapp is a control and visualization surface, but the vault itself should remain useful even when opened directly in Obsidian.

### Question Answering

At this scale, the knowledge base is intentionally simple.
Agents should first rely on:

- the raw source tree,
- the compiled wiki,
- concise local index files and manifests,
- direct reading of the most relevant files.

Do not assume a sophisticated RAG system is required.
For a moderately sized research vault, carefully maintained summaries, backlinks, and indexes are often enough for strong question answering.
Advanced answer jobs should preserve this same order of operations:

1. read the vault,
2. use local helper tools if needed,
3. use web search only when the vault lacks necessary context or verification.

### Persistent Outputs

Answers should often be written back into the repo instead of only returned in chat.
Common output forms include:

- Markdown reports and answers
- Marp slide decks
- charts or diagrams
- briefings and summaries
- health-check reports

Whenever an output has lasting value, it should either:

- live under `outputs/` as a reusable artifact, or
- be filed back into `wiki/` as durable knowledge.

### Health Checks and Incremental Improvement

The vault is expected to improve over time.
Agents should periodically look for:

- inconsistent facts or naming
- missing metadata
- broken or weak links
- missing summaries
- opportunities for new article or concept pages
- interesting unanswered questions worth pursuing

The goal is not only to answer questions, but to continuously improve the quality and navigability of the knowledge base.

Health checks are report-first in v1.
They should write findings and candidate fixes under `outputs/health-checks/` instead of silently rewriting the wiki.

## Directory Tree

```text
vault/
├── raw/
│   └── <kind>/
│       └── <doc-id>/
│           ├── source.md
│           └── <asset files>
├── wiki/
│   └── <namespace>/
│       └── <slug>.md
├── briefs/
│   └── daily/
│       └── YYYY-MM-DD/
│           ├── brief.md
│           ├── brief.json
│           ├── slides.md
│           ├── audio-script.md
│           └── audio.mp3
├── outputs/
│   ├── answers/
│   ├── slides/
│   ├── charts/
│   ├── health-checks/
│   └── viewer/
│       ├── latest/
│       └── history/
└── system/
    ├── config/
    │   └── sources.json
    ├── indexes/
    ├── runs/
    └── leases/
```

## Source Definitions

`system/config/sources.json` is the durable source-definition file for the Mac ingestion pipelines.
It defines which dedicated sources the backend should sync into `raw/`, how discovery works, and which raw kind each source writes.

In the default setup this includes:

- `openai-website`
- `anthropic-research`
- `tldr-email`
- `medium-email`
- `alphaxiv-paper`

Agents should treat this file as canonical configuration, not as a transient cache.

## Content Conventions

- Raw documents and wiki pages are primarily Markdown with YAML frontmatter.
- JSON is used for machine-oriented manifests and durable config.
- Binary source files such as PDFs, images, and audio may live beside a raw document folder.
- Source metadata should be deterministic whenever possible.
- Lightweight enrichment should stay small and cheap.
- Indexes are rebuildable navigation aids, not canonical knowledge.
- Generated directories should be treated as read-only unless you are intentionally repairing them.
- Operational indexes under `system/indexes/` may be useful for navigation, but durable knowledge should not live only there.
- Valuable query results should accumulate in the repo instead of disappearing into chat history.

## Typical Workflow

1. Pull the latest vault changes.
2. Add or normalize source material under `raw/`.
3. Compile or refine `wiki/` pages, summaries, and backlinks.
4. Ask questions against the vault and write persistent outputs under `outputs/` when useful.
5. File durable insights back into `wiki/`.
6. Let the backend regenerate briefs, audio, and viewer outputs as needed.
7. Commit focused changes and push them back to GitHub.

## Future Direction

As the corpus grows, it may become useful to explore:

- richer search tools over the vault,
- synthetic data generation from the curated wiki,
- finetuning or other methods that compress some of the knowledge into model behavior.

Those are downstream enhancements. The primary system remains: raw data -> compiled wiki -> persistent outputs -> iterative refinement.

For agent-specific operating rules, see [AGENTS.md](AGENTS.md).
