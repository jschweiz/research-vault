---
id: page:2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
page_type: source-note
title: Computer vision is a lot harder and less general than generative text
aliases:
- Computer vision is a lot harder and less general than generative text
source_refs:
- 2026-03-16-jack-clark-import-ai-computer-vision-is-a-lot-harder-and-less-general-3d585cef
backlinks:
- page:2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
- page:2026-02-23-jack-clark-import-ai-llms-are-more-trigger-happy-than-humans-in-a-nuc-12330914
- page:2026-03-02-jack-clark-import-ai-ais-can-teach-people-anything-including-how-to-g-39df0bb2
- page:2026-03-16-jack-clark-import-ai-can-llms-autonomously-refine-other-llms-for-new--e6f5236c
- topic:generative-text
- topic:llms
- topic:philosophy
updated_at: '2026-04-09T23:10:02.718972Z'
managed: true
---
# Computer vision is a lot harder and less general than generative text

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2603.06382
- Document kind: paper
- Published at: 2026-03-16T12:30:50+00:00
- Authors: Singleton
- Tags: newsletter, ai, analysis, policy, website, paper, computer vision, generative text, llms, philosophy, sub-document
- Topics: [Computer Vision](../topics/computer-vision.md), [Generative Text](../topics/generative-text.md), [Llms](../topics/llms.md), [Newsletter](../topics/newsletter.md), [Philosophy](../topics/philosophy.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 6.80

## Summary

This document discusses the difficulty of computer vision compared to generative text models, using the CHMv2 dataset as an example. It also explores philosophical themes regarding individuality, communication, and the nature of human existence.

## Topic Map

- [Computer Vision](../topics/computer-vision.md)
- [Generative Text](../topics/generative-text.md)
- [Llms](../topics/llms.md)
- [Newsletter](../topics/newsletter.md)
- [Philosophy](../topics/philosophy.md)
- [Policy](../topics/policy.md)

## Related Research

- [Can LLMs autonomously refine other LLMs for new tasks? Somewhat.](can-llms-autonomously-refine-other-llms-for-new-tasks-somewhat-738c53.md) (shared topics: Llms, Newsletter, Policy)
- [LLMs are still very bad at videogames](llms-are-still-very-bad-at-videogames-0b77f6.md) (shared topics: Llms, Newsletter, Policy)
- [AIs can teach people anything, including how to get better at making bioweapons](ais-can-teach-people-anything-including-how-to-get-better-at-mak-b38e22.md) (shared topics: Llms, Newsletter, Policy)
- [LLMs are more trigger happy than humans in a nuclear war simulation](llms-are-more-trigger-happy-than-humans-in-a-nuclear-war-simulat-f20e52.md) (shared topics: Llms, Newsletter, Policy)
- [Google paper suggests that LLMs simulate multiple personalities to answer questions](google-paper-suggests-that-llms-simulate-multiple-personalities--911861.md) (shared topics: Llms, Newsletter, Policy)
- [The Art of Letting Go](the-art-of-letting-go-f520a2.md) (shared topics: Newsletter, Philosophy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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

Humans prize variety. We do not know why. Humans are fundamentally alone, trapped as they are in their flesh and forced to communicate to one another through sound and
