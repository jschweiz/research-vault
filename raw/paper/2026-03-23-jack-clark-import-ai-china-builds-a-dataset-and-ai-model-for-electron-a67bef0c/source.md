---
id: 2026-03-23-jack-clark-import-ai-china-builds-a-dataset-and-ai-model-for-electron-a67bef0c
kind: paper
title: China builds a dataset and AI model for electronic warfare
source_url: https://arxiv.org/abs/2603.08174
source_name: Import AI
authors:
- Tsinghua University
- Beijing University of Posts and Telecommunications
- Tianjin University
- Chinese Academy of Sciences
- HKUST
- National University of Defense Technology
published_at: '2026-03-23T12:31:45Z'
ingested_at: '2026-04-09T20:15:41.699948Z'
content_hash: 773b5a33864ee9ff8995a642ebb436d2989b0c797713e43145d4ad64dd598acf
identity_hash: 3f3a4ee728a0d3832a04edd81d860ae4327eaa80d000fe956765365687a53910
tags:
- newsletter
- ai
- analysis
- policy
- website
- paper
- electronic warfare
- dataset
- machine learning
- electromagnetic signals
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks::story::3:https://arxiv.org/abs/2603.08174
canonical_url: https://arxiv.org/abs/2603.08174
doc_role: derived
parent_id: 2026-03-23-jack-clark-import-ai-import-ai-450-chinas-electronic-warfare-model-tr-26ab1bcb
index_visibility: visible
fetched_at: '2026-04-13T18:14:44.117359Z'
short_summary: Chinese researchers built a dataset, benchmark, and AI model called MERLIN to improve AI's ability to handle low-signal-to-noise-ratio signals in electronic warfare environments. MERLIN significantly outperformed other frontier models in both perception and reasoning tasks related to electromagnetic signals.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-13T18:54:34.781925Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: ddd29db00268c75766e27c07075690e8c7a8fb5df8aabd4a47b21ad33a98b639
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 4bd14643068f8158886151149c62f7d25e474f0ada8d57ccdfb8e05c06ff53ec
lightweight_score:
  relevance_score: 0.85
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses frontier LLM evaluation and reasoning by showcasing a model (MERLIN) that significantly outperforms other frontier models on complex reasoning tasks.
  evidence_quotes:
  - MERLIN significantly outperformed other frontier models in both perception and reasoning tasks related to electromagnetic signals.
  - MERLIN wins on all reasoning tasks.
  - 'Performance: MERLIN does extremely well in tests against frontier models, including GPT-5, Claude-4-Sonnet, DeepSeek-v3.2-exp, Qwen3-Next-80b-A3B, Gemini-2.5-Pr'
---
# China builds a dataset and AI model for electronic warfare

Source newsletter: Import AI 450: China’s electronic warfare model; traumatized LLMs; and a scaling law for cyberattacks
Source issue: https://jack-clark.net/2026/03/23/import-ai-450-chinas-electronic-warfare-model-traumatized-llms-and-a-scaling-law-for-cyberattacks
Published At: 2026-03-23T12:31:45+00:00
Canonical URL: https://arxiv.org/abs/2603.08174

## Newsletter Context

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
