---
id: 2026-04-06-alphaxiv-paper-medgemma-1-5-technical-report-00751a99
kind: paper
title: MedGemma 1.5 Technical Report
source_url: https://www.alphaxiv.org/abs/2604.05081
source_name: alphaXiv Papers
authors:
- Andrew Sellergren
- Chufan Gao
- Fereshteh Mahvar
- Timo Kohlberger
- Fayaz Jamil
- Madeleine Traverse
- Alberto Tono
- Bashir Sadjad
- Lin Yang
- Charles Lau
- Liron Yatziv
- Tiffany Chen
- Bram Sterling
- Kenneth Philbrick
- Richa Tiwari
- Yun Liu
- Madhuram Jajoo
- Chandrashekar Sankarapu
- Swapnil Vispute
- Harshad Purandare
- Abhishek Bijay Mishra
- Sam Schmidgall
- Tao Tu
- Anil Palepu
- Chunjong Park
- Tim Strother
- Rahul Thapa
- Yong Cheng
- Preeti Singh
- Kat Black
- Yossi Matias
- Katherine Chou
- Avinatan Hassidim
- Kavi Goel
- Joelle Barral
- Tris Warkentin
- Shravya Shetty
- Dale Webster
- Sunny Virmani
- David F. Steiner
- Can Kirmizibayrak
- Daniel Golden
published_at: '2026-04-06T18:35:57Z'
ingested_at: '2026-04-09T09:57:36.758774Z'
content_hash: df6c0c872cd45dd0670149583f8b3193921f641c8acd2f94e307c628419f3c87
identity_hash: 88cbd5a840e30fef295f8fcc7a38c2603fd55ce89a2a40c6c94a4d5c6f7a5a17
tags:
- paper
- alphaxiv
- research
- ai-for-health
- Computer Science
- cs.AI
- fine-tuning
- information-extraction
- multi-modal-learning
- object-detection
- reasoning
- representation-learning
- transformers
- audio
- summary
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-overview-status.json
- alphaxiv-overview.json
- alphaxiv-overview.md
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.05081
canonical_url: https://www.alphaxiv.org/abs/2604.05081
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T09:57:36.758780Z'
short_summary: Google Research and Google DeepMind's MedGemma 1.5 expands open-weight medical foundation models to integrate complex high-dimensional medical data such as 3D CT/MRI, whole slide images, and multi-timepoint radiology within an efficient 4B parameter model. It demonstrates notable performance gains, including an 11% macro accuracy increase in 3D MRI condition classification and a 35% rise in IoU for chest X-ray anatomical localization.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# MedGemma 1.5 Technical Report

## alphaXiv Summary

Google Research and Google DeepMind's MedGemma 1.5 expands open-weight medical foundation models to integrate complex high-dimensional medical data such as 3D CT/MRI, whole slide images, and multi-timepoint radiology within an efficient 4B parameter model. It demonstrates notable performance gains, including an 11% macro accuracy increase in 3D MRI condition classification and a 35% rise in IoU for chest X-ray anatomical localization.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05081
- Source paper: https://arxiv.org/abs/2604.05081
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05081v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05081v1.png
- Paper ID: 2604.05081
- Canonical ID: 2604.05081v1
- Paper group ID: 019d6ab8-4d12-70f6-938a-90e878ef5461
- Version ID: 019d6ab8-4d74-79f7-999f-fc6222fe731c
- Version: v1
- Version order: 1
- Published at: 2026-04-06T18:35:57+00:00
- First published at: 2026-04-06T18:35:57+00:00
- Updated at: 2026-04-08T01:32:36.498000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Andrew Sellergren
- Chufan Gao
- Fereshteh Mahvar
- Timo Kohlberger
- Fayaz Jamil
- Madeleine Traverse
- Alberto Tono
- Bashir Sadjad
- Lin Yang
- Charles Lau
- Liron Yatziv
- Tiffany Chen
- Bram Sterling
- Kenneth Philbrick
- Richa Tiwari
- Yun Liu
- Madhuram Jajoo
- Chandrashekar Sankarapu
- Swapnil Vispute
- Harshad Purandare
- Abhishek Bijay Mishra
- Sam Schmidgall
- Tao Tu
- Anil Palepu
- Chunjong Park
- Tim Strother
- Rahul Thapa
- Yong Cheng
- Preeti Singh
- Kat Black
- Yossi Matias
- Katherine Chou
- Avinatan Hassidim
- Kavi Goel
- Joelle Barral
- Tris Warkentin
- Shravya Shetty
- Dale Webster
- Sunny Virmani
- David F. Steiner
- Can Kirmizibayrak
- Daniel Golden

## Topics

- ai-for-health
- Computer Science
- cs.AI
- fine-tuning
- information-extraction
- multi-modal-learning
- object-detection
- reasoning
- representation-learning
- transformers

## Metrics

- Visits (all): 29
- Visits (last 7 days): 29
- Total votes: 1
- Public total votes: 5
- X likes: 0

## Abstract

We introduce MedGemma 1.5 4B, the latest model in the MedGemma collection. MedGemma 1.5 expands on MedGemma 1 by integrating additional capabilities: high-dimensional medical imaging (CT/MRI volumes and histopathology whole slide images), anatomical localization via bounding boxes, multi-timepoint chest X-ray analysis, and improved medical document understanding (lab reports, electronic health records). We detail the innovations required to enable these modalities within a single architecture, including new training data, long-context 3D volume slicing, and whole-slide pathology sampling. Compared to MedGemma 1 4B, MedGemma 1.5 4B demonstrates significant gains in these new areas, improving 3D MRI condition classification accuracy by 11% and 3D CT condition classification by 3% (absolute improvements). In whole slide pathology imaging, MedGemma 1.5 4B achieves a 47% macro F1 gain. Additionally, it improves anatomical localization with a 35% increase in Intersection over Union on chest X-rays and achieves a 4% macro accuracy for longitudinal (multi-timepoint) chest x-ray analysis. Beyond its improved multimodal performance over MedGemma 1, MedGemma 1.5 improves on text-based clinical knowledge and reasoning, improving by 5% on MedQA accuracy and 22% on EHRQA accuracy. It also achieves an average of 18% macro F1 on 4 different lab report information extraction datasets (EHR Datasets 2, 3, 4, and Mendeley Clinical Laboratory Test Reports). Taken together, MedGemma 1.5 serves as a robust, open resource for the community, designed as an improved foundation on which developers can create the next generation of medical AI systems. Resources and tutorials for building upon MedGemma 1.5 can be found at this https URL.

## Problem

- Existing open-weight medical foundation models had limited support for complex, high-dimensional medical data modalities like volumetric 3D CT/MRI and whole slide images (WSIs).
- Comprehensive healthcare AI development was hindered by models primarily focusing on 2D imaging and text, lacking capabilities for fine-grained anatomical localization and multi-timepoint radiology analysis.
- There was a need for an open and robust foundational resource that could interpret a broader spectrum of medical data for advanced clinical applications.

## Method

- MedGemma 1.5 4B builds upon the MedGemma 1 architecture, integrating a 400M MedSigLIP encoder and a Gemma3 foundation model, with the vision encoder kept frozen during training.
- The model was trained through pretraining, distillation, and reinforcement learning, incorporating extensive new medical domain-specific image-text paired datasets for 3D radiology, WSIs, and various medical documents.
- Specific preprocessing pipelines were developed for volumetric images (slicing, multi-channel windowing for CT, min-max normalization for MRI) and whole slide images (tissue segmentation, spatially ordered patch extraction) to adapt them for the 2D image encoder.

## Results

- MedGemma 1.5 4B achieved an 11% absolute improvement in macro accuracy for 3D MRI condition classification and a 3% improvement for 3D CT condition classification.
- It showed a 47% macro F1 gain in ROUGE-L score for Whole Slide Pathology Image report generation and a 35% increase in Intersection over Union (IoU) for anatomical localization on chest X-rays.
- The model improved average macro F1 by 18% across four lab report information extraction datasets and increased MedQA accuracy by 5% and EHRQA accuracy by 22%.

## Takeaways

- An efficient 4B parameter model can effectively process and interpret intricate medical data, including 3D CT/MRI volumes, whole-slide pathology images, and longitudinal imaging sequences.
- Domain-specialized foundation models offer a valuable advantage in interpreting nuanced multimodal reasoning for medical AI compared to more generalist models of similar size.
- Careful preprocessing strategies, such as multi-channel windowing for CT and spatially ordered patch extraction for WSIs, are crucial for adapting complex medical data to existing 2D vision encoders while preserving critical information.

## Full Overview

Saved in `alphaxiv-overview.md` and `alphaxiv-overview.json`.

## Overview Languages

- de
- en
- es
- fr
- hi
- ja
- ko
- ru
- zh

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d6ab8-4d12-70f6-938a-90e878ef5461/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ab8-4d12-70f6-938a-90e878ef5461/transcript.json

## Similar Papers

- MedGemma Technical Report (2507.05201v4)
- GMAI-VL-R1: Harnessing Reinforcement Learning for Multimodal Medical  Reasoning (2504.01886v1): Shanghai AI Lab and international collaborators develop GMAI-VL-R1, a reinforcement learning-enhanced multimodal medical reasoning model that achieves improved accuracy across multiple medical benchmarks (57.33% on MMMU, 61.01% on OmniMedVQA) by incorporating chain-of-thought reasoning and utilizing a specially curated dataset of 10,000 medical visual question-answer pairs.
- BiomedCLIP: a multimodal biomedical foundation model pretrained from fifteen million scientific image-text pairs (2303.00915v3): This research introduces BiomedCLIP, a multimodal biomedical foundation model pretrained on PMC-15M, a new dataset comprising 15 million public biomedical image-text pairs. The model demonstrates superior performance across diverse biomedical vision-language tasks, including cross-modal retrieval, image classification, and medical visual question answering, often outperforming existing general-domain and domain-specific models, and shows potential for privacy-preserving analysis of clinical data.
- ChestX-Reasoner: Advancing Radiology Foundation Models with Reasoning  through Step-by-Step Verification (2504.20930v2): ChestX-Reasoner develops a radiology diagnosis multimodal large language model that improves reasoning capabilities by mining step-by-step process supervision directly from clinical reports. This model demonstrates superior performance in both reasoning and diagnostic accuracy compared to existing general and medical MLLMs.
- Generalist Foundation Models from a Multimodal Dataset for 3D Computed Tomography (2403.17834v5): Researchers at the International School of Medicine, Istanbul Medipol University, and the University of Zurich developed CT-RATE, a large-scale, open-source multimodal 3D chest CT dataset, and introduced CT-CLIP and CT-CHAT, generalist foundation models for 3D medical imaging. CT-CLIP achieved superior zero-shot multi-abnormality detection compared to supervised methods, and CT-CHAT outperformed existing 2D vision-language models and 3D report generation methods in various visual question answering tasks.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
