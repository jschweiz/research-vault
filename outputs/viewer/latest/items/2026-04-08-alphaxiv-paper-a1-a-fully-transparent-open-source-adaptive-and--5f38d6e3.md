# A1: A Fully Transparent Open-Source, Adaptive and Efficient Truncated Vision-Language-Action Model

Source: alphaXiv Papers
Published: 2026-04-08T08:24:30+00:00
Canonical URL: https://www.alphaxiv.org/abs/2604.05672

## Summary

Researchers from SYSU and MBZUAI developed A1, a fully open-source Vision-Language-Action (VLA) framework designed for efficient, real-time robotic control. A1 adaptively accelerates both its VLM backbone and flow-matching action head, achieving up to a 72.3% reduction in inference time while maintaining high manipulation success rates across diverse real-world and simulated tasks.

## Audio

https://paper-podcasts.alphaxiv.org/019d6acc-c27f-798f-a358-b7c5679e836e/podcast.mp3

## Text

## Abstract

Vision-Language-Action (VLA) models have emerged as a powerful paradigm for open-world robot manipulation, but their practical deployment is often constrained by cost: billion-scale VLM backbones and iterative diffusion/flow-based action heads incur high latency and compute, making real-time control expensive on commodity hardware. We present A1, a fully open-source and transparent VLA framework designed for low-cost, high-throughput inference without sacrificing manipulation success; Our approach leverages pretrained VLMs that provide implicit affordance priors for action generation. We release the full training stack (training code, data/data-processing pipeline, intermediate checkpoints, and evaluation scripts) to enable end-to-end reproducibility. Beyond optimizing the VLM alone, A1 targets the full inference pipeline by introducing a budget-aware adaptive inference scheme that jointly accelerates the backbone and the action head. Specifically, we monitor action consistency across intermediate VLM layers to trigger early termination, and propose Inter-Layer Truncated Flow Matching that warm-starts denoising across layers, enabling accurate actions with substantially fewer effective denoising iterations. Across simulation benchmarks (LIBERO, VLABench) and real robots (Franka, AgiBot), A1 achieves state-of-the-art success rates while significantly reducing inference cost (e.g., up to 72% lower per-episode latency for flow-matching inference and up to 76.6% backbone computation reduction with minor performance degradation). On RoboChallenge, A1 achieves an average success rate of 29.00%, outperforming baselines including pi0(28.33%), X-VLA (21.33%), and RDT-1B (15.00%).

## Problem

- Existing Vision-Language-Action (VLA) models suffer from high computational cost and latency, primarily due to multi-billion-parameter VLM backbones and numerous iterative denoising steps in their action heads.
- The computational demands of current VLA models restrict real-time deployment on commodity hardware, necessitating expensive hardware and significant energy budgets.
- While VLM latency reduction has been explored, the action head often remains an unaddressed bottleneck, increasing overall inference time and hindering practical adoption.

## Method

- A1 integrates a Molmo-7B VLM backbone with a Qwen3-based flow-matching (A1-FM) or MLP (A1-MLP) action head, pre-trained on a diverse, large-scale robotic trajectory corpus.
- A budget-aware adaptive inference mechanism jointly accelerates the VLM and action head using multi-exit training and early-termination based on action-consistency thresholding.
- Inter-Layer Truncated Flow Matching warm-starts denoising for the FM head across VLM layers, significantly reducing iterative denoising steps from 10 to 2 and decreasing per-episode inference time.

## Results

- A1 achieved an average success rate of 96.6% on the LIBERO benchmark and 56.7% on real-world tasks across four robot platforms (Franka, AgiBot, WuJie-Arm, Dobot-Arm), outperforming baselines like π0 and π0.5.
- Inter-Layer Truncated Flow Matching reduced per-episode inference time by 72.3% (from 37.8s to 10.5s) while maintaining a 96.4% success rate, by reducing denoising steps from 10 to 2 and using warm-start initialization.
- The model demonstrated robust zero-shot generalization on the LIBERO-Plus benchmark, achieving a 75.3% success rate even under significant distribution shifts, exceeding OpenVLA-OFT (69.6%).

## Summary

Researchers from SYSU and MBZUAI developed A1, a fully open-source Vision-Language-Action (VLA) framework designed for efficient, real-time robotic control. A1 adaptively accelerates both its VLM backbone and flow-matching action head, achieving up to a 72.3% reduction in inference time while maintaining high manipulation success rates across diverse real-world and simulated tasks.

## Takeaways

- Flow-matching trajectories often converge to correct action modes within few denoising steps (fewer than three), indicating redundancy in extensive iterative denoising.
- Robot actions often evolve smoothly across consecutive control steps, suggesting that full VLA re-evaluation at every timestep may be inefficient.
- Intermediate hidden states within the VLM backbone can encode sufficient spatial and visual features to adequately seed downstream action prediction, allowing for earlier exits.
