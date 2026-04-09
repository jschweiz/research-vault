# MoRight: Motion Control Done Right

Source: alphaXiv Papers
Published: 2026-04-08T17:59:22+00:00
Canonical URL: https://www.alphaxiv.org/abs/2604.07348

## Summary

MoRight, developed by researchers at NVIDIA and the University of Illinois Urbana-Champaign, introduces a Diffusion Transformer-based framework for controllable video generation. It achieves disentangled control of camera and object motion while integrating motion causality reasoning, allowing users to define object actions in a canonical view, independently adjust camera viewpoints, and infer physically plausible action-consequence relationships.

## Audio

https://paper-podcasts.alphaxiv.org/019d6ff4-39fa-7566-9a26-8a93c1dce29b/podcast.mp3

## Text

## Abstract

Generating motion-controlled videos--where user-specified actions drive physically plausible scene dynamics under freely chosen viewpoints--demands two capabilities: (1) disentangled motion control, allowing users to separately control the object motion and adjust camera viewpoint; and (2) motion causality, ensuring that user-driven actions trigger coherent reactions from other objects rather than merely displacing pixels. Existing methods fall short on both fronts: they entangle camera and object motion into a single tracking signal and treat motion as kinematic displacement without modeling causal relationships between object motion. We introduce MoRight, a unified framework that addresses both limitations through disentangled motion modeling. Object motion is specified in a canonical static-view and transferred to an arbitrary target camera viewpoint via temporal cross-view attention, enabling disentangled camera and object control. We further decompose motion into active (user-driven) and passive (consequence) components, training the model to learn motion causality from data. At inference, users can either supply active motion and MoRight predicts consequences (forward reasoning), or specify desired passive outcomes and MoRight recovers plausible driving actions (inverse reasoning), all while freely adjusting the camera viewpoint. Experiments on three benchmarks demonstrate state-of-the-art performance in generation quality, motion controllability, and interaction awareness.

## Problem

- Existing controllable video generation methods often entangle camera and object motion, making it challenging to control movements independently of the camera viewpoint.
- Current models frequently treat motion as kinematic displacement, neglecting underlying causal relationships, which requires laborious detailed inputs or external physics engines for physically plausible interactions.
- Generating interactive scenes typically demands extensive, privileged motion inputs (e.g., per-frame depth maps, 3D object trajectories) or relies on external models, increasing complexity and potential for error.

## Method

- A dual-stream Diffusion Transformer (DiT) architecture is employed, featuring a canonical stream for object motion in a static view and a target stream for the final video, interacting via shared weights and self-attention for disentangled camera-object control.
- Motion causality modeling is integrated through active/passive motion decomposition and motion dropout training, enabling the model to infer missing motion components and learn action-consequence relationships.
- A comprehensive data curation pipeline combines motion extraction, canonicalization, synthetic paired two-view video generation, and mixed training with real-world single-view data to enhance robustness and generalization.

## Results

- MoRight received superior human preference scores, with 53.5% for controllability, 54.6% for motion realism, and 55.9% for photorealism, outperforming state-of-the-art baselines.
- The framework demonstrated strong motion accuracy (e.g., best EPE and Rotation/Translation error on the Cooking benchmark) and visual quality (best FID and FVD on WISA and Cooking datasets) while maintaining consistent object dynamics.
- It achieved the highest Physical Commonsense score on WISA and successfully performed both forward (predicting consequences from actions) and inverse (inferring actions from desired outcomes) causal reasoning from sparse user inputs.

## Summary

MoRight, developed by researchers at NVIDIA and the University of Illinois Urbana-Champaign, introduces a Diffusion Transformer-based framework for controllable video generation. It achieves disentangled control of camera and object motion while integrating motion causality reasoning, allowing users to define object actions in a canonical view, independently adjust camera viewpoints, and infer physically plausible action-consequence relationships.

## Takeaways

- Object motion is unambiguously defined and transferred across different camera viewpoints when initially processed in a canonical static view, acting as a 'virtual anchor' within a dual-stream architecture.
- Decomposing object motion into active (user-driven) and passive (causal outcomes) components, combined with asymmetric supervision during training, enables the model to reason about and generate physically coherent action-consequence relationships.
- A hybrid training approach, leveraging both synthetic paired data for disentangled control and abundant single-view real-world data, significantly improves the model's robustness, generalization, and diversity in camera motion handling.
