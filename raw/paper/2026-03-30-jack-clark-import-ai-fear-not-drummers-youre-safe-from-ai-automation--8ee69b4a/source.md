---
id: 2026-03-30-jack-clark-import-ai-fear-not-drummers-youre-safe-from-ai-automation--8ee69b4a
kind: paper
title: Fear not, drummers, you’re safe from AI automation for now
source_url: https://arxiv.org/abs/2603.22263
source_name: Import AI
authors: []
published_at: '2026-03-30T12:28:13Z'
ingested_at: '2026-04-09T20:15:30.862233Z'
content_hash: 7a14f0641ca60ba1c34597428edf9a6aaf42256390e8e2485157aa8561647a62
identity_hash: eb7728f69312cbf9c5bbbc026eaa44d26c2ad212fd5c1c20d32d70fe5b70ee1e
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- robotics
- dexdrummer
- reinforcement learning
- robot hands
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer::story::2:https://arxiv.org/abs/2603.22263
canonical_url: https://arxiv.org/abs/2603.22263
doc_role: derived
parent_id: 2026-03-30-jack-clark-import-ai-import-ai-451-political-superintelligence-google-39f0537b
index_visibility: visible
fetched_at: '2026-04-13T18:13:10.078657Z'
short_summary: The paper introduces DexDrummer, a hierarchical, two-stage policy for teaching a robot hand to play the drums. The research explores the challenges of fine-grained low-latency dexterous control in robotics.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:34.831253Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: c13d7da6e16c60665f1e51ff3713ff0a81125c5ada32fd9aac5a5c0f3092560a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: c45b2e14a38a10330bc0cad40cd0c90bde777c229261f38004e00867e65dba13
lightweight_score:
  relevance_score: 0.36
  source_fit_score: 0.35
  topic_fit_score: 0.55
  author_fit_score: 0.0
  evidence_fit_score: 0.65
  confidence_score: 0.85
  bucket_hint: worth_a_skim
  reason: The document touches on reinforcement learning and control policies, which aligns with the user's interest in reasoning and LLM training, but the topic is focused on robotics rather than core LLM research.
  evidence_quotes:
  - The paper introduces DexDrummer, a hierarchical, two-stage policy for teaching a robot hand to play the drums.
  - They built DexDrummer “a hierarchical, two-stage policy for drumming” which has a high-level RL policy, as well as a low-level dexterous policy.
  - This is an area where I’d strongly encourage people to view the videos online to get some calibration about just how fiendishly hard this task is – the robots a
---
# Fear not, drummers, you’re safe from AI automation for now

Source newsletter: Import AI 451: Political superintelligence; Google’s society of minds, and a robot drummer
Source issue: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer
Published At: 2026-03-30T12:28:13+00:00
Canonical URL: https://arxiv.org/abs/2603.22263

## Newsletter Context

…DexDrummer tackles a fiendishly hard robot hand problem… Whenever I get a bit worried about the pace of AI progress I toggle over to the ‘robotics’ sub-section of arXiv, read some papers, and feel a huge sense of relief. Robots, as everyone knows, are extremely hard to do well, with reality tending to screw up even the most advanced techniques. An even harder version of robotics is fine-grained low-latency dexterous control, where you need to get a robot hand to do something. So it’s with a combination of amusement and empathy that I read DexDrummer, a paper testing out how well contemporary AI approaches can get a robot hand to play the drums. The short answer is: robot hands are pretty terrible drummers!

What they did: They built DexDrummer “a hierarchical, two-stage policy for drumming” which has a high-level RL policy, as well as a low-level dexterous policy. They train their system in a simulated environment that contains a bimanual robot setup and a full drum set (snare, tom, ride, hi-hat, and crash). The main system generates a stick trajectory in task space, then a low-level system which tries to control the hand – this part is complex and involves encouraging the thumb and index finger to grasp the center of the drumstick paired with an “arm penalty constraint, which reduces excessive arm movements”. There is also work shaping rewards to ensure the robot is able to chain multiple drumhits together – this is achieved via a “contact curriculum” which allows the agent to practice trajectory following in free space while following the trajectory reward.

Real world testing: They test out the trained policy in reality on two 7-DOF Franka Panda arms and two 20-DOF Tesollo DG-5F hands. This is an area where I’d strongly encourage people to view the videos online to get some calibration about just how fiendishly hard this task is – the robots are able to hit the drums, but it’s painfully awkward to watch, and my sense is it’ll be quite a while till a human drummer has to look over their proverbial shoulder.

Why this matters – robotics as the last eval: Robotics in anything approximating a dynamic, rapidly changing environment (for instance, improvising drums with a live band) feels like one of the last frontiers for AI – and as this research shows, much like with modern computer vision research, getting AI to perform well requires the crafting of highly complicated artisanal policies. We’re a very long way from the generality of pretrained language models here. Read more: DexDrummer: In-Hand, Contact-Rich, and Long-Horizon Dexterous Robot Drumming (arXiv) . Please, I am begging you, check out the videos for a good time : DexDrummer site .
