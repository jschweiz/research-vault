---
id: page:2026-03-20-the-batch-research-apples-atoken-a-multimodal-model-with-a-single-e-2ba5af34
page_type: source-note
title: Apple’s AToken, a Multimodal Model with a Single Encoder and Tokenizer for Images, Videos, and 3D Objects
aliases:
- Apple’s AToken, a Multimodal Model with a Single Encoder and Tokenizer for Images, Videos, and 3D Objects
source_refs:
- 2026-03-20-the-batch-research-apples-atoken-a-multimodal-model-with-a-single-e-2ba5af34
backlinks:
- topic:3d-objects
- topic:atoken
- topic:image-generation
- topic:multimodal
- topic:multimodal-models
updated_at: '2026-04-09T23:10:03.761515Z'
managed: true
---
# Apple’s AToken, a Multimodal Model with a Single Encoder and Tokenizer for Images, Videos, and 3D Objects

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/apples-atoken-a-multimodal-model-with-a-single-encoder-and-tokenizer-for-images-videos-and-3d-objects
- Document kind: blog-post
- Published at: 2026-03-20T08:50:17-07:00
- Authors: Jiasen Lu, Liangchen Song
- Tags: deeplearning-ai, official, research, website, blog-post, multimodal models, atoken, image generation, video, 3d objects
- Topics: [Image Generation](../topics/image-generation.md), [Multimodal](../topics/multimodal.md), [3D Objects](../topics/3d-objects.md), [Atoken](../topics/atoken.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Multimodal Models](../topics/multimodal-models.md)
- Trend score: 31.16
- Novelty score: 2.00

## Summary

Apple developed AToken, a multimodal model featuring a single encoder and tokenizer for images, videos, and 3D objects. This model unifies these media types by training to reconstruct inputs and align embeddings to text.

## Topic Map

- [Image Generation](../topics/image-generation.md)
- [Multimodal](../topics/multimodal.md)
- [3D Objects](../topics/3d-objects.md)
- [Atoken](../topics/atoken.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Multimodal Models](../topics/multimodal-models.md)

## Related Research

- [Inside Feature Auto-Encoder, a Diffusion Image Generator That Shrinks Embeddings for More Speed](inside-feature-auto-encoder-a-diffusion-image-generator-that-shr-02f31c.md) (shared topics: Deeplearning Ai, Image Generation)
- [Nano Banana 2, aka Gemini 3.1 Flash Image, Makes Edits Easier and Faster](nano-banana-2-aka-gemini-3-1-flash-image-makes-edits-easier-and--52d417.md) (shared topics: Deeplearning Ai, Image Generation)
- [Meta debuts Muse Spark combining multimodal inputs, tool use, and agent orchestration in one system](meta-debuts-muse-spark-combining-multimodal-inputs-tool-use-and--acb2ab.md) (shared topics: Multimodal)
- [GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos](genlca-3d-diffusion-for-full-body-avatars-from-in-the-wild-video-d8c0b8.md) (shared topics: Image Generation)
- [A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model](a1-a-fully-transparent-open-source-adaptive-and-efficient-trunca-ac0efe.md) (shared topics: Multimodal)
- [SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing](spatialedit-benchmarking-fine-grained-image-spatial-editing-3317d6.md) (shared topics: Image Generation)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Multimodal models typically use different tokenizers to embed different media types, and different encoders when training to generate media rather than classify it. A team at Apple created a multidimensional tokenizer that maps not just images and videos, but also 3D objects into a shared token space for any of these visual media — and a shared encoder that performs well at both identifying such objects and generating them.
What’s new: Jiasen Lu, Liangchen Song, and colleagues from Apple trained [AToken,](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrVs3qgz0W6N1vHY6lZ3lsW3TtmBQ4_q2j4V8-y_P62mQRDW1vy8QB8Q9jm0N1v3ZtWT0pF5W1grG5r1lsJLQW6rSddk6dXS-8N5DBYcTYXsqfW70vVdf8pZklJW69q4wp6sZ3psW63KNZ66DSc8_W14lSp229cgnrW8B-TJR80sJkYN54kdymxX_xrW2d2Jxg28lGR5W26Yhlz6T-wG_My3rc1kz3nhW3k2MDQ1p9XvfW970w-V3FpJqfW1lm5QQ57fW7wW20GhL81SLBl9W2GWH5K5bCB95W222_Wq86cL6Nf1m4yd-04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152868656%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=fRtrHm7VYifErx22LZC8WTufKEb9KmzyhUcvGW2pw6o%3D&reserved=0) a transformer model with an all-purpose visual tokenizer. The new model can both generate and classify images, videos, and 3D, approaching the performance of specialized models for each of these input and output types.
Key insight: Image generation models use encoders (like VAEs or VQ-VAEs) that preserve visual details (is the cat’s/ball’s surface orange?) but discard semantics (is it a cat or a ball?), and therefore don’t recognize objects as well as classification models. Image classification models, on the other hand, use encoders (like CLIP or SigLIP) that capture types of objects (say, “cat” or “ball”) but miss visual details, so they are worse at generation. Moving from still images to video and 3D complicates matters further. Before they’re encoded, video and 3D typically require separate tokenizers to break down images into data an encoder can process, each with its own architecture and embedding space. If the three media types are analyzed using the same tokenizer in a single format, one transformer can learn to work with all of them. Further, training the model to reconstruct these media types and align them to matching text descriptions forces embeddings to retain both fine visual details and semantic references, eliminating the need for separate generation and classification models.
How it works: AToken consists of a pretrained SigLIP2[ ](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrVs3qgz0W6N1vHY6lZ3lkW8zgJRl6lLWwdW5ffhCX3qfbdvW1D2Rxx4GRjpzW5MvXLt1_pctqW5nYQNn4Z2DCWW1tW7y22FBzG9W4BzQY81dwl1tW1q2NdP8TngYkN8WZl09SCK-sN7RXx1xm-sTDW7sFKmX1pK58GW2gLzcN6GHjhlW4RDy1c8yG6nRW7RkqkF7-PjrKW8S6L-C5G1S7sW5CYq6r2Kql2_W7XYL1j5m_n7VW3PDFjf1_3sjqW4-Qs_48xYY0VW146B8365rBXpW6dbwsn2X3yP6W8GzwD962M_Skf11WD0R04&data=05%7C02%7C%7C2780d0079cbb44819f1e08de855014d6%7C84df9e7fe9f640afb435aaaaaaaaaaaa%7C1%7C0%7C639094776152883515%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=TifodlH1ZSmAvYztjvSKO8vbhPPgNsXipp6Eucnm8HI%3D&reserved=0)vision encoder (400 million parameters) — here extended from two dimensions to four — and an untrained decoder of the same size. The authors trained AToken to reconstruct inputs and align their embeddings to text using three image sets ([two](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Finfo.deeplearning.ai%2Fe3t%2FCtc%2FLX%2B113%2FcJhC404%2FVVB8zD6XLF9xW70l18b5DsD2CW7TctdS5LQfpgMQqrVs3qgz0W6N1vHY6lZ3nsW8hlYnh1-2GyMN2dshWt8P76YW3264rW2cj5zCN3xNMyjpH6K6W55vN8R6tJyjcVFpGhQ6k7dyrW16qslG8WQ-vWW7P0gcx8cCM3lW53v3PF3_VWypW8hwQC-
