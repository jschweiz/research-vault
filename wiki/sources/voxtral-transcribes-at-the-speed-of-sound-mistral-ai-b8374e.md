---
id: page:2026-02-04-mistral-research-voxtral-transcribes-at-the-speed-of-sound-mistra-4bb4537b
page_type: source-note
title: Voxtral transcribes at the speed of sound. | Mistral AI
aliases:
- Voxtral transcribes at the speed of sound. | Mistral AI
source_refs:
- 2026-02-04-mistral-research-voxtral-transcribes-at-the-speed-of-sound-mistra-4bb4537b
backlinks:
- page:2024-11-18-mistral-research-deprecated-pixtral-large-mistral-ai-236cab33
- page:2025-01-13-mistral-research-codestral-25-01-mistral-ai-b8c278ab
- page:2025-01-30-mistral-research-mistral-small-3-mistral-ai-5a7173c6
- page:2025-02-17-mistral-research-mistral-saba-mistral-ai-7649c064
- page:2025-03-06-mistral-research-mistral-ocr-mistral-ai-78ded670
- page:2025-05-21-mistral-research-devstral-mistral-ai-f4d5cce5
- page:2025-05-28-mistral-research-codestral-embed-mistral-ai-9aa5a5a7
- page:2025-06-10-mistral-research-magistral-mistral-ai-f37de11b
- page:2025-07-15-mistral-research-voxtral-mistral-ai-d4863455
- page:2025-07-30-mistral-research-announcing-codestral-25-08-and-the-complete-mist-98053d11
- page:2025-12-02-mistral-research-introducing-mistral-3-mistral-ai-3772caab
- page:2025-12-09-mistral-research-introducing-devstral-2-and-mistral-vibe-cli-mist-3175b131
- page:2026-03-16-mistral-research-leanstral-open-source-foundation-for-trustworthy-1714cec3
- page:2026-03-23-mistral-research-speaking-of-voxtral-mistral-ai-6a35b94f
- topic:mistral
- topic:multilingual
- topic:realtime
- topic:speech-text
updated_at: '2026-04-09T16:35:04.258981Z'
managed: true
---
# Voxtral transcribes at the speed of sound. | Mistral AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Mistral Research
- Canonical URL: https://mistral.ai/news/voxtral-transcribe-2
- Document kind: blog-post
- Published at: 2026-02-04T16:00:00+00:00
- Tags: mistral, official, research, website, blog-post, voxtral, speech-to-text, ai, realtime, multilingual
- Topics: [Audio](../topics/audio.md), [Mistral](../topics/mistral.md), [Multilingual](../topics/multilingual.md), [Official](../topics/official.md), [Realtime](../topics/realtime.md), [Speech Text](../topics/speech-text.md)
- Trend score: 53.40
- Novelty score: 4.80

## Summary

Mistral AI released Voxtral Transcribe 2, two next-generation speech-to-text models, including Voxtral Realtime for ultra-low latency applications. These models offer state-of-the-art transcription quality, speaker diarization, and multilingual support.

## Topic Map

- [Audio](../topics/audio.md)
- [Mistral](../topics/mistral.md)
- [Multilingual](../topics/multilingual.md)
- [Official](../topics/official.md)
- [Realtime](../topics/realtime.md)
- [Speech Text](../topics/speech-text.md)

## Related Research

- [Speaking of Voxtral | Mistral AI](speaking-of-voxtral-mistral-ai-88f3b2.md) (shared topics: Audio, Mistral, Multilingual, Official)
- [Voxtral | Mistral AI](voxtral-mistral-ai-ae07c3.md) (shared topics: Audio, Mistral, Official)
- [Magistral | Mistral AI](magistral-mistral-ai-df7660.md) (shared topics: Mistral, Multilingual, Official)
- [Leanstral: Open-Source foundation for trustworthy vibe-coding | Mistral AI](leanstral-open-source-foundation-for-trustworthy-vibe-coding-mis-d6f053.md) (shared topics: Mistral, Official)
- [Introducing Mistral OCR 3 | Mistral AI](introducing-mistral-ocr-3-mistral-ai-0ff4ac.md) (shared topics: Mistral, Official)
- [Introducing: Devstral 2 and Mistral Vibe CLI. | Mistral AI](introducing-devstral-2-and-mistral-vibe-cli-mistral-ai-5539ea.md) (shared topics: Mistral, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Today, we're releasing Voxtral Transcribe 2, two next-generation speech-to-text models with state-of-the-art transcription quality, diarization, and ultra-low latency. The family includes Voxtral Mini Transcribe V2 for batch transcription and Voxtral Realtime for live applications. Voxtral Realtime is open-weights under the Apache 2.0 license.
We're also launching an [audio playground in Mistral Studio](https://console.mistral.ai/build/audio/speech-to-text) to test transcription instantly, powered by Voxtral Transcribe 2, with diarization and timestamps.
Highlights.
-
Voxtral Mini Transcribe V2: State-of-the-art transcription with speaker diarization, context biasing, and word-level timestamps in 13 languages.
-
Voxtral Realtime: Purpose-built for live transcription with latency configurable down to sub-200ms, enabling voice agents and real-time applications.
-
Best-in-class efficiency: Industry-leading accuracy at a fraction of the cost, with Voxtral Mini Transcribe V2 achieving the lowest word error rate, at the lowest price point.
-
Open weights: Voxtral Realtime ships under Apache 2.0, deployable on edge for privacy-first applications.
Voxtral Realtime.
Voxtral Realtime is purpose-built for applications where latency matters. Unlike approaches that adapt offline models by processing audio in chunks, Realtime uses a novel streaming architecture that transcribes audio as it arrives. The model delivers transcriptions with delay configurable down to sub-200ms, unlocking a new class of voice-first applications.
Word error rate (lower is better) across languages in the FLEURS transcription benchmark.
At 2.4 seconds delay, ideal for subtitling, Realtime matches Voxtral Mini Transcribe V2, our latest batch model. At 480ms delay, it stays within 1-2% word error rate, enabling voice agents with near-offline accuracy.
The model is natively multilingual, achieving strong transcription performance in 13 languages, including English, Chinese, Hindi, Spanish, Arabic, French, Portuguese, Russian, German, Japanese, Korean, Italian, and Dutch. With a 4B parameter footprint, it runs efficiently on edge devices, ensuring privacy and security for sensitive deployments.
We’re releasing the model weights under Apache 2.0 on the [Hugging Face Hub.](https://huggingface.co/mistralai/Voxtral-Mini-4B-Realtime-2602)
Voxtral Mini Transcribe V2.
Average diarization error rate (lower is better) across five English benchmarks (Switchboard, CallHome, AMI-IHM, AMI-SDM, SBCSAE) and the TalkBank multilingual benchmark (German, Spanish, English, Chinese, Japanese).
Average word error rate (lower is better) across the top-10 languages in the FLEURS transcription benchmark.
Voxtral Mini Transcribe V2 delivers significant improvements in transcription and diarization quality across languages and domains. At approximately 4% word error rate on FLEURS and $0.003/min, Voxtral offers the best price-performance of any transcription API. It outperforms GPT-4o mini Transcribe, Gemini 2.5 Flash, Assembly Universal, and Deepgram Nova on accuracy, and processes audio approximately 3x faster than ElevenLabs’ Scribe v2 while matching on quality at one-fifth the cost.
Model features.
Voxtral Mini Transcribe 2 introduces key capabilities.
Speaker diarization.
Generate transcriptions with speaker labels and precise start/end times. Ideal for meeting transcription, interview analysis, and multi-party call processing. Note: with overlapping speech, the model typically transcribes one speaker.
Context biasing.
Provide up to 100 words or phrases to guide the model toward correct spellings of names, technical terms, or domain-specific vocabulary. Particularly useful for proper nouns or industry terminology that standard models often miss. Context biasing is optimized for English; support for other languages is experimental.
Word-level timestamps.
Generate precise start and end timestamps for each word, enabling applications like subtitle generation, audio search, and content alignme
