---
id: 2026-04-06-alphaxiv-paper-muon-dynamics-as-a-spectral-wasserstein-flow-bfacf3b1
kind: paper
title: Muon Dynamics as a Spectral Wasserstein Flow
source_url: https://www.alphaxiv.org/abs/2604.04891
source_name: alphaXiv Papers
authors:
- Gabriel Peyré
published_at: '2026-04-06T17:41:12Z'
ingested_at: '2026-04-07T21:42:23.328772Z'
content_hash: f5c68af1112aea42012e6f78dcc5f3811e3a7711a3dd196227af815da842f425
tags:
- paper
- alphaxiv
- research
- bayesian-deep-learning
- computer science
- cs.ai
- geometric-deep-learning
- mathematics
- math.oc
- optimization-methods
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
- alphaxiv-transcript.json
- alphaxiv-transcript.md
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.04891
canonical_url: https://www.alphaxiv.org/abs/2604.04891
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T08:11:57.777888Z'
short_summary: This research introduces Spectral Wasserstein distances to provide a unified geometric interpretation for matrix-normalized deep learning optimizers like Muon. It establishes these distances as metrics and connects continuous-time dynamics to discrete optimization algorithms.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T08:41:48.481310Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 9de7d887080d2dd318acd3431e27d3d612e89afe4d7098f5f387943b1d23404e
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 6cc39869db6bfabcf3619132d232d6e03d406a34c19c024d54cb9f2121886f29
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.75
  topic_fit_score: 1.0
  author_fit_score: 0.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses core favorite topics like LLM optimization, deep learning, and specific authors like Muon.
  evidence_quotes:
  - This research introduces Spectral Wasserstein distances to provide a unified geometric interpretation for matrix-normalized deep learning optimizers like Muon.
  - We develop both static (Kantorovich) and dynamic (Benamou-Brenier) formulations for $W_\gamma$, and prove their equivalence for monotone norms.
  - The continuum Spectral Wasserstein gradient flow corresponds to an explicit finite-dimensional normalized particle dynamics, $\dot{X}_t = \Xi_p(\nabla F_n(X_t))
---
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

- Visits (all): 226
- Visits (last 7 days): 226
- Total votes: 4
- Public total votes: 21
- X likes: 0

## Abstract

Gradient normalization is central in deep-learning optimization because it stabilizes training and reduces sensitivity to scale. For deep architectures, parameters are naturally grouped into matrices or blocks, so spectral normalizations are often more faithful than coordinatewise Euclidean ones; Muon is the main motivating example of this paper. More broadly, we study a family of spectral normalization rules, ranging from ordinary gradient descent to Muon and intermediate Schatten-type schemes, in a mean-field regime where parameters are modeled by probability measures. We introduce a family of Spectral Wasserstein distances indexed by a norm gamma on positive semidefinite matrices. The trace norm recovers the classical quadratic Wasserstein distance, the operator norm recovers the Muon geometry, and intermediate Schatten norms interpolate between them. We develop the static Kantorovich formulation, prove comparison bounds with W2, derive a max-min representation, and obtain a conditional Brenier theorem. For Gaussian marginals, the problem reduces to a constrained optimization on covariance matrices, extending the Bures formula and yielding a closed form for commuting covariances in the Schatten family. For monotone norms, including all Schatten cases, we prove the equivalence between the static and dynamic Benamou-Brenier formulations, deduce that the resulting transport cost is a genuine metric equivalent to W2 in fixed dimension, and show that the induced Gaussian covariance cost is also a metric. We then interpret the associated normalized continuity equation as a Spectral Wasserstein gradient flow, identify its exact finite-particle counterpart as a normalized matrix flow, obtain first geodesic-convexity results, and show how positively homogeneous mean-field models induce a spectral unbalanced transport on the sphere.

## Problem

- A lack of rigorous mathematical and geometric understanding for widely used spectral normalization procedures, such as the Muon optimizer, in deep learning.
- The need for a unified framework to analyze and generalize various gradient normalization techniques, especially for matrix-shaped parameters in deep neural networks.
- Developing a mean-field perspective that can describe the collective behavior of an arbitrarily large number of parameters in a geometrically consistent way.

## Method

- Introducing Spectral Wasserstein distances, $W_\gamma$, parameterized by a norm $\gamma$ on positive semidefinite matrices, to unify various normalization schemes (trace norm for classical $W_2$, operator norm for Muon).
- Developing both static (Kantorovich) and dynamic (Benamou-Brenier) formulations for $W_\gamma$, and proving their equivalence for monotone norms.
- Interpreting normalized dynamics as Spectral Wasserstein gradient flows and identifying their exact finite-particle counterparts, thus connecting continuous-time theory to discrete optimization algorithms.

## Results

- The Spectral Wasserstein distance $W_\gamma$ is topologically equivalent to the classical $W_2$ distance and can be represented as a max-min problem $\max_{Q \in K_\gamma} W_Q(\mu, \nu)^2$.
- For Gaussian marginals, the problem reduces to a finite-dimensional optimization over cross-covariance matrices, defining a generalized Bures distance, with a closed-form solution for commuting covariances under Schatten norms.
- The continuum Spectral Wasserstein gradient flow corresponds to an explicit finite-dimensional normalized particle dynamics, $\dot{X}_t = \Xi_p(\nabla F_n(X_t))$, with specific matrix selectors $\Xi_p$ for Schatten norms, connecting directly to standard gradient descent (p=1) and Muon (p=$\infty$).

## Takeaways

- Spectral Wasserstein distances offer a robust Wasserstein distance framework, equivalent to optimizing over admissible quadratic transport costs, allowing for a precise geometric interpretation of matrix normalizations.
- The equivalence between the static and dynamic formulations establishes Spectral Wasserstein as a genuine metric, providing a foundation for analyzing optimization landscapes and geodesic paths.
- Different Schatten norms (e.g., trace, Frobenius, operator) induce distinct gradient flow behaviors, where operator-norm flows (Muon) lead to more globally coordinated particle movements compared to the local movements of trace-norm flows.

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

- MP3: https://paper-podcasts.alphaxiv.org/019d65d5-f340-75a1-9c48-6fdd17f6fa1c/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d65d5-f340-75a1-9c48-6fdd17f6fa1c/transcript.json
- Transcript lines: 16
- Transcript assets: `alphaxiv-transcript.md`, `alphaxiv-transcript.json`

## Similar Papers

- Old Optimizer, New Norm: An Anthology (2409.20325v2): Researchers at MIT CSAIL reinterpret prominent deep learning optimizers like Adam, Shampoo, and Prodigy, demonstrating that, by disabling Exponential Moving Averages, each performs exact first-order steepest descent under specific, implicitly chosen norms. This unified framework simplifies their theoretical understanding and proposes a systematic design space for new optimization algorithms based on intentional norm assignment.
- Understanding Gradient Orthogonalization for Deep Learning via  Non-Euclidean Trust-Region Optimization (2503.12645v2): This research from Yandex Research provides a rigorous theoretical interpretation of gradient orthogonalization methods, such as Muon, by demonstrating their equivalence to a first-order trust-region optimization method defined with respect to non-Euclidean norms. The work unifies several gradient-based optimizers, establishing state-of-the-art convergence guarantees for non-convex, star-convex, and second-order smooth objective functions, and explains practical phenomena like Muon's empirical success and the importance of weight decay in large language model training.
- Towards Understanding Gradient Dynamics of the Sliced-Wasserstein Distance via Critical Point Analysis (2502.06525v2)
- When do spectral gradient updates help in deep learning? (2512.04299v2): A theoretical framework identifies conditions for spectral gradient methods to surpass Euclidean approaches in deep learning optimization. The work demonstrates that spectral updates are advantageous when the gradient's nuclear rank is sufficiently high relative to the low stable rank of activation matrices, a condition frequently met in modern neural networks like transformers.
- Isotropic Curvature Model for Understanding Deep Learning Optimization: Is Gradient Orthogonalization Optimal? (2511.00674v1): Weijie Su of the University of Pennsylvania developed the isotropic curvature model, a theoretical framework to explain the effectiveness of matrix-gradient optimizers like Muon. This model rigorously demonstrates that optimal update strategies involve aligning singular spaces with the gradient and homogenizing its spectrum, providing a theoretical justification for Muon's design and suggesting a nuanced understanding of when full orthogonalization is optimal.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
