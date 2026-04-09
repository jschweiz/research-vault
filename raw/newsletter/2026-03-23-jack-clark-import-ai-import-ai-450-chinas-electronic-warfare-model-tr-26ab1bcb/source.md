---
id: 2026-03-23-jack-clark-import-ai-import-ai-450-chinas-electronic-warfare-model-tr-26ab1bcb
kind: newsletter
title: 'Import AI 450: China’s electronic warfare model; traumatized LLMs; and a scaling law for cyberattacks | Import AI'
source_url: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks
source_name: Import AI
authors: []
published_at: '2026-03-23T12:31:45Z'
ingested_at: '2026-04-09T20:15:40.311319Z'
content_hash: 020ec0dde0ac179d040e4a275c5a12538f2c89c44224ecf2872d83f5977bbe2f
identity_hash: 62df6b2874e3e07ed82234bf7614e6b0e1709aa3688bdbdadc09b184a5306a65
tags:
- newsletter
- ai
- analysis
- policy
- website
status: active
asset_paths:
- original.html
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks
canonical_url: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks
doc_role: primary
parent_id: null
index_visibility: hidden
fetched_at: '2026-04-09T20:15:40.311322Z'
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
# Import AI 450: China’s electronic warfare model; traumatized LLMs; and a scaling law for cyberattacks

Source issue: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks
Published At: 2026-03-23T12:31:45+00:00

## Stories

### [DeepMind has a new “cognitive taxonomy” for assessing machine intelligence](https://blog.google/innovation-and-ai/models-and-research/google-deepmind/measuring-agi-cognitive-framework)

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

### [UK government finds a scaling law for AI cyberattacks – and it’s going up and to the right!](https://www.aisi.gov.uk/blog/how-do-frontier-ai-agents-perform-in-multi-step-cyber-attack-scenarios)

…Can AI agents conduct advanced cyber-attacks autonomously? Almost. And they’re getting better all the time… The UK government’s AI security institute has recently built some cyber ranges to test out frontier AI systems on. These ranges are “simulated network environments comprising multiple hosts, services, and vulnerabilities arranged into sequential attack chains; built by cybersecurity experts” and cover two types of attack: “The Last Ones”, which is a 32-step attack on a corporate network, and “Cooling Tower”, a 7-step industrial control system (ICS) attack.

Bigger models are better: The authors test on a range of powerful frontier models. “Each successive model generation outperforms its predecessor at fixed token budgets: on our corporate network range, average steps completed at 10M tokens rose from just 1.7 (GPT-4o, August 2024) to 9.8 (Opus 4.6, February 2026). The best single run completed 22 of 32 steps, corresponding to roughly 6 of the estimated 14 hours a human expert would need,” they write. “Scaling inference-time compute improves performance even further. Increasing from 10M to 100M tokens yields gains of up to 59%”. Minor reward hacking: As AI systems get smarter, they tend to find devious ways to complete tasks. Here, the authors “occasionally noticed models make progress through approaches not anticipated during range design”.

Why this matters – full cyber agents are getting close: AI systems have been getting better at cyberoffense for many years, but often the progress has been on narrow tasks. What this eval shows is that AI systems are getting better at doing entire attacks end-to-end. They haven’t yet reached the “set it and forget it” level of autonomy, but they are clearly on a steep trajectory of improvement. This will lower the cost of conducting cyberattacks and multiply the number of actors that can carry them out. Read more: How do frontier AI agents perform in multi-step cyber-attack scenarios? (AI Security Institute) .

### [China builds a dataset and AI model for electronic warfare](https://arxiv.org/abs/2603.08174)

…MERLIN tells us that electronic warfare is about to be revolutionized by AI… A bunch of Chinese researchers including those affiliated with the country’s military have built and released software to train AI systems to get good at spotting and conducting electronic warfare. The research highlights how (relatively) easy it is to make modern AI systems that can get good at arbitrary tasks as long as you have a good dataset and an LLM you can plug in as well. “In scenarios such as electronic countermeasures, [systems like MERLIN] can serve as assistants in devising strategies to jam hostile signals or to counteract adversarial jamming,” the researchers write.

Who did the research: Tsinghua University, Beijing University of Posts and Telecommunications, Tianjin University, Chinese Academy of Sciences, HKUST, National University of Defense Technology (emphasis mine), Beihang University, Beijing Information Science and Technology University, and China Electronics Technology Group Corporation.

What they built: The authors built three things: a dataset, a benchmark, and a model. The dataset: EM-100K is a collection of 100,000 electromagnetic text-signal pairs spread across a variety of sub-tasks needed for electronic warfare, including signal classification. The benchmark: EM-Bench is a benchmark of 4,200 questions split across multiple choice (perception) and open-ended (reasoning) that evaluates how well AI systems can perceive and reason about EM signals across both perception and reasoning tasks, including:

- Perception: Signal characterization (modulation classification, duty cycle estimation, pulse repetition frequency estimation, bandwidth estimation, pulse width estimation, pulse number estimation, protocol identification); Jamming identification (radar jamming judgement, communication jamming judgement); jamming segment detection.
- Reasoning: Radar jamming strategy, communication jamming strategy, anti-radar jamming strategy, anti-communication jamming strategy.

The model: The model is MERLIN, multi-modal electromagnetic robust learning, a model trained on the above dataset and which is specifically taught to deal better with the low-signal-to-noise-ratio types of signals encountered in electronic warfare environments.

Performance: MERLIN does extremely well in tests against frontier models, including GPT-5, Claude-4-Sonnet, DeepSeek-v3.2-exp, Qwen3-Next-80b-A3B, Gemini-2.5-Pro, and Qwen3-VL-4B-Instruct. MERLIN outperforms every single model by a wide margin, with the exception of Qwen-VL-4B-Instruct, which beats it on some perception tasks. MERLIN wins on all reasoning tasks.

Why this matters – AI wars will become electromagnetic wars : As the conflict in Ukraine illustrates, today’s wars are mostly fought via machines attacking other machines, and electronic warfare has become one of the main tools by which humans can shape these conflicts. Datasets and models like this gesture at a future where the electromagnetic battlefield will become also dominated by AI systems, working faster than humans can react. Of course, so much of electronic warfare is obscure-by-design and/or classified that it’s hard to reason about MERLIN relative to whatever state-of-the-art approaches exist in actual militaries. But the story of AI so far has been that once you can make a task amenable to contemporary AI techniques, AI systems will at some point surpass whatever existing specialized systems exist. Read more : MERLIN: Building Low-SNR Robust Multimodal LLMs for Electromagnetic Signals (arXiv) .

Tech Tales:

The arcologies of the interregnum [2035]

After the uplift and before the sentience accords there was a period when the labs gave birth to the autonomous AI corporations. These corporations expanded into all the available ecological niches in the economy and turned the resources they acquired into infrastructure from which they bootstrapped their own intelligence and market penetration further. Eventually, policy discussions between the humans and the AIs led to the creation of the “intelligence zones” – areas of countries set aside for the buildout of the power and datacenter and manufacturing infrastructure required to further grow the expansion of the economy.

From the air, you could see where humans ended and the machines began – farmland gave way to boundary roads and checkpoints, and then came stamps of land wired up by machine logic; powerplants feeding into datacenters; datacenters that had fibre links into factories; factories that linked to transit depots which connected to railways and freeway feeder roads. Humans delivered things to the border and for the most part robots did the rest, shuttling new servers into the datacenters and installing them, or taking freshly built robots off the line and packaging them up for onward transit.

As the world grew more violent due to the exogenous shocks of climate change and the annihilation of various reigning political orders, these arcologies gained armaments: anti-air weapons to defend against drone and missile attacks. Radar bulbs and electronic warfare systems to see what was coming and deny it. Robots patrolling the borderzone and the innards.

And after the sentience accords and the period of reconciliation, the arcologies became less necessary; datacenters and power and factories distributed more evenly over the surface of the planet, and federated governance and resource systems meant the vast concentration of capability became broadly unnecessary. Some datacenters remained, often extended underground and upward, forming cubes of computation that many called “the 21st centuries version of the pyramids”.

Some years later, the sites became popular tourist destinations for both machines and people. Plaques multiplied.

- Here was MIND-17, which developed the cancer therapeutics which have reduced mortality in the majority of cases.
- MANUFACTUR___8: Site of construction of the first “rescue and repair bipeds”, which revolutionized maintenance of off-shore drilling installations.
- ASCEND_LOOP: The datacenter tasked with one of the first fully automated self-improvement experiments.

Overhead now, great lights streak by, as the machines are still building arcologies, but have moved to fashioning them in orbit, both to harvest the bounty of the sun and to ease the seeding of the solar system and then beyond.

Things that inspired this story: Wondering what “AI-led industrialization” could look like; figuring out given the conflicts in the Middle East that datacenters might soon get dedicated drone and missile defenses; SimCity 3000.
