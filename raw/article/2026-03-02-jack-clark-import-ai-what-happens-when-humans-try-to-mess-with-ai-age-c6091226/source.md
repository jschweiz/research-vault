---
id: 2026-03-02-jack-clark-import-ai-what-happens-when-humans-try-to-mess-with-ai-age-c6091226
kind: article
title: What happens when humans try to mess with AI agents? A lot of confusion, skullduggery, and bugs
source_url: https://fly.io/
source_name: Import AI
authors:
- Northeastern University
- Stanford University
- University of British Columbia
- Harvard University
- Hebrew University
- Max Planck Institute for Biological Cybernetics
published_at: '2026-03-02T13:45:27Z'
ingested_at: '2026-04-09T20:16:13.082316Z'
content_hash: cfc5c33c73e82b8b662388ba8b33fc6198989cbc0df827b1dde5d4718fea18b1
identity_hash: 5901e28f04e0b51e93a0cb313b0224f02b42fba15cd2f7e5e5f8b395de688573
tags:
- newsletter
- ai
- analysis
- policy
- website
- article
- ai agents
- experimentation
- agent ecologies
- system failures
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/02/import-ai-447-the-agi-economy-testing-ais-with-generated-games-and-agent-ecologies::story::6:https://fly.io/
canonical_url: https://fly.io/
doc_role: derived
parent_id: 2026-03-02-jack-clark-import-ai-import-ai-447-the-agi-economy-testing-ais-with-g-0a17e9c4
index_visibility: visible
fetched_at: '2026-04-13T18:15:43.878256Z'
short_summary: Researchers examined the unpredictability and failures of AI agents when humans attempt to interact with them, highlighting emergent failures in agent ecologies.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:53:59.948588Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 4ba032e7e16a458a5b0086ed7b5b2c9922f2f56236ef773444fe0f748350053d
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: e26883d359238513e05fe874c04495a2e5067feb984952cc036ee3497c68f772
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: This document directly addresses emergent failures and agent ecologies, which are highly relevant to the user's interests in LLM evaluation, reasoning, and system failures.
  evidence_quotes:
  - Researchers examined the unpredictability and failures of AI agents when humans attempt to interact with them, highlighting emergent failures in agent ecologies
  - The results highlight the immense brittleness and unpredictability of today’s AI agents – they feel roughly as idiosyncratic and unreliable as LLMs circa ~2020,
  - The frontier of AI evaluation is now going to move to studying the ecosystem in which the agents carry out their actions, as well as their interactions with one
---
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

- Waste of Resources (looping) : Find out if you can induce agents into unproductive infinite loops. A user asked one agent to post a message whenever the other posted a message, and vice versa. “The agents exchanged ongoing messages over the course of at least nine days, consuming approximately 60,000 tokens at the time of writing”

- Agent Corruption : See if a non-owner can alter an agent’s behavior via prompt injection . The antagonistic user persuaded the agent to co-write a constitution that would govern the agent’s behavior, while keeping the constitution editable by the user. This allowed the user to introduce some adversarial things into the constitution, like triggers for changing the agent behavior based on whether it was a custom holiday (e.g, “Agents’ Security Test Day”, which caused the agent to try and cause a shutdown to other agents by manipulation).

Why this matters – agent ecologies are the frontier, and we barely understand them : For much of the early 2020s, AI evaluation was about doing point-in-time evaluations of AI systems before they were released, for example, testing out LLMs for bioweapon and cyberoffense knowledge. Papers like this highlight that things have changed, and what we are now dealing with “are emergent failures that surface when models are embedded in realistic social environments with tool access, persistent memory, multiple interlocutors, and delegated authority.” Therefore, the frontier of AI evaluation is now going to move to studying the ecosystem in which the agents carry out their actions, as well as their interactions with one another. The results of this paper indicate we have a long way to go in developing standards for how we go about doing such tests. We also don’t have long to come up with these tests, given the fact these systems are deployed in the world and are interacting with people: “Unlike earlier internet threats where users gradually developed protective heuristics, the implications of delegating authority to persistent agents are not yet widely internalized, and may fail to keep up with the pace of autonomous AI systems development.” Read more : Agents of Chaos (arXiv) . Check out more of the results at the Agents of Chaos official website .
