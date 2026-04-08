---
id: 2026-04-06-alphaxiv-paper-mineru2-5-pro-pushing-the-limits-of-data-centric-1711e66b
kind: paper
title: MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale
source_url: https://www.alphaxiv.org/abs/2604.04771
source_name: alphaXiv Papers
authors:
  - Bin Wang
  - Tianyao He
  - Linke Ouyang
  - Fan Wu
  - Zhiyuan Zhao
  - Tao Chu
  - Yuan Qu
  - Zhenjiang Jin
  - Weijun Zeng
  - Ziyang Miao
  - Bangrui Xu
  - Junbo Niu
  - Mengzhang Cai
  - Jiantao Qiu
  - Qintong Zhang
  - Dongsheng Ma
  - Yuefeng Sun
  - Hejun Dong
  - Wenzheng Zhang
  - Jutao Xiao
  - Jiayong Shi
  - Pengyu Liao
  - Xiaomeng Zhao
  - Huaping Zhong
  - Liqun Wei
  - Jing Yu
  - Jie Yang
  - Wei Li
  - Shasha Wang
  - Qianqian Wu
  - Xuanhe Zhou
  - Weijia Li
  - Zhenxiang Li
  - Zhongying Tu
  - Jiang Wu
  - Lijun Wu
  - Chao Xu
  - Kai Chen
  - Wentao Zhang
  - Yu Qiao
  - Bowen Zhou
  - Dahua Lin
  - Conghui He
published_at: 2026-04-06T15:44:18Z
ingested_at: 2026-04-07T21:42:45.558112Z
content_hash: 80fdb684c68393c2f126d2f61dd6fee73d538dd45be397c4147219686984d429
tags:
  - paper
  - alphaxiv
  - research
  - computer science
  - cs.cl
  - cs.cv
  - audio
  - summary
  - document parsing
  - data engineering
  - Computer Science
  - cs.CL
  - cs.CV
  - github
  - transcript
status: active
asset_paths:
  - alphaxiv-ai-detection.json
  - alphaxiv-legacy.json
  - alphaxiv-metadata.json
  - alphaxiv-overview-status.json
  - alphaxiv-overview.json
  - alphaxiv-overview.md
  - alphaxiv-paper.json
  - alphaxiv-preview.json
  - alphaxiv-similar-papers.json
  - alphaxiv-transcript.json
  - alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04771
canonical_url: https://www.alphaxiv.org/abs/2604.04771
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: 2026-04-08T09:28:10.600654Z
short_summary: Researchers from Shanghai Artificial Intelligence Laboratory advanced document parsing performance by developing MinerU2.5-Pro, a data-centric framework that significantly improves training data quality and implements a progressive training strategy. This approach led to a 95.69 overall score on OmniDocBench v1.6 Full, representing a 2.71-point improvement over the baseline model while maintaining the original 1.2B-parameter architecture.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
---
# MinerU2.5-Pro: Pushing the Limits of Data-Centric Document Parsing at Scale

## alphaXiv Summary

Researchers from Shanghai Artificial Intelligence Laboratory advanced document parsing performance by developing MinerU2.5-Pro, a data-centric framework that significantly improves training data quality and implements a progressive training strategy. This approach led to a 95.69 overall score on OmniDocBench v1.6 Full, representing a 2.71-point improvement over the baseline model while maintaining the original 1.2B-parameter architecture.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04771
- Source paper: https://arxiv.org/abs/2604.04771
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04771v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04771v1.png
- GitHub: https://github.com/opendatalab/MinerU
- GitHub stars: 0
- Paper ID: 2604.04771
- Canonical ID: 2604.04771v1
- Paper group ID: 019d65bf-f725-70ff-9b02-154aff67da82
- Version ID: 019d65bf-f79a-7903-9c16-117911e19e0d
- Version: v1
- Version order: 1
- Published at: 2026-04-06T15:44:18+00:00
- First published at: 2026-04-06T15:44:18+00:00
- Updated at: 2026-04-07T02:22:52.709000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Bin Wang
- Tianyao He
- Linke Ouyang
- Fan Wu
- Zhiyuan Zhao
- Tao Chu
- Yuan Qu
- Zhenjiang Jin
- Weijun Zeng
- Ziyang Miao
- Bangrui Xu
- Junbo Niu
- Mengzhang Cai
- Jiantao Qiu
- Qintong Zhang
- Dongsheng Ma
- Yuefeng Sun
- Hejun Dong
- Wenzheng Zhang
- Jutao Xiao
- Jiayong Shi
- Pengyu Liao
- Xiaomeng Zhao
- Huaping Zhong
- Liqun Wei
- Jing Yu
- Jie Yang
- Wei Li
- Shasha Wang
- Qianqian Wu
- Xuanhe Zhou
- Weijia Li
- Zhenxiang Li
- Zhongying Tu
- Jiang Wu
- Lijun Wu
- Chao Xu
- Kai Chen
- Wentao Zhang
- Yu Qiao
- Bowen Zhou
- Dahua Lin
- Conghui He

## Topics

- Computer Science
- cs.CL
- cs.CV

## Metrics

- Visits (all): 128
- Visits (last 7 days): 128
- Total votes: 0
- Public total votes: 8
- X likes: 0

## Abstract

Current document parsing methods compete primarily on model architecture innovation, while systematic engineering of training data remains underexplored. Yet SOTA models of different architectures and parameter scales exhibit highly consistent failure patterns on the same set of hard samples, suggesting that the performance bottleneck stems from shared deficiencies in training data rather than architecture itself. Building on this finding, we present \minerupro, which advances the state of the art solely through data engineering and training strategy optimization while keeping the 1.2B-parameter architecture of \mineru completely fixed. At its core is a Data Engine co-designed around coverage, informativeness, and annotation accuracy: Diversity-and-Difficulty-Aware Sampling expands training data from under 10M to 65.5M samples while correcting distribution shift; Cross-Model Consistency Verification leverages output agreement among heterogeneous models to assess sample difficulty and generate reliable annotations; the Judge-and-Refine pipeline improves annotation quality for hard samples through render-then-verify iterative correction. A three-stage progressive training strategy -- large-scale pre-training, hard sample fine-tuning, and GRPO alignment -- sequentially exploits these data at different quality tiers. On the evaluation front, we fix element-matching biases in OmniDocBench~v1.5 and introduce a Hard subset, establishing the more discriminative OmniDocBench~v1.6 protocol. Without any architectural modification, \minerupro achieves 95.69 on OmniDocBench~v1.6, improving over the same-architecture baseline by 2.71 points and surpassing all existing methods including models with over 200$\times$ more parameters.

## Problem

- Existing state-of-the-art document parsing models exhibit similar failure patterns on challenging samples, suggesting training data deficiencies as a primary bottleneck.
- Current training datasets lack coverage for "long-tail" complex document structures and suffer from annotation noise, particularly for hard samples.
- The OmniDocBench v1.5 evaluation benchmark contains element-matching biases and insufficient challenging samples, limiting its discriminative power for advanced models.

## Method

- A comprehensive Data Engine was developed to co-optimize training data coverage, informativeness, and annotation accuracy through diversity-aware sampling and cross-model consistency verification.
- A Judge-and-Refine annotation pipeline, supported by targeted expert annotation, was implemented to enhance the quality of labels for challenging "hard" samples.
- A three-stage progressive training strategy, including large-scale pre-training, high-quality supervised fine-tuning, and reinforcement learning, was designed for a fixed 1.2B-parameter model.
- The OmniDocBench benchmark was upgraded to v1.6, introducing Multi-Granularity Adaptive Matching and a new Hard subset for more robust and discriminative evaluation.

## Results

- MinerU2.5-Pro attained an overall score of 95.69 on OmniDocBench v1.6 Full, improving the baseline MinerU2.5 by 2.71 points while maintaining the same 1.2B-parameter architecture.
- The model achieved a score of 94.08 on the challenging new Hard subset, demonstrating enhanced robustness and outperforming other leading models by more than 2 points.
- Element-specific evaluations showed MinerU2.5-Pro achieved a 0.019 Edit Distance for text recognition (a 30.5% reduction) and top scores in formula (CDM 97.29) and table recognition (TEDS 93.42).

## Takeaways

- Performance gains in document parsing can be primarily driven by systematic data engineering, even with a fixed model architecture.
- Cross-Model Consistency Verification (CMCV) effectively assesses sample difficulty and generates high-quality pseudo-labels by leveraging consensus among multiple heterogeneous models.
- The "render-then-verify" iterative correction mechanism in annotation significantly improves accuracy for complex structural elements by visually detecting errors.
- A progressive training strategy, combining large-scale diverse data with targeted high-quality hard samples and metric-aligned reinforcement learning, is effective for comprehensive model improvement.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65bf-f725-70ff-9b02-154aff67da82/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65bf-f725-70ff-9b02-154aff67da82/transcript.json
- Transcript lines: 18
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## AI Detection

- State: done
- Prediction: Human
- Headline: Mostly Human Written
- Fraction AI: 0.07296856
- Fraction AI-assisted: 0
- Fraction human: 0.92703146

## Resources

- GitHub repository: https://github.com/opendatalab/MinerU

## Similar Papers

- MinerU2.5: A Decoupled Vision-Language Model for Efficient High-Resolution Document Parsing (2509.22186v2): Researchers from Shanghai AI Lab, Peking University, and Shanghai Jiao Tong University developed MinerU2.5, a decoupled Vision-Language Model that achieves state-of-the-art accuracy for high-resolution document parsing while maintaining exceptional computational efficiency. Its two-stage, coarse-to-fine strategy yields a throughput of 2.12 pages/s on an A100 GPU, outperforming previous models by up to 7x, and secures an overall score of 90.67 on the OmniDocBench benchmark.
- MonkeyOCR: Document Parsing with a Structure-Recognition-Relation Triplet Paradigm (2506.05218v2)
- Document Parsing Unveiled: Techniques, Challenges, and Prospects for  Structured Information Extraction (2410.21169v4): This survey provides a comprehensive review of document parsing, categorizing methodologies into modular pipelines and end-to-end vision-language models while detailing their advancements, persistent challenges, and future directions for structured data extraction from diverse documents. It addresses gaps in existing, outdated surveys by incorporating recent developments in deep learning and large language models.
- Dolphin: Document Image Parsing via Heterogeneous Anchor Prompting (2505.14059v1): Dolphin, developed by ByteDance, introduces an "analyze-then-parse" paradigm that uses heterogeneous anchor prompting to achieve state-of-the-art accuracy and nearly 2x faster processing for document image parsing. It effectively handles complex layouts and diverse content types by first analyzing global structure and then performing parallel, type-specific content extraction.
- OmniDocBench: Benchmarking Diverse PDF Document Parsing with  Comprehensive Annotations (2412.07626v2): OmniDocBench establishes a new benchmark for diverse PDF document parsing, offering a dataset of 981 pages across nine document types with comprehensive layout and content annotations. The paper presents a multi-level evaluation framework and reveals that while pipeline tools excel in structured and dense documents, general Vision-Language Models demonstrate superior generalization and robustness to visual degradation.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
