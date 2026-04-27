---
id: 2026-04-03-the-batch-research-google-debuted-lyria-3-an-app-that-turns-text-or-51adf4c3
kind: blog-post
title: Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs
source_url: https://www.deeplearning.ai/the-batch/google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30-second-songs
source_name: The Batch Research
authors:
- Google
published_at: '2026-04-03T11:42:23-07:00'
ingested_at: '2026-04-09T20:51:37.868247Z'
content_hash: d9c4b4cad26a13c59baeaca71bfa05e93144d20565c2601f21b31b07edcdede1
identity_hash: d00d9c7688d0056c921de92207ec38dcb4b0196f39c82c8a87188cb8eaccf220
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- ai
- music generation
- lyria 3
- copyright
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30-second-songs
canonical_url: https://www.deeplearning.ai/the-batch/google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30-second-songs
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:33:32.808143Z'
short_summary: Google introduced Lyria 3, a music generator that creates 30-second audio clips from text or images, incorporating features like style specification and multiple languages. The model includes safeguards to avoid copyright violations by licensing training data and watermarking synthetic media.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:48.737804Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 919ac45216eb64241f39ea643226533fd76619fd592dec8cd01450782c821843
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 345705e3edc7bcb2d063d5e903cc1d380b37ef8505ec49196048e7310739bfbc
lightweight_score:
  relevance_score: 0.16
  source_fit_score: 0.36
  topic_fit_score: 0.16
  author_fit_score: 0.0
  evidence_fit_score: 0.36
  confidence_score: 0.8
  bucket_hint: archive
  reason: The document is about music generation and copyright safeguards, which is tangentially related to LLM training but does not directly address the user's core interests in LLM architecture, reasoning, or efficiency.
  evidence_quotes:
  - Google introduced Lyria 3, a music generator that creates 30-second audio clips from text or images, incorporating features like style specification and multipl
  - The model includes safeguards to avoid copyright violations by licensing training data and watermarking synthetic media.
  - 'Architecture: Latent diffusion model'
---
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
[SynthID](https://deepmind.google/technologies/synthid/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag), a hidden watermark that identifies synthetic media. Users can upload audio files to the Gemini app to check whether they were generated by a Google model. - If a prompt mentions a specific musician, the model will generate music in a similar style without replicating the artist’s voice or sound. Google said it compares outputs with existing music to avoid copyright violations, but acknowledged the approach is fallible and invites users to report outputs that may violate intellectual-property rights.
Behind the news: Lyria 3 arrives as the music industry is aggressively prosecuting developers of AI music generators for alleged copyright violations. The leading music generators, Suno and Udio, no longer generating music from scratch, leaving Google among a dwindling number of developers that do.
- In June 2024, Sony Music, Universal Music Group (UMG), and Warner Music, the world’s three largest music companies,
[sued](https://www.deeplearning.ai/the-batch/sony-umg-and-warner-music-sue-suno-and-udio-over-alleged-copyright-violations/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)Suno and Udio, which offer web-based music generators, for alleged copyright violations. In late 2025, the defendants[settled](https://www.deeplearning.ai/the-batch/universal-music-group-and-music-generator-udio-struck-a-deal-to-settle-a-lawsuit-and-build-a-new-platform-to-remix-copyrighted-music/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)with Universal Music Group and changed their services to emphasize altering existing, licensed recordings rather than generating new music. Sony’s lawsuit remains in progress. - Google responded to music-industry pressure partly by exploring models geared for professional music production. In spring 2025, it introduced Music AI Sandbox, MusicFX DJ, and Lyria RealTime, which enable more fine-grained control over generated music. Days after launching Lyria 3, Google
[acquired](https://techcrunch.com/2026/02/24/music-generator-producerai-joins-google-labs?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)another professional production tool, ProducerAI, formerly known as Riffusion.
Why it matters: Music generation is finding its place in an entertainment industry dominated by large, powerful incumbents. Lyria 3 puts it in front of more than [750 million](https://blog.google/company-news/inside-google/message-ceo/alphabet-earnings-q4-2025/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag#introduction) Gemini users, dwarfing the current user bases of Suno ([around two million](https://techcrunch.com/2026/02/27/ai-music-generator-suno-hits-2-million-paid-subscribers-and-300m-in-annual-recurring-revenue/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) paid subscribers) and Udio (around 3.3 million monthly users). It continues to produce original music — the direction that put Suno and Udio in the crosshairs of the world’s biggest recording companies — but adds safeguards, such as training on licensed music, to avoid aggravating copyright holders.
We’re thinking: Music generators produce impressive, versatile, surprisingly human-like output, yet we’re still waiting for generated music to have its ChatGPT moment. It may happen quietly as, say, producers of YouTube clips increasingly use Lyria 3 rather than pre-recorded sources.
