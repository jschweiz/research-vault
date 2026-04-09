---
id: 2026-04-07-alphaxiv-paper-neural-computers-503b0501
kind: paper
title: Neural Computers
source_url: https://www.alphaxiv.org/abs/2604.06425
source_name: alphaXiv Papers
authors:
- Mingchen Zhuge
- Changsheng Zhao
- Haozhe Liu
- Zijian Zhou
- Shuming Liu
- Wenyi Wang
- Ernie Chang
- Gael Le Lan
- Junjie Fei
- Wenxuan Zhang
- Yasheng Sun
- Zhipeng Cai
- Zechun Liu
- Yunyang Xiong
- Yining Yang
- Yuandong Tian
- Yangyang Shi
- Vikas Chandra
- Jürgen Schmidhuber
published_at: '2026-04-07T20:01:05Z'
ingested_at: '2026-04-09T12:07:22.423055Z'
content_hash: 7ca58f9b341f46a47ffdde6176324e58724908f99f0eb073c71ce10f52ae9d39
identity_hash: 5255e9e5bddc3b7afae39805c8c35cfac580ef8a4e00b4200f007318b2bcb9d8
tags:
- paper
- alphaxiv
- research
- agents
- computer science
- cs.ai
- cs.lg
- generative-models
- multi-modal-learning
- neuro-symbolic-ai
status: active
asset_paths:
- alphaxiv-legacy.json
- alphaxiv-metadata.json
- alphaxiv-paper.json
- alphaxiv-preview.json
- alphaxiv-similar-papers.json
source_id: alphaxiv-paper
source_pipeline_id: alphaxiv-paper
external_key: https://www.alphaxiv.org/abs/2604.06425
canonical_url: https://www.alphaxiv.org/abs/2604.06425
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T12:07:22.423061Z'
short_summary: The paper proposes Neural Computers (NCs), an emerging machine form that unifies computation, memory, and I/O in a learned runtime state. The long-term goal is the Completely Neural Computer (CNC), a general-purpose realization of this machine form.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T16:19:42.746039Z'
lightweight_enrichment_model: deterministic:alphaxiv-metadata
lightweight_enrichment_input_hash: a7a4f213566a52a5ec4317f1387bb3d07e91c5327cde313632df6b398cf98706
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b+alphaxiv-metrics-v1
lightweight_scoring_input_hash: deae6f803d10426b74f8906561f048f8f93b981ea84b5043412a2c62ac410922
lightweight_score:
  relevance_score: 1.0
  source_fit_score: 0.5942
  topic_fit_score: 1.0
  author_fit_score: 0.8
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: 'The document directly addresses core favorite topics like machine forms, agents, and memory, and features authors from the user''s preferred list. alphaXiv engagement signals: 0 public votes, 0 total votes, 48 visits in the last 7 days.'
  evidence_quotes:
  - The paper proposes Neural Computers (NCs), an emerging machine form that unifies computation, memory, and I/O in a learned runtime state.
  - 'Our long-term goal is the Completely Neural Computer (CNC): the mature, general-purpose realization of this emerging machine form, with stable execution, explic'
  - We outline a roadmap toward CNCs around these challenges.
---
# Neural Computers

## Metadata

- alphaXiv URL: https://www.alphaxiv.org/abs/2604.06425
- Source paper: https://arxiv.org/abs/2604.06425
- PDF: https://fetcher.alphaxiv.org/v2/pdf/2604.06425v1.pdf
- Cover image: https://www.alphaxiv.org/image/2604.06425v1.png
- GitHub: https://github.com/google-deepmind/dnc
- GitHub stars: 2529
- Paper ID: 2604.06425
- Canonical ID: 2604.06425v1
- Paper group ID: 019d7001-5dc5-729c-97a1-de4d2734efad
- Version ID: 019d7001-5e40-7620-b12c-b768cd023787
- Version: v1
- Version order: 1
- Published at: 2026-04-07T20:01:05+00:00
- First published at: 2026-04-07T20:01:05+00:00
- Updated at: 2026-04-09T02:10:30.981000+00:00
- License: http://arxiv.org/licenses/nonexclusive-distrib/1.0/
- Citations: 0

## Authors

- Mingchen Zhuge
- Changsheng Zhao
- Haozhe Liu
- Zijian Zhou
- Shuming Liu
- Wenyi Wang
- Ernie Chang
- Gael Le Lan
- Junjie Fei
- Wenxuan Zhang
- Yasheng Sun
- Zhipeng Cai
- Zechun Liu
- Yunyang Xiong
- Yining Yang
- Yuandong Tian
- Yangyang Shi
- Vikas Chandra
- Jürgen Schmidhuber

## Topics

- agents
- Computer Science
- cs.AI
- cs.LG
- generative-models
- multi-modal-learning
- neuro-symbolic-ai
- reinforcement-learning
- representation-learning
- self-supervised-learning
- video-understanding

## Metrics

- Visits (all): 48
- Visits (last 7 days): 48
- Total votes: 0
- Public total votes: 0
- X likes: 0

## Abstract

We propose a new frontier: Neural Computers (NCs) -- an emerging machine form that unifies computation, memory, and I/O in a learned runtime state. Unlike conventional computers, which execute explicit programs, agents, which act over external execution environments, and world models, which learn environment dynamics, NCs aim to make the model itself the running computer. Our long-term goal is the Completely Neural Computer (CNC): the mature, general-purpose realization of this emerging machine form, with stable execution, explicit reprogramming, and durable capability reuse. As an initial step, we study whether early NC primitives can be learned solely from collected I/O traces, without instrumented program state. Concretely, we instantiate NCs as video models that roll out screen frames from instructions, pixels, and user actions (when available) in CLI and GUI settings. These implementations show that learned runtimes can acquire early interface primitives, especially I/O alignment and short-horizon control, while routine reuse, controlled updates, and symbolic stability remain open. We outline a roadmap toward CNCs around these challenges. If overcome, CNCs could establish a new computing paradigm beyond today's agents, world models, and conventional computers.

## Audio Summary

- MP3: https://paper-podcasts.alphaxiv.org/019d7001-5dc5-729c-97a1-de4d2734efad/podcast.mp3
- Transcript JSON: https://paper-podcasts.alphaxiv.org/019d7001-5dc5-729c-97a1-de4d2734efad/transcript.json

## Resources

- GitHub repository: https://github.com/google-deepmind/dnc

## Similar Papers

- A Survey of Neuromorphic Computing and Neural Networks in Hardware (1705.06963v1)
- Personalized Artificial General Intelligence (AGI) via  Neuroscience-Inspired Continuous Learning Systems (2504.20109v1): A neuroscience-inspired architecture combines tri-memory systems (short-term, long-term, and permanent memory) with Hebbian learning principles to enable continuous learning and personalization in edge AI systems, drawing from biological mechanisms like synaptic pruning and sparse coding to address catastrophic forgetting while maintaining resource efficiency.
- Position: Episodic Memory is the Missing Piece for Long-Term LLM Agents (2502.06975v1): This position paper argues that an integrated episodic memory system is essential for developing large language model (LLM) agents capable of sustained, adaptive operation over long periods. It proposes a biologically-inspired framework to unify existing memory approaches, enabling continuous learning and context-sensitive knowledge retention.
- Modular Memory is the Key to Continual Learning Agents (2603.01761v1): A conceptual framework outlines a modular memory system designed to integrate In-Weight Learning and In-Context Learning, enabling AI agents to achieve robust and scalable continual adaptation. This framework provides a comprehensive blueprint for addressing the limitations of current foundation models and traditional continual learning.
- The Thousand Brains Project: A New Paradigm for Sensorimotor Intelligence (2412.18354v1): Researchers at Numenta, Inc., are developing a biologically-inspired AI system called 'The Thousand Brains Project,' which models intelligence based on the neocortex's principles of building multiple object models in parallel. Their initial implementation, Monty, uses modular 'Learning Modules' that learn structured, spatial world models from sensorimotor input, communicating via a universal 'Cortical Messaging Protocol' to enable rapid, continual learning and interaction in complex environments.
- Full similar-paper payload saved in `alphaxiv-similar-papers.json`.
