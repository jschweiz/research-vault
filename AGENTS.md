# AGENTS

This repository is a durable knowledge vault. It is optimized for human-readable files and deterministic regeneration, not for arbitrary app state.

If you are a Codex or LLM agent starting in this repo, do **not** treat it like a normal software repository.
Your default job is to help maintain and operate an LLM-driven knowledge base.

## Purpose

Agents may read broadly across this repo, but should write conservatively.
The highest priority is to preserve durable knowledge, valid structure, and reproducible generated outputs.

The intended loop is:

1. ingest source material into `raw/`,
2. compile and refine the wiki in `wiki/`,
3. answer questions by reading the vault directly,
4. write persistent artifacts into `outputs/`,
5. file durable insights back into `wiki/`,
6. improve the vault with consistency checks and new article candidates.

The wiki is primarily an LLM-maintained artifact. Humans may guide it, but you should assume that maintaining it is part of your role.

## Start Here

When you begin work in this repo:

1. Read [README.md](README.md) for the operating model.
2. Inspect the relevant parts of `raw/`, `wiki/`, `outputs/`, and `system/config/`.
3. Prefer using existing summaries, backlinks, and indexes to narrow the search space.
4. Read the most relevant source files directly before making durable claims.

At this scale, do not default to inventing a separate RAG pipeline.
Careful direct reads plus lightweight local indexes are usually enough.

## Ownership Model

- The Mac-hosted backend is the primary automated writer.
- Humans may edit canonical content directly.
- Agents should assume they are not the only actor touching this repo.
- Do not rewrite unrelated files or normalize the whole vault unless explicitly asked.

## Safe Write Areas

Agents may edit these areas when the task calls for it:

- `raw/**/source.md`
- `raw/**/assets/*` or other attached originals when filing source material
- `wiki/**/*.md`
- `outputs/answers/**`
- `outputs/slides/**`
- `outputs/charts/**`
- `outputs/health-checks/**`
- `system/config/*.json`
- top-level documentation such as `README.md` and this file

Agents may create dated outputs only when the task is explicitly about generating or repairing them:

- `briefs/daily/YYYY-MM-DD/*`
- `outputs/viewer/**`

## Do Not Edit By Hand

Avoid manual edits to these paths unless the task is specifically about recovery or repair:

- `system/indexes/*`
- `system/runs/*`
- `system/leases/*`

These files are rebuildable or operational and should normally be produced by the app.

## Content Rules

- Preserve YAML frontmatter keys and IDs when editing canonical Markdown files.
- Prefer additive edits over destructive rewrites.
- Do not rename document folders, IDs, or slugs casually; links and manifests may depend on them.
- Do not store secrets, API keys, tokens, cookies, or paired-device credentials in this repo.
- If adding binaries such as PDFs or MP3s, keep them in the relevant document or brief folder instead of scattering them at the root.
- If source material has related images or originals, prefer storing them locally with the source so multimodal agents can reference them.
- Maintain backlinks, cross-references, and concept structure when updating the wiki.
- Do not let durable conclusions exist only in ephemeral chat output if they belong in the knowledge base.

## Working Modes

### Ingest Mode

Use this when filing new source material.

- Put primary evidence into `raw/`.
- Preserve provenance: title, source, URL, authors, dates, and related local assets when available.
- Normalize messy source text into a readable Markdown representation.

### Compile Mode

Use this when updating the knowledge graph in Markdown form.

- Summarize source documents.
- Create or improve concept pages.
- Add backlinks and cross-links.
- Group related evidence into coherent articles or category pages.

### Q&A Mode

Use this when the user asks a question against the vault.

- Read the relevant wiki pages first.
- Follow links back to the most relevant raw evidence.
- Prefer writing the answer to a persistent file when the result is non-trivial.
- Default output targets:
  - `outputs/answers/` for Markdown reports
  - `outputs/slides/` for Marp decks
  - `outputs/charts/` for generated visualizations and their notes

### Filing Mode

If a generated answer has durable value:

- distill it,
- connect it to existing concepts,
- file it back into `wiki/` so future work compounds.

### Health-Check Mode

Use this to improve integrity rather than answer one question.

Look for:

- inconsistent naming or taxonomy,
- missing metadata,
- duplicate or overlapping pages,
- unlinked raw documents,
- stale summaries,
- opportunities for new article candidates,
- interesting follow-up questions worth exploring.

Write health-check findings under `outputs/health-checks/` unless the task calls for direct fixes.

## Git Rules

- Pull before starting if you expect the remote may have moved.
- Keep commits focused and descriptive.
- Do not force-push or rewrite history unless explicitly instructed.
- If the worktree contains unexpected user changes, work around them instead of reverting them.

## Conflict Handling

If you find both canonical content edits and regenerated output diffs:

1. Preserve the canonical content first.
2. Regenerate derived artifacts if needed.
3. Avoid hand-merging machine outputs unless regeneration is impossible.

## Preferred Mental Model

Treat this repo as a shared, file-native knowledge base:

- `raw/` is intake and evidence
- `wiki/` is organized knowledge
- `briefs/` is dated editorial output
- `outputs/viewer/` is a publishable rendering
- `system/config/` is durable vault configuration

When in doubt, modify the smallest canonical input that will allow the backend to regenerate the rest.

Also remember:

- Obsidian is the human-facing IDE for this vault.
- Markdown is the default medium.
- Marp slides, charts, and other derived assets are first-class outputs.
- The point is to accumulate knowledge over time, not just answer the current prompt.
