# Meta-Harness: End-to-End Optimization of Model Harnesses

Source: alphaXiv Papers
Published: 2026-03-30T05:33:50+00:00
Canonical URL: https://www.alphaxiv.org/abs/2603.28052

## Summary

Meta-Harness is an end-to-end optimization framework for LLM harnesses, using an agentic proposer to search for optimal code harnesses. This system improves performance in text classification, math reasoning, and agentic coding by accessing uncompressed historical code and execution traces.

## Audio

https://paper-podcasts.alphaxiv.org/019d41b7-1156-7866-b991-94545a578703/podcast.mp3

## Text

## Abstract

The performance of large language model (LLM) systems depends not only on model weights, but also on their harness: the code that determines what information to store, retrieve, and present to the model. Yet harnesses are still designed largely by hand, and existing text optimizers are poorly matched to this setting because they compress feedback too aggressively. We introduce Meta-Harness, an outer-loop system that searches over harness code for LLM applications. It uses an agentic proposer that accesses the source code, scores, and execution traces of all prior candidates through a filesystem. On online text classification, Meta-Harness improves over a state-of-the-art context management system by 7.7 points while using 4x fewer context tokens. On retrieval-augmented math reasoning, a single discovered harness improves accuracy on 200 IMO-level problems by 4.7 points on average across five held-out models. On agentic coding, discovered harnesses surpass the best hand-engineered baselines on TerminalBench-2. Together, these results show that richer access to prior experience can enable automated harness engineering.

## Problem

- Harness engineering, which designs how large language models (LLMs) store, retrieve, and present information, is a largely manual, iterative process relying on human intuition and heuristics.
- The performance of LLM systems is highly sensitive to harness design, with variations potentially causing up to a 6x difference in model performance on the same benchmark.
- Existing text optimization methods are inadequate for complex harness logic due to aggressive feedback compression and limited context, which discards crucial information needed to diagnose long-horizon failures.

## Method

- Meta-Harness implements an outer-loop optimization procedure where an agentic proposer (a coding LLM) searches over task-specific harnesses.
- The proposer has selective, uncompressed access to a growing filesystem containing the source code, detailed execution traces, and evaluation scores of all prior candidate harnesses.
- The agent iteratively inspects this comprehensive history, reasons about failure modes, and proposes new harness candidates by modifying the Python code directly.

## Results

- Meta-Harness achieved 48.6% accuracy in online text classification, outperforming state-of-the-art hand-designed methods (ACE) by 7.7 points while using 4x fewer context tokens.
- A single discovered retrieval harness improved accuracy on 200 IMO-level math problems by an average of 4.7 points across five held-out models (e.g., GPT-5.4n, Gemini-3F) compared to a 'No Retriever' baseline.
- The system automatically discovered harnesses that achieved top-tier pass rates on TerminalBench-2, reaching 76.4% with Claude Opus 4.6 (ranking #2) and 37.6% with Claude Haiku 4.5 (ranking #1).

## Summary

Meta-Harness provides an end-to-end optimization framework for LLM harnesses, the external code that dictates how models interact with their environment. The system utilizes an agentic proposer with filesystem access to uncompressed historical code and execution traces, leading to a 7.7-point accuracy improvement in text classification, a 4.7-point average gain in math reasoning, and competitive pass rates on agentic coding benchmarks.

## Takeaways

- Full, uncompressed access to historical diagnostic data (raw code, execution traces, and evaluation scores) is critical for an agent to perform causal reasoning and targeted modifications in complex, stateful code-space search.
- Direct optimization in the code space, enabled by an agentic proposer, facilitates algorithmic modifications and complete program rewrites, providing a natural regularization bias towards coherent solutions.
- An agent, when provided with rich, granular feedback, can effectively identify and address complex, long-horizon failures in stateful programs, going beyond fixed templates or summary-based feedback.
