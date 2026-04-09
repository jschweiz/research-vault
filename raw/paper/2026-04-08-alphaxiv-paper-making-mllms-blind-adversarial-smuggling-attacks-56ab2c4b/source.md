---
id: 2026-04-08-alphaxiv-paper-making-mllms-blind-adversarial-smuggling-attacks-56ab2c4b
kind: paper
title: 'Making MLLMs Blind: Adversarial Smuggling Attacks in MLLM Content Moderation'
source_url: https://www.alphaxiv.org/abs/2604.06950
source_name: alphaXiv Papers
authors:
- Zhiheng Li
- Zongyang Ma
- Yuntong Pan
- Ziqi Zhang
- Xiaolei Lv
- Bo Li
- Jun Gao
- Jianing Zhang
- Chunfeng Yuan
- Bing Li
- Weiming Hu
published_at: '2026-04-08T11:13:16Z'
ingested_at: '2026-04-09T10:00:33.573738Z'
content_hash: c53cdb481d370c0bc4ca6f639dcd5b22eeb8d6e21496df3a85fed3f483d68fdb
identity_hash: 27dcfbcf8fa276cde15c7a9e13e213c415fd0af4707c77dd7dd63d23de36ca7e
tags:
- paper
- alphaxiv
- research
- adversarial-attacks
- adversarial-robustness
- chain-of-thought
- Computer Science
- computer-vision-security
- cs.CV
- cybersecurity
- fine-tuning
- model-interpretation
- vision-language-models
- github
- audio
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06950
canonical_url: https://www.alphaxiv.org/abs/2604.06950
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:00:33.573743Z'
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
# Making MLLMs Blind: Adversarial Smuggling Attacks in MLLM Content Moderation

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06950
- Source paper: https://arxiv.org/abs/2604.06950
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06950v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06950v1.png
- GitHub: https://github.com/zhihengli-casia/smugglebench
- GitHub stars: 8
- Paper ID: 2604.06950
- Canonical ID: 2604.06950v1
- Paper group ID: 019d6ff4-62c2-7826-82e3-2b6c60aac201
- Version ID: 019d6ff4-631d-704a-af85-271015b5198f
- Version: v1
- Version order: 1
- Published at: 2026-04-08T11:13:16+00:00
- First published at: 2026-04-08T11:13:16+00:00
- Updated at: 2026-04-09T01:56:20.290000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Zhiheng Li
- Zongyang Ma
- Yuntong Pan
- Ziqi Zhang
- Xiaolei Lv
- Bo Li
- Jun Gao
- Jianing Zhang
- Chunfeng Yuan
- Bing Li
- Weiming Hu

## Topics

- adversarial-attacks
- adversarial-robustness
- chain-of-thought
- Computer Science
- computer-vision-security
- cs.CV
- cybersecurity
- fine-tuning
- model-interpretation
- vision-language-models

## Metrics

- Visits (all): 19
- Visits (last 7 days): 19
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Multimodal Large Language Models (MLLMs) are increasingly being deployed as automated content moderators. Within this landscape, we uncover a critical threat: Adversarial Smuggling Attacks. Unlike adversarial perturbations (for misclassification) and adversarial jailbreaks (for harmful output generation), adversarial smuggling exploits the Human-AI capability gap. It encodes harmful content into human-readable visual formats that remain AI-unreadable, thereby evading automated detection and enabling the dissemination of harmful content. We classify smuggling attacks into two pathways: (1) Perceptual Blindness, disrupting text recognition; and (2) Reasoning Blockade, inhibiting semantic understanding despite successful text recognition. To evaluate this threat, we constructed SmuggleBench, the first comprehensive benchmark comprising 1,700 adversarial smuggling attack instances. Evaluations on SmuggleBench reveal that both proprietary (e.g., GPT-5) and open-source (e.g., Qwen3-VL) state-of-the-art models are vulnerable to this threat, producing Attack Success Rates (ASR) exceeding 90%. By analyzing the vulnerability through the lenses of perception and reasoning, we identify three root causes: the limited capabilities of vision encoders, the robustness gap in OCR, and the scarcity of domain-specific adversarial examples. We conduct a preliminary exploration of mitigation strategies, investigating the potential of test-time scaling (via CoT) and adversarial training (via SFT) to mitigate this threat. Our code is publicly available at this https URL.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6ff4-62c2-7826-82e3-2b6c60aac201/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ff4-62c2-7826-82e3-2b6c60aac201/transcript.json

## Resources

- GitHub repository: https://github.com/zhihengli-casia/smugglebench

## Similar Papers

- PiCo: Jailbreaking Multimodal Large Language Models via Pictorial Code Contextualization (2504.01444v4): PiCo, a framework developed by researchers from Wuhan University, Peking University, and BAAI, demonstrates a method for jailbreaking Multimodal Large Language Models by exploiting weaknesses in visual modality integration and code processing. It achieved an average attack success rate of 84.13% on Gemini-Pro Vision and 52.66% on GPT-4o, significantly surpassing previous methods.
- On Evaluating Adversarial Robustness of Large Vision-Language Models (2305.16934v2): This study systematically evaluates the adversarial robustness of large vision-language models (VLMs) against black-box, targeted attacks. Researchers developed a combined transfer-based and query-based strategy that successfully induces models like MiniGPT-4 and LLaVA to generate specific, malicious text responses from imperceptibly perturbed images, with these effects persisting over multi-round conversations.
- MM-SafetyBench: A Benchmark for Safety Evaluation of Multimodal Large Language Models (2311.17600v5): A new benchmark, MM-SafetyBench, evaluates the safety of Multimodal Large Language Models (MLLMs), demonstrating that current models are highly susceptible to visual prompt attacks using query-relevant images, even when text-based safety mechanisms are in place. The research also shows that a simple safety prompt can significantly reduce the success rate of these attacks.
- Visual Adversarial Examples Jailbreak Aligned Large Language Models (2306.13213v2): Researchers developed visual adversarial examples that can universally bypass the safety guardrails of aligned Visual Language Models (VLMs), compelling them to generate harmful content across various categories, even when optimized on a narrow corpus. The method significantly increased harmful outputs on tested VLMs, including the highly aligned LLaMA-2-based LLaVA, and proved more potent and efficient than text-based attacks.
- Odysseus: Jailbreaking Commercial Multimodal LLM-integrated Systems via Dual Steganography (2512.20168v1): Researchers from Southeast University and Nanyang Technological University developed "Odysseus," a dual steganography method that covertly embeds and extracts malicious content in images to jailbreak commercial multimodal large language models. The technique achieved an average Attack Success Rate of 78% against leading MLLMs like GPT-4o and Gemini, bypassing explicit input/output safety filters by exploiting implicit communication channels.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
