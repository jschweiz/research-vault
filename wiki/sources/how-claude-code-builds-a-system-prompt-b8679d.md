---
id: page:2026-04-06-tldr-email-how-claude-code-builds-a-system-prompt-a4d9c7c0
page_type: source-note
title: How Claude Code Builds a System Prompt
aliases:
- How Claude Code Builds a System Prompt
source_refs:
- 2026-04-06-tldr-email-how-claude-code-builds-a-system-prompt-a4d9c7c0
backlinks:
- page:2026-04-03-medium-email-claude-code-is-great-a7134001
- page:2026-04-09-tldr-email-the-git-commands-i-run-before-reading-any-code-f4fec80d
- topic:claude-code
- topic:context-engineering
- topic:programming
updated_at: '2026-04-09T23:10:03.124653Z'
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
- Tags: newsletter, tldr, email, ai, article, system prompts, claude code, context engineering, programming, sub-document
- Topics: [Claude Code](../topics/claude-code.md), [Context Engineering](../topics/context-engineering.md), [Email](../topics/email.md), [Newsletter](../topics/newsletter.md), [Programming](../topics/programming.md), [Sub Document](../topics/sub-document.md)
- Trend score: 721.95
- Novelty score: 6.80

## Summary

This article explores how Claude Code builds system prompts, highlighting the complexity of context engineering and the importance of harnesses. It includes a table demonstrating the components of a system prompt.

## Topic Map

- [Claude Code](../topics/claude-code.md)
- [Context Engineering](../topics/context-engineering.md)
- [Email](../topics/email.md)
- [Newsletter](../topics/newsletter.md)
- [Programming](../topics/programming.md)
- [Sub Document](../topics/sub-document.md)

## Related Research

- [Claude Code is Great](claude-code-is-great-71ed2c.md) (shared topics: Claude Code, Email, Newsletter, Sub Document)
- [The Git Commands I Run Before Reading Any Code](the-git-commands-i-run-before-reading-any-code-7e8ab0.md) (shared topics: Email, Newsletter, Programming)
- [The 2-Sigma Problem: The 1:1 Tutor](the-2-sigma-problem-the-1-1-tutor-9725b7.md) (shared topics: Email, Newsletter, Sub Document)
- [Feedback Flywheel](feedback-flywheel-c22a0d.md) (shared topics: Email, Newsletter, Sub Document)
- [Cast Adrift, Meta Employees Have No Idea Who the ‘Token Legend' Is Anymore](cast-adrift-meta-employees-have-no-idea-who-the-token-legend-is--331cc0.md) (shared topics: Email, Newsletter, Sub Document)
- [Z.ai announces open-source GLM-5.1 coding model topping SWE-Bench Pro and beating GPT-5.4 and Opus 4.6](z-ai-announces-open-source-glm-5-1-coding-model-topping-swe-benc-b77584.md) (shared topics: Email, Newsletter, Sub Document)

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
