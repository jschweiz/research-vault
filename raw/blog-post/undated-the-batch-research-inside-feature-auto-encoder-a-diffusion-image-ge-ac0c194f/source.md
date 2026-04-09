---
id: undated-the-batch-research-inside-feature-auto-encoder-a-diffusion-image-ge-ac0c194f
kind: blog-post
title: Inside Feature Auto-Encoder, a Diffusion Image Generator That Shrinks Embeddings for More Speed
source_url: https://www.deeplearning.ai/the-batch/inside-feature-auto-encoder-a-diffusion-image-generator-that-shrinks-embeddings-for-more-speed
source_name: The Batch Research
authors:
- Yuan Gao
- Chen Chen
- Tianrong Chen
- Jiatao Gu
published_at: '2026-03-16T08:31:25-07:00'
ingested_at: '2026-04-09T20:54:30.153259Z'
content_hash: ec1b7c49c92df9bfa3d11ec1592a1b5ea345bf5f348092659690bb4aa2a2f5a7
identity_hash: 81509bfcd04ca215094521a96ae1ff7609963281652dc0acb6c49b313127b165
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- diffusion
- image generator
- embeddings
- speed
- feature auto-encoder
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/inside-feature-auto-encoder-a-diffusion-image-generator-that-shrinks-embeddings-for-more-speed
canonical_url: https://www.deeplearning.ai/the-batch/inside-feature-auto-encoder-a-diffusion-image-generator-that-shrinks-embeddings-for-more-speed
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T21:59:37.451349Z'
short_summary: The Feature Auto-Encoder (FAE) is a diffusion image generator that learns to shrink embeddings produced by vision encoders, allowing for faster training and better image generation. This approach leverages the knowledge from vision-trained encoders to produce high-quality images in significantly less time.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:49.734724Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: a2a10815d0d0b712ff7de8ddee48eb3edeabcbf5f9aa8ad6f7b04ad6968307c5
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 822ada12f63b3a6d7d3d12c522ae85f8a7fa64feaacab2e4ab2e5ed28e276d96
lightweight_score:
  relevance_score: 0.418
  source_fit_score: 0.55
  topic_fit_score: 0.18
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on generic profile-fit fallback.
  evidence_quotes:
  - The Feature Auto-Encoder (FAE) is a diffusion image generator that learns to shrink embeddings produced by vision encoders, allowing for faster training and bet
---
Research shows that diffusion image generators can train somewhat faster if they learn to reconstruct embeddings from a pretrained encoder that’s built for vision tasks like classification, segmentation, and retrieval — not image generation. Recent work shows they can train dramatically faster if the diffusion model learns to reconstruct a smaller version of these embeddings.
What’s new: Yuan Gao, Chen Chen, Tianrong Chen, and Jiatao Gu at Apple proposed [Feature Auto-Encoder](https://arxiv.org/abs/2512.07829?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes) (FAE), a diffusion image generator that learned to reconstruct embeddings produced by the vision encoder DINOv2. Where earlier work bogged down on the large size of DINOv2’s embeddings, FAE learned to shrink them before reconstructing them.
Key insight: Latent diffusion models, which remove noise from embeddings that a decoder then turns into images, [produce better images from larger embeddings](https://arxiv.org/abs/2501.01423?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes). Embeddings produced by vision encoders such as DINOv2 and SigLIP fit the bill: They’re large and semantically rich. This approach not only improves the output, it potentially accelerates training because the image generator takes advantage of the vision encoder’s pretraining. On the other hand, processing larger embeddings requires a larger architecture and significantly more training, which counteracts much of the speed-up. A solution is to shrink the vision encoder’s embeddings using a second, smaller encoder. The diffusion model can learn to remove noise from this smaller embedding, which requires less training. Then decoders can expand the embedding to its original embedding space, restoring the benefits of the larger embedding, and ultimately produce an image.
How it works: At inference, FAE works like this: Given noise and an ImageNet class or text embedding, [SiT](https://arxiv.org/abs/2401.08740?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes) (a latent diffusion model) generates a shrunken image embedding. Given that embedding, an embedding decoder produces a full-size embedding, from which an image decoder produces an image. The authors trained two separate FAE systems to generate images from input text labels (using [ImageNet](https://www.image-net.org/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes) at 256x256-pixel resolution) and text descriptions (using [CC12M](https://arxiv.org/abs/2102.08981?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes).)
- During training, FAE needed targets to learn to generate the full-size and shrunken embeddings. Given an image,
[DINOv2](https://arxiv.org/abs/2304.07193?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes)produced a full-size embedding. Given the full-size embedding, a small encoder (a single attention layer) produced the shrunken embedding. Given the shrunken embedding, an embedding decoder expanded it to full size. - Given the expanded embedding, an image decoder learned to produce an image. It used three loss terms: (i) a reconstruction loss that minimized the difference between predicted and ground-truth pixels; (ii) a perceptual loss in which an unidentified model embedded both a predicted image and ground truth, and the loss term minimized the distance between them; and (iii) an adversarial loss in which an unidentified discriminator classified predicted images and ground truth, and the loss term trained the image decoder to fool it.
- Given a noisy version of a shrunken embedding plus an ImageNet class or text embedding produced by a pretrained
[SigLIP 2](https://arxiv.org/abs/2502.14786?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes)), SiT learned to remove the noise.
Results: FAE performed comparably to state-of-the-art diffusion models while training faster.
- Generating ImageNet images from labels, FAE (675 million parameters) achieved 1.29 FID (a measure of the difference between
[Inception-V3](https://arxiv.org/abs/1512.00567?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes)’s embeddings of an original image and a generated version, lower is better) after training for 800 epochs. This was better than[RAE](https://arxiv.org/abs/2510.11690?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes)(676 million parameters), a diffusion image generator that learned to reconstruct DINOv2 embeddings without shrinking them. RAE achieved 1.41 FID after 800 epochs. FAE reached 1.41 FID after around seven times faster, in 110 epochs. - Generating images from text descriptions, FAE (1.1 billion parameters) achieved 6.9 FID on
[MS COCO](https://arxiv.org/abs/1405.0312?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes). This performance was similar to[Re-Imagen](https://arxiv.org/abs/2209.14491?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes)(3.2 billion parameters), which reached 6.88 FID after training on roughly four times more training data.
Why it matters: Encoders trained for vision tasks have different knowledge than encoders trained for image generation. That knowledge can help to generate better images, but it resides in bigger embeddings that require more processing power to handle. Shrinking them makes this knowledge available to image generators in a more practical way, making it possible to generate high-quality images in much less time.
We’re thinking: This work produces better images in less training time not by getting better at removing noise, but by removing noise from a richer embedding space.
