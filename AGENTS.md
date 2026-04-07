# AGENTS

This repository is a durable knowledge vault. It is optimized for human-readable files and deterministic regeneration, not for arbitrary app state.

## Purpose

Agents may read broadly across this repo, but should write conservatively.
The highest priority is to preserve durable knowledge, valid structure, and reproducible generated outputs.

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
