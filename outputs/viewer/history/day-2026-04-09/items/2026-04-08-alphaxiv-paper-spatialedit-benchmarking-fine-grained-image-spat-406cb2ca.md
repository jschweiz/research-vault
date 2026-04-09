# SpatialEdit: Benchmarking Fine-Grained Image Spatial Editing

Source: alphaXiv Papers
Published: 2026-04-08T04:54:06+00:00
Canonical URL: https://www.alphaxiv.org/abs/2604.04911

## Summary

This paper introduces SpatialEdit-Bench, a benchmark for fine-grained image spatial editing, and SpatialEdit-16B, a baseline model for spatial manipulation. It uses a synthetic dataset to evaluate perceptual plausibility and geometric fidelity in spatial editing tasks.

## Audio

https://paper-podcasts.alphaxiv.org/019d65d7-b155-731f-9120-a8ca4f7ce509/podcast.mp3

## Text

## Abstract

Image spatial editing performs geometry-driven transformations, allowing precise control over object layout and camera viewpoints. Current models are insufficient for fine-grained spatial manipulations, motivating a dedicated assessment suite. Our contributions are listed: (i) We introduce SpatialEdit-Bench, a complete benchmark that evaluates spatial editing by jointly measuring perceptual plausibility and geometric fidelity via viewpoint reconstruction and framing analysis. (ii) To address the data bottleneck for scalable training, we construct SpatialEdit-500k, a synthetic dataset generated with a controllable Blender pipeline that renders objects across diverse backgrounds and systematic camera trajectories, providing precise ground-truth transformations for both object- and camera-centric operations. (iii) Building on this data, we develop SpatialEdit-16B, a baseline model for fine-grained spatial editing. Our method achieves competitive performance on general editing while substantially outperforming prior methods on spatial manipulation tasks. All resources will be made public at this https URL.
