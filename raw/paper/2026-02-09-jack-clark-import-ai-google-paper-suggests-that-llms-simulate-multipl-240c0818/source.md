---
id: 2026-02-09-jack-clark-import-ai-google-paper-suggests-that-llms-simulate-multipl-240c0818
kind: paper
title: Google paper suggests that LLMs simulate multiple personalities to answer questions
source_url: https://arxiv.org/abs/2601.10825
source_name: Import AI
authors: []
published_at: '2026-02-09T14:03:34Z'
ingested_at: '2026-04-09T20:16:51.419162Z'
content_hash: 326dc59cae066e629a6e52994b246367a3d0e667eae3649f8db89a8110386bfe
identity_hash: 1dd404eb230f0c2ad4078858391f84f75bb43c9b9f647d5b8785e2d24e201ba1
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench::story::1:https://arxiv.org/abs/2601.10825
canonical_url: https://arxiv.org/abs/2601.10825
doc_role: derived
parent_id: 2026-02-09-jack-clark-import-ai-import-ai-444-llm-societies-huawei-makes-kernels-6922e476
index_visibility: visible
fetched_at: '2026-04-09T20:16:51.419170Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Google paper suggests that LLMs simulate multiple personalities to answer questions

Source newsletter: Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench
Source issue: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
Published At: 2026-02-09T14:03:34+00:00
Canonical URL: https://arxiv.org/abs/2601.10825

## Newsletter Context

…The smarter we make language models, the more they tend towards building and manipulating rich, multi-agent world models… When thinking about hard problems, I often find it’s helpful to try and view them from multiple perspectives, especially when it comes to checking my own assumptions and biases. Now, researchers with Google, the University of Chicago, and the Santa Fe Institute, have studied how AI reasoning models work and have concluded they do the same thing, with LLMs seeming to invoke multiple different perspectives in their chains of thought when solving hard problems.

The key finding: In tests on DeepSeek-R1 and QwQ-32B (one wonders why the Google researchers didn’t touch Google models here…) they find that “enhanced reasoning emerges not from extended computation alone, but from the implicit simulation of complex, multi-agent-like interactions—a society of thought—which enables the deliberate diversification and debate among internal cognitive perspectives characterized by distinct personality traits and domain expertise.”

How it works: It appears that different forms of persona and discussion style modeling emerge as a consequence of training models through RL to do reasoning – the results don’t show up on base pre-trained models like DeepSeek v3. The authors find that models embody a variety of conversational styles, including question and answering, perspective shifts, reconciliation, and conflict of perspectives. “In an organic chemistry problem requiring multistep reaction analysis to identify the final product’s structure (i.e., multi-step Diels-Alder synthesis), DeepSeek-R1 exhibits perspective shifts and conflict, expressed through socio-emotional roles such as disagreement, giving opinion, and giving orientation,” they find. Similarly, “In a creative writing trace where the model rewrites the sentence “I flung my hatred into the burning fire,” seven perspectives emerge, including a creative ideator (highest Openness and Extraversion) who generates stylistic alternatives and a semantic fidelity checker (low agreeableness, high neuroticism) who prevents scope creep—“But that adds ‘deep-seated’ which wasn’t in the original”. And in a mathematical puzzle “at step 40, the model produces mechanical, enumerative chain-of-thought-style reasoning, whereas by step 120, two distinctive simulated personas have appeared, recognizing their collectivity with the pronoun “we”— expressing uncertainty (“Again no luck”), considering alternatives (“Maybe we can try using negative numbers”), and reflecting on problem constraints.”

Why this matters: Janus strikes again: Back in September 2022 janus wrote a post on LessWrong saying the correct way to view LLMs was as “simulators”. The post correctly called out many of the phenomena we now experience, where LLMs seem to be coming alive with all kinds of wild behaviors which are best explained by the LLMs learning to model and represent rich concepts to themselves to help them compute answers to our questions. “Calling GPT a simulator gets across that in order to do anything, it has to simulate something,” Janus wrote. “Training a model to predict diverse trajectories seems to make it internalize general laws underlying the distribution, allowing it to simulate counterfactuals that can be constructed from the distributional semantics.”. This Google paper lines up with this, along with other recent findings that as we make LLMs more advanced they both develop richer and more powerful representations of reality, as well as exhibiting a greater ability to model a theory of mind. It all adds up to a conclusion that LLMs are becoming alive, in the sense that to solve hard problems they must simulate for themselves a world model containing different concepts, even including representations of other perspectives or other minds. As the authors say: “Our findings suggest that reasoning models like DeepSeek-R1 do not simply generate longer or more elaborate chains of thought. Rather, they exhibit patterns characteristic of a social and conversational process generating “societies of thought”—posing questions, introducing alternative perspectives, generating and resolving conflicts, and coordinating diverse socio-emotional roles.” Read more : Reasoning Models Generate Societies of Thought (arXiv) .
