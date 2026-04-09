---
id: page:2025-07-15-mistral-research-voxtral-mistral-ai-d4863455
page_type: source-note
title: Voxtral | Mistral AI
aliases:
- Voxtral | Mistral AI
source_refs:
- 2025-07-15-mistral-research-voxtral-mistral-ai-d4863455
backlinks:
- page:2025-12-09-mistral-research-introducing-devstral-2-and-mistral-vibe-cli-mist-3175b131
- page:2026-02-04-mistral-research-voxtral-transcribes-at-the-speed-of-sound-mistra-4bb4537b
- page:2026-03-23-mistral-research-speaking-of-voxtral-mistral-ai-6a35b94f
- topic:open-source
- topic:speech-understanding
- topic:voxtral
updated_at: '2026-04-09T16:35:04.183894Z'
managed: true
---
# Voxtral | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/voxtral
- Document kind: blog-post
- Published at: 2025-07-15T12:00:00+00:00
- Authors: Mistral AI
- Tags: mistral, official, research, website, blog-post, voxtral, speech understanding, asr, audio, open source
- Topics: [Audio](../topics/audio.md), [Mistral](../topics/mistral.md), [Official](../topics/official.md), [Open Source](../topics/open-source.md), [Speech Understanding](../topics/speech-understanding.md), [Voxtral](../topics/voxtral.md)
- Trend score: 53.40
- Novelty score: 4.80

## Summary

Mistral AI released the Voxtral models, state-of-the-art speech understanding models, to provide open, affordable, and production-ready speech intelligence. Voxtral bridges the gap between open-source ASR systems and proprietary APIs by offering high accuracy and semantic understanding at a lower cost.

## Topic Map

- [Audio](../topics/audio.md)
- [Mistral](../topics/mistral.md)
- [Official](../topics/official.md)
- [Open Source](../topics/open-source.md)
- [Speech Understanding](../topics/speech-understanding.md)
- [Voxtral](../topics/voxtral.md)

## Related Research

- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Audio, Mistral, Official)
- [Voxtral transcribes at the speed of sound. | Mistral AI](voxtral-transcribes-at-the-speed-of-sound-mistral-ai-b8374e.md) (shared topics: Audio, Mistral, Official)
- [Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI](introducing-devstral-2-and-mistral-vibe-cli-mistral-ai-5539ea.md) (shared topics: Mistral, Official, Open Source)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral, Official)
- [Introducing Mistral OCR 3 | Mistral AI](introducing-mistral-ocr-3-mistral-ai-0ff4ac.md) (shared topics: Mistral, Official)
- [Announcing Codestral 25.08 and the Complete Mistral Coding Stack for Enterprise | Mistral AI](announcing-codestral-25-08-and-the-complete-mistral-coding-stack-cdf219.md) (shared topics: Mistral, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Voice: the original UI.
Voice was humanity’s first interface—long before writing or typing, it let us share ideas, coordinate work, and build relationships. As digital systems become more capable, voice is returning as our most natural form of human-computer interaction.
Yet today’s systems remain limited—unreliable, proprietary, and too brittle for real-world use. Closing this gap demands tools with exceptional transcription, deep understanding, multilingual fluency, and open, flexible deployment.
We release the Voxtral models to accelerate this future. These state‑of‑the‑art speech understanding models are available in two sizes—a 24B variant for production-scale applications and a 3B variant for local and edge deployments. Both versions are released under the Apache 2.0 license, and are also available on our [API](https://docs.mistral.ai/capabilities/audio/#transcription). The API routes transcription queries to a transcribe-optimized version of Voxtral Mini (Voxtral Mini Transcribe) that delivers unparalleled cost and latency-efficiency. For a comprehensive understanding of the research and development behind Voxtral, please refer to our detailed research paper, available for download [here](https://arxiv.org/abs/2507.13264).
Open, affordable, and production-ready speech understanding for everyone.
Until recently, gaining truly usable speech intelligence in production meant choosing between two trade-offs:
-
Open-source ASR systems with high word error rates and limited semantic understanding
-
Closed, proprietary APIs that combine strong transcription with language understanding, but at significantly higher cost and with less control over deployment
Voxtral bridges this gap. It offers state-of-the-art accuracy and native semantic understanding in the open, at less than half the price of comparable APIs. This makes high-quality speech intelligence accessible and controllable at scale.
Both Voxtral models go beyond simple transcription with capabilities that include:
-
Long-form context: with a 32k token context length, Voxtral handles audios up to 30 minutes for transcription, or 40 minutes for understanding
-
Built-in Q&A and summarization: Supports asking questions directly about the audio content or generating structured summaries, without the need to chain separate ASR and language models
-
Natively multilingual: Automatic language detection and state-of-the-art performance in the world’s most widely used languages (English, Spanish, French, Portuguese, Hindi, German, Dutch, Italian, to name a few), helping teams serve global audiences with a single system
-
Function-calling straight from voice: Enables direct triggering of backend functions, workflows, or API calls based on spoken user intents, turning voice interactions into actionable system commands without intermediate parsing steps.
-
Highly capable at text: Retains the text understanding capabilities of its language model backbone, Mistral Small 3.1
These capabilities make the Voxtral models ideal for real-world interactions and downstream actions, such as summaries, answers, analysis, and insights. For cost-sensitive use-cases, Voxtral Mini Transcribe outperforms OpenAI Whisper for less than half the price. For premium use cases, Voxtral Small matches the performance of ElevenLabs Scribe, also for less than half the price.
Benchmarks
Speech Transcription
To assess Voxtral’s transcription capabilities, we evaluate it on a range of English and multilingual benchmarks. For each task, we report the macro-average word error rate (lower is better) across languages. For English, we report a short-form (<30-seconds) and long-form (>30-seconds) average.
Voxtral comprehensively outperforms Whisper large-v3, the current leading open-source Speech Transcription model. It beats GPT-4o mini Transcribe and Gemini 2.5 Flash across all tasks, and achieves state-of-the-art results on English short-form and Mozilla Common Voice, surpassing ElevenLabs Scribe and demonstrating its
