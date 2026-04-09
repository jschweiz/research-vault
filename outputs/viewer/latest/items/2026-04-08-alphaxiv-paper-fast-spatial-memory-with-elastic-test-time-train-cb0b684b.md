# Fast Spatial Memory with Elastic Test-Time Training

Source: alphaXiv Papers
Published: 2026-04-08T17:59:48+00:00
Canonical URL: https://www.alphaxiv.org/abs/2604.07350

## Summary

Researchers from MIT-IBM Watson AI Lab, University of Michigan, and University of Massachusetts Amherst developed Elastic Test-Time Training (LaCET) to stabilize fast-weight updates in Transformer-based models, enabling robust multi-chunk adaptation for long 4D sequences. Their Fast Spatial Memory (FSM) model, incorporating LaCET, achieved a PSNR of 32.16 and LPIPS of 0.043 for 4D novel view synthesis on the Stereo4D dataset.

## Audio

https://paper-podcasts.alphaxiv.org/019d7000-b398-7a6d-8d19-56347f7e17ba/podcast.mp3

## Text

## Abstract

Large Chunk Test-Time Training (LaCT) has shown strong performance on long-context 3D reconstruction, but its fully plastic inference-time updates remain vulnerable to catastrophic forgetting and overfitting. As a result, LaCT is typically instantiated with a single large chunk spanning the full input sequence, falling short of the broader goal of handling arbitrarily long sequences in a single pass. We propose Elastic Test-Time Training inspired by elastic weight consolidation, that stabilizes LaCT fast-weight updates with a Fisher-weighted elastic prior around a maintained anchor state. The anchor evolves as an exponential moving average of past fast weights to balance stability and plasticity. Based on this updated architecture, we introduce Fast Spatial Memory (FSM), an efficient and scalable model for 4D reconstruction that learns spatiotemporal representations from long observation sequences and renders novel view-time combinations. We pre-trained FSM on large-scale curated 3D/4D data to capture the dynamics and semantics of complex spatial environments. Extensive experiments show that FSM supports fast adaptation over long sequences and delivers high-quality 3D/4D reconstruction with smaller chunks and mitigating the camera-interpolation shortcut. Overall, we hope to advance LaCT beyond the bounded single-chunk setting toward robust multi-chunk adaptation, a necessary step for generalization to genuinely longer sequences, while substantially alleviating the activation-memory bottleneck.

## Problem

- Existing Large Reconstruction Models (LRMs) and Large View Synthesis Models (LVSMs) struggle with processing arbitrarily long 4D sequences due to activation memory constraints, leading to performance degradation beyond training context length.
- Previous Test-Time Training (TTT) methods like LaCT suffer from unstable fast-weight updates, causing catastrophic forgetting, overfitting, and instability, which limits them to single large chunks and prevents true long-sequence scalability.
- Models often exploit camera-pose interpolation shortcuts, failing to learn generalized spatiotemporal representations, which hinders performance in scenarios with sparse or novel viewpoints.

## Method

- Introduces Elastic Test-Time Training (LaCET), an enhancement to LaCT that incorporates an elastic regularization mechanism to stabilize fast-weight updates, mitigating catastrophic forgetting and overfitting during continuous adaptation.
- LaCET employs a Fisher-weighted quadratic penalty that pulls fast weights towards a dynamically evolving "anchor state," using a Streaming-EMA policy to balance stability and plasticity across multiple chunks.
- Integrates LaCET blocks into the Fast Spatial Memory (FSM) model, an end-to-end feedforward network that learns 4D scene representations from visual observations, utilizing Plücker ray maps and timestamp maps for spatiotemporal conditioning.

## Results

- FSM-LVSM achieved a PSNR of 32.16, LPIPS of 0.043, and SSIM of 0.931 on the Stereo4D dataset for 4D novel view synthesis, significantly outperforming prior rendering-based methods like MoVieS (PSNR 27.19).
- Ablation studies demonstrated that LaCET significantly reduced the generalization gap and improved stability over vanilla LaCT, with the Streaming-EMA anchoring policy showing the most effective elastic memory behavior.
- The model exhibited reduced susceptibility to camera-pose interpolation shortcuts, maintaining robust performance under sparse input views and achieving a substantially smaller performance gap between discrete-view and continuous-view regimes compared to LaCT.

## Summary

Researchers from MIT-IBM Watson AI Lab, University of Michigan, and University of Massachusetts Amherst developed Elastic Test-Time Training (LaCET) to stabilize fast-weight updates in Transformer-based models, enabling robust multi-chunk adaptation for long 4D sequences. Their Fast Spatial Memory (FSM) model, incorporating LaCET, achieved a PSNR of 32.16 and LPIPS of 0.043 for 4D novel view synthesis on the Stereo4D dataset.

## Takeaways

- Elastic regularization, particularly with a Streaming-EMA anchor update policy, effectively stabilizes fast-weight dynamics in Test-Time Training, enabling robust multi-chunk adaptation and improved information transfer over long sequences.
- Stabilized fast-weight updates help models learn more generalizable view-conditioned spatial representations, reducing the tendency to rely on camera-pose interpolation shortcuts and improving performance under sparse inputs.
- The FSM architecture, with its LaCET backbone and combined Plücker ray/timestamp map inputs, can efficiently compress visual observations into unified 4D representations for high-quality novel view synthesis.
