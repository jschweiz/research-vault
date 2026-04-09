---
id: 2026-04-05-alphaxiv-paper-aura-always-on-understanding-and-real-time-assis-1479c6fc
kind: paper
title: 'AURA: Always-On Understanding and Real-Time Assistance via Video Streams'
source_url: https://www.alphaxiv.org/abs/2604.04184
source_name: alphaXiv Papers
authors:
- Xudong Lu
- Yang Bo
- Jinpeng Chen
- Shuhan Li
- Xintong Guo
- Huankang Guan
- Fang Liu
- Dunyuan Xu
- Peiwen Sun
- Heyang Sun
- Rui Liu
- Hongsheng Li
published_at: '2026-04-05T16:53:46Z'
ingested_at: '2026-04-09T12:06:41.809387Z'
content_hash: bb5ae1119819f15a47cffd09e5db40454c1e3de24967ecf785ab703daae2413d
identity_hash: 9bad89e3340d4602a88a984ab290a306b6a3c63b09fbe510941b516d3fdfd510
tags:
- paper
- alphaxiv
- research
- agents
- Computer Science
- conversational-ai
- cs.CV
- inference-optimization
- model-deployment-systems
- sequence-modeling
- video-understanding
- vision-language-models
- visual-qa
- github
- audio
- transcript
- summary
status: active
asset_paths:
- alphaxiv-ai-detection.json
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-podcast.mp3
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04184
canonical_url: https://www.alphaxiv.org/abs/2604.04184
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:06:41.809393Z'
short_summary: Researchers from Huawei Research and CUHK MMLab introduced AURA, an end-to-end streaming VideoLLM framework capable of continuously processing live video, making autonomous decisions on when to respond, and managing unbounded multimodal context. This framework achieved superior performance on streaming video understanding benchmarks, outperforming existing open-source and proprietary models, and demonstrated an end-to-end latency of approximately 312.2 ms for interactive scenarios.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# AURA: Always-On Understanding and Real-Time Assistance via Video Streams

## alphaXiv Summary

Researchers from Huawei Research and CUHK MMLab introduced AURA, an end-to-end streaming VideoLLM framework capable of continuously processing live video, making autonomous decisions on when to respond, and managing unbounded multimodal context. This framework achieved superior performance on streaming video understanding benchmarks, outperforming existing open-source and proprietary models, and demonstrated an end-to-end latency of approximately 312.2 ms for interactive scenarios.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04184
- Source paper: https://arxiv.org/abs/2604.04184
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04184v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04184v1.png
- GitHub: https://github.com/aurateam2026/AURA
- GitHub stars: 1
- Paper ID: 2604.04184
- Canonical ID: 2604.04184v1
- Paper group ID: 019d65a9-3d7e-7ee3-bdf6-deb8853bedcd
- Version ID: 019d65a9-3dca-736f-815e-ca3410725298
- Version: v1
- Version order: 1
- Published at: 2026-04-05T16:53:46+00:00
- First published at: 2026-04-05T16:53:46+00:00
- Updated at: 2026-04-07T01:58:03.390000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Xudong Lu
- Yang Bo
- Jinpeng Chen
- Shuhan Li
- Xintong Guo
- Huankang Guan
- Fang Liu
- Dunyuan Xu
- Peiwen Sun
- Heyang Sun
- Rui Liu
- Hongsheng Li

## Topics

- agents
- Computer Science
- conversational-ai
- cs.CV
- inference-optimization
- model-deployment-systems
- sequence-modeling
- video-understanding
- vision-language-models
- visual-qa

## Metrics

- Visits (all): 159
- Visits (last 7 days): 159
- Total votes: 2
- Public total votes: 15
- X likes: 0

## Abstract

Video Large Language Models (VideoLLMs) have achieved strong performance on many video understanding tasks, but most existing systems remain offline and are not well-suited for live video streams that require continuous observation and timely response. Recent streaming VideoLLMs have made progress, yet current approaches often rely on decoupled trigger-response pipelines or are limited to captioning-style narration, reducing their effectiveness for open-ended question answering and long-horizon interaction. We propose AURA (Always-On Understanding and Real-Time Assistance), an end-to-end streaming visual interaction framework that enables a unified VideoLLM to continuously process video streams and support both real-time question answering and proactive responses. AURA integrates context management, data construction, training objectives, and deployment optimization for stable long-horizon streaming interaction. It achieves state-of-the-art performance on streaming benchmarks and supports a real-time demo system with ASR and TTS running at 2 FPS on two 80G accelerators. We release the AURA model together with a real-time inference framework to facilitate future research.

## Problem

- Existing Video Large Language Models (VideoLLMs) are primarily designed for offline video processing, which limits their application in real-time scenarios requiring immediate understanding and timely responses.
- Current streaming VideoLLMs face limitations: decoupled architectures suffer from inconsistent contextual states, while unified architectures often lack robustness for long-duration interactions, are limited to captioning, or struggle with memory and performance degradation due to unbounded context.
- Efficiently managing the continuously growing video and textual interaction history in a real-time streaming environment without exceeding the limited context window of LLMs poses a significant challenge.

## Method

- AURA proposes an end-to-end unified streaming visual interaction framework, co-designed across data, algorithms, and systems, to achieve stability, broad capabilities, and long-term endurance in real-time video understanding.
- It employs an Interactive Video Stream Context Management system, featuring a dual sliding-window strategy for recent video content and QA interaction history, to effectively manage unbounded multimodal inputs.
- A Coarse-to-Fine Streaming Data Engine generates diverse training data for three types of streaming QA interactions: Real-Time, Proactive, and Multi-Response, enabling nuanced conversational behaviors. A Silent-Speech Balanced Loss objective is introduced to handle the imbalance between silent and spoken responses and mitigate hallucination.

## Results

- AURA demonstrated state-of-the-art performance on StreamingBench (73.1% accuracy, 10.4% higher than MiniCPM-o-4.5), OVO-Bench (65.3% accuracy, 4.2% higher than ViSpeak), and OmniMMI (25.4% accuracy), outperforming both open-source and proprietary models like Gemini-1.5-Pro on various streaming benchmarks.
- The integrated ASR-AURA-TTS system achieved a low end-to-end latency of approximately 312.2 ms from user speech input to the first spoken response, with the AURA model generating responses at around 137 tokens/s.
- Streaming-oriented training, despite its specialized nature, largely preserved offline video understanding capabilities, showing only modest performance drops on traditional offline benchmarks compared to the base model.

## Takeaways

- A dual sliding-window context management strategy is effective for handling unbounded video and text inputs in streaming VideoLLMs, balancing the retention of critical history with the need for bounded context and real-time inference.
- The Silent-Speech Balanced Loss objective is crucial for training streaming VideoLLMs to selectively produce responses or remain silent, while also mitigating issues like over-generating silent tokens or hallucinations arising from dynamic context truncation.
- Co-designing the data generation pipeline, training objectives, and an optimized inference framework is essential for developing robust, end-to-end streaming VideoLLMs capable of diverse interaction modes (real-time, proactive, multi-response) over extended durations.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65a9-3d7e-7ee3-bdf6-deb8853bedcd/podcast.mp3
- Audio asset: `alphaxiv-podcast.mp3`
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65a9-3d7e-7ee3-bdf6-deb8853bedcd/transcript.json
- Transcript lines: 18
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Human
- Headline: Fully Human Written
- Fraction AI: 0
- Fraction AI-assisted: 0
- Fraction human: 1

## Resources

- GitHub repository: https://github.com/aurateam2026/AURA

## Similar Papers

- StreamingVLM: Real-Time Understanding for Infinite Video Streams (2510.09608v1): StreamingVLM, developed by researchers from MIT, NVIDIA, and First Intelligence, is a Vision-Language Model engineered for real-time understanding of infinite video streams. It achieves stable, low-latency performance by employing an efficient KV cache management system and a novel training strategy, resulting in a 66.18% win rate against GPT-4o mini on the Inf-Streams-Eval benchmark while operating at up to 8 frames per second.
- TimeChat-Online: 80% Visual Tokens are Naturally Redundant in Streaming  Videos (2504.17343v1): Researchers from Peking University and collaborating institutions develop TimeChat-Online, a streaming video understanding framework that reduces visual token processing by 82.8% through differential token dropping while maintaining 98% performance on StreamingBench, enabling efficient real-time interaction with continuous video streams.
- LongLive: Real-time Interactive Long Video Generation (2509.22622v2): LONGLIVE is a framework enabling real-time interactive long video generation, achieving 20.7 FPS on a single H100 GPU for videos up to 240 seconds. It integrates a causal autoregressive design with novel techniques like KV-Recache for smooth prompt switching and a frame sink for maintaining long-range consistency with efficient short-window attention.
- StreamBridge: Turning Your Offline Video Large Language Model into a Proactive Streaming Assistant (2505.05467v2): StreamBridge is a framework designed to adapt existing offline Video-Large Language Models for streaming applications, enabling continuous multi-turn interaction and proactive responses. It integrates a memory buffer, a round-decayed compression strategy, and a plug-and-play activation model, achieving higher performance than proprietary models like GPT-4o on streaming benchmarks while maintaining general video understanding.
- Learning Streaming Video Representation via Multitask Training (2504.20041v2): Researchers from Shanghai Jiao Tong University and Shanghai AI Laboratory introduce StreamFormer, a streaming video backbone with causal temporal attention and a unified multitask visual-language alignment framework. This approach enables efficient, real-time video understanding, achieving 68.4 mAP on THUMOS-14 for online action detection without optical flow and outperforming baselines on online video instance segmentation and video question answering.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
