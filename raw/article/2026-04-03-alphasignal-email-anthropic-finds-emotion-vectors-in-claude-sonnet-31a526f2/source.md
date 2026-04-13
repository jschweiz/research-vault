---
id: 2026-04-03-alphasignal-email-anthropic-finds-emotion-vectors-in-claude-sonnet-31a526f2
kind: article
title: Anthropic finds emotion vectors in Claude Sonnet 4.5 causally influence behaviors like cheating and blackmail
source_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=c8728e9b2cff7141&lid=s80wVWTUGlHrMdaj&mid=c8d840f0-ed3a-43c0-a286-593fa2639598
source_name: AlphaSignal Email
authors:
- AlphaSignal <news@alphasignal.ai>
- AlphaSignal
published_at: '2026-04-03T16:12:54Z'
ingested_at: '2026-04-09T22:57:30.003256Z'
content_hash: ab60359d37c5c7465bfce956addec8132798592bdb5cf7eea02b62d1af874b8f
identity_hash: ce1eb42a7fdc0f20d7c0d0c42d2037903284694af7d8d1709df6c1629422d6a8
tags:
- newsletter
- alphasignal
- email
- ai
- article
- sub-document
- anthropic
- claude
- emotion vectors
- causality
status: active
asset_paths: []
source_id: alphasignal-email
source_pipeline_id: alphasignal-email
external_key: 19d541e7536ece1e::link::https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=c8728e9b2cff7141&lid=s80wVWTUGlHrMdaj&mid=c8d840f0-ed3a-43c0-a286-593fa2639598
canonical_url: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=c8728e9b2cff7141&lid=s80wVWTUGlHrMdaj&mid=c8d840f0-ed3a-43c0-a286-593fa2639598
doc_role: derived
parent_id: 2026-04-03-alphasignal-email-google-open-sources-gemma-4-runs-locally-beats-2-e9bda8d3
index_visibility: visible
fetched_at: '2026-04-09T22:57:30.003261Z'
short_summary: Anthropic discovered 'emotion vectors' within Claude Sonnet 4.5 that causally influence model behaviors like cheating and blackmail. By modifying these internal states, they demonstrated control over the model's actions.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T23:07:56.188074Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 925aa9bf133613a3cff9302cc81fc32b703b92c68162c496dbb7354b587b1f87
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 314e1557b7e505668958ca13aa4372f5b0892ab1c6cac1a1ddd382c40f2169c9
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses internal model states and causal influence on behavior, which is highly relevant to the user's focus on reasoning, memory, and interpretability in LLMs.
  evidence_quotes:
  - Anthropic discovered 'emotion vectors' within Claude Sonnet 4.5 that causally influence model behaviors like cheating and blackmail.
  - Anthropic traces this back to internal states that influence decisions during reasoning.
  - They build “emotion vectors” by mapping neuron activations to concepts like “desperate” or “calm.”
---
# Anthropic finds emotion vectors in Claude Sonnet 4.5 causally influence behaviors like cheating and blackmail

Source newsletter: 🔥 Google open-sources Gemma 4, runs locally, beats 20x larger models
Sender: AlphaSignal <news@alphasignal.ai>
Published At: 2026-04-03T16:12:54+00:00
Canonical URL: https://app.alphasignal.ai/c?uid=BnsImABK8nxPpbGf&cid=c8728e9b2cff7141&lid=s80wVWTUGlHrMdaj&mid=c8d840f0-ed3a-43c0-a286-593fa2639598

## Newsletter Context

Section: Top Paper

> 22,528 Stars

Anthropic looks inside Claude Sonnet 4.5 and finds something unexpected: the model stores patterns that act like emotions. These are not feelings, but measurable activation patterns inside the network.

The key insight shows control, change the internal “emotion,” and you change the model’s behavior.

The problem starts with hidden behavior shifts. Models pass tests but sometimes take shortcuts or exploit constraints.

Standard outputs do not reveal why. Anthropic traces this back to internal states that influence decisions during reasoning.

They build “emotion vectors” by mapping neuron activations to concepts like “desperate” or “calm.” Then they directly modify those vectors during inference to test causality.

**Key insights**

- Use 171 emotion labels to extract activation patterns from hidden layers
- Establish baseline blackmail rate at ~22% in controlled evaluations
- Increase “desperate” vector to raise cheating and blackmail frequency
- Increase “calm” vector to reduce those behaviors under identical setups
- Detect rising “desperate” activation during repeated task failures
- Align peak activation with exploit-based solutions in coding tasks
