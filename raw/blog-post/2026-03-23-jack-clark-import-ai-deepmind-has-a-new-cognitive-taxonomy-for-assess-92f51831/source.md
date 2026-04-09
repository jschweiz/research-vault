---
id: 2026-03-23-jack-clark-import-ai-deepmind-has-a-new-cognitive-taxonomy-for-assess-92f51831
kind: blog-post
title: DeepMind has a new “cognitive taxonomy” for assessing machine intelligence
source_url: https://blog.google/innovation-and-ai/models-and-research/google-deepmind/measuring-agi-cognitive-framework
source_name: Import AI
authors:
- Google DeepMind
published_at: '2026-03-23T12:31:45Z'
ingested_at: '2026-04-09T20:15:40.749747Z'
content_hash: 916ba57b6631ae286037c3203324454d75a81e3d38e5454b674ad87e99fb7894
identity_hash: 3cad0bbc3d1adbaeccc8551c012d04bf71b98d88ad14e8e8273b5337e0949c6e
tags:
- newsletter
- ai
- analysis
- policy
- website
- blog-post
- cognitive taxonomy
- machine intelligence
- agi
- ai assessment
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks::story::1:https://blog.google/innovation-and-ai/models-and-research/google-deepmind/measuring-agi-cognitive-framework
canonical_url: https://blog.google/innovation-and-ai/models-and-research/google-deepmind/measuring-agi-cognitive-framework
doc_role: derived
parent_id: 2026-03-23-jack-clark-import-ai-import-ai-450-chinas-electronic-warfare-model-tr-26ab1bcb
index_visibility: visible
fetched_at: '2026-04-09T20:15:40.749756Z'
short_summary: Google DeepMind has introduced a 'cognitive taxonomy' with ten dimensions to assess machine intelligence, including perception, reasoning, and metacognition. The taxonomy suggests a three-stage process for assessing AI systems against human cognitive baselines.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:43.005761Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: ef26cb6f3786121f8f10dda8c1e645c5d0a323b5b381b391919e213d7776d3e6
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: d8bf38a2921e60b4bb49fefa6b08c9061aaeccf2012f9931c67853e514c3be5d
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.5
  topic_fit_score: 1.0
  author_fit_score: 1.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses favorite topics like LLM evaluation, reasoning, and the work of DeepMind, making it a high-priority read.
  evidence_quotes:
  - Google DeepMind has introduced a 'cognitive taxonomy' with ten dimensions to assess machine intelligence, including perception, reasoning, and metacognition.
  - The taxonomy involves ten distinct dimensions, two of which are composites.
  - 'Here, DeepMind recommends a three-stage process: - Conduct cognitive assessment: Assess the AI system for the different skills. - Collect human baselines: Figur'
---
# DeepMind has a new “cognitive taxonomy” for assessing machine intelligence

Source newsletter: Import AI 450: China’s electronic warfare model; traumatized LLMs; and a scaling law for cyberattacks
Source issue: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks
Published At: 2026-03-23T12:31:45+00:00
Canonical URL: https://blog.google/innovation-and-ai/models-and-research/google-deepmind/measuring-agi-cognitive-framework

## Newsletter Context

…Towards the ultimate test for a smarter-than-human synthetic mind… Google DeepMind has published a nice, short paper laying out a ‘cognitive taxonomy’ they hope to develop and use to assess increasingly powerful synthetic minds. This work is a followup to DeepMind’s 2023 work where it tried to define the “Levels of AGI” ( Import AI 348 ).

Cognitive taxonomy: The taxonomy involves ten distinct dimensions, two of which are composites.

- Perception : Extract and process information from the environment.

- Generation : Produce outputs like speech, text, motor movements, and computer control.
- Attention: Focus cognitive resources on specific aspects of perceptual stimuli, thoughts, or tasks.
- Learning: Acquire new knowledge, skills, or understanding.
- Memory : Store and retrieve information over time.
- Reasoning : Draw valid conclusions and make inferences by applying logical principles.
- Metacognition : Knowledge about how the system’s own cognitive processes and control over them work.
- Executive functions : Facilitate goal-directed behavior via planning, inhibition, and cognitive flexibility.
- Problem solving (composite faculty): Find effective solutions to domain-specific problems.
- Social cognition (composite faculty): Process and interpret social information and respond appropriately.

How to assess this? Of course, once you have a taxonomy, running and assessing the right evaluations is going to be one of the challenges. Here, DeepMind recommends a three-stage process:

- Conduct cognitive assessment: Assess the AI system for the different skills.
- Collect human baselines: Figure out where humans baseline on the same tests.
- Build cognitive profiles: “Map out the strengths and weaknesses of the system relative to human performance across the 10 cognitive faculties”.

Why this matters: The Turing test is dead, evals are mostly saturated, but it sure would be nice to know if we’ve definitely built a machine that outcompetes humans on all the cognitive dimensions that matter. The rule with these things is that once an AI system saturates an eval, you realize all the ways the eval was broken and design a new one. Here, DeepMind is trying really hard to build things in such a way that if you fully outperform humans across the cognitive taxonomy, you might really have built a superintelligence. It’ll be interesting to see what evals they develop or pull-in for assessing the different cognitive factors. Read more: Measuring progress toward AGI: A cognitive framework (Google blog) . Read the research : Measuring Progress Toward AGI: A Cognitive Framework (PDF) .
