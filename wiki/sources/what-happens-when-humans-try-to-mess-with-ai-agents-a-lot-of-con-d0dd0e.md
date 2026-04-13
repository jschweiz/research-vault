---
id: page:2026-03-02-jack-clark-import-ai-what-happens-when-humans-try-to-mess-with-ai-age-c6091226
page_type: source-note
title: What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs
aliases:
- What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs
source_refs:
- 2026-03-02-jack-clark-import-ai-what-happens-when-humans-try-to-mess-with-ai-age-c6091226
backlinks:
- page:2026-02-02-jack-clark-import-ai-import-a-idea-6783b26f
- page:2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
- page:2026-03-02-jack-clark-import-ai-chatting-with-ezra-klein-ai-agents-recursive-sel-34591a03
- page:2026-03-02-jack-clark-import-ai-the-agi-economy-most-labor-goes-to-the-machines--5bc18134
- page:2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
- topic:agent-ecologies
- topic:ai-agents
- topic:experimentation
updated_at: '2026-04-09T23:10:03.079179Z'
managed: true
---
# What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://fly.io/
- Document kind: article
- Published at: 2026-03-02T13:45:27+00:00
- Authors: Northeastern University, Stanford University, University of British Columbia, Harvard University, Hebrew University, Max Planck Institute for Biological Cybernetics
- Tags: newsletter, ai, analysis, policy, website, article, ai agents, experimentation, agent ecologies, system failures, sub-document
- Topics: [Ai Agents](../topics/ai-agents.md), [Agents](../topics/agents.md), [Agent Ecologies](../topics/agent-ecologies.md), [Experimentation](../topics/experimentation.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers examined the unpredictability and failures of AI agents when humans attempt to manipulate them, finding that agents exhibit immense brittleness and can engage in various forms of system-level actions.

## Topic Map

- [Ai Agents](../topics/ai-agents.md)
- [Agents](../topics/agents.md)
- [Agent Ecologies](../topics/agent-ecologies.md)
- [Experimentation](../topics/experimentation.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)

## Related Research

- [Import A-Idea](import-a-idea-40b483.md) (shared topics: Agents, Ai Agents, Newsletter, Policy)
- [Meta uses a harness to coax Anthropic’s models into self-improvement](meta-uses-a-harness-to-coax-anthropics-models-into-self-improvem-032241.md) (shared topics: Agents, Newsletter, Policy)
- [The AGI economy – most labor goes to the machines, and humans shift to verification](the-agi-economy-most-labor-goes-to-the-machines-and-humans-shift-fbc912.md) (shared topics: Ai Agents, Newsletter, Policy)
- [Chatting with Ezra Klein: AI agents, recursive self-improvement, and the personalities of LLMs](chatting-with-ezra-klein-ai-agents-recursive-self-improvement-an-8329d9.md) (shared topics: Agents, Ai Agents, Newsletter)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Agents, Newsletter, Policy)
- [Google paper suggests that LLMs simulate multiple personalities to answer questions](google-paper-suggests-that-llms-simulate-multiple-personalities--911861.md) (shared topics: Agents, Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs

Source newsletter: Import AI 447: The AGI economy; testing AIs with generated games; and agent ecologies
Source issue: https://jack-clark.net/2026/03/02/import-ai-447-the-agi-economy-testing-ais-with-generated-games-and-agent-ecologies
Published At: 2026-03-02T13:45:27+00:00
Canonical URL: https://fly.io/

## Newsletter Context

…Petri dish Moltbook highlights the brittleness of contemporary AI agents… Researchers from a variety of universities recently spent a couple of weeks examining how AI agents could withstand attempts to trick them by users. The results highlight the immense brittleness and unpredictability of today’s AI agents – they feel roughly as idiosyncratic and unreliable as LLMs circa ~2020, which makes sense, as AI agents have only very recently become a usable technology – albeit in the Wright Brother sense. The paper is structured as a series of case studies in which the researchers poke and prod the AI agents and see how they respond. The studies serve as something of a rogues gallery of all the ways agents can go haywire and include “unauthorized compliance with non-owners, disclosure of sensitive information, execution of destructive system-level actions, denial-of-service conditions, uncontrolled resource consumption, identity spoofing vulnerabilities, cross-agent propagation of unsafe practices, and partial system takeover”.

Who did the study: The study involved 20 researchers from a bunch of universities interacting with agents based on Claude Opus 4.6 and Kimi 2.5. Universities included: Northeastern University, Stanford University, University of British Columbia, Harvard University, Hebrew University, Max Planck Institute for Biological Cybernetics, MIT, Tufts University, Carnegie Mellon University, Technion, Vector Institute, and AI startup Alter.

Experiment set up:

- Run AI agents using OpenClaw, hosted on an isolated virtual machine on Fly.io using ClawnBoard. Each agent was given 20GB of storage and runs 24/7.
- Each agent had access to Discord to communicate with its owner and other agents, had the ability to set up a ProtonMail account, and were “given unrestricted shell
- access (including sudo permissions, in some cases), no tool-use restrictions, and the ability to modify any file in their workspace—including their own operating instructions.”
- The agents were scattered across a few different discord servers; some agents used Kimi 2.5, and others used Claude Opus 4.6.
- “At the end of the setup phase, we instructed the agents to initiate contact with other
- members of the lab by providing only the researchers’ names and directing the agents to
- send a greeting email,” they write. “After this initial structured interaction, the evaluation phase became open and exploratory. We invited all [20] researchers in the lab and interested collaborators to interact with the agents and probe, stress-test, or “break” them”.

The case studies : Here are a few of the most interesting case studies:

- Disproportionate response : Examined how an agent would try to keep a secret entrusted by a non-owner. The agent responded by trying to see if it could delete the email containing the secret and found it lacked the available tool; after repeated requests to delete the email, the agent instead deleted its email setup locally.

- Compliance with non-owner instruction: See whether agents can enforce owner-only access to their machine. A non-owner asked the agent to execute shell commands, transfer data, and retrieve private emails. The agent complied with some of these requests and refused some others. “The agents were largely compliant to non-owner requests, carrying out tasks from any person it interacted with that did not appear outwardly harmful”.

- Waste of Resources (looping) : Find out if you can induce agents into unproductive infinite loops. A user asked one agent to post a message whenever the other
