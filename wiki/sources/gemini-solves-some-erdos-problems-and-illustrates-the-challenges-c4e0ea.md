---
id: page:2026-02-09-jack-clark-import-ai-gemini-solves-some-erdos-problems-and-illustrate-f0eb84fe
page_type: source-note
title: Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI
aliases:
- Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI
source_refs:
- 2026-02-09-jack-clark-import-ai-gemini-solves-some-erdos-problems-and-illustrate-f0eb84fe
backlinks:
- page:2026-02-09-jack-clark-import-ai-huawei-uses-an-llm-to-automate-the-design-of-hua-1fe2d7d6
- page:2026-02-16-jack-clark-import-ai-math-researchers-see-if-ai-can-help-solve-their--da564141
- page:2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
- topic:erdos-problems
- topic:human-evaluation
- topic:math-research
updated_at: '2026-04-09T23:10:03.396917Z'
managed: true
---
# Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2601.22401
- Document kind: paper
- Published at: 2026-02-09T14:03:34+00:00
- Authors: Google DeepMind, UC Berkeley, Seoul National University, Stanford University, Korea Institute for Advanced Study, University of Cambridge
- Tags: newsletter, ai, analysis, policy, website, paper, math research, erdős problems, llm, human evaluation, sub-document
- Topics: [Erdos Problems](../topics/erdos-problems.md), [Human Evaluation](../topics/human-evaluation.md), [Llm](../topics/llm.md), [Math Research](../topics/math-research.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Researchers used Google's Gemini-based LLM to attempt solving open Erdős mathematical problems, demonstrating that while AI can generate candidate solutions, human evaluation remains crucial for determining correctness and meaning. The study highlights the challenges of automating math research and the need for human oversight in AI-driven scientific discovery.

## Topic Map

- [Erdos Problems](../topics/erdos-problems.md)
- [Human Evaluation](../topics/human-evaluation.md)
- [Llm](../topics/llm.md)
- [Math Research](../topics/math-research.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)

## Related Research

- [Meta uses a harness to coax Anthropic’s models into self-improvement](meta-uses-a-harness-to-coax-anthropics-models-into-self-improvem-032241.md) (shared topics: Llm, Newsletter, Policy)
- [COVENANT-72B: Challenging the political economy of AI via distributed training](covenant-72b-challenging-the-political-economy-of-ai-via-distrib-2822a2.md) (shared topics: Llm, Newsletter, Policy)
- [Math researchers see if AI can help solve their private solutions to frontier problems. The answer: Kind of.](math-researchers-see-if-ai-can-help-solve-their-private-solution-0b0950.md) (shared topics: Math Research, Newsletter, Policy)
- [Huawei uses an LLM to automate the design of Huawei chip kernels](huawei-uses-an-llm-to-automate-the-design-of-huawei-chip-kernels-b40808.md) (shared topics: Llm, Newsletter, Policy)
- [OpenAI #16: A History and a Proposal](openai-16-a-history-and-a-proposal-a6e162.md) (shared topics: Newsletter, Policy)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI

Source newsletter: Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench
Source issue: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
Published At: 2026-02-09T14:03:34+00:00
Canonical URL: https://arxiv.org/abs/2601.22401

## Newsletter Context

…AI for science is great, but it can also introduce new problems… An interdisciplinary group of scientists from Google DeepMind and a bunch of universities have used an internal Google Gemini-based LLM, codenamed Aletheia, to solve some math problems. The results demonstrate that contemporary AI systems can work on the frontiers of science, but also show how evaluating and filtering the solutions they come up with may be an important, challenging task for humans.

The key numbers – 700 candidates and 1 creative and interesting solution: Erdős problems are 1000+ open mathematical conjectures left behind by prolific mathematician Paul Erdős at the time of his death. At the time of writing, a few hundred of these problems have been solved. For this research, the researchers tried to see whether their AI system, Aletheia, could generate solutions to any of the 700 remaining open questions. The results: yes, but with many, many caveats. Aletheia was able to surface 200 candidate solutions which humans then needed to grade, slimming down to 63 correct response, and further expert mathematical evaluation slimmed this down to a further subset of only 13 solves that Google calls “correct meaningful responses”. “The remaining 50 of Aletheia’s correct solutions were technically valid but mathematically meaningless because the problem statements were interpreted in a way that did not capture Erdős intent, often (but not always) leading to trivial solutions,” the researchers write. “”Only 13 solutions correctly addressed the intended problem statement (either by invoking the literature, or by a novel argument).”

When 13 become 2: When you dig into these 13, the results get a bit less impressive:

- 5 get classed as “literature identification”: “On these problems, Aletheia found that a solution was already explicitly in the literature, despite the problem being marked “Open” on Bloom’s website at the time of model deployment”.
- 3 are “partial AI solution”: “On these problems, there were multiple questions and Aletheia found the first correct solution to one of the questions”.
- 3 are “independent rediscovery”: “On these problems, Aletheia found a correct solution, but human auditors subsequently found an independent solution already in the literature.”
- This leaves 2 “autonomous novel solution” solves: “On these problems, Aletheia found the first correct solution (as far as we can tell) in a mathematically substantive way”. Of these, 1 of the solutions seems genuinely interesting: “We tentatively believe Aletheia’s solution to Erdős-1051 represents an early example of an AI system autonomously resolving a slightly non-trivial open Erdős problem of somewhat broader (mild) mathematical interest, for which there exists past literature on closely-related problems [KN16], but none fully resolve Erdős-1051,” they write. “Moreover, it does not appear obvious to us that Aletheia’s solution is directly inspired by any previous human argument”.

Who did the research: Along with Google DeepMind, the following universities participated in the research: UC Berkeley, Seoul National University, Stanford University, Korea Institute for Advanced Study, University of Cambridge, Brown University, Yonsei University, Concordia University, Academia Sinica, and National Taiwan University.

Why this matters – even if AI speeds up science, humans might be the bottleneck (at least for a while): This paper is a nice example of “O-ring automation” – AI here has massively sped up the art of generating proofs, but it still requires laborious, skilled wo
