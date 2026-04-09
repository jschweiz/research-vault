---
id: page:2026-04-06-tldr-email-how-claude-code-builds-a-system-prompt-a4d9c7c0
page_type: source-note
title: How Claude Code Builds a System Prompt
aliases:
- How Claude Code Builds a System Prompt
source_refs:
- 2026-04-06-tldr-email-how-claude-code-builds-a-system-prompt-a4d9c7c0
backlinks:
- page:2026-04-09-tldr-email-the-git-commands-i-run-before-reading-any-code-f4fec80d
- topic:claude-code
- topic:context-engineering
- topic:programming
- topic:system-prompts
updated_at: '2026-04-09T16:35:04.199869Z'
managed: true
---
# How Claude Code Builds a System Prompt

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: TLDR Email
- Canonical URL: https://www.dbreunig.com/2026/04/04/how-claude-code-builds-a-system-prompt.html
- Document kind: article
- Published at: 2026-04-06T11:04:43+00:00
- Authors: TLDR <dan@tldrnewsletter.com>, TLDR
- Tags: newsletter, tldr, email, ai, article, system prompts, claude code, context engineering, programming
- Topics: [Claude Code](../topics/claude-code.md), [Context Engineering](../topics/context-engineering.md), [Email](../topics/email.md), [Newsletter](../topics/newsletter.md), [Programming](../topics/programming.md), [System Prompts](../topics/system-prompts.md)
- Trend score: 500.30
- Novelty score: 6.80

## Summary

This article explores how Claude Code builds system prompts, highlighting the complexity of context engineering and the importance of harnesses. It includes a table demonstrating the components of a system prompt.

## Topic Map

- [Claude Code](../topics/claude-code.md)
- [Context Engineering](../topics/context-engineering.md)
- [Email](../topics/email.md)
- [Newsletter](../topics/newsletter.md)
- [Programming](../topics/programming.md)
- [System Prompts](../topics/system-prompts.md)

## Related Research

- [The Git Commands I Run Before Reading Any Code](the-git-commands-i-run-before-reading-any-code-7e8ab0.md) (shared topics: Email, Newsletter, Programming)
- [What I Learnt Using Claude Code to Build Production-Ready Apps](what-i-learnt-using-claude-code-to-build-production-ready-apps-217125.md) (shared topics: Claude Code, Email, Newsletter)
- [Claude Code is Great](claude-code-is-great-71ed2c.md) (shared topics: Claude Code, Email, Newsletter)
- [US nuclear startup Antares gets DOE approval for its Mark0 reactor demonstrator](us-nuclear-startup-antares-gets-doe-approval-for-its-mark0-react-1699ad.md) (shared topics: Email, Newsletter)
- [The 2-Sigma Problem: The 1:1 Tutor](the-2-sigma-problem-the-1-1-tutor-9725b7.md) (shared topics: Email, Newsletter)
- [My Quest to Solve Bitcoin's Great Mystery](my-quest-to-solve-bitcoin-s-great-mystery-656f8f.md) (shared topics: Email, Newsletter)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# How Claude Code Builds a System Prompt

Source newsletter: Apple eGPU support ⚡, inside AI lab finances 💰, Claude Code system prompts 🤖
Sender: TLDR <dan@tldrnewsletter.com>
Published At: 2026-04-06T11:04:43+00:00
Canonical URL: https://www.dbreunig.com/2026/04/04/how-claude-code-builds-a-system-prompt.html

## Newsletter Context

Section: Programming, Design & Data Science

System prompts are often the best manual for how an app is intended to work. The accidental leak of Claude Code's source code reveals how Claude Code assembles a context and shows how complex context engineering can be, and the importance of harnesses. This post contains a table that shows how Claude Code assembles a system prompt. Some components are always included, while others are conditional, and components may have variations.
