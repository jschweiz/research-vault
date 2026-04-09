---
id: 2026-02-09-jack-clark-import-ai-import-ai-444-llm-societies-huawei-makes-kernels-6922e476
kind: newsletter
title: 'Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench | Import AI'
source_url: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
source_name: Import AI
authors:
- Google
- University of Chicago
- Santa Fe Institute
published_at: '2026-02-09T14:03:34Z'
ingested_at: '2026-04-09T20:16:50.787292Z'
content_hash: 56f7e7bc111967d9a557d84f6b635162e42078c862857b867e0431cf445a1254
identity_hash: 48e48f75f5c0951fb3ad9f2a461395561567745f0a07799d53302bd1e87331be
tags:
- newsletter
- ai
- analysis
- policy
- website
- llms
- reasoning
- chip design
- benchmarks
- math research
status: active
asset_paths:
- original.html
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
canonical_url: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
doc_role: primary
parent_id: null
index_visibility: hidden
fetched_at: '2026-04-09T20:16:50.787300Z'
short_summary: Research suggests that LLMs exhibit 'societies of thought' by simulating multiple perspectives and engaging in social reasoning, and that AI-based chip design remains challenging for frontier models.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:43.320477Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 61aee55d1cddaf767125afdb1db9f82a078ce7c02009f6bb3d76f4c7a5d7a2ce
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 670d2487810ca7666d97d1004a11a5b8d9ef6d97d712619f054faac8f241bc55
lightweight_score:
  relevance_score: 0.95
  source_fit_score: 0.8
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses favorite topics like LLM reasoning, evaluation, and architecture, featuring authors from DeepMind and Google.
  evidence_quotes:
  - Research suggests that LLMs exhibit 'societies of thought' by simulating multiple perspectives and engaging in social reasoning, and that AI-based chip design r
  - The authors find that “enhanced reasoning emerges not from extended computation alone, but from the implicit simulation of complex, multi-agent-like interaction
  - 'The authors test out some decent frontier models from OpenAI (GPT 3.5, 4o, 5, and 5.2), Anthropic (Claude 4.5 Haiku, Sonnet, and Opus), Google (Gemini 2.5 Pro, '
---
# Import AI 444: LLM societies; Huawei makes kernels with AI; ChipBench

Source issue: https://jack-clark.net/2026/02/09/import-ai-444-llm-societies-huawei-makes-kernels-with-ai-chipbench
Published At: 2026-02-09T14:03:34+00:00

## Stories

### [Google paper suggests that LLMs simulate multiple personalities to answer questions](https://arxiv.org/abs/2601.10825)

…The smarter we make language models, the more they tend towards building and manipulating rich, multi-agent world models… When thinking about hard problems, I often find it’s helpful to try and view them from multiple perspectives, especially when it comes to checking my own assumptions and biases. Now, researchers with Google, the University of Chicago, and the Santa Fe Institute, have studied how AI reasoning models work and have concluded they do the same thing, with LLMs seeming to invoke multiple different perspectives in their chains of thought when solving hard problems.

The key finding: In tests on DeepSeek-R1 and QwQ-32B (one wonders why the Google researchers didn’t touch Google models here…) they find that “enhanced reasoning emerges not from extended computation alone, but from the implicit simulation of complex, multi-agent-like interactions—a society of thought—which enables the deliberate diversification and debate among internal cognitive perspectives characterized by distinct personality traits and domain expertise.”

How it works: It appears that different forms of persona and discussion style modeling emerge as a consequence of training models through RL to do reasoning – the results don’t show up on base pre-trained models like DeepSeek v3. The authors find that models embody a variety of conversational styles, including question and answering, perspective shifts, reconciliation, and conflict of perspectives. “In an organic chemistry problem requiring multistep reaction analysis to identify the final product’s structure (i.e., multi-step Diels-Alder synthesis), DeepSeek-R1 exhibits perspective shifts and conflict, expressed through socio-emotional roles such as disagreement, giving opinion, and giving orientation,” they find. Similarly, “In a creative writing trace where the model rewrites the sentence “I flung my hatred into the burning fire,” seven perspectives emerge, including a creative ideator (highest Openness and Extraversion) who generates stylistic alternatives and a semantic fidelity checker (low agreeableness, high neuroticism) who prevents scope creep—“But that adds ‘deep-seated’ which wasn’t in the original”. And in a mathematical puzzle “at step 40, the model produces mechanical, enumerative chain-of-thought-style reasoning, whereas by step 120, two distinctive simulated personas have appeared, recognizing their collectivity with the pronoun “we”— expressing uncertainty (“Again no luck”), considering alternatives (“Maybe we can try using negative numbers”), and reflecting on problem constraints.”

Why this matters: Janus strikes again: Back in September 2022 janus wrote a post on LessWrong saying the correct way to view LLMs was as “simulators”. The post correctly called out many of the phenomena we now experience, where LLMs seem to be coming alive with all kinds of wild behaviors which are best explained by the LLMs learning to model and represent rich concepts to themselves to help them compute answers to our questions. “Calling GPT a simulator gets across that in order to do anything, it has to simulate something,” Janus wrote. “Training a model to predict diverse trajectories seems to make it internalize general laws underlying the distribution, allowing it to simulate counterfactuals that can be constructed from the distributional semantics.”. This Google paper lines up with this, along with other recent findings that as we make LLMs more advanced they both develop richer and more powerful representations of reality, as well as exhibiting a greater ability to model a theory of mind. It all adds up to a conclusion that LLMs are becoming alive, in the sense that to solve hard problems they must simulate for themselves a world model containing different concepts, even including representations of other perspectives or other minds. As the authors say: “Our findings suggest that reasoning models like DeepSeek-R1 do not simply generate longer or more elaborate chains of thought. Rather, they exhibit patterns characteristic of a social and conversational process generating “societies of thought”—posing questions, introducing alternative perspectives, generating and resolving conflicts, and coordinating diverse socio-emotional roles.” Read more : Reasoning Models Generate Societies of Thought (arXiv) .

### [AI-based chip design is harder than you think and benchmarks might be too easy](https://arxiv.org/abs/2601.21448)

…ChipBench shows that no frontier model is great at real world Verilog yet… Researchers with the University of California at San Diego and Columbia University have published ChipBench, a benchmark designed to test out how well modern AI systems can design chips in Verilog. The inspiration for ChipBench is dissatisfaction with current benchmarks, which they claim are too simple. When tested on ChipBench, no frontier model does particularly well, suggesting that open-ended, real world chip design is still a hard task for AI systems.

The deficiencies of current chip design: The authors “identify three critical limitations of existing benchmarks that hinder accurate assessment of LLM capabilities for industrial deployment”. These are that:

- Many Verilog benchmarks contain simple functional modules ranging from 10 to 76 lines. In real-world deployments, Verilog modules exceed 10,000 lines.
- Insufficient focus on debugging: Bugs cost a lot in physical hardware, so it may be better to concentrate on using LLMs for debugging chip designs.
- Verilog focus detracts from reference model evaluation: “In industrial workflows, reference model generation is even more resource-intensive than Verilog design, reflected in a 1:1 – 5:1 ratio of verification engineers (write reference model) to design engineers (write Verilog)”.

ChipBench : ChipBench tests out AI systems on three distinct competencies – writing Verilog code, debugging Verilog code, and writing reference models.

- Verilog writing: Based on 44 modules from real world hardware. “Our dataset features 3.8x longer code length and 13.9x more cells than VerilogEval.” These tests have three categories: self-contained module tests, hierarchical modules that are non-self-contained, and CPU IP modules sourced directly from open-source CPU projects.
- Verilog debugging : 89 test cases covering four error types: timing, arithmetic, assignment, and state machine bugs. These tests were built by manually injecting faults into known-good Verilog modules. Provides two types of debugging tests: zero-shot and one-shot. “The zero-shot test provides the model with the module description and buggy implementation, indicating that an error exists without providing localization details. The one-shot test provides identical information but supplements it with simulation waveform data (.vcd files)”.
- Reference model generation : 132 samples, enabling evaluation of reference model generation across Python, SystemC, and CXXRTL.

How well do modern systems do? The authors test out some decent frontier models from OpenAI (GPT 3.5, 4o, 5, and 5.2), Anthropic (Claude 4.5 Haiku, Sonnet, and Opus), Google (Gemini 2.5 Pro, and 3 Flash), Meta (LLaMa3.1 8B and 80B), and DeepSeek (V3.2). No model does well: “Despite testing on advanced models, the average pass@1 is relatively low,” they write.

- Verilog generation: CPU IP: Highest is 22.22% (Claude 4.5 Opus, Gemini 3 Flash, GPT 5.2) Non-Self-Contained: Highest is 50% (DeepSeek-Coder) Self-contained: Highest is 36.67% (Claude 4.5 Opus, Gemini 3 Flash)
- CPU IP: Highest is 22.22% (Claude 4.5 Opus, Gemini 3 Flash, GPT 5.2)
- Non-Self-Contained: Highest is 50% (DeepSeek-Coder)
- Self-contained: Highest is 36.67% (Claude 4.5 Opus, Gemini 3 Flash)

- Python reference model generation: CPU IP: 11.1% (Claude 4.5 Sonnet, Gemini 3 Flash) Non-Self-Contained: 0% (pass@1). Self-Contained: 40% (Claude-4.5 Haiku, Opus, Gemini 2.5 Pro, GPT-5)
- CPU IP: 11.1% (Claude 4.5 Sonnet, Gemini 3 Flash)
- Non-Self-Contained: 0% (pass@1).
- Self-Contained: 40% (Claude-4.5 Haiku, Opus, Gemini 2.5 Pro, GPT-5)

- Verilog debugging: Generally better performance, but still no model cracks 50% pass@1 when averaged across tasks.
- Generally better performance, but still no model cracks 50% pass@1 when averaged across tasks.

Why this matters : Though some AI systems have been used to build chips, they’ve been typically highly specialized, or stuck inside incredibly good scaffolds for eliciting good chip design behavior and stopping them from causing problems. What the researchers show here is that out-of-the-box LLMs are still pretty shitty at doing general purpose, real world chip design: “Current models have significant limitations in AI-aided chip design and remain far from ready for real industrial workflow integration.” At the same time, I can’t escape the feeling that there’s a scaffold for “being good at Verilog” which a contemporary AI system might be able to build if asked to and which would radically improve performance of systems on this benchmark. Read more: ChipBench: A Next-Step Benchmark for Evaluating LLM Performance in AI-Aided Chip Design (arXiv) . Get the code for ChipBench here (GitHub) .

### [Gemini solves some Erdős problems – and illustrates the challenges of automating math research with AI](https://arxiv.org/abs/2601.22401)

…AI for science is great, but it can also introduce new problems… An interdisciplinary group of scientists from Google DeepMind and a bunch of universities have used an internal Google Gemini-based LLM, codenamed Aletheia, to solve some math problems. The results demonstrate that contemporary AI systems can work on the frontiers of science, but also show how evaluating and filtering the solutions they come up with may be an important, challenging task for humans.

The key numbers – 700 candidates and 1 creative and interesting solution: Erdős problems are 1000+ open mathematical conjectures left behind by prolific mathematician Paul Erdős at the time of his death. At the time of writing, a few hundred of these problems have been solved. For this research, the researchers tried to see whether their AI system, Aletheia, could generate solutions to any of the 700 remaining open questions. The results: yes, but with many, many caveats. Aletheia was able to surface 200 candidate solutions which humans then needed to grade, slimming down to 63 correct response, and further expert mathematical evaluation slimmed this down to a further subset of only 13 solves that Google calls “correct meaningful responses”. “The remaining 50 of Aletheia’s correct solutions were technically valid but mathematically meaningless because the problem statements were interpreted in a way that did not capture Erdős intent, often (but not always) leading to trivial solutions,” the researchers write. “”Only 13 solutions correctly addressed the intended problem statement (either by invoking the literature, or by a novel argument).”

When 13 become 2: When you dig into these 13, the results get a bit less impressive:

- 5 get classed as “literature identification”: “On these problems, Aletheia found that a solution was already explicitly in the literature, despite the problem being marked “Open” on Bloom’s website at the time of model deployment”.
- 3 are “partial AI solution”: “On these problems, there were multiple questions and Aletheia found the first correct solution to one of the questions”.
- 3 are “independent rediscovery”: “On these problems, Aletheia found a correct solution, but human auditors subsequently found an independent solution already in the literature.”
- This leaves 2 “autonomous novel solution” solves: “On these problems, Aletheia found the first correct solution (as far as we can tell) in a mathematically substantive way”. Of these, 1 of the solutions seems genuinely interesting: “We tentatively believe Aletheia’s solution to Erdős-1051 represents an early example of an AI system autonomously resolving a slightly non-trivial open Erdős problem of somewhat broader (mild) mathematical interest, for which there exists past literature on closely-related problems [KN16], but none fully resolve Erdős-1051,” they write. “Moreover, it does not appear obvious to us that Aletheia’s solution is directly inspired by any previous human argument”.

Who did the research: Along with Google DeepMind, the following universities participated in the research: UC Berkeley, Seoul National University, Stanford University, Korea Institute for Advanced Study, University of Cambridge, Brown University, Yonsei University, Concordia University, Academia Sinica, and National Taiwan University.

Why this matters – even if AI speeds up science, humans might be the bottleneck (at least for a while): This paper is a nice example of “O-ring automation” – AI here has massively sped up the art of generating proofs, but it still requires laborious, skilled work by humans to filter this down to the actually correct and useful responses. This trend will likely hold for some years, where AI will not be able to autonomously do science end-to-end, partially because a big chunk of scientific advancement comes down to something you might think of as “expert intuition” which exists in the heads of a small number of living scientists and was refined by their own biological intelligence by reading the same literature as the LLMs. Extracting this kind of expert taste feels like something that is tractable but will take a while. “Large Language Models can easily generate candidate solutions, but the number of experts who can judge the correctness of a solution is relatively small, and even for experts, substantial time is required to carry out such evaluations”, the authors write. “As AI-generated mathematics grows, the community must remain vigilant of “subconscious plagiarism”, whereby AI reproduces knowledge of the literature acquired during training, without proper acknowledgment. Note that formal verification cannot help with any of these difficulties.” Read more: Semi-Autonomous Mathematics Discovery with Gemini: A Case Study on the Erdős Problems (arXiv) .

### [Huawei uses an LLM to automate the design of Huawei chip kernels](https://arxiv.org/abs/2601.22760)

…LLMs need scaffolds for more obscure chips… Researchers with Nanjing University and Huawei have used LLMs to help automate the design of kernels for AscendC Huawei chips, as a further symptom of how modern AI systems can accelerate their own development.

AscendCraft: AscendCraft is software for automating the generation of code for Huawei kernels. Modern LLMs can generate quite good kernel code for widely used chips like NVIDIA GPUs, but relatively obscure chips like Huawei are less well understood by LLMs, mostly due to data availability. “Publicly available NPU kernel implementations are far scarcer than GPU counterparts, limiting the training corpus for LLMs,” the authors write. “The lack of largescale, high-quality NPU code makes it difficult for LLMs to generate correct and efficient kernels”.

What they did: To build AscendCraft, the authors developed a two stage pipeline. In stage one, they have an LLM build “a high-level DSL program that describes the kernel’s core computation, tiling strategy, and on-chip dataflow.” The DSL is “designed to be LLM-friendly, appropriately abstracted, and sufficiently expressive to capture high-performance NPU kernel designs” – I think of it as basically a scaffold to focus the LLM around the specifics of building kernels for Huawei hardware. In the second stage, they “”transcompile the DSL into AscendC code through a sequence of structured LLM-based lowering passes, each responsible for translating a specific aspect of the DSL into valid and efficient AscendC constructs”.

Slightly odd thing: Strangely, the paper doesn’t disclose precisely which LLM is used here.

The results: They test out a range of kernels built in this way on MultiKernelBench. In their tests, they find that “AscendCraft achieves 98.1% compilation success and 90.4% functional correctness. Moreover, 46.2% of generated kernels match or exceed PyTorch eager execution performance”. This is promising enough performance that it’s going to be worth them continuing with this research, but not so good that it instantly knocks things out of the park and revolutionizes how kernels for Huawei chips get made. Nonetheless, the signs are clear: we can use AI to accelerate the optimizing of AI hardware, even for systems which are relatively new and/or underdiscussed in the pre-training corpus LLMs are trained on. Read more : AscendCraft: Automatic Ascend NPU Kernel Generation via DSL-Guided Transcompilation (arXiv) .
