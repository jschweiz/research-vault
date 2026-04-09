---
id: 2026-04-06-alphaxiv-paper-full-duplex-bench-v3-benchmarking-tool-use-for-f-75d960ee
kind: paper
title: 'Full-Duplex-Bench-v3: Benchmarking Tool Use for Full-Duplex Voice Agents Under Real-World Disfluency'
source_url: https://www.alphaxiv.org/abs/2604.04847
source_name: alphaXiv Papers
authors:
- Guan-Ting Lin
- Chen Chen
- Zhehuai Chen
- Hung-yi Lee
published_at: '2026-04-06T16:46:52Z'
ingested_at: '2026-04-09T10:03:02.760868Z'
content_hash: 9b9d14190be6bb3781d1260fcf16111f71073445166ec4842bf5468b06361c6f
identity_hash: 5e497b73f83c7d208944f08c2a6cdc2a4d070fa9d236a223ed749afbf3f6a7e6
tags:
- paper
- alphaxiv
- research
- agents
- Computer Science
- conversational-ai
- cs.CL
- data-curation
- eess.AS
- Electrical Engineering and Systems Science
- inference-optimization
- multi-modal-learning
- reasoning
- speech-recognition
- tool-use
- transformers
- github
- audio
- summary
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04847
canonical_url: https://www.alphaxiv.org/abs/2604.04847
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:03:02.760876Z'
short_summary: Full-Duplex-Bench-v3 (FDB-v3) introduces a benchmark for real-time voice agents performing multi-step tool execution using authentic human speech with systematic disfluency annotations. Its evaluation of six leading models quantifies the trade-offs between processing speed, accuracy, and conversational dynamics, revealing persistent challenges in handling dynamic user intent and self-corrections.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Full-Duplex-Bench-v3: Benchmarking Tool Use for Full-Duplex Voice Agents Under Real-World Disfluency

## alphaXiv Summary

Full-Duplex-Bench-v3 (FDB-v3) introduces a benchmark for real-time voice agents performing multi-step tool execution using authentic human speech with systematic disfluency annotations. Its evaluation of six leading models quantifies the trade-offs between processing speed, accuracy, and conversational dynamics, revealing persistent challenges in handling dynamic user intent and self-corrections.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04847
- Source paper: https://arxiv.org/abs/2604.04847
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04847v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04847v1.png
- GitHub: https://github.com/DanielLin94144/Full-Duplex-Bench
- GitHub stars: 149
- Paper ID: 2604.04847
- Canonical ID: 2604.04847v1
- Paper group ID: 019d65d7-7768-76e2-8c08-ee63463280b6
- Version ID: 019d65d7-777f-7eb3-876c-f91e5b030d99
- Version: v1
- Version order: 1
- Published at: 2026-04-06T16:46:52+00:00
- First published at: 2026-04-06T16:46:52+00:00
- Updated at: 2026-04-07T02:48:32.872000+00:00
- License: http://creativecommons.org/licenses/by-sa/4.0/
- Citations: 0

## Authors

- Guan-Ting Lin
- Chen Chen
- Zhehuai Chen
- Hung-yi Lee

## Topics

- agents
- Computer Science
- conversational-ai
- cs.CL
- data-curation
- eess.AS
- Electrical Engineering and Systems Science
- inference-optimization
- multi-modal-learning
- reasoning
- speech-recognition
- tool-use
- transformers

## Metrics

- Visits (all): 44
- Visits (last 7 days): 44
- Total votes: 1
- Public total votes: 7
- X likes: 0

## Abstract

We introduce Full-Duplex-Bench-v3 (FDB-v3), a benchmark for evaluating spoken language models under naturalistic speech conditions and multi-step tool use. Unlike prior work, our dataset consists entirely of real human audio annotated for five disfluency categories, paired with scenarios requiring chained API calls across four task domains. We evaluate six model configurations -- GPT-Realtime, Gemini Live 2.5, Gemini Live 3.1, Grok, Ultravox v0.7, and a traditional Cascaded pipeline (Whisper$\rightarrow$GPT-4o$\rightarrow$TTS) -- across accuracy, latency, and turn-taking dimensions. GPT-Realtime leads on Pass@1 (0.600) and interruption avoidance (13.5\%); Gemini Live 3.1 achieves the fastest latency (4.25~s) but the lowest turn-take rate (78.0\%); and the Cascaded baseline, despite a perfect turn-take rate, incurs the highest latency (10.12~s). Across all systems, self-correction handling and multi-step reasoning under hard scenarios remain the most consistent failure modes.

## Problem

- Most existing spoken dialogue systems primarily focus on conversational chat and lack the capacity to invoke external APIs or execute practical actions on behalf of the user.
- Current benchmarks for voice agents often rely on synthetic audio, omit natural speech disfluencies, or are restricted to single-step tasks, failing to represent complex, real-world human-agent interactions.
- Proprietary real-time voice agents, despite their capabilities, lack rigorous evaluation under controlled, reproducible conditions, hindering transparent performance comparisons.

## Method

- Developed Full-Duplex-Bench-v3 (FDB-v3), a benchmark comprising 100 multi-step tool-use scenarios across four diverse task domains, including 21 scenarios specifically designed to test self-correction capabilities.
- Collected and systematically annotated real human audio data, incorporating natural disfluencies like false starts, self-corrections, fillers, pauses, and hesitations, to assess model robustness in realistic acoustic conditions.
- Employed locally executed mock APIs with deterministic, zero-latency responses to isolate model reasoning and parameter-passing from external factors, and a multi-dimensional evaluation framework to assess accuracy, latency, and conversational dynamics.

## Results

- GPT-Realtime exhibited the strongest overall performance with a Task Completion (Pass@1) of 0.600, leading in tool selection F1 (0.876) and argument accuracy (0.680), and maintaining the lowest interruption rate (13.5%).
- Gemini Live 3.1 achieved the fastest task completion latency (4.25 s) but had the lowest turn-take rate (78.0%), while the traditional Cascaded baseline incurred the highest latency (10.12 s) due to sequential processing.
- Performance consistently degraded for all models as scenario difficulty increased and with the presence of disfluencies, particularly self-corrections, where even the top-performing GPT-Realtime scored 0.588.

## Takeaways

- Real-time voice agents face significant challenges in dynamically updating internal states and correctly processing mid-utterance self-corrections, often committing to parameters prematurely before user corrections are fully registered.
- There are inherent trade-offs between processing speed, overall accuracy in tool execution, and maintaining natural conversational flow and turn-taking dynamics in full-duplex interactions.
- Different architectural approaches and processing strategies (e.g., eager execution, silent pre-processing, high filler usage) result in distinct behavioral patterns and performance characteristics, each with unique implications for user experience.

## Full Overview

Saved in `alphaxiv-overview.md` and `alphaxiv-overview.json`.

## Overview Languages

- de
- en
- es
- fr
- hi
- ja
- ko
- ru
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d65d7-7768-76e2-8c08-ee63463280b6/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d7-7768-76e2-8c08-ee63463280b6/transcript.json

## Resources

- GitHub repository: https://github.com/DanielLin94144/Full-Duplex-Bench

## Similar Papers

- Full-Duplex-Bench: A Benchmark to Evaluate Full-duplex Spoken Dialogue Models on Turn-taking Capabilities (2503.04721v3): Full-Duplex-Bench introduces a scenario-driven benchmark to evaluate full-duplex spoken dialogue models' capabilities in turn-taking, pause handling, backchanneling, and user interruption management using automatic, time-aligned metrics. The evaluation reveals that commercial systems like Gemini Live and cascaded architectures with explicit control modules generally outperform transparent end-to-end models in nuanced interactive behaviors.
- MultiChallenge: A Realistic Multi-Turn Conversation Evaluation Benchmark  Challenging to Frontier LLMs (2501.17399v2): Scale AI developed MultiChallenge, a new benchmark designed to evaluate Large Language Models' (LLMs) multi-turn conversational abilities, identifying critical weaknesses even in frontier models that achieve near-perfect scores on older benchmarks. The benchmark's hybrid data generation and novel LLM-as-judge evaluation method show high alignment with human assessments, providing a reliable tool for future LLM development.
- VoiceBench: Benchmarking LLM-Based Voice Assistants (2410.17196v3): VoiceBench introduces the first comprehensive benchmark for evaluating LLM-based voice assistants across general knowledge, instruction-following, and safety, under diverse real-world speaker, environmental, and content variations. It reveals that current open-source end-to-end models underperform compared to pipeline approaches and proprietary solutions, struggling with real-world complexities and exhibiting specific safety vulnerabilities in speech mode.
- URO-Bench: Towards Comprehensive Evaluation for End-to-End Spoken Dialogue Models (2502.17810v3): URO-Bench introduces the first comprehensive benchmark for end-to-end speech-to-speech dialogue models, assessing multilingualism, multi-round conversations, and paralinguistic features across both cognitive and speech dimensions. It reveals a substantial performance gap between current open-source models and proprietary systems, particularly in advanced reasoning and nuanced audio understanding.
- Gaia2: Benchmarking LLM Agents on Dynamic and Asynchronous Environments (2602.11964v1): Researchers at Meta SuperIntelligence Labs developed GAIA2, a benchmark and open-source ARE framework, to evaluate large language model agents in dynamic, asynchronous, and multi-agent environments. Empirical evaluation revealed that state-of-the-art models, including GPT-5 (high) at 42.1% pass@1 and Kimi-K2 at 20.1% pass@1 among open-source models, face significant challenges with temporal reasoning, noise robustness, and ambiguity resolution.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
