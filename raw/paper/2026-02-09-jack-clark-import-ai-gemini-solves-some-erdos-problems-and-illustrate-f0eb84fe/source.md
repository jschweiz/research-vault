---
id: 2026-02-09-jack-clark-import-ai-gemini-solves-some-erdos-problems-and-illustrate-f0eb84fe
kind: paper
title: Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI
source_url: https://arxiv.org/abs/2601.22401
source_name: Import AI
authors:
- Google DeepMind
- UC Berkeley
- Seoul National University
- Stanford University
- Korea Institute for Advanced Study
- University of Cambridge
published_at: '2026-02-09T14:03:34Z'
ingested_at: '2026-04-09T20:16:52.448903Z'
content_hash: 1dadc573f7126558cc9e667b7dc730e7258de997d50bd96ea79a3be511ca91f5
identity_hash: 8f3e6faa87b27d952201a12a8747e0a4eb182acd48006fa3811254569dc41216
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- math research
- erdős problems
- llm
- human evaluation
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench::story::3:https://arxiv.org/abs/2601.22401
canonical_url: https://arxiv.org/abs/2601.22401
doc_role: derived
parent_id: 2026-02-09-jack-clark-import-ai-import-ai-444-llm-societies-huawei-makes-kernels-6922e476
index_visibility: visible
fetched_at: '2026-04-13T18:16:29.991590Z'
short_summary: An interdisciplinary group used Google's Gemini-based LLM to attempt solving open Erdős mathematical problems, demonstrating that while AI can generate candidate solutions, human evaluation remains crucial for determining correctness and meaning.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:33.820012Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 9a5724b28048f2a52bddac313c3bc344713ae3c23a112acb707fdf945851c3eb
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: d3060ec7be507eef85165d8607dea441117194a6787dfa1e8f092c1884baf092
lightweight_score:
  relevance_score: 0.65
  source_fit_score: 0.3
  topic_fit_score: 0.95
  author_fit_score: 0.8
  evidence_fit_score: 0.9
  confidence_score: 1.0
  bucket_hint: worth_a_skim
  reason: The document strongly aligns with the user's favorite topics (LLM evaluation, reasoning, and human oversight) and features a top-tier author (DeepMind).
  evidence_quotes:
  - An interdisciplinary group used Google's Gemini-based LLM to attempt solving open Erdős mathematical problems, demonstrating that while AI can generate candidat
  - Large Language Models can easily generate candidate solutions, but the number of experts who can judge the correctness of a solution is relatively small, and ev
  - 'This paper is a nice example of “O-ring automation” – AI here has massively sped up the art of generating proofs, but it still requires laborious, skilled work '
---
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

Why this matters – even if AI speeds up science, humans might be the bottleneck (at least for a while): This paper is a nice example of “O-ring automation” – AI here has massively sped up the art of generating proofs, but it still requires laborious, skilled work by humans to filter this down to the actually correct and useful responses. This trend will likely hold for some years, where AI will not be able to autonomously do science end-to-end, partially because a big chunk of scientific advancement comes down to something you might think of as “expert intuition” which exists in the heads of a small number of living scientists and was refined by their own biological intelligence by reading the same literature as the LLMs. Extracting this kind of expert taste feels like something that is tractable but will take a while. “Large Language Models can easily generate candidate solutions, but the number of experts who can judge the correctness of a solution is relatively small, and even for experts, substantial time is required to carry out such evaluations”, the authors write. “As AI-generated mathematics grows, the community must remain vigilant of “subconscious plagiarism”, whereby AI reproduces knowledge of the literature acquired during training, without proper acknowledgment. Note that formal verification cannot help with any of these difficulties.” Read more: Semi-Autonomous Mathematics Discovery with Gemini: A Case Study on the Erdős Problems (arXiv) .
