# GenLCA: 3D Diffusion for Full-Body Avatars from In-the-Wild Videos

Source: alphaXiv Papers
Published: 2026-04-08T16:34:07+00:00
Canonical URL: https://www.alphaxiv.org/abs/2604.07273

## Summary

GenLCA is a diffusion-based generative model that creates and edits photorealistic full-body avatars from text and image inputs. It achieves this by training a 3D diffusion model natively in 3D using large-scale real-world video data.

## Audio

https://paper-podcasts.alphaxiv.org/019d7014-6d53-738d-8883-ffdc0c9a52de/podcast.mp3

## Text

## Abstract

We present GenLCA, a diffusion-based generative model for generating and editing photorealistic full-body avatars from text and image inputs. The generated avatars are faithful to the inputs, while supporting high-fidelity facial and full-body animations. The core idea is a novel paradigm that enables training a full-body 3D diffusion model from partially observable 2D data, allowing the training dataset to scale to millions of real-world videos. This scalability contributes to the superior photorealism and generalizability of GenLCA. Specifically, we scale up the dataset by repurposing a pretrained feed-forward avatar reconstruction model as an animatable 3D tokenizer, which encodes unstructured video frames into structured 3D tokens. However, most real-world videos only provide partial observations of body parts, resulting in excessive blurring or transparency artifacts in the 3D tokens. To address this, we propose a novel visibility-aware diffusion training strategy that replaces invalid regions with learnable tokens and computes losses only over valid regions. We then train a flow-based diffusion model on the token dataset, inherently maintaining the photorealism and animatability provided by the pretrained avatar reconstruction model. Our approach effectively enables the use of large-scale real-world video data to train a diffusion model natively in 3D. We demonstrate the efficacy of our method through diverse and high-fidelity generation and editing results, outperforming existing solutions by a large margin. The project page is available at this https URL.
