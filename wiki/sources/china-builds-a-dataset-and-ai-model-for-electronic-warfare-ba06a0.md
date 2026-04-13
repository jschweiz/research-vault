---
id: page:2026-03-23-jack-clark-import-ai-china-builds-a-dataset-and-ai-model-for-electron-a67bef0c
page_type: source-note
title: China builds a dataset and AI model for electronic warfare
aliases:
- China builds a dataset and AI model for electronic warfare
source_refs:
- 2026-03-23-jack-clark-import-ai-china-builds-a-dataset-and-ai-model-for-electron-a67bef0c
backlinks:
- page:2026-02-16-jack-clark-import-ai-facebook-makes-a-better-recommender-system-and-f-e7ec92ff
- topic:data-curation
- topic:electromagnetic-signals
- topic:electronic-warfare
updated_at: '2026-04-09T23:10:02.563314Z'
managed: true
---
# China builds a dataset and AI model for electronic warfare

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2603.08174
- Document kind: paper
- Published at: 2026-03-23T12:31:45+00:00
- Authors: Tsinghua University, Beijing University of Posts and Telecommunications, Tianjin University, Chinese Academy of Sciences, HKUST, National University of Defense Technology
- Tags: newsletter, ai, analysis, policy, website, paper, electronic warfare, dataset, machine learning, electromagnetic signals, sub-document
- Topics: [Data Curation](../topics/data-curation.md), [Electromagnetic Signals](../topics/electromagnetic-signals.md), [Electronic Warfare](../topics/electronic-warfare.md), [Machine Learning](../topics/machine-learning.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md)
- Trend score: 655.21
- Novelty score: 4.80

## Summary

Chinese researchers built a dataset, benchmark, and AI model called MERLIN to improve AI's ability to handle low-signal-to-noise-ratio signals in electronic warfare environments.

## Topic Map

- [Data Curation](../topics/data-curation.md)
- [Electromagnetic Signals](../topics/electromagnetic-signals.md)
- [Electronic Warfare](../topics/electronic-warfare.md)
- [Machine Learning](../topics/machine-learning.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)

## Related Research

- [Facebook makes a better recommender system, and figures out some recommender scaling laws](facebook-makes-a-better-recommender-system-and-figures-out-some--286484.md) (shared topics: Machine Learning, Newsletter, Policy)
- [Can AI agents independently do basic AI research tasks? AIRS-BENCH says yes](can-ai-agents-independently-do-basic-ai-research-tasks-airs-benc-9ad337.md) (shared topics: Machine Learning, Newsletter, Policy)
- [Feedback Flywheel](feedback-flywheel-c22a0d.md) (shared topics: Machine Learning, Newsletter)
- [Build Self-Learning Agents Without Any Fine-Tuning](build-self-learning-agents-without-any-fine-tuning-7c2f7d.md) (shared topics: Machine Learning, Newsletter)
- [Automatic Speech Recognition (ASR) From Scratch (With Intuition)](automatic-speech-recognition-asr-from-scratch-with-intuition-b589b8.md) (shared topics: Machine Learning, Newsletter)
- [OpenAI #16: A History and a Proposal](openai-16-a-history-and-a-proposal-a6e162.md) (shared topics: Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

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

Tech
