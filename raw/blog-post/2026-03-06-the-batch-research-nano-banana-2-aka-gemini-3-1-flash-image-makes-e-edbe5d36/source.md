---
id: 2026-03-06-the-batch-research-nano-banana-2-aka-gemini-3-1-flash-image-makes-e-edbe5d36
kind: blog-post
title: Nano Banana 2, aka Gemini 3.1 Flash Image, Makes Edits Easier and Faster
source_url: https://www.deeplearning.ai/the-batch/nano-banana-2-aka-gemini-3-1-flash-image-makes-edits-easier-and-faster
source_name: The Batch Research
authors: []
published_at: '2026-03-06T07:49:52-08:00'
ingested_at: '2026-04-09T20:54:52.121475Z'
content_hash: 24b86470d6a70bc96f7112dcd154e5e9b58753064374c54760f5ab635166f389
identity_hash: cd6905275a4579d64632a8aad25183b3015c8c70ffad8852feba9ba696c484fd
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- image generation
- gemini
- ai
- nano banana 2
- google
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/nano-banana-2-aka-gemini-3-1-flash-image-makes-edits-easier-and-faster
canonical_url: https://www.deeplearning.ai/the-batch/nano-banana-2-aka-gemini-3-1-flash-image-makes-edits-easier-and-faster
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T21:59:44.659704Z'
short_summary: Google launched Nano Banana 2 (Gemini 3.1 Flash Image), a faster and cheaper image generation system based on Gemini 3 Flash. This new model offers enhanced features and performance, positioning it among the top image generators.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:48.157732Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 5d65e99794c94d0882476af366234af875ebc21e47374170a97ef40bdf1bd573
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 7c630079a6035229b587271cc87fb35a0218aa6f8e96e6c7eba4aa15e5ca4f42
lightweight_score:
  relevance_score: 0.65
  source_fit_score: 0.3
  topic_fit_score: 0.85
  author_fit_score: 0.0
  evidence_fit_score: 0.95
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document strongly aligns with the user's favorite topics (LLM architecture, evaluation, and research tooling) and features relevant AI model developments.
  evidence_quotes:
  - Google launched Nano Banana 2 (Gemini 3.1 Flash Image), a faster and cheaper image generation system based on Gemini 3 Flash.
  - 'Nano Banana 2 (formally designated Gemini 3.1 Flash Image), an image-generation system that takes advantage of Gemini 3 Flash’s speed and strengths in language '
  - Nano Banana 2 ranks among the top three image generators on independent leaderboards.
---
Google launched a cheaper, faster successor to its flagship image generator, delivering greater interactivity at roughly half the price.
What’s new: Google [launched](https://blog.google/innovation-and-ai/technology/ai/nano-banana-2/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) Nano Banana 2 (formally designated Gemini 3.1 Flash Image), an image-generation system that takes advantage of Gemini 3 Flash’s speed and strengths in language and reasoning. It’s around four times faster and costs roughly half as much per image as its predecessor Nano Banana Pro.
- Input/output: Text and images in (up to 1 million tokens), images out (up to 4,000 tokens; 512x512, 1024x1024, 2048x2048, or 4096x4096 pixel resolutions; 14 aspect ratios; 4 seconds to 6 seconds per image)
- Architecture: Mixture-of-experts transformer based on Gemini 3 Flash, undisclosed rendering model
- Features: Search (text and image), two levels of reasoning (minimal or high), multilingual text rendering, character and object consistency for up to five characters and 14 objects across multiple generated images, output marked with invisible
[SynthID](https://deepmind.google/models/synthid/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)watermark and[C2PA](https://c2pa.org/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)Content Credentials that record how and when images were generated - Performance: Leads
[Arena.ai](http://arena.ai/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)text-to-image leaderboard of human preference, ranks second and third on Artificial Analysis Text to Image and Image Editing arena-style leaderboards after GPT Image 1.5 and Nano Banana Pro - Availability: Free (with limits) via Gemini app, Google Ads, Google Antigravity, and Flow;
[API](https://ai.google.dev/gemini-api/docs/pricing?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)input $0.50 per 1 million tokens, output $0.045 (512x512 pixel resolution), $0.067 (1024x1024 pixel resolution), $0.101 (2048x2048 pixel resolution), and $0.151 (4096x4096 pixel resolution) per image; image search free for the first 5,000 queries per month, $14 per 1,000 additional queries - Undisclosed: Architecture details, parameter count, training data and methods, rendering model
How it works: Google [disclosed](https://deepmind.google/models/model-cards/gemini-3-1-flash-image/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) few details about how it built Nano Banana 2 beyond stating that it is “based on” Gemini 3 Flash. Capabilities such as grounding in web search, reasoning, and high-resolution output essentially match those of the previous version Nano Banana Pro. However, the new system is faster, which makes it easier to refine the output iteratively and sequentially. [Some](https://x.com/MrDavids1/status/1991507991804162555?s=20&utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) [users](https://x.com/mark_k/status/1987822081363583381?s=20&utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) [reported](https://x.com/shub_vedi/status/2027077552838509047?s=20&utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) that it renders text more accurately.
Performance: Nano Banana 2 ranks among the top three image generators on independent leaderboards.
- On
[Arena.ai](http://arena.ai/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)’s text-to-image leaderboard (a head-to-head comparison that ranks systems by human preference), Nano Banana 2[leads](https://arena.ai/leaderboard/text-to-image?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)(1,280 Elo), ahead of GPT Image 1.5 (1,248) and Nano Banana Pro (1,238). On[Arena.ai](http://arena.ai/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)’s image edit leaderboard, Nano Banana 2 (with web search enabled) places second (1,401 Elo, preliminary results) behind OpenAI’s GPT Image (1,407 Elo) and ahead of Nano Banana Pro (1,398 Elo). However, Nano Banana 2’s score is preliminary (around 3,000 votes), while GPT Image 1.5’s score is well established (around 50,000 votes). - On the Artificial Analysis text-to-image
[leaderboard](https://artificialanalysis.ai/image/leaderboard/text-to-image?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)(also a head-to-head comparison that ranks systems by human preference), Nano Banana 2 (1,264 Elo) fell behind OpenAI’s GPT Image 1.5 set to high reasoning (1,268 Elo) and ahead of Nano Banana Pro (Elo 1,220). On the Artificial Analysis image editing[leaderboard](https://artificialanalysis.ai/image/leaderboard/editing?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX), Nano Banana 2 (1,233 Elo) trailed GPT Image 1.5 set to high reasoning (1,268 Elo) and Nano Banana Pro (1,250 Elo).
Behind the news: Competition in image generation has been fast and furious. Launched in late August 2025, the first version of Nano Banana (officially called Gemini 2.5 Flash Image) [attracted](https://x.com/joshwoodward/status/1963627742618165270?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) over 10 million new users to the Gemini app within weeks. In November, Nano Banana Pro, based on Google’s Gemini 3 Pro vision-language model, topped image-generation leaderboards. OpenAI [responded](https://openai.com/index/new-chatgpt-images-is-here/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) in December with GPT Image 1.5 — a launch that OpenAI accelerated in response to CEO Sam Altman’s “code red” instructions to catch up to Google, [according to](https://techcrunch.com/2025/12/16/openai-continues-on-its-code-red-warpath-with-new-image-generation-model/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) TechCrunch. Nano Banana 2 nears the top text-to-image position at a price roughly 60 percent lower than that of GPT Image 1.5 set to high quality.
Why it matters: Creative applications like producing marketing materials, product visualization, or storyboards often require many iterations to arrive at a desired composition, lighting, and style. That makes per-image cost and speed important factors. Grounding in web search can reduce the number of attempts needed to get the output right, and halving the cost per image doubles the budget for those that remain.
We’re thinking: Nano Banana keeps ripening!
