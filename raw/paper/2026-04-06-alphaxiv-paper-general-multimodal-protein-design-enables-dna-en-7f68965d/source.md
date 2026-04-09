---
id: 2026-04-06-alphaxiv-paper-general-multimodal-protein-design-enables-dna-en-7f68965d
kind: paper
title: General Multimodal Protein Design Enables DNA-Encoding of Chemistry
source_url: https://www.alphaxiv.org/abs/2604.05181
source_name: alphaXiv Papers
authors:
- Jarrid Rector-Brooks
- Théophile Lambert
- Marta Skreta
- Daniel Roth
- Yueming Long
- Zi-Qi Li
published_at: '2026-04-06T21:21:11Z'
ingested_at: '2026-04-09T12:06:18.194314Z'
content_hash: a20d6512e02048a1c9c55939ac3aaa06ffb8e6bf1a6acea84e536e7ed90a6868
identity_hash: 43b40a72092d11ae0dbacfc114367342d6182f0d938ad9abada7d5e29feaeacf
tags:
- paper
- alphaxiv
- research
- ai-for-genomics
- ai-for-health
- computer science
- cs.lg
- generative-models
- geometric-deep-learning
- inference-optimization
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
external_key: https://www.alphaxiv.org/abs/2604.05181
canonical_url: https://www.alphaxiv.org/abs/2604.05181
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:06:18.194319Z'
short_summary: The DISCO model is a multimodal generative framework that simultaneously designs protein sequences and 3D structures to create enzymes for new-to-nature chemical reactions. It demonstrated the ability to design highly active enzymes with novel active-site geometries that are further evolvable.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T14:23:57.703595Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 5625c17d024489492b807d1c30ce46dfe3832e649623b254ee4a8decd3d574c5
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: 42aef8c0ca1b4fed548ef3e9183fb0d5c01ffb7a7c5e096c4a5bfe9ddea74b14
lightweight_score:
  relevance_score: 0.418
  source_fit_score: 0.55
  topic_fit_score: 0.18
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on generic profile-fit fallback.
  evidence_quotes:
  - The DISCO model is a multimodal generative framework that simultaneously designs protein sequences and 3D structures to create enzymes for new-to-nature chemica
---
# General Multimodal Protein Design Enables DNA-Encoding of Chemistry

## alphaXiv Summary

A multimodal generative model named DISCO was developed to simultaneously design protein sequences and 3D structures, enabling the creation of enzymes for new-to-nature chemical reactions without predefined active sites. It successfully generated highly active carbene transferases, achieving up to 98% yield and 5,170 total turnover numbers for transformations like B-H insertion, and demonstrating evolvability for further optimization.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.05181
- Source paper: https://arxiv.org/abs/2604.05181
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.05181v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.05181v1.png
- GitHub: https://github.com/DISCO-design/DISCO
- GitHub stars: 0
- Paper ID: 2604.05181
- Canonical ID: 2604.05181v1
- Paper group ID: 019d6b4a-4068-735f-a730-861aef6164e8
- Version ID: 019d6b4a-40bb-725b-b58e-a4a97c9e127a
- Version: v1
- Version order: 1
- Published at: 2026-04-06T21:21:11+00:00
- First published at: 2026-04-06T21:21:11+00:00
- Updated at: 2026-04-08T04:12:01.512000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Jarrid Rector-Brooks
- Théophile Lambert
- Marta Skreta
- Daniel Roth
- Yueming Long
- Zi-Qi Li
- Xi Zhang
- Miruna Cretu
- Francesca-Zhoufan Li
- Tanvi Ganapathy
- Emily Jin
- Avishek Joey Bose
- Jason Yang
- Kirill Neklyudov
- Yoshua Bengio
- Alexander Tong
- Frances H. Arnold
- Cheng-Hao Liu

## Topics

- ai-for-genomics
- ai-for-health
- Computer Science
- cs.LG
- generative-models
- geometric-deep-learning
- inference-optimization
- multi-modal-learning
- sequence-modeling

## Metrics

- Visits (all): 65
- Visits (last 7 days): 65
- Total votes: 1
- Public total votes: 3
- X likes: 0

## Abstract

Evolution is an extraordinary engine for enzymatic diversity, yet the chemistry it has explored remains a narrow slice of what DNA can encode. Deep generative models can design new proteins that bind ligands, but none have created enzymes without pre-specifying catalytic residues. We introduce DISCO (DIffusion for Sequence-structure CO-design), a multimodal model that co-designs protein sequence and 3D structure around arbitrary biomolecules, as well as inference-time scaling methods that optimize objectives across both modalities. Conditioned solely on reactive intermediates, DISCO designs diverse heme enzymes with novel active-site geometries. These enzymes catalyze new-to-nature carbene-transfer reactions, including alkene cyclopropanation, spirocyclopropanation, B-H, and C(sp$^3$)-H insertions, with high activities exceeding those of engineered enzymes. Random mutagenesis of a selected design further confirmed that enzyme activity can be improved through directed evolution. By providing a scalable route to evolvable enzymes, DISCO broadens the potential scope of genetically encodable transformations. Code is available at this https URL.

## Problem

- Traditional protein engineering, like directed evolution, struggles to design enzymes for new-to-nature chemistries due to the absence of natural starting points and the labor-intensive nature of identifying initial active proteins.
- Current computational enzyme design methods often rely on pre-specified active site geometries or predefined theozymes, limiting the discovery of novel catalytic motifs and mechanisms.
- Existing validated generative pipelines decouple protein backbone generation from sequence design (inverse folding), which is suboptimal as protein sequence and 3D structure are fundamentally linked in determining function.

## Method

- Introduced DISCO (DIffusion for Sequence-structure CO-design), a multimodal generative framework that simultaneously models discrete sequences and 3D structures using parallel masked discrete and continuous diffusion processes.
- Incorporated key inference strategy enhancements including cross-modal recycling, sequence self-correction via random remasking, and an entropy-adaptive sequence temperature for improved co-designability and error correction.
- Developed Multimodal Feynman-Kac Correctors (FKC-MM and FKC-SG) for inference steering, allowing direct optimization of desired properties (e.g., disulfide bonds, binding specificity) during the generative process.

## Results

- DISCO achieved high co-designability (approximately 90% refolding accuracy) and demonstrated superior diversity and novelty compared to existing methods in unconditional and conditional protein generation.
- Multiple functional carbene transferases were designed for four new-to-nature reactions, with the top variant achieving 98% yield and 5,170 total turnover number for B-H insertion, outperforming previous engineered and computationally designed catalysts.
- Designed enzymes exhibited novel active-site geometries (over 80% with >3 Å RMSD from natural homologs) and were shown to be evolvable, with a single round of error-prone PCR yielding variants with improved activity or inverted enantioselectivity.

## Takeaways

- Simultaneously generating protein sequence and structure, conditioned on arbitrary biomolecules without pre-specifying catalytic residues, allows for a broader and more effective exploration of the chemical design space.
- Advanced inference strategies are crucial for improving the quality, diversity, and co-designability of generated proteins in multimodal diffusion models, leading to significant gains in performance.
- Multimodal inference steering techniques enable controllable search and direct optimization of complex protein properties, transforming protein generation from passive sampling to goal-directed design.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6b4a-4068-735f-a730-861aef6164e8/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6b4a-4068-735f-a730-861aef6164e8/transcript.json

## Resources

- GitHub repository: https://github.com/DISCO-design/DISCO

## Similar Papers

- Prot42: a Novel Family of Protein Language Models for Target-aware  Protein Binder Generation (2504.04453v2): Prot42, a family of protein language models developed by Inception Institute of Artificial Intelligence and Cerebras Systems, generates high-affinity protein binders directly from target sequences, eliminating the need for 3D structural information. The models demonstrate state-of-the-art predictive performance across 14 PEER benchmarks and generate binders with predicted affinities for therapeutic targets that are in the low-nanomolar range.
- Proteina: Scaling Flow-based Protein Structure Generative Models (2503.00710v1): PROTEINA introduces a large-scale flow-based generative model for de novo protein backbone design, leveraging a 20+ million synthetic protein dataset and a non-equivariant transformer to achieve semantic control and generate diverse structures up to 800 residues, outperforming prior methods.
- ProteinGuide: On-the-fly property guidance for protein sequence generative models (2505.04823v4)
- Scoring-Assisted Generative Exploration for Proteins (SAGE-Prot): A  Framework for Multi-Objective Protein Optimization via Iterative Sequence  Generation and Evaluation (2505.01277v1): SAGE-Prot is a framework that combines autoregressive protein generation, genetic algorithms, and quantitative structure-property relationship (QSPR) models for multi-objective protein optimization. The approach, which incorporates curriculum learning, generates protein variants with improved properties, such as a TEM-1 β-lactamase variant showing 17-fold higher enzymatic activity than wild-type in experimental validation.
- AMix-1: A Pathway to Test-Time Scalable Protein Foundation Model (2507.08920v3)
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
