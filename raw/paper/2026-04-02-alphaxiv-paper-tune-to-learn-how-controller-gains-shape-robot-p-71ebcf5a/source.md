---
id: 2026-04-02-alphaxiv-paper-tune-to-learn-how-controller-gains-shape-robot-p-71ebcf5a
kind: paper
title: 'Tune to Learn: How Controller Gains Shape Robot Policy Learning'
source_url: https://www.alphaxiv.org/abs/2604.02523
source_name: alphaXiv Papers
authors:
- Antonia Bronars
- Younghyo Park
- Pulkit Agrawal
published_at: '2026-04-02T21:23:08Z'
ingested_at: '2026-04-09T10:02:05.886402Z'
content_hash: bc6ae22274260a67a5d600464c6a0c33c055233b4705bdbcd8fa4876513dacdb
identity_hash: e33c7e80bb1d7de63e89d3897fed7e8ca2d36b6393ca8df0bb11623d0ca4d3b4
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
external_key: https://www.alphaxiv.org/abs/2604.02523
canonical_url: https://www.alphaxiv.org/abs/2604.02523
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T10:02:05.886412Z'
short_summary: Researchers at MIT systematically analyzed how position controller gains influence robot policy learning across behavior cloning, reinforcement learning, and sim-to-real transfer. The work found that compliant and overdamped gains enhance behavior cloning and teleoperation efficiency, while stiff gains, despite yielding better system models, paradoxically reduce sim-to-real transferability.
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# Tune to Learn: How Controller Gains Shape Robot Policy Learning

## alphaXiv Summary

Researchers at MIT systematically analyzed how position controller gains influence robot policy learning across behavior cloning, reinforcement learning, and sim-to-real transfer. The work found that compliant and overdamped gains enhance behavior cloning and teleoperation efficiency, while stiff gains, despite yielding better system models, paradoxically reduce sim-to-real transferability.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.02523
- Source paper: https://arxiv.org/abs/2604.02523
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.02523v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.02523v1.png
- Paper ID: 2604.02523
- Canonical ID: 2604.02523v1
- Paper group ID: 019d6082-0c8d-738d-929f-9e9e93152a46
- Version ID: 019d6082-0cca-7dd3-8eed-3c6eef1ae9df
- Version: v1
- Version order: 1
- Published at: 2026-04-02T21:23:08+00:00
- First published at: 2026-04-02T21:23:08+00:00
- Updated at: 2026-04-06T01:57:08.877000+00:00
- License: http://creativecommons.org/licenses/by/4.0/
- Citations: 0

## Authors

- Antonia Bronars
- Younghyo Park
- Pulkit Agrawal

## Topics

- Computer Science
- cs.RO

## Metrics

- Visits (all): 81
- Visits (last 7 days): 81
- Total votes: 2
- Public total votes: 5
- X likes: 0

## Abstract

Position controllers have become the dominant interface for executing learned manipulation policies. Yet a critical design decision remains understudied: how should we choose controller gains for policy learning? The conventional wisdom is to select gains based on desired task compliance or stiffness. However, this logic breaks down when controllers are paired with state-conditioned policies: effective stiffness emerges from the interplay between learned reactions and control dynamics, not from gains alone. We argue that gain selection should instead be guided by learnability: how amenable different gain settings are to the learning algorithm in use. In this work, we systematically investigate how position controller gains affect three core components of modern robot learning pipelines: behavior cloning, reinforcement learning from scratch, and sim-to-real transfer. Through extensive experiments across multiple tasks and robot embodiments, we find that: (1) behavior cloning benefits from compliant and overdamped gain regimes, (2) reinforcement learning can succeed across all gain regimes given compatible hyperparameter tuning, and (3) sim-to-real transfer is harmed by stiff and overdamped gain regimes. These findings reveal that optimal gain selection depends not on the desired task behavior, but on the learning paradigm employed. Project website: this https URL

## Problem

- Absence of systematic principles for selecting position controller gains in robot learning, unlike established guidelines in classical control theory.
- Conventional approaches tie low-level gains directly to desired task behavior (e.g., compliance for contact), which may be an insufficient heuristic for state-conditioned learned policies.
- Lack of understanding regarding how controller gains impact policy learnability, hyperparameter optimization for RL, and the fidelity of sim-to-real transfer.

## Method

- A systematic evaluation of proportional (K_p) and derivative (K_d) gain setpoints was conducted across behavior cloning (BC), reinforcement learning (RL), and sim-to-real transfer scenarios.
- For BC, a Torque-to-Position Retargeting (TPR) method was developed to isolate the effect of gains on action targets while maintaining nearly identical state trajectories.
- For sim-to-real transfer, gain-specific simulation environments were created through system identification, and RL policies were trained and evaluated for zero-shot deployment.

## Results

- Behavior cloning policies achieved significantly higher closed-loop success rates with compliant and overdamped gains (low K_p, high K_d), with comparable teleoperation efficiency for data collection.
- Reinforcement learning demonstrated adaptability, with successful policies (99%+ success rate) discoverable across all evaluated gain regimes given appropriate environment-specific hyperparameter tuning.
- Stiff and overdamped gains, despite yielding the lowest system identification errors, resulted in lower sim-to-real transferability and exacerbated high-frequency oscillations on real robots, while lower policy frequencies mitigated these failures.

## Takeaways

- Controller gains act as an 'inductive bias' that shapes the learnability of policies, rather than directly determining task-level behaviors like stiffness or compliance, which emerge from the policy's reactive outputs.
- For behavior cloning, compliant and overdamped gain settings lead to more robust policies due to error-attenuation properties, despite potentially higher training loss.
- Traditional metrics for simulation fidelity (e.g., low system identification error with stiff gains) do not directly correlate with successful closed-loop policy transfer; stiff gains can amplify modeling errors into instability in real-world deployment.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d6082-0c8d-738d-929f-9e9e93152a46/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d6082-0c8d-738d-929f-9e9e93152a46/transcript.json

## Similar Papers

- Empirical Analysis of Sim-and-Real Cotraining of Diffusion Policies for Planar Pushing from Pixels (2503.22634v2): An empirical study from MIT explored sim-and-real cotraining of diffusion policies for planar pushing, showing it substantially boosts robot policy performance with limited real data. The analysis highlighted the critical role of physical simulation accuracy and the benefit of policies distinguishing between real and simulated domains for optimal action prediction.
- Learning a Unified Policy for Position and Force Control in Legged Loco-Manipulation (2505.20829v2): Researchers at BIGAI and UniTree Robotics developed a unified policy for legged robots to control both position and contact force without relying on external force sensors. This policy enhanced imitation learning by generating force-aware data, leading to a 39.5% improvement in success rates for contact-rich manipulation tasks on quadrupedal and humanoid robots.
- Demystifying Action Space Design for Robotic Manipulation Policies (2602.23408v1): This empirical study systematically investigates action space design for robotic manipulation, establishing principled guidelines for policy learnability and control stability. It demonstrates that chunk-wise delta actions reduce cumulative errors, delta representations improve learning efficiency, and task-space actions enhance transferability for generalist robot models across various tasks and platforms.
- FACET: Force-Adaptive Control via Impedance Reference Tracking for  Legged Robots (2505.06883v2): FACET is a reinforcement learning framework that enables legged robots to achieve force-adaptive control and tunable compliance by learning to imitate a virtual mass-spring-damper system. This approach allows robots to gracefully manage external forces, perform high-force interaction tasks, and demonstrates improved robustness against perturbations, successfully pulling payloads up to 10 kg on a real quadruped robot.
- AnyBody: A Benchmark Suite for Cross-Embodiment Manipulation (2505.14986v1): Princeton University researchers developed "AnyBody," a benchmark suite for cross-embodiment manipulation, revealing that while multi-embodiment policies can achieve competitive performance on seen robots and interpolation tasks, they largely fail at zero-shot generalization to entirely novel or compositionally different robot structures. This highlights the limitations of current methods in achieving broad morphological adaptability for manipulation.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
