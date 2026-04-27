---
id: 2026-04-08-alphasignal-email-anthropic-glasswing-claude-mythos-finds-zero-day-a1374861
kind: newsletter
title: '🔍 Anthropic Glasswing: Claude Mythos finds zero-day vulnerabilities'
source_url: https://mail.google.com/mail/u/0/#inbox/19d6dbf92e50efc7
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-08T15:39:23Z'
ingested_at: '2026-04-09T22:56:20.394463Z'
content_hash: 1e7c13835bef04acc5324f06ffad25fe87af18a0b7dd0b99d65fcc4285a11a53
identity_hash: edbb0c2cbccff30c10045f53d7def4a0f8f16f1c6b1a4ace909813aed5a3e194
tags:
- newsletter
- alphasignal
- email
- ai
- anthropic
- glasswing
- claude
- software engineering
- s3 files
status: active
asset_paths:
- original.html
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d6dbf92e50efc7
canonical_url: https://mail.google.com/mail/u/0/#inbox/19d6dbf92e50efc7
doc_role: primary
parent_id: null
index_visibility: hidden
fetched_at: '2026-04-13T18:07:48.759412Z'
short_summary: Anthropic introduced Project Glasswing, an initiative using Claude Mythos Preview to automate vulnerability discovery and security testing. The document also highlights advancements in open-source coding models and Amazon S3 Files for file system access.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:57.575675Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 533a9c6873cef3a336a11616457ebd49c86f8f341f7d22b595131402e3ad99f5
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 1a6fa2a935d34f0204d25eaf75ef0ac733404d9316dc96e41c96f2153825a0c8
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.95
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses frontier LLM evaluation, security, and agentic reasoning, which aligns perfectly with the user's focus areas.
  evidence_quotes:
  - Anthropic introduces Project Glasswing, an initiative using Claude Mythos Preview to automate vulnerability discovery and security testing.
  - Scores 83.1% on CyberGym vulnerability reproduction benchmark
  - Z.ai releases GLM-5.1, an open-source model for agent-based software tasks.
---
# 🔍 Anthropic Glasswing: Claude Mythos finds zero-day vulnerabilities

## Top News

### [Anthropic launches Glasswing, using Claude Mythos Preview to detect vulnerabilities across critical infrastructure](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=6eNrgOxAS9w13Chw&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 73,692 Likes

Anthropic introduces Project Glasswing, a coordinated effort to secure critical software using a new frontier model. Claude Mythos Preview shows a step-change in vulnerability discovery, outperforming most human experts.

The initiative focuses on defensive deployment before such capabilities spread widely.

**What it does**

It applies AI to automate vulnerability discovery and security testing at scale.

- Scans large codebases to detect zero-day vulnerabilities (unknown security bugs)
- Simulates exploit paths by chaining multiple weaknesses across system components
- Works autonomously, reducing reliance on manual security audits and expert review

**Evaluation and benchmarks**

The model shows higher performance across coding and cybersecurity evaluations.

- Scores 83.1% on CyberGym vulnerability reproduction benchmark
- Achieves 93.9% on SWE-bench Verified for software engineering tasks
- Reaches 82.0% on Terminal-Bench 2.0 for agentic command-line workflows
- Records 79.6% on OSWorld-Verified for real-world computer use scenarios

**Controlled deployment**

Access is limited due to the model’s dual-use cybersecurity capabilities.

- Restricted to approved partners for defensive security use cases
- Deployment includes safeguards to block high-risk outputs
- Future rollout depends on additional safety systems under development

### [Z.ai announces open-source GLM-5.1 coding model topping SWE-Bench Pro and beating GPT-5.4 and Opus 4.6](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=lkhAYsp7DxOpuXUb&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 12,536 Stars

Z.ai releases GLM-5.1, an open-source model for agent-based software tasks. It focuses on long-horizon work, which means it keeps improving results across many steps instead of finishing after one response.

The most notable result: it continues optimization over hundreds of iterations and thousands of tool calls.

**What it does**

It runs coding agents that execute, test, and refine code over time.

- Breaks tasks into steps, runs code, checks outputs, and revises strategy
- Handles complex workflows like debugging, repo generation, and system builds
- Uses tools such as file editing, compilers, and test runners in loops

**Key results**

It reports strong performance across benchmarks and long tasks.

- Scores 58.4 on SWE-Bench Pro , ranking first among open models
- Reaches 21.5k QPS after 600+ iterations in database optimization
- Achieves 3.6× GPU speedup on KernelBench Level 3 workloads

**How to use it**

You run it inside an agent framework with tool access.

- Set model name to GLM-5.1 in agents like Claude Code or OpenClaw
- Use a loop: run code, evaluate results, update, and repeat
- Deploy locally with vLLM or SGLang, or use via API

### [Amazon introduces S3 Files, enabling file system access directly on S3 without duplicating or moving data](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=1evhZTeUPUJVQSGS6&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 3,528 Stars

Amazon Web Services introduces S3 Files to close a long-standing gap between object storage and file systems. S3 stores data as objects, while many tools expect files with folders and paths, forcing teams to duplicate or sync data across systems.

S3 Files removes that step by letting you access S3 like a regular file system, so existing applications run directly on stored data.

**What problem it solves**

Teams store data lakes in S3 but tools require file-based access.

- Removes need to copy data between object storage and file systems
- Eliminates pipelines that keep two storage systems in sync
- Allows file-based tools to operate directly on S3 data

**How it works**

S3 Files creates a file system view over objects.

- Uses Amazon Elastic File System to map file operations to S3 requests
- Keeps data in S3 while presenting folders, files, and paths
- Caches frequently accessed data to reduce access latency

**How to use it**

You mount and access it like a file system.

- Connect from EC2, containers, or serverless environments
- Use standard file operations instead of S3 APIs when needed
- Access the same data through both file system and S3 APIs

## Signals

### [Anthropic adds /autofix-pr command to Claude Code CLI to fix PR issues automatically](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=1cvMH4iwFhN1Acn3C&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 2,101 Likes

### [Cognition releases SWE-1.6 with parallel tool calls and fewer reasoning loops](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=4npUrQV545GfDSbx&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 1,419 Likes

### [Ai2 presents open-source WildDet3D enabling 3D object detection from a single image](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=Wqe0Wh9CvtfQ8wSE&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 1,332 Likes

### [World Labs refines Marble models for better visuals and introduces scalable environment generation model](https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=tK94uEeY1OImNpbN&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b)

> 983 Likes
