---
id: 2026-03-30-jack-clark-import-ai-how-long-will-a-new-math-benchmark-horizonmath-l-19e5f6c5
kind: paper
title: How long will a new math benchmark, HorizonMath, last?
source_url: https://arxiv.org/abs/2603.15617
source_name: Import AI
authors:
- University of Oxford
- Harvard University
- Princeton University
- Ellison Institute of Technology
published_at: '2026-03-30T12:28:13Z'
ingested_at: '2026-04-09T20:15:33.556892Z'
content_hash: 734ff94ad45988091b932ae698bfee52f7268b3682e6e2bb528d0eff105094a0
identity_hash: 256c46275380a5f8fad37f5c437994aa6ef5a69e798e373a0552997460bf23c4
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- math benchmark
- mathematics
- automated verification
- gpt 5.4 pro
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer::story::5:https://arxiv.org/abs/2603.15617
canonical_url: https://arxiv.org/abs/2603.15617
doc_role: derived
parent_id: 2026-03-30-jack-clark-import-ai-import-ai-451-political-superintelligence-google-39f0537b
index_visibility: visible
fetched_at: '2026-04-09T20:15:33.556897Z'
short_summary: HorizonMath is a new math benchmark designed to test AI systems on solving unknown mathematical problems, featuring automated verification and covering various mathematical domains.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:44.648054Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: e9ebf968345c9d1b2dc0e6eebf6b89478dc696fe48a5d99dcc28fdf7498bcd8a
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 3d68f2b7b6cfcb801abc900f91148d519e443f025c27542b36be966ebe9e8c02
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 0.95
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses AI evaluation and reasoning by introducing a new benchmark designed to test AI systems on solving unknown mathematical problems.
  evidence_quotes:
  - 'HorizonMath is a new math benchmark designed to test AI systems on solving unknown mathematical problems, featuring automated verification and covering various '
  - A core feature of our benchmark is its fully automated, reproducible, and human-free evaluation pipeline”, the authors write. “We automate verification using hi
  - With HorizonMath, we have another useful benchmark to help us see if AI is about to cross some ‘creativity rubicon’ and begin solving unsolved problems.
---
# How long will a new math benchmark, HorizonMath, last?

Source newsletter: Import AI 451: Political superintelligence; Google’s society of minds, and a robot drummer
Source issue: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer
Published At: 2026-03-30T12:28:13+00:00
Canonical URL: https://arxiv.org/abs/2603.15617

## Newsletter Context

…New test challenges AI systems to solve unknown problems, then automatically verifies the answers… Another day brings another hard math benchmark that I imagine will crumple in the face of ongoing AI progress in the coming year. This time it’s HorizonMath, a benchmark containing 100 “predominantly unsolved” problems across 8 domains in applied and computational mathematics. The benchmark was built by researchers with the University of Oxford, Harvard University, Princeton University, and the Ellison Institute of Technology.

Special features about HorizonMath:

- Contamination-Proof: “Because the solutions are unknown, they do not exist in any training corpus, and any correct solution produced by a model would therefore signal genuine reasoning ability and autonomous discovery.”
- Automated verification : “A core feature of our benchmark is its fully automated, reproducible, and human-free evaluation pipeline”, the authors write. “We automate verification using high-precision numeric comparison and deterministic constraint-checkers”.

What HorizonMath contains: HorizonMath’s 100 problems are classified along three axes: output types, which specifies how the model needs to solve the task ranging from identifying an exact closed-form expression for a numerically approximated target value, to the production of discrete mathematical objects; solvability levels, which span ‘level 0’ (problems with known closed forms) to ‘level 3’ (problems that could be conjectured unsolvable or lack finite closed forms); and mathematical domains, which specifies the type of domain ranging from number theory to discrete geometry to mathematical constants.

Reassuringly hard: On the full dataset, the highest scoring model is GPT 5.4 Pro with 7%, followed by Opus 4.6 and Gemini 3.1 Pro which both tie at 3%. On the “Level 0” (aka, the easiest) problems, GPT 5.4 Pro leads at 50% completion, with both Opus 4.6 and Gemini 3.1 in a tie again at 30% each.

Next steps: They will expand the benchmark in two ways, first by liberalizing the sorts of solutions that they will take in, as well as by “extending beyond the three current problem categories to include open problems that require proof-based verification, integrating with formal systems such as Lean”.

Why this matters – perhaps the first truly creative AI systems will show up in mathematics: AI systems are pushing on the frontiers of math today, with systems like Gemini already helping humans to come up with seemingly original math proofs ( Import AI 441 ), and tests like “First Proof” emerging which examine how well AI systems can handle problems that have never been talked about publicly let alone solved ( Import AI 445 ). With HorizonMath, we have another useful benchmark to help us see if AI is about to cross some ‘creativity rubicon’ and begin solving unsolved problems. Read more : HorizonMath: Measuring AI Progress Toward Mathematical Discovery with Automatic Verification (arXiv) . Get the benchmark here : HorizonMath (GitHub) .

Tech Tales:

Site report [2029]

Percentage of compute and power below ground: 70% (+50 absolute points). Number of staff living fully onsite: 300 (+250). Estimated duration of ‘hard seal’ based on current supplies and a projected population of ~500: 4 months (+3 months). Estimated lead of the project relative to others in-country: 6 months. Capability estimates: 90%-110% of our own leading system.

Recommendation: Based on the substantial increase in resources allocated to hardening the facility for closed-loop development, we believe additional measures must be taken to disrupt the project. The following report lists options for consideration, many of which can be combined together. These include:

- Food system sabotage.
- Staff interference.
- Data poisoning.

Things that inspired this story: How at some point surely there will be such a thing as a hardened datacenter for AI training and inference? How the intelligence community might analyze other AI projects.
