---
id: 2026-04-08-alphaxiv-paper-bidexgrasp-coordinated-bimanual-dexterous-grasps-e1915b84
kind: paper
title: 'BiDexGrasp: Coordinated Bimanual Dexterous Grasps across Object Geometries and Sizes'
source_url: https://www.alphaxiv.org/abs/2604.06589
source_name: alphaXiv Papers
authors:
- Mu Lin
- Yi-Lin Wei
- Jiaxuan Chen
- Yuhao Lin
- Shuoyu Chen
- Jiangran Lyu
- Jiayi Chen
- Yansong Tang
- He Wang
- Wei-Shi Zheng
published_at: '2026-04-08T02:17:11Z'
ingested_at: '2026-04-09T10:00:43.306742Z'
content_hash: 87051836e39da3a593b443d66f7c1bb4c6769731f93f28a447f85a8765600b59
identity_hash: 1f2efd03fe8ca61104c83c11f63bcb5bc535305681d43c7e74592e855db3ab71
tags:
- paper
- alphaxiv
- research
- Computer Science
- cs.RO
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
external_key: https://www.alphaxiv.org/abs/2604.06589
canonical_url: https://www.alphaxiv.org/abs/2604.06589
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:00:43.306747Z'
short_summary: Researchers developed BiDexGrasp, a large-scale dataset featuring 9.7 million bimanual dexterous grasps for 6,351 objects of varied sizes and geometries, alongside a generative framework for coordinated bimanual grasping. This framework achieves significantly higher grasp success rates (66.78%) and efficiency compared to previous methods, enabling robots to handle diverse objects in both simulation and real-world scenarios.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# BiDexGrasp: Coordinated Bimanual Dexterous Grasps across Object Geometries and Sizes

## alphaXiv Summary

Researchers developed BiDexGrasp, a large-scale dataset featuring 9.7 million bimanual dexterous grasps for 6,351 objects of varied sizes and geometries, alongside a generative framework for coordinated bimanual grasping. This framework achieves significantly higher grasp success rates (66.78%) and efficiency compared to previous methods, enabling robots to handle diverse objects in both simulation and real-world scenarios.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06589
- Source paper: https://arxiv.org/abs/2604.06589
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06589v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06589v1.png
- Paper ID: 2604.06589
- Canonical ID: 2604.06589v1
- Paper group ID: 019d6ffa-c498-7d6f-b85c-1b3b0a8b9904
- Version ID: 019d6ffa-c4d4-7cc1-b2e5-721fee6ae4b7
- Version: v1
- Version order: 1
- Published at: 2026-04-08T02:17:11+00:00
- First published at: 2026-04-08T02:17:11+00:00
- Updated at: 2026-04-09T02:03:18.552000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Mu Lin
- Yi-Lin Wei
- Jiaxuan Chen
- Yuhao Lin
- Shuoyu Chen
- Jiangran Lyu
- Jiayi Chen
- Yansong Tang
- He Wang
- Wei-Shi Zheng

## Topics

- Computer Science
- cs.RO

## Metrics

- Visits (all): 18
- Visits (last 7 days): 18
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

Bimanual dexterous grasping is a fundamental and promising area in robotics, yet its progress is constrained by the lack of comprehensive datasets and powerful generation models. In this work, we propose BiDexGrasp, consists of a large-scale bimanual dexterous grasp dataset and a novel generation model. For dataset, we propose a novel bimanual grasp synthesis pipeline to efficiently annotate physically feasible data for dataset construction. This pipeline addresses the challenges of high-dimensional bimanual grasping through a two-stage synthesis strategy of efficient region-based grasp initialization and decoupled force-closure grasp optimization. Powered by this pipeline, we construct a large-scale bimanual dexterous grasp dataset, comprising 6351 diverse objects with sizes ranging from 30 to 80 cm, along with 9.7 million annotated grasp data. Based on this dataset, we further introduce a bimanual-coordinated and geometry-size-adaptive dexterous grasping generation framework. The framework lies in two key designs: a bimanual coordination module and a geometry-size-adaptive grasp generation strategy to generate coordinated and high-quality grasps on unseen objects. Extensive experiments conducted in both simulation and real world demonstrate the superior performance of our proposed data synthesis pipeline and learned generative framework.

## Problem

- Lack of large-scale, high-quality bimanual dexterous grasp datasets covering diverse object geometries and sizes.
- Current bimanual grasping methods perform inadequately on objects with varied scales and complex geometries due to difficulties in bimanual coordination and the expanded search space.
- The high dimensionality of bimanual grasping makes efficient data synthesis and model learning challenging, leading to low success rates and slow speeds for existing pipelines.

## Method

- Developed BiDexGrasp, a large-scale dataset of 9.7 million bimanual dexterous grasps for 6,351 objects of diverse sizes (30-80cm) and geometries, synthesized using a novel, efficient pipeline.
- Designed a data-driven generative framework featuring a Bimanual Coordination Module to ensure collaborative hand movements and avoid collisions.
- Incorporated a Geometry-Size-Adaptive strategy using Scale-Adaptive Grasp Anchors and Geometry-Adaptive Features to improve generalization across varied object characteristics.

## Results

- The data synthesis pipeline improved grasp success rate by 2.8x and synthesis speed by 40x compared to existing bimanual grasp generation methods.
- The BiDexGrasp generation framework achieved a 66.78% lift success rate in simulation, surpassing SceneDiffuser (15.17%) and DGTR (41.45%), with lower penetration depths.
- Real-world deployment demonstrated the framework's capability to generate robust bimanual grasps for unseen objects, achieving success rates between 33.3% and 100% across various objects and robotic hands.

## Takeaways

- Decoupling force closure and employing region-constrained initialization are critical for efficient and high-quality bimanual grasp data synthesis.
- Adopting scale-adaptive grasp anchors and geometry-adaptive features allows generative models to effectively generalize bimanual grasping across objects with diverse sizes and complex geometries.
- A diffusion model framework, when augmented with specific modules for bimanual coordination and geometry-size adaptation, can generate robust and physically feasible bimanual grasps.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6ffa-c498-7d6f-b85c-1b3b0a8b9904/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6ffa-c498-7d6f-b85c-1b3b0a8b9904/transcript.json

## Similar Papers

- ZeroGrasp: Zero-Shot Shape Reconstruction Enabled Robotic Grasping (2504.10857v1): A framework from Carnegie Mellon and Toyota Research Institute enables zero-shot robotic grasping by combining octree-based 3D shape reconstruction with grasp pose prediction from single RGB-D images, achieving state-of-the-art performance on the GraspNet-1B benchmark while generalizing to novel real-world objects through training on synthetic data.
- RDT-1B: a Diffusion Foundation Model for Bimanual Manipulation (2410.07864v2): Researchers at Tsinghua University developed RDT-1B, the first diffusion-based foundation model for bimanual robotic manipulation, featuring 1.2 billion parameters. This model achieved an average 56% improvement in success rates over state-of-the-art baselines across diverse bimanual tasks, showcasing strong zero-shot generalization to unseen objects and scenes, and few-shot learning capabilities.
- ManipTrans: Efficient Dexterous Bimanual Manipulation Transfer via  Residual Learning (2503.21860v1): Researchers from BIGAI and Tsinghua University introduce MANIPTRANS, a two-stage framework that enables efficient transfer of human bimanual manipulation skills to robotic hands through combined trajectory imitation and residual learning, while generating DEXMANIPNET - a dataset of 3.3K manipulation episodes demonstrating generalization across multiple robotic hand designs.
- DexGrasp Anything: Towards Universal Robotic Dexterous Grasping with  Physics Awareness (2503.08257v2): Researchers at ShanghaiTech University developed DexGrasp Anything, a physics-aware diffusion model that generates dexterous grasp poses by integrating explicit physical constraints and leveraging an LLM-enhanced object representation. This method, supported by the newly introduced large-scale DexGrasp Anything (DGA) dataset, achieved state-of-the-art performance on multiple benchmarks and successfully demonstrated stable grasping with a real ShadowHand robot.
- Dex1B: Learning with 1B Demonstrations for Dexterous Manipulation (2506.17198v1): Researchers at UC San Diego introduced Dex1B, a dataset comprising one billion physically plausible demonstrations for dexterous grasping and articulation tasks, utilizing an iterative data generation pipeline. Policies trained on Dex1B achieve state-of-the-art performance on benchmarks and demonstrate high success rates in direct sim-to-real deployment on physical robots.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
