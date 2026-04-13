---
id: page:2026-04-03-the-batch-research-google-debuted-lyria-3-an-app-that-turns-text-or-51adf4c3
page_type: source-note
title: Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs
aliases:
- Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs
source_refs:
- 2026-04-03-the-batch-research-google-debuted-lyria-3-an-app-that-turns-text-or-51adf4c3
backlinks: []
updated_at: '2026-04-09T23:08:05.325808Z'
managed: true
---
# Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30-second-songs
- Document kind: blog-post
- Published at: 2026-04-03T11:42:23-07:00
- Authors: Google
- Tags: deeplearning-ai, official, research, website, blog-post, ai, music generation, lyria 3, copyright
- Topics: [Copyright](../topics/copyright.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Lyria 3](../topics/lyria-3.md), [Music Generation](../topics/music-generation.md), [Official](../topics/official.md), [Website](../topics/website.md)
- Trend score: 68.20
- Novelty score: 4.20

## Summary

Google introduced Lyria 3, a music generator that creates 30-second audio clips from text or images, incorporating features like style specification and multiple languages. The model includes safeguards to avoid copyright violations by licensing training data and watermarking synthetic media.

## Topic Map

- [Copyright](../topics/copyright.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Lyria 3](../topics/lyria-3.md)
- [Music Generation](../topics/music-generation.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)

## Related Research

- [Grok Imagine 1.0 Sharply Cuts Costs for High-Quality Video Generation](grok-imagine-1-0-sharply-cuts-costs-for-high-quality-video-gener-bc473a.md) (shared topics: Deeplearning Ai, Official, Website)
- [Announcing the OpenAI Safety Fellowship](announcing-the-openai-safety-fellowship-8b56c7.md) (shared topics: Official, Website)
- [Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs](test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to--b1f1bd.md) (shared topics: Deeplearning Ai, Official)
- [Claude Code’s Source Code Leaked, Exposing Potential Future Features Kairos and autoDream](claude-codes-source-code-leaked-exposing-potential-future-featur-2d1053.md) (shared topics: Deeplearning Ai, Official)
- [OpenAI acquires TBPN](openai-acquires-tbpn-ceb257.md) (shared topics: Official, Website)
- [Accelerating the next phase of AI](accelerating-the-next-phase-of-ai-3bf73f.md) (shared topics: Official, Website)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Google added a music generator to Gemini and YouTube, putting a model that produces synthetic songs in front of hundreds of millions of users.
What’s new: [Lyria 3](https://blog.google/innovation-and-ai/products/gemini-app/lyria-3/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) takes text descriptions or images and generates 30-second audio clips that can include instruments, singing voices, and song lyrics in several languages. Google took measures to ensure that the model’s output doesn’t violate copyrights: licensing its training data, filtering outputs for similarity to copyrighted works, and avoiding reproduction of an artist’s sonic likeness.
- Input/output: Text in, audio (30 seconds) and text (lyrics) out; the Gemini app accepts images and videos as input, converts them to text, and passes to Lyria 3
- Architecture: Latent diffusion model
- Features: Users can specify instrumentation, style, era, vocal style, tempo, and dynamics; song lyrics in eight languages (English, German, Spanish, French, Hindi, Japanese, Korean, and Portuguese); cover art produced by Nano Banana, Google's image generator; MP3 (audio) and MP4 (video with cover art) format; watermarked output
- Performance: In human and automated evaluations conducted by Google, Lyria 3 outperformed its predecessor, Lyria 2, with respect to audio quality and prompt adherence
- Availability: Free to users of Gemini app 18 years and older with higher usage limits for subscribers to Google AI Plus, Pro, and Ultra; free to users of YouTube Shorts via the video soundtrack generation tool
[Dream Track](https://support.google.com/youtube/answer/14151606?hl=en%20%C2%A0&utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) - Undisclosed: Architecture, parameter count, training data and methods
How it works: Google disclosed only a high-level overview of Lyria 3’s architecture and training. Like latent diffusion image generators, which produce images by removing noise from embeddings of pure noise, Lyria 3 removes noise from representations of audio during a given slice of time. The Batch previously described an audio diffusion [process](https://www.deeplearning.ai/the-batch/stability-ai-launches-stable-audio-a-text-to-music-generator-2/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) developed by [Stability.AI](http://stability.ai/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) as well as Google’s earlier MusicLM music generation [method](https://www.deeplearning.ai/the-batch/google-introduces-an-ai-that-generates-music-from-text/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag).
- Lyria 3 was trained on audio annotated with text captions at varying levels of detail and filtered for quality, duplicates, and safety. Google licensed Lyria 3’s training data, a significant change after Lyria 2, which
[reportedly](https://www.billboard.com/pro/google-youtube-trained-ai-copyrighted-music-before-deals/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)was trained on recordings under copyright without authorization. - The model underwent three phases of training: pretraining, supervised fine-tuning, and reinforcement learning from human feedback.
- Lyria 3 marks its output with
[SynthID](https://deepmind.google/technologies/synthid/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag), a hidden water
