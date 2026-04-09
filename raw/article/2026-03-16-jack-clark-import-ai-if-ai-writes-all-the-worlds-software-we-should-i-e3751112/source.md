---
id: 2026-03-16-jack-clark-import-ai-if-ai-writes-all-the-worlds-software-we-should-i-e3751112
kind: article
title: If AI writes all the world’s software, we should invest more in verification
source_url: https://lean-lang.org/
source_name: Import AI
authors: []
published_at: '2026-03-16T12:30:50Z'
ingested_at: '2026-04-09T20:15:47.004464Z'
content_hash: 947163fce40bc4c99fce2e9105f5c5987906b88612b2b4e7e7db1e7e55c444f1
identity_hash: da945344a3f3d38f87f04386da6c07fbfad36a8d2cfb27d945cb61200cd9b421
tags:
- newsletter
- ai
- analysis
- policy
- website
- article
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text::story::3:https://lean-lang.org/
canonical_url: https://lean-lang.org/
doc_role: derived
parent_id: 2026-03-16-jack-clark-import-ai-importai-449-llms-training-other-llms-72b-distri-4e9550da
index_visibility: visible
fetched_at: '2026-04-09T20:15:47.004470Z'
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
# If AI writes all the world’s software, we should invest more in verification

Source newsletter: ImportAI 449: LLMs training other LLMs; 72B distributed training run; computer vision is harder than generative text
Source issue: https://jack-clark.net/2026/03/16/importai-449-llms-training-other-llms-72b-distributed-training-run-computer-vision-is-harder-than-generative-text
Published At: 2026-03-16T12:30:50+00:00
Canonical URL: https://lean-lang.org/

## Newsletter Context

…Can we just rewrite most of our software into Lean?… Leonardo de Moura, a scientist who is also the Chief Architect of the Lean Focused Research Organization (FRO), thinks that the rise of AI for the creation of new software means that humans need to invest a lot more in verification and testing infrastructure – and he has an interesting idea for how to do it. Of course, someone who loves Lean , a programming language dedicated to building correct and formally verified code, would think this. But his arguments are quite persuasive, and generally map onto the idea that if AI eats the economy we should expect a lot of human value to shift towards verification of the code and systems that AI develops ( Import AI 447 ).

Why verification matters: “The friction of writing code manually used to force careful design. AI removes that friction, including the beneficial friction. The answer is not to slow AI down. It is to replace human friction with mathematical friction: let AI move fast, but make it prove its work,” he writes. “Verification, testing, and specification have always been the bottleneck, not implementation… the value is not in the verification workforce. It is in what verified delivery enables.”

A proof of concept for this futuristic world: The Lean FRO recently helped build a proof of concept for what this kind of verified world might look like; they had an AI agent convert zlib, a C compression library, to Lean. “The result demonstrates that AI can convert production software to a verified form today. This was not expected to be possible yet,” he writes. The conversion involved four steps:

- The LLM (Claude) made a clean Lean implementation of the zlib compression format, including the DEFLATE algorithm it uses.
- They ran the rewritten zlib through the library’s test suite and it passed, confirming equivalence.
- Key properties were stated and proved as mathematical theorems – for example, a machine-checked proof that ensures that decompressing a compressed buffer always returns the original data.
- Now, an optimized version of the library is being developed and proved equivalent to the verified model.

A verification platform: Moura imagines a world where we re-develop the critical software stack of the world to have mathematical proofs built into it. “The goal is a verified software stack: open source, freely available, mathematically guaranteed correct. Developers building critical systems choose verified components the way they choose open-source libraries today, except these carry proofs, not just tests,” he writes. “The target is the foundation of the modern software stack: cryptography, because everything else trusts it. Core libraries (data structures, algorithms, compression) because they are the building blocks of all software. Storage engines like SQLite, embedded in every device on earth. Parsers and protocol implementations (JSON, HTTP, DNS, certificate validation) because every message passes through them. And compilers and runtimes, because they build everything else,” he writes. “Each verified component is a permanent public good…Once verified components are cheap, you compose them with confidence.”

Why this matters – the world needs infrastructure it can rely on: It seems like we’re heading to a world where AI writes the vast majority of the world’s software. Given that, we need to figure out how we relate to this world – my suspicion is a lot of human labor is going to shift to analyzing and verifying the work of AI systems, so it seems sensible to invest in some fundamental infrastructure that can guarantee a higher level of verification and reliability in the software built by AI. Read more: When AI Writes the World’s Software, Who Verifies It? (Leonardo de Moura blog) .
