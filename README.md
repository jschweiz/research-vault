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

## What Lives Here

- `raw/`: source documents, notes, images, and attached originals
- `wiki/`: compiled or curated knowledge pages generated from `raw/`
- `briefs/`: dated daily brief artifacts, including markdown, JSON, and audio
- `outputs/`: persistent query answers, slides, charts, health checks, and viewer bundles
- `system/config/`: durable configuration that belongs with the vault

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

### Wiki Compile

The `wiki/` tree is not just a set of hand-authored notes. It is the compiled knowledge layer.
Agents should incrementally maintain:

- summaries of important source documents
- concept pages and category pages
- backlinks and cross-references
- synthesized articles that connect multiple sources

Humans may inspect and guide the wiki, but the default assumption is that the LLM maintains most of it.

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
    ├── indexes/
    ├── runs/
    └── leases/
```

## Content Conventions

- Raw documents and wiki pages are primarily Markdown with YAML frontmatter.
- JSON is used for machine-oriented manifests and durable config.
- Binary source files such as PDFs, images, and audio may live beside a raw document folder.
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
