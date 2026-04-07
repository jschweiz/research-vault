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

## Staged Pipeline Rules

This vault follows a strict four-stage ingest model:

1. `fetching`
   Deterministic discovery, normalization, raw file writes, and newsletter decomposition only.
   No LLM-generated metadata belongs here.
2. `lightweight enrichment`
   A one-time-per-content-hash local Ollama pass for small metadata only.
   Think short summary, missing authors, and light tags.
3. `enrichment`
   Codex-agent work for cross-links, synthesis, wiki maintenance, Q&A, and health checks.
4. `indexing`
   Rebuild helper indexes from durable files only.
   Indexing must never invent metadata or hidden knowledge.

If you are modifying ingest logic, preserve these boundaries.
Do not silently move generation into fetch or indexing.

## Start Here

When you begin work in this repo:

1. Read [README.md](README.md) for the operating model.
2. Inspect the relevant parts of `raw/`, `wiki/`, `outputs/`, and `system/config/`.
3. Prefer using existing summaries, backlinks, and indexes to narrow the search space.
4. Read the most relevant source files directly before making durable claims.

At this scale, do not default to inventing a separate RAG pipeline.
Careful direct reads plus lightweight local indexes are usually enough.

`system/config/sources.json` is the canonical list of dedicated ingestion sources for the automated Mac pipeline.
If a task is about changing source ingestion behavior, edit that file deliberately and preserve raw kind correctness:

- website sources should write `blog-post` raw documents
- Gmail newsletter sources should write `newsletter` raw documents
- newsletter child docs may then emit `blog-post`, `article`, or `news`
- paper sources such as alphaXiv should write `paper` raw documents

Important default source fields:

- `classification_mode`
- `decomposition_mode`

For example:

- website sources normally use `classification_mode = fixed`
- Gmail newsletter sources normally use `classification_mode = written_content_auto`
- newsletter sources that should split issues into child docs use `decomposition_mode = newsletter_entries`

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
- New raw IDs are readable and should stay stable:
  `YYYY-MM-DD-source-slug-title-slug-hash8`
- Prefer additive edits over destructive rewrites.
- Do not rename document folders, IDs, or slugs casually; links and manifests may depend on them.
- Do not store secrets, API keys, tokens, cookies, or paired-device credentials in this repo.
- Do not add arbitrary runtime source definitions unless the task explicitly calls for them; prefer updating `system/config/sources.json` deliberately.
- If adding binaries such as PDFs or MP3s, keep them in the relevant document or brief folder instead of scattering them at the root.
- If source material has related images or originals, prefer storing them locally with the source so multimodal agents can reference them.
- Maintain backlinks, cross-references, and concept structure when updating the wiki.
- Do not let durable conclusions exist only in ephemeral chat output if they belong in the knowledge base.

### Raw Document Expectations

Canonical raw metadata lives in `source.md` frontmatter.
Key fields include:

- `source_id`
- `source_pipeline_id`
- `external_key`
- `canonical_url`
- `doc_role`
- `parent_id`
- `index_visibility`
- `fetched_at`
- `short_summary`
- `lightweight_enrichment_status`

Do not create parallel metadata stores when frontmatter should be the source of truth.

### Newsletter Modeling

When a newsletter source emits child docs:

- keep the original email as the parent provenance record
- keep `doc_role = primary` on the parent
- keep `doc_role = derived` on each child
- use `parent_id` on children
- allow the parent to be hidden from default indexes when children exist

Do not delete the parent issue just because child entries were created.

## Working Modes

### Ingest Mode

Use this when filing new source material.

- Put primary evidence into `raw/`.
- Preserve provenance: title, source, URL, authors, dates, and related local assets when available.
- Normalize messy source text into a readable Markdown representation.
- Prefer deterministic classification into `blog-post`, `article`, `news`, `newsletter`, or `paper`.

### Compile Mode

Use this when updating the knowledge graph in Markdown form.

- Summarize source documents.
- Create or improve concept pages.
- Add backlinks and cross-links.
- Group related evidence into coherent articles or category pages.
- Respect that wiki compile is a separate downstream action from ingest.
- The backend will rebuild `system/indexes/pages.json` and `system/indexes/graph.json` after you finish.
- Do not rewrite `raw/**` in normal compile mode.

### Health-Check Mode

Use this to improve integrity without silently changing the wiki.

- Inspect the vault for inconsistent naming or taxonomy.
- Look for missing metadata, duplicate or stale pages, and weak links.
- Suggest article candidates and follow-up questions.
- Write findings under `outputs/health-checks/`.
- Web search is allowed for fact-gap verification, but the vault comes first.

### Answer Mode

Use this when producing durable outputs against the vault.

- Start from the vault, not the open web.
- Use local helper tools or shell commands when they reduce context stuffing.
- Write reports under `outputs/answers/`.
- Write slide decks under `outputs/slides/`.
- Write chart bundles under `outputs/charts/`.
- Do not silently file the result into the wiki; filing is a separate explicit step.

### Q&A Mode

Use this when the user asks a question against the vault.

- Read the relevant wiki pages first.
- Follow links back to the most relevant raw evidence.
- Prefer writing the answer to a persistent file when the result is non-trivial.
- Prefer filing reusable outputs into the vault instead of leaving value only in chat.
- Default output targets:
  - `outputs/answers/` for Markdown reports
  - `outputs/slides/` for Marp decks
  - `outputs/charts/` for generated visualizations and their notes

### Filing Mode

If a generated answer has durable value:

- distill it,
- connect it to existing concepts,
- file it back into `wiki/` so future work compounds.

When filing an output back into the wiki:

- keep durable claims grounded in the source output artifact,
- add backlinks from destination wiki pages to that output when relevant,
- keep writes limited to `wiki/**`.

## Codex Runner Contract

The app may invoke Codex non-interactively to operate on this vault.
Those runs use local run bundles outside the synced repo:

- `.local-state/codex-enrichment/runs/<run-id>/manifest.json`
- `.local-state/codex-enrichment/runs/<run-id>/prompt.md`
- `.local-state/codex-enrichment/runs/<run-id>/final-schema.json`
- `.local-state/codex-enrichment/runs/<run-id>/events.jsonl`
- `.local-state/codex-enrichment/runs/<run-id>/final.json`
- `.local-state/codex-enrichment/runs/<run-id>/stderr.log`

Compile staleness also lives outside the vault:

- `.local-state/codex-enrichment/compile-state.json`

When you are the Codex process operating from this vault:

- read `README.md` and this file first,
- obey the allowed write scope from the prompt,
- keep the workflow vault-first and web-second,
- return the required structured JSON summary,
- avoid changing app code or local state unless the prompt explicitly allows it.

## Indexes And Generated Files

Treat these as rebuildable:

- `system/indexes/items.json`
- `system/indexes/pages.json`
- `system/indexes/graph.json`
- `system/runs/run-log.jsonl`

These files help the frontend and agents navigate the vault, but they are not canonical content.
If the information can be reconstructed from raw docs or wiki pages, it should not exist only in the indexes.

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
