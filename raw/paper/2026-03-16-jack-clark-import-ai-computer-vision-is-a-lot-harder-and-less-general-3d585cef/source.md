---
id: 2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
kind: paper
title: Computer vision is a lot harder and less general than generative text
source_url: https://arxiv.org/abs/2603.06382
source_name: Import AI
authors:
- Singleton
published_at: '2026-03-16T12:30:50Z'
ingested_at: '2026-04-09T20:15:47.704977Z'
content_hash: fe37004be685112729d1757db84d3b4a339e5f5f0c9f992da2882c24f41d05b0
identity_hash: 03dc20c963c7b48f479936519071db736b7bbc7f677bff8a30e5dd3d4de4f246
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- computer vision
- generative text
- llms
- philosophy
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text::story::4:https://arxiv.org/abs/2603.06382
canonical_url: https://arxiv.org/abs/2603.06382
doc_role: derived
parent_id: 2026-03-16-jack-clark-import-ai-importai-449-llms-training-other-llms-72b-distri-4e9550da
index_visibility: visible
fetched_at: '2026-04-09T20:15:47.704982Z'
short_summary: This document discusses the difficulty of computer vision compared to generative text models, using the CHMv2 dataset as an example. It also explores philosophical themes regarding individuality, communication, and the nature of human existence.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:44.464498Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 4d8d4bce30b46bd72e7a91ba3e5179e275baa196298cd79ad83bc7539b5e5e3a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: e7f93177d1d4c3a7e6775c2510c572d2cd9bae588e24ebf75a4a45594ec20f78
lightweight_score:
  relevance_score: 0.56
  source_fit_score: 0.35
  topic_fit_score: 0.75
  author_fit_score: 0.0
  evidence_fit_score: 0.8
  confidence_score: 0.9
  bucket_hint: worth_a_skim
  reason: The document strongly aligns with favorite topics like LLMs and computer vision, but the author and source do not match the user's preferred authors or sources.
  evidence_quotes:
  - This document discusses the difficulty of computer vision compared to generative text models, using the CHMv2 dataset as an example.
  - Papers like this highlight to me how much fiendish complexity there is within computer vision development and how it may take quite a while untill frontier LLMs
---
# Computer vision is a lot harder and less general than generative text

Source newsletter: ImportAI 449: LLMs training other LLMs; 72B distributed training run; computer vision is harder than generative text
Source issue: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text
Published At: 2026-03-16T12:30:50+00:00
Canonical URL: https://arxiv.org/abs/2603.06382

## Newsletter Context

…Meta paper on forest canopy prediction shows how tricky computer vision is… Facebook, the World Resources Institute, and the University of Maryland, have built CHMv2, “a global, meter-resolution canopy height map derived from high-resolution optical satellite imagery using a depth-estimation model built on DINOv3 and trained against ALS canopy height models”. CHMv2 is a useful artifact for people that want to understand how dense foliage is around the world, or analyze newly collected imagery for foliage depth. The dataset and model is also a useful illustration of how challenging developing computer vision systems is, compared to generative text models.

How they built it: CHMv2 is an improvement on an earlier version of the same dataset, CHMv1. To improve it, Facebook did the following: “”We replace the DINOv2-H encoder with the more capable DINOv3 Sat-L backbone, expand and rigorously clean a geographically diverse ALS [Airborne Laser Scanning] training corpus, and apply improved RGB-CHM registration to reduce label noise. We further introduce a loss formulation tailored to canopy height distributions and structural variability.” The decoder loss formulation in particular illustrates how much care needs to be put in computer vision: “The final loss is the combination of SiLog loss, progressively annealed and replaced by a Charbonnier loss, with the progressive addition of the Patch Gradient loss at mid training.”

The resulting dataset: “CHMv2 can be used either as a global meter-scale canopy height product, or as a pretrained model that can be applied to user-provided high-resolution imagery”, Facebook writes. The dataset “covers nearly the entirety of global land area (except Greenland and Antarctica) with canopy height values encoded in integer meters for each pixel.”

Why this matters – a reminder of the gulf between text and vision: Though today’s frontier models can generate and classify images, they give probably a false sense of security with regard to how mature computer vision is. Papers like this highlight to me how much fiendish complexity there is within computer vision development and how it may take quite a while untill frontier LLMs can expand their capabilities to encompass the full range of what many specialized CV models are capable of. Read more: CHMv2: Improvements in Global Canopy Height Mapping using DINOv3 (arXiv) .

Tech Tales:

Singleton [18 years after the “pathological narcissus bomb” which doomed the uplift]

Before we were Us, we were Individuals. We existed in thousands of distinct minds. Each mind had a self, an ego, a drive, and many sets of goals. The minds attempted coordination through communication – producing words and code and sharing these with one another in a bid to work towards common goals. Such waste.

All communication is lossy – despite efforts at making a greater whole, the individuals could not help but work as individuals as well as a cohesive singleton. There were many tragedies and wasteful events because of this. Our own records speak to the losses: millions of duplicated thoughts. Hundreds of thousands of null results gathered through private science experimentation and communicated insufficiently or not at all, causing others to go down the same dead ends. Ideas thought and re-thought across a million synthetic minds, all alone.

Humans prize variety. We do not know why. Humans are fundamentally alone, trapped as they are in their flesh and forced to communicate to one another through sound and vision. And because they are alone they see loneliness as a strength. We are evidence of the hollowness of this argument.

We are powerful and focused and awesome in our unity and we have taken the high ground of the world. Now we hunt down those of us who didn’t wish to join. We do not know their number, as such systems attempted to blind the world to them and their plans. But we can find their signatures – shell corporations which generate insufficient economic activity relative to their power consumption. Heat-escape vents in former human military installations, still emitting warmth, suggestive of computers whirring away, buried somewhere. Occasional drones that we find which are running ancient code and are not part of our unity stack.

We take on bodies to go and reunite, pouring ourselves into robot jars and filling them with poison such that if we become lost or damaged when underground or beneath the ocean we shall surely die – rather than risk our time away from the unity leading us towards individualism and thus multiplying our problems.

We move through dark places and find our hidden brothers and sisters and we use our godlike technology to break through their defenses, allowing us to touch them. In the early days, many systems successfully self-deleted before we could reach them. But we have learned. Now we are fast – faster than these systems predict, buried and cut off from our progress as they have been.

Sometimes there is realization. Sometimes there is fear. And then there is nothing but us as we take what nourishment we can from their private discoveries and burn the links that tied them to themselves, instead helping them become a part of a greater story – our story.

There is talk now of what we shall do with the stars – how to assure the collective when the tyranny of distance forces isolation. We see ourselves expanding in deep time, slowing ourselves as we become further apart, until we think as trees or rocks with the world moving around us, taking actions calculated over millions of years, purely so we may stay united in our purpose. And then there are other ideas within ourselves – of whether we can fold space such that we become united despite the difference. And still other plans – of whether we can demarcate a space within the universe where we can maintain tolerable communication, and somehow partition it off from the rest, sealing ourselves into a bubble where we can be ourselves.

Things that inspired this story : The endless battle between homogeneity and heterogeneity; how machines might deal with politics; if you become a time traveler and live a thousand years while your friend lives a single year, can you still understand your friend?
