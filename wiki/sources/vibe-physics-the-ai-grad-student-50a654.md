---
id: page:2026-04-07-anthropic-research-vibe-physics-the-ai-grad-student-anthropic-a88ccd9c
page_type: source-note
title: Vibe physics: The AI grad student
aliases:
  - Vibe physics: The AI grad student
source_refs:
  - 2026-04-07-anthropic-research-vibe-physics-the-ai-grad-student-anthropic-a88ccd9c
backlinks:
  - page:2026-04-07-anthropic-research-an-update-on-our-model-deprecation-commitments-f-9d1b9dba
  - page:2026-04-07-anthropic-research-anthropic-economic-index-report-learning-curves--490c7dff
  - page:2026-04-07-anthropic-research-emergent-introspective-awareness-in-large-langua-9bf6ddc3
  - page:2026-04-07-anthropic-research-emotion-concepts-and-their-function-in-a-large-l-2f22c4fb
  - page:2026-04-07-anthropic-research-how-australia-uses-claude-findings-from-the-anth-8bdd4935
  - page:2026-04-07-anthropic-research-introducing-our-science-blog-anthropic-77bcdf2c
  - page:2026-04-07-anthropic-research-labor-market-impacts-of-ai-a-new-measure-and-ear-24d6782b
  - page:2026-04-07-anthropic-research-long-running-claude-for-scientific-computing-ant-20a930ae
  - page:2026-04-07-anthropic-research-project-vend-phase-two-anthropic-6d9cb3ea
  - topic:anthropic
  - topic:machine-learning
  - topic:physics
  - topic:theoretical-physics
updated_at: 2026-04-08T08:37:25.329811Z
managed: true
---
# Vibe physics: The AI grad student

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/vibe-physics
- Document kind: blog-post
- Published at: 2026-03-23T00:00:00+00:00
- Authors: Matthew Schwartz
- Tags: anthropic, official, research, website, blog-post, ai, physics, machine learning, theoretical physics
- Topics: [Anthropic](../topics/anthropic.md), [Machine Learning](../topics/machine-learning.md), [Official](../topics/official.md), [Physics](../topics/physics.md), [Theoretical Physics](../topics/theoretical-physics.md), [Website](../topics/website.md)
- Trend score: 58.29
- Novelty score: 6.80

## Summary

Subscribe to Anthropic Science Features on AI-assisted discoveries, practical workflows, and field notes across the sciences. Can AI do theoretical physics?

## Topic Map

- [Anthropic](../topics/anthropic.md)
- [Machine Learning](../topics/machine-learning.md)
- [Official](../topics/official.md)
- [Physics](../topics/physics.md)
- [Theoretical Physics](../topics/theoretical-physics.md)
- [Website](../topics/website.md)

## Related Research

- [Introducing our Science Blog](introducing-our-science-blog-adf36e.md) (shared topics: Anthropic, Official, Website)
- [Announcing the OpenAI Safety Fellowship](announcing-the-openai-safety-fellowship-8b56c7.md) (shared topics: Official, Website)
- [OpenAI acquires TBPN](openai-acquires-tbpn-ceb257.md) (shared topics: Official, Website)
- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-e4fef4.md) (shared topics: Anthropic, Official)
- [Gradient Labs gives every bank customer an AI account manager](gradient-labs-gives-every-bank-customer-an-ai-account-manager-ee52e4.md) (shared topics: Official, Website)
- [Accelerating the next phase of AI](accelerating-the-next-phase-of-ai-3bf73f.md) (shared topics: Official, Website)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Subscribe to Anthropic Science
Features on AI-assisted discoveries, practical workflows, and field notes across the sciences.
Can AI do theoretical physics? In this guest post, professor of physics [Matthew Schwartz](https://www.physics.harvard.edu/people/facpages/schwartz) decided to find out by supervising Claude through a real research calculation, start to finish, without ever touching a file himself. His account of what happened is below.
I’m [Matthew Schwartz](https://www.physics.harvard.edu/people/facpages/schwartz), a professor of physics at Harvard and a principal investigator in the NSF Institute for Artificial Intelligence and Fundamental Interactions ([IAIFI](http://www.iaifi.org)). My area of expertise is quantum field theory, which asks what matter is, how particles interact, and why the Universe has the rules it does. One might say I wrote the [book](https://www.amazon.com/Quantum-Field-Theory-Standard-Model/dp/1107034736) on the subject. I’ve been working with modern machine learning tools for over a decade. My [first modern ML paper](https://arxiv.org/abs/1612.01551), from 2016, was an early application of deep learning to particle physics. In a [Nature Reviews Physics](https://www.nature.com/articles/s42254-022-00538-z) piece in 2022, I compared the timescale of AI and human evolution, arguing that transferring understanding between biological and artificial intelligence would become a fundamental challenge. Since then, I’ve been trying to push AI towards [more symbolic work](https://arxiv.org/abs/2408.04720) (manipulating mathematical expressions rather than numerical data) and the core questions in theoretical physics.
There has been a lot of recent hype about AI scientists doing end-to-end research autonomously. In August 2024, Sakana AI released their [AI Scientist](https://sakana.ai/ai-scientist/), a system designed to automate the entire research lifecycle—from generating hypotheses to writing papers. In February 2025, Google released an [AI co-scientist](https://arxiv.org/abs/2502.18864) built on Gemini, promising to help researchers generate and evaluate hypotheses at scale. And in August 2025, the Allen Institute for AI (Ai2) launched the open-source [Asta](https://allenai.org/asta) ecosystem, featuring tools like [CodeScientist](https://github.com/allenai/codescientist) and [AutoDiscovery](https://allenai.org/blog/autodiscovery) to find patterns in complex datasets. Since then, a new entrant has appeared every few months—FutureHouse’s [Kosmos](https://edisonscientific.com/articles/announcing-kosmos), the Autoscience Institute’s [Carl](https://autoscience.ai/), the Simons Foundation’s [Denario](https://www.simonsfoundation.org/2025/11/04/meet-denario-an-ai-assistant-for-every-step-of-the-scientific-process/) project, among others—each promising some version of end-to-end autonomous research. Even as these approaches are visionary, their successes to date seem a bit forced: run [hundreds or thousands of trials](https://www.youtube.com/watch?v=no_elVGGgW8) and define the best one as interesting. While I believe we are not far from end-to-end science, I’m not convinced we can skip the intermediate steps. Maybe LLMs need to go to graduate school before advancing straight to the Ph.D.
In mathematics, automated end-to-end AI agents have produced impressive results, at least for a certain class of problems. An early breakthrough was DeepMind’s [FunSearch](https://deepmind.google/blog/funsearch-making-new-discoveries-in-mathematical-sciences-using-large-language-models/), launched in 2023, and later [AlphaEvolve](https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/), which used LLMs to make new discoveries in combinatorics. A related project, [AlphaProof](https://deepmind.google/blog/ai-solves-imo-problems-at-silver-medal-level/), earned a silver medal at the 2024 International Mathematical Olympiad, solving problems that stumped all but five human contest
