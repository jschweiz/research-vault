# Research Vault

This repository is the durable knowledge vault for Research Center.

It is a file-native content store, not an application codebase and not a database dump.
The Mac-hosted backend writes into this repo, commits changes, and syncs them to GitHub.
Humans and agents should treat the Markdown and JSON files here as the source of truth for durable knowledge.

## What Lives Here

- `raw/`: source documents, notes, and attached originals
- `wiki/`: compiled or curated knowledge pages
- `briefs/`: dated daily brief artifacts, including markdown, JSON, and audio
- `outputs/viewer/`: read-only viewer bundle derived from the current vault state
- `system/config/`: durable configuration that belongs with the vault

These directories are rebuildable runtime state and are intentionally ignored from Git:

- `system/indexes/`
- `system/runs/`
- `system/leases/`

Local secrets, pairing tokens, caches, and machine-only auth material do not belong in this repo.

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

## Typical Workflow

1. Pull the latest vault changes.
2. Edit canonical content under `raw/`, `wiki/`, or `system/config/`.
3. Let the backend regenerate briefs, audio, and viewer outputs as needed.
4. Commit focused changes and push them back to GitHub.

For agent-specific operating rules, see [AGENTS.md](AGENTS.md).
