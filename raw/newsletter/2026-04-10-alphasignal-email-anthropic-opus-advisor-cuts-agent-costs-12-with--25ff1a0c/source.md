---
id: 2026-04-10-alphasignal-email-anthropic-opus-advisor-cuts-agent-costs-12-with--25ff1a0c
kind: newsletter
title: 🔄 Anthropic Opus Advisor cuts agent costs 12% with auto-escalation
source_url: https://mail.google.com/mail/u/0/#inbox/19d780beb0977c87
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-10T15:38:59Z'
ingested_at: '2026-04-13T18:07:07.277785Z'
content_hash: 485943ca138027ac19c9f126a69c9037d338bc3b6d79ac39a47cfbcf9bca6f2e
identity_hash: ca4a11580e829b5031d64f412de4446779e98c9db92c7a31d56803f5000138ce
tags:
- newsletter
- alphasignal
- email
- ai
- anthropic
- agent_cost
- ai_tools
- claude
- openai
- meta
status: active
asset_paths:
- original.html
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d780beb0977c87
canonical_url: https://mail.google.com/mail/u/0/#inbox/19d780beb0977c87
doc_role: primary
parent_id: null
index_visibility: hidden
fetched_at: '2026-04-13T18:07:07.277788Z'
short_summary: Anthropic introduced an advisor tool for agents that allows smaller models to call Opus only when needed, resulting in a 12% cost reduction for agent execution. The document also discusses advancements in AI systems, including a new model that runs computation internally and updates from various AI announcements.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:27.668133Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 3a8ee27fb97567ee0a6d3dfb1339862bb99a7175d23a6afce6381dc9ef3de536
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: ab15d0162b2f63baba848e3713fc231bb9b4df1567222b8c3e9a658621da611c
lightweight_score:
  relevance_score: 0.75
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses agent cost reduction and architectural advancements relevant to LLM efficiency and reasoning, aligning perfectly with the user's favorite topics and authors.
  evidence_quotes:
  - Anthropic introduced an advisor tool for agents that allows smaller models to call Opus only when needed, resulting in a 12% cost reduction for agent execution.
  - SWE-bench Multilingual increases by 2.7 points over Sonnet alone
  - Meta AI proposes a shift from models that use computers to models that act as computers.
---
# 🔄 Anthropic Opus Advisor cuts agent costs 12% with auto-escalation

## Top News

### [Anthropic introduces an advisor tool that lets smaller models call Opus only when needed during agent execution](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=gea2YtmCVsUdR10E&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 33,539 Likes

Anthropic adds the advisor tool to the Claude Platform to simplify a common agent pattern.

You run Claude Sonnet or Claude Haiku as the main agent, and bring in Claude Opus only for harder decisions. This setup keeps most execution at lower cost while still using a stronger model when reasoning becomes difficult.

**How it works**

The executor model runs the task end-to-end and calls the advisor when needed.

- Executor handles tools, steps through tasks, and produces final outputs directly
- Advisor reads shared context and returns a plan or correction, then exits
- Advisor does not call tools or generate user-visible responses during execution
- Entire interaction runs inside a single API request without external orchestration

**Results and performance**

Anthropic reports gains across benchmarks with lower cost per task.

- SWE-bench Multilingual increases by 2.7 points over Sonnet alone
- Cost per task reduces by 11.9% compared to Sonnet-only execution
- Haiku improves from 19.7% to 41.2% on BrowseComp with advisor enabled
- Haiku setup remains 85% cheaper than Sonnet for comparable workloads

**How to use it**

You add the advisor tool directly in your API call.

- Define advisor_20260301 with Opus as the advisor model
- Set max_uses to control how often the advisor gets invoked
- Send your task through /v1/messages and let the executor decide escalation
- Monitor separate token usage for advisor and executor in the response

### [OpenAI announces a $100/month ChatGPT Pro tier with higher Codex limits for long coding sessions](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=QyU6QaDkpBR1P5QC&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 16,349 Likes

OpenAI updates ChatGPT Plus and Pro plans to support increased Codex usage. The new Pro tier costs $100/month and provides higher limits for longer, high-effort coding sessions.

A limited-time promotion increases Pro Codex usage to 10× Plus capacity through May 31 .

**Codex Usage Changes**

OpenAI adjusts how Codex usage is allocated across subscription tiers.

- Plus shifts toward consistent weekly usage instead of concentrated single-day session limits
- Existing Plus promotion ends, with usage rebalanced for more frequent but shorter sessions
- Pro tier supports longer uninterrupted sessions designed for extended coding workflows
- Changes align usage patterns with observed demand for sustained development sessions

**Pro Tier Capabilities**

Pro expands model access, limits, and system capacity compared to Plus.

- Includes access to GPT-5.4 Pro reasoning model with higher compute allocation
- Supports larger context windows, up to roughly 400K tokens for reasoning tasks
- Provides maximum Codex task capacity for multi-step workflows and larger codebases
- Maintains unlimited model usage within defined abuse guardrails

**Plan Positioning**

Each plan now targets a different Codex usage pattern.

- Plus remains priced at $20 for steady daily usage across coding tasks
- Pro acts as a higher tier for users with sustained or intensive workloads
- Upgrade path focuses on increased usage limits rather than new core features
- Pricing structure reflects differences in session length and compute allocation

## Top Paper

### [Meta presents Neural Computer, a model that runs computation, memory, and I/O inside one learned system](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=1gHrRbjepy5Kjkc5u&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 1,836 Stars

Meta AI proposes a shift from models that use computers to models that act as computers. Instead of calling APIs or tools, the model executes tasks directly from learned behavior.

The prototype trains on screen recordings and reproduces parts of real desktop and terminal workflows.

**How it works**

The model learns full interaction loops from recorded computer usage.

- Trains on sequences of pixels, cursor movements, and keyboard inputs
- Predicts next screen state and action at each step in sequence
- Encodes logic and control flow directly in model weights
- Treats UI interactions as data instead of fixed program interfaces

**Core idea**

The paper frames this as a shift in where system responsibilities live.

- Moves execution logic from external software stack into model runtime
- Removes need for toolchains, APIs, and explicit program orchestration layers
- Positions model as both controller and executor of computational processes
- Distinguishes approach from memory-augmented models like NTM and DNC

**Key findings and limitations**

The prototype exposes clear gaps in reliability and abstraction.

- Fails on multi-step reasoning tasks with dependencies across steps
- Shows unstable memory across longer interaction sequences
- Does not form reusable abstractions from learned behaviors
- Generalization drops outside training distribution of interface patterns

## Signals

### [Anthropic announces Monitor tool which lets Claude run background scripts and wake on events](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=13YmAxSkEb7yjXqil&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 4,901 Likes

### [Perplexity integrates Plaid to connect bank accounts, credit cards, and loans for unified financial tracking](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=1pAXTmniWCWX9ADUs&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 6,632 Likes

### [Cursor enables agents to attach demos and screenshots to pull requests for easier review](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=1legUpGPPKSHfcRXw&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 1,532 Likes

### [Augment Code hosts Vibe Code Cup, a live AI coding competition with 90-minute build window](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=mk6dckq1AaExN8NF&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 1,419 Likes

### [Google proposes ConvApparel to evaluate and improve realism of simulated human conversations in AI systems](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=5cab7f3aef8cfef5&lid=cy4KilGRUgglYTgE&mid=3feb7337-64eb-4569-b52d-fc5970cc2625)

> 1,225 Likes
