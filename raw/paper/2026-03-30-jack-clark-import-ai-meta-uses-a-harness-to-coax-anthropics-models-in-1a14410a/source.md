---
id: 2026-03-30-jack-clark-import-ai-meta-uses-a-harness-to-coax-anthropics-models-in-1a14410a
kind: paper
title: Meta uses a harness to coax Anthropic’s models into self-improvement
source_url: https://arxiv.org/abs/2603.19461
source_name: Import AI
authors:
- University of British Columbia
- Vector Institute
- University of Edinburgh
- New York University
- CIFAR
- Meta
published_at: '2026-03-30T12:28:13Z'
ingested_at: '2026-04-09T20:15:31.949568Z'
content_hash: b3be0a83ff91bb9bb38a2ea473becab9bee18ac3a15bf0d8731fee86e8587c32
identity_hash: e954780e3c754d73c0bb87a024a152114386f8fc4a2e5dc0a4abb83b3e7376dd
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- llm
- self-improvement
- hyperagent
- agent
- sub-document
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer::story::4:https://arxiv.org/abs/2603.19461
canonical_url: https://arxiv.org/abs/2603.19461
doc_role: derived
parent_id: 2026-03-30-jack-clark-import-ai-import-ai-451-political-superintelligence-google-39f0537b
index_visibility: visible
fetched_at: '2026-04-13T18:13:17.233912Z'
short_summary: Researchers developed a 'hyperagent' harness that allows Large Language Models (LLMs) to self-improve performance across various tasks by iteratively modifying their prompts and system mechanisms.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Meta uses a harness to coax Anthropic’s models into self-improvement

Source newsletter: Import AI 451: Political superintelligence; Google’s society of minds, and a robot drummer
Source issue: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer
Published At: 2026-03-30T12:28:13+00:00
Canonical URL: https://arxiv.org/abs/2603.19461

## Newsletter Context

…Give an LLM some tools and a recursive loop and the ability to edit its harness, step back, and let the magic happen… Researchers with the University of British Columbia, Vector Institute, University of Edinburgh, New York University, CIFAR, and Meta have built a harness for LLMs that has the ability to self-improve performance for arbitrary tasks. The approach is called a hyperagent, and it means giving an LLM a scaffold that can iteratively improve the prompts it uses to bootstrap its performance on tasks as well as the system it uses to get better at generating future prompts. Hyperagents work over generations, so one hyperagent begets a few hyperagents and the ones which do the best on the task will themselves spawn some more hyperagents, forming multiple layers of AI genealogy until performance is saturated.

Cyberpunk name of the year award: Hyperagent is actually short for “Darwin Godel Machine Hyperagents”: Besides the research being cool, my congratulations to the authors on coming up with a name I’d love to see chiseled into the moon by a laserbeam wielded by a superintelligence.

How hyperagents work : Hyperagents are “self-referential agents that integrate a task agent (which solves the target task) and a meta agent (which modifies itself and the task agent) into a single editable program. Crucially, the meta-level modification procedure is itself editable, enabling metacognitive self-modification, improving not only task-solving behavior, but also the mechanism that generates future improvements,” the researchers write. “This initial hyperagent is equipped with two tools: a bash tool for executing shell commands, and a specialized tool for inspecting and modifying files.”

Testing the agents in four different domains: The authors test out hyperagents by applying them to four problems – coding (polyglot), prediction (paper review), robotics (robotics reward design), and math understanding (olympiad-level math grading). For most problems, the Hyperagents use Claude Sonnet 4.5 as their base model, with one exception (Polyglot). Evaluations are done via several different models: o3-mini (Polyglot), GPT-4o (paper review), Claude Sonnet 4.5 (robotics reward design), and o4-mini (IMO-level grading). In all cases, the hyperagent approach improves performance significantly above the baseline.

- Polyglot: “the agent is given a code repository and a natural language instruction describing a desired change, and must modify the repository accordingly”. Results: “Across 5 runs, the DGM-H improves its training performance on the 50-task Polyglot subset from 0.140 (the initial agent) to 0.340 (CI: 0.300 – 0.380).”

- Paper review: “For each task, the agent is given the full text of an AI research paper and must predict a binary accept/reject decision”. Results: “On test tasks, DGM-H improves paper review performance from 0.0 (the initial agent) to 0.710 (CI: 0.590 – 0.750)”

- Robotics reward design: “Given a natural language description of a robotics task, an agent must generate a suitable reward function. This reward function is then used to train a quadruped robot in simulation using RL” Results : “DGM-H improves performance from 0.060 (the initial agent) to 0.372 (CI: 0.355 – 0.436), surpassing the default reward function that directly optimizes the evaluation metric (0.348)”

Why this matters – bootstrapping the singularity: Papers like this show that today’s AI systems are already capable of autonomously improving their performance when given the right scaffold and starting ingredients. An interesting idea is to combine the design approach here with giving the AI systems the ability to finetune themselves (e.g, in the style imagined by the PostTrainBench research, Import AI #449 ). Another limitation is that “although hyperagents can modify their self-improvement mechanisms, they cannot alter the outer process that determines which agents are selected or how they are evaluated” – though again, I think there are technical ways to achieve both of these objectives. Of course, an AI system that can autonomously improve itself on arbitrary domains has a range of safety issues, some of which are potentially cataclysmic. The authors acknowledge this while also being realistic about the problems that lie ahead: “a central challenge lies in balancing the potential of AI as a catalyst for human progress and well-being (e.g., automating scientific discovery) with the degree of trust humans are willing to place in these systems (e.g., delegating decisions or actions without requiring continuous human verification), while minimizing the many potential risks and downsides,” they write. Read more: Hyperagents (arXiv) . Get the code for HyperAgents here (Facebook Research, HyperAgents) .
