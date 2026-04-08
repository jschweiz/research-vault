---
id: page:2026-04-06-alphaxiv-paper-muon-dynamics-as-a-spectral-wasserstein-flow-bfacf3b1
page_type: source-note
title: Muon Dynamics as a Spectral Wasserstein Flow
aliases:
  - Muon Dynamics as a Spectral Wasserstein Flow
source_refs:
  - 2026-04-06-alphaxiv-paper-muon-dynamics-as-a-spectral-wasserstein-flow-bfacf3b1
backlinks:
  - page:2026-04-02-alphaxiv-paper-the-latent-space-foundation-evolution-mechanism--4559cf35
  - page:2026-04-03-alphaxiv-paper-joyai-llm-flash-advancing-mid-scale-llms-with-to-7299ba1c
  - topic:artificial-intelligence
  - topic:bayesian-deep-learning
  - topic:computer-science
  - topic:geometric-deep-learning
  - topic:math-oc
  - topic:mathematics
updated_at: 2026-04-08T07:14:52.210116Z
managed: true
---
# Muon Dynamics as a Spectral Wasserstein Flow

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: alphaXiv Papers
- Canonical URL: https://www.alphaxiv.org/abs/2604.04891
- Document kind: paper
- Published at: 2026-04-06T17:41:12+00:00
- Authors: Gabriel Peyré
- Tags: paper, alphaxiv, research, bayesian-deep-learning, computer science, cs.ai, geometric-deep-learning, mathematics, math.oc, optimization-methods
- Topics: [Artificial Intelligence](../topics/artificial-intelligence.md), [Bayesian Deep Learning](../topics/bayesian-deep-learning.md), [Computer Science](../topics/computer-science.md), [Geometric Deep Learning](../topics/geometric-deep-learning.md), [Math Oc](../topics/math-oc.md), [Mathematics](../topics/mathematics.md)
- Trend score: 87.95
- Novelty score: 6.80

## Summary

# Muon Dynamics as a Spectral Wasserstein Flow ## alphaXiv Summary This research develops a mathematical framework for matrix-normalized deep learning optimizers by introducing Spectral Wasserstein distances, which provide a unified geometric interpretation for gradient descent, Muon, and intermediate Schatten-type normalizations. The work establishes these distances as bona fide metrics and identifies their associated gradient flows, rigorously connecting continuous-time dynamics to discrete op

## Topic Map

- [Artificial Intelligence](../topics/artificial-intelligence.md)
- [Bayesian Deep Learning](../topics/bayesian-deep-learning.md)
- [Computer Science](../topics/computer-science.md)
- [Geometric Deep Learning](../topics/geometric-deep-learning.md)
- [Math Oc](../topics/math-oc.md)
- [Mathematics](../topics/mathematics.md)

## Related Research

- [SkillX: Automatically Constructing Skill Knowledge Bases for Agents](skillx-automatically-constructing-skill-knowledge-bases-for-agen-113a3f.md) (shared topics: Artificial Intelligence, Computer Science)
- [Memory Intelligence Agent](memory-intelligence-agent-7ffa81.md) (shared topics: Artificial Intelligence, Computer Science)
- [LightThinker++: From Reasoning Compression to Memory Management](lightthinker-from-reasoning-compression-to-memory-management-cb5236.md) (shared topics: Artificial Intelligence, Computer Science)
- [JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency](joyai-llm-flash-advancing-mid-scale-llms-with-token-efficiency-ea0c5b.md) (shared topics: Artificial Intelligence, Computer Science)
- [The Latent Space: Foundation, Evolution, Mechanism, Ability, and Outlook](the-latent-space-foundation-evolution-mechanism-ability-and-outl-af2bc6.md) (shared topics: Artificial Intelligence, Computer Science)
- [CORAL: Towards Autonomous Multi-Agent Evolution for Open-Ended Discovery](coral-towards-autonomous-multi-agent-evolution-for-open-ended-di-462c70.md) (shared topics: Artificial Intelligence, Computer Science)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Muon Dynamics as a Spectral Wasserstein Flow

## alphaXiv Summary

This research develops a mathematical framework for matrix-normalized deep learning optimizers by introducing Spectral Wasserstein distances, which provide a unified geometric interpretation for gradient descent, Muon, and intermediate Schatten-type normalizations. The work establishes these distances as bona fide metrics and identifies their associated gradient flows, rigorously connecting continuous-time dynamics to discrete optimization algorithms.

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.04891
- Source paper: https://arxiv.org/abs/2604.04891
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.04891v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.04891v1.png
- Paper ID: 2604.04891
- Canonical ID: 2604.04891v1
- Paper group ID: 019d65d5-f340-75a1-9c48-6fdd17f6fa1c
- Version ID: 019d65d5-f37d-7409-a464-39c64d50f957
- Version: v1
- Version order: 1
- Published at: 2026-04-06T17:41:12+00:00
- First published at: 2026-04-06T17:41:12+00:00
- Updated at: 2026-04-07T02:46:53.504000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Gabriel Peyré

## Topics

- bayesian-deep-learning
- Computer Science
- cs.AI
- geometric-deep-learning
- Mathematics
- math.OC
- optimization-methods
- representation-learning
- statistical-learning
- Statistics
- stat.ML

## Metrics

- Visits (all): 113
- Visits (last 7 days): 113
- Total votes: 2
- Public total votes: 9
- X likes: 0

## Abstract

Gradient normalization is central in deep-learning optimization because it stabilizes training and reduces sensitivity to scale. For deep architectures, parameters are naturally grouped into matrices or blocks, so spectral normalizations are often more faithful than coordinatewise Euclidean ones; Muon is the main motivating example of this paper. More broadly, we study a family of spectral normalization rules, ranging from ordinary gradient descent to Muon and intermediate Schatten-type schemes, in a mean-field regime where parameters are modeled by probability measures. We introduce a family of Spectral Wasserstein distances indexed by a norm gamma on positive semidefinite matrices. The trace norm recovers the classical quadratic Wasserstein distance, the operator norm recovers the Muon geometry, and intermediate Schatten norms interpolate between them. We develop the static Kantorovich formulation, prove comparison bounds with W2, derive a max-min representation, and obtain a conditional Brenier theorem. For Gaussian marginals, the problem reduces to a constrained optimization on covariance matrices, extending the Bures formula and yielding a closed form for commuting covariances in the Schatten family. For monotone norms, including all Schatten cases, we prove the equivalence between the static and dynamic Benamou-Brenier formulations, deduce that the resulting transport cost is a genuine metric equivalent to W2 in fixed dimension, and show that the induced Gaussian covariance cost is also a metric. We then interpret the associated normalized continuity equation as a Spectral Wasserstein gradient flow, identify its exact finite-particle counterpart as a normalized matrix flow, obtain first geodesic-convexity results, and show how positively homogeneous mean-field models induce a spectral unbalanced transport on the sphere.

## Problem

- A lack of rigorous mathematical and geometric understanding for widely used spectral normalization procedures, such as the Muon optimizer, in deep learning.
- The need for a unified framework to analyze and generalize various gradient normalization techniques, especially for matrix-shaped parameters in deep neural networks.
- Developing a mean-field perspective that can describe the collective behavior of an arbitrarily large number of parameters in a geometrically consistent way.

## Method

- Introducing Spectral Wasserstein distances, $W_\gamma$, parameterized by a norm $\gamma
