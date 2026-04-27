---
id: 2026-04-08-alphasignal-email-amazon-introduces-s3-files-enabling-file-system--174140fc
kind: article
title: Amazon introduces S3 Files, enabling file system access directly on S3 without duplicating or moving data
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=1evhZTeUPUJVQSGS6&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-08T15:39:23Z'
ingested_at: '2026-04-09T22:56:23.353511Z'
content_hash: caa79c8311c1c08d9a843483e00e8ccd0be2b3effc96aa085c9910a379cde902
identity_hash: a34325a4a0a026c4e8368fc498546319e22aba69bb972809b387173dda087008
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- amazon
- s3
- files
- file system
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d6dbf92e50efc7::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=1evhZTeUPUJVQSGS6&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=1evhZTeUPUJVQSGS6&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b
doc_role: derived
parent_id: 2026-04-08-alphasignal-email-anthropic-glasswing-claude-mythos-finds-zero-day-a1374861
index_visibility: visible
fetched_at: '2026-04-13T18:07:54.779543Z'
short_summary: Amazon Web Services introduced S3 Files to provide file system access directly on S3, eliminating the need to duplicate or move data between object storage and file systems.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:57.000059Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 534e4f9dbdeb2415e37ab068943635d16361369eacefbeeac0d6e540b030ca3a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 97ff700c02280147f7ba198a4f13d8549c0bcb4a5e316d5de810a9bd94f3318e
lightweight_score:
  relevance_score: 0.16
  source_fit_score: 0.16
  topic_fit_score: 0.16
  author_fit_score: 0.0
  evidence_fit_score: 0.16
  confidence_score: 1.0
  bucket_hint: archive
  reason: The document discusses AWS S3 Files, which is relevant to data storage and file systems, but it does not directly address the user's focus areas of LLM training, evaluation, reasoning, memory, or architecture.
  evidence_quotes:
  - Amazon Web Services introduced S3 Files to close a long-standing gap between object storage and file systems.
  - S3 Files removes that step by letting you access S3 like a file system, so existing applications run directly on stored data.
  - S3 Files creates a file system view over objects.
---
# Amazon introduces S3 Files, enabling file system access directly on S3 without duplicating or moving data

Source newsletter: 🔍 Anthropic Glasswing: Claude Mythos finds zero-day vulnerabilities
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-08T15:39:23+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=60d1ab77a0d96ec8&lid=1evhZTeUPUJVQSGS6&mid=f67ed4e7-2faa-4e37-adf1-feae44acc66b

## Newsletter Context

Section: Top News

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
