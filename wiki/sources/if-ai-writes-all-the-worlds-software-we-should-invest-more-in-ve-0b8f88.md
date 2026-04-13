---
id: page:2026-03-16-jack-clark-import-ai-if-ai-writes-all-the-worlds-software-we-should-i-e3751112
page_type: source-note
title: If AI writes all the world’s software, we should invest more in verification
aliases:
- If AI writes all the world’s software, we should invest more in verification
source_refs:
- 2026-03-16-jack-clark-import-ai-if-ai-writes-all-the-worlds-software-we-should-i-e3751112
backlinks:
- page:2026-02-02-jack-clark-import-ai-brain-emulation-is-tractable-within-our-lifetime-d0e88b07
- page:2026-02-02-jack-clark-import-ai-one-way-of-seeing-ai-progress-how-hard-its-getti-b88405ad
- page:2026-02-16-jack-clark-import-ai-superintelligence-could-save-and-extend-lives-so-430fb582
- page:2026-03-02-jack-clark-import-ai-physical-intelligence-shows-off-some-of-its-robo-b58b416c
- page:2026-03-02-jack-clark-import-ai-the-agi-economy-most-labor-goes-to-the-machines--5bc18134
- page:2026-03-09-jack-clark-import-ai-ai-progress-is-moving-faster-than-even-well-rega-7aa560e6
- page:2026-03-09-jack-clark-import-ai-indian-researchers-use-edge-computing-to-prototy-fac45e73
- page:2026-03-16-jack-clark-import-ai-covenant-72b-challenging-the-political-economy-o-5a266f00
- page:2026-03-30-jack-clark-import-ai-ai-might-let-us-build-political-superintelligenc-34706c0a
- page:2026-04-06-jack-clark-import-ai-uh-oh-theres-a-scaling-war-for-cyberattacks-as-w-cdadb242
- topic:lean
- topic:software
updated_at: '2026-04-09T23:10:02.771405Z'
managed: true
---
# If AI writes all the world’s software, we should invest more in verification

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://lean-lang.org/
- Document kind: article
- Published at: 2026-03-16T12:30:50+00:00
- Authors: Leonardo de Moura
- Tags: newsletter, ai, analysis, policy, website, article, verification, software, lean, infrastructure, sub-document
- Topics: [Infrastructure](../topics/infrastructure.md), [Lean](../topics/lean.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Software](../topics/software.md), [Sub Document](../topics/sub-document.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

If AI writes most of the world's software, humans should invest more in verification and testing infrastructure. This involves creating a verified software stack where critical components are mathematically guaranteed correct.

## Topic Map

- [Infrastructure](../topics/infrastructure.md)
- [Lean](../topics/lean.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Software](../topics/software.md)
- [Sub Document](../topics/sub-document.md)

## Related Research

- [Cursor introduces warp decode, where each GPU warp computes one output instead of grouping work by experts](cursor-introduces-warp-decode-where-each-gpu-warp-computes-one-o-46e94c.md) (shared topics: Infrastructure, Newsletter, Sub Document)
- [Confessions of a Millennial in Tech](confessions-of-a-millennial-in-tech-7bf0b3.md) (shared topics: Newsletter, Software, Sub Document)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy, Sub Document)
- [AI might let us build “political superintelligence”](ai-might-let-us-build-political-superintelligence-25b211.md) (shared topics: Newsletter, Policy, Sub Document)
- [COVENANT-72B: Challenging the political economy of AI via distributed training](covenant-72b-challenging-the-political-economy-of-ai-via-distrib-2822a2.md) (shared topics: Infrastructure, Newsletter, Policy)
- [Indian researchers use edge computing to prototype a citywide camera network](indian-researchers-use-edge-computing-to-prototype-a-citywide-ca-1f10dc.md) (shared topics: Newsletter, Policy, Sub Document)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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

Why this matters – the world needs infrastructure it can rely on: It seems like we’re heading to a world where AI writes the vast majority of the world’s software. Given that, we need to figure out how we relate to this world – my suspicion is a lot of human labor is going to shift to analyzing and verifying the work of AI systems,
