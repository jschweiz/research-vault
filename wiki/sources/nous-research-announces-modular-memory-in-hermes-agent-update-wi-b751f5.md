---
id: page:2026-04-06-alphasignal-email-nous-research-announces-modular-memory-in-hermes-b7181f28
page_type: source-note
title: Nous Research announces modular memory in Hermes Agent update with support for custom backend providers
aliases:
- Nous Research announces modular memory in Hermes Agent update with support for custom backend providers
source_refs:
- 2026-04-06-alphasignal-email-nous-research-announces-modular-memory-in-hermes-b7181f28
backlinks:
- page:2026-04-09-alphasignal-email-meta-debuts-muse-spark-combining-multimodal-inpu-e251f316
- topic:agent-execution
- topic:hermes-agent
- topic:modular-memory
updated_at: '2026-04-09T23:10:03.436833Z'
managed: true
---
# Nous Research announces modular memory in Hermes Agent update with support for custom backend providers

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: AlphaSignal Email
- Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d
- Document kind: article
- Published at: 2026-04-06T16:19:19+00:00
- Authors: AlphaSignal <news@alphasignal.ai>, Nous Research
- Tags: newsletter, alphasignal, email, ai, article, sub-document, hermes agent, modular memory, plugin system, agent execution
- Topics: [Hermes Agent](../topics/hermes-agent.md), [Modular Memory](../topics/modular-memory.md), [Agents](../topics/agents.md), [Agent Execution](../topics/agent-execution.md), [Alphasignal](../topics/alphasignal.md), [Email](../topics/email.md)
- Trend score: 721.95
- Novelty score: 6.80

## Summary

Nous Research released Hermes Agent v0.7.0, introducing modular memory and a plugin system that allows for custom memory backends.

## Topic Map

- [Hermes Agent](../topics/hermes-agent.md)
- [Modular Memory](../topics/modular-memory.md)
- [Agents](../topics/agents.md)
- [Agent Execution](../topics/agent-execution.md)
- [Alphasignal](../topics/alphasignal.md)
- [Email](../topics/email.md)

## Related Research

- [Perplexity rolls out startup competition focused on building companies powered entirely by Computer agents](perplexity-rolls-out-startup-competition-focused-on-building-com-6788e5.md) (shared topics: Agents, Alphasignal, Email)
- [Meta debuts Muse Spark combining multimodal inputs, tool use, and agent orchestration in one system](meta-debuts-muse-spark-combining-multimodal-inputs-tool-use-and--acb2ab.md) (shared topics: Agents, Alphasignal, Email)
- [Cursor enables running agents on any machine while controlling them remotely from your phone](cursor-enables-running-agents-on-any-machine-while-controlling-t-27a349.md) (shared topics: Agents, Alphasignal, Email)
- [Anthropic outlines Managed Agents system enabling reliable execution with decoupled infrastructure components](anthropic-outlines-managed-agents-system-enabling-reliable-execu-8a2e1c.md) (shared topics: Agents, Alphasignal, Email)
- [Pika introduces video chat skill allowing agents to interact and perform tasks during calls](pika-introduces-video-chat-skill-allowing-agents-to-interact-and-1a3bc5.md) (shared topics: Agents, Alphasignal, Email)
- [Nous Research integrates Manim into Hermes Agent for visualizing algorithms, equations, and technical concepts](nous-research-integrates-manim-into-hermes-agent-for-visualizing-d7d2c9.md) (shared topics: Alphasignal, Email, Hermes Agent)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Nous Research announces modular memory in Hermes Agent update with support for custom backend providers

Source newsletter: 🚨 Anthropic blocks OpenClaw access, requires API keys starting April 4
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-06T16:19:19+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=1414c8fd5f18a9c6&lid=CiJNs7nS7TsFcwaC&mid=53a079f7-c01a-447c-83a7-c5835d17963d

## Newsletter Context

Section: Top News

> 2,592 Likes

Nous Research releases Hermes Agent v0.7.0 with a shift toward modular memory and more stable agent execution.

The update replaces fixed memory with a plugin system, so the agent no longer depends on a single storage design. The key change lets you choose or build memory backends, which changes how agents store and retrieve context across tasks.

**What it does**

Hermes Agent runs autonomous tasks using tools, APIs, and stored context.

- Executes multi-step workflows using models, tools, and external services
- Stores context (“memory”) so agents reuse past information across tasks
- Integrates with editors, APIs, and browsers through tool plugins
- Supports long-running sessions with persistent state and tool access

**Key features**

This release adds modular systems and execution visibility.

- Pluggable memory system supports custom backends like vector stores or databases
- Credential pools rotate API keys automatically to handle failures and limits
- Camofox browser enables local browsing with session persistence and debugging access
- Inline diff previews show file changes before the agent continues execution
- Security checks block secret leaks from prompts, URLs, and tool outputs
