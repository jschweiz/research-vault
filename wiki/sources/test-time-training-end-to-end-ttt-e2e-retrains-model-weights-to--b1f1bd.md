---
id: page:2026-04-03-the-batch-research-test-time-training-end-to-end-ttt-e2e-retrains-m-87b314e7
page_type: source-note
title: Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs
aliases:
- Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs
source_refs:
- 2026-04-03-the-batch-research-test-time-training-end-to-end-ttt-e2e-retrains-m-87b314e7
backlinks: []
updated_at: '2026-04-09T23:08:05.321135Z'
managed: true
---
# Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to-handle-long-inputs
- Document kind: blog-post
- Published at: 2026-04-03T11:44:06-07:00
- Authors: Arnuv Tandon, Karan Dalal
- Tags: deeplearning-ai, official, research, website, blog-post, llm, test-time training, transformer, inference, context length
- Topics: [Inference](../topics/inference.md), [Context Length](../topics/context-length.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Llm](../topics/llm.md), [Official](../topics/official.md), [Test Time Training](../topics/test-time-training.md)
- Trend score: 68.20
- Novelty score: 4.20

## Summary

The authors introduced Test-Time Training End-to-End (TTT-E2E), a method that compresses context into transformer weights by training during inference to maintain stable accuracy and constant inference time as context grows. This approach demonstrated faster inference for long contexts, though training was more complex.

## Topic Map

- [Inference](../topics/inference.md)
- [Context Length](../topics/context-length.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Llm](../topics/llm.md)
- [Official](../topics/official.md)
- [Test Time Training](../topics/test-time-training.md)

## Related Research

- [Google Debuted Lyria 3, An App That Turns Text or Images Into 30-Second Songs](google-debuted-lyria-3-an-app-that-turns-text-or-images-into-30--7835fb.md) (shared topics: Deeplearning Ai, Official)
- [Claude Code’s Source Code Leaked, Exposing Potential Future Features Kairos and autoDream](claude-codes-source-code-leaked-exposing-potential-future-featur-2d1053.md) (shared topics: Deeplearning Ai, Official)
- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-9e1ca2.md) (shared topics: Llm, Official)
- [Recursive Language Models Offer Path To Dramatically Expand Beyond the Context Window](recursive-language-models-offer-path-to-dramatically-expand-beyo-eade39.md) (shared topics: Deeplearning Ai, Official)
- [Grok Imagine 1.0 Sharply Cuts Costs for High-Quality Video Generation](grok-imagine-1-0-sharply-cuts-costs-for-high-quality-video-gener-bc473a.md) (shared topics: Deeplearning Ai, Official)
- [Nvidia’s Open Nemotron 3 Super 120B-A12B Model Sets New Paces In Its Class](nvidias-open-nemotron-3-super-120b-a12b-model-sets-new-paces-in--503103.md) (shared topics: Deeplearning Ai, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Large language models typically become less accurate and slower when they process longer contexts, but researchers enabled an LLM to keep accuracy stable and inference time constant as its context grew.
What’s new: Arnuv Tandon, Karan Dalal, and colleagues at the nonprofit Astera Institute, Nvidia, Stanford, UC Berkeley, and UC San Diego introduced [Test-Time Training, End-to-End](https://arxiv.org/abs/2512.23675?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) (TTT-E2E), a method that compresses context into a transformer’s weights by training it during inference.
Key insight: LLMs built on the transformer architecture attend to the entire context (all tokens input and output so far) to generate the next output token. Thus, generating each new output token takes more processing than the last, potentially making inference expensive and slow. Instead of attending to the entire context, a transformer can restrict attention to a smaller window of fixed size — which keeps the time required to generate each output token constant — and learn from the context by updating its weights.
How it works: The authors built a 3 billion-parameter transformer that implemented [sliding-window attention](https://arxiv.org/abs/2004.05150?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag), which restricted attention to a fixed window of 8,000 tokens. They pretrained the model on sequences of 8,000 tokens — 164 billion tokens total — drawn from a filtered [dataset](https://arxiv.org/abs/2406.11794?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) of text scraped from the web. To enable it to track longer contexts, they fine-tuned it on sequences of up to 128,000 tokens drawn from the Books subset of [The Pile](https://arxiv.org/abs/2101.00027?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag). The authors used a form of meta-learning, or learning how to learn; in this case, the model learns how to learn from input provided at inference time.
- Training and fine-tuning took place in two loops, one (which we’ll call the inner loop) encompassed by the other (the outer loop). The inner loop simulated learning a chunk of context at inference, and the outer cycle evaluated how well the model would perform after that learning and adjusted the weights accordingly.
- The inner loop took a training sequence and split it into consecutive chunks of 1,000 tokens. For each chunk, the model used sliding-window attention to (i) predict each token in turn, (ii) compute a typical next-token prediction loss, and (iii) use the loss to compute how the weights should change in the fully connected layers of the last quarter of the network. The result was a sequence of weight updates, one for every 1,000 tokens.
- The outer loop used these weight updates to compute the average next-token prediction loss after the simulated weight updates. It backpropagated through the sequence of simulated weight updates and updated the entire model’s weights. (This process increased training time, because it required computing gradients of gradients.)
- During inference, the model followed the inner loop. It split the input context into chunks, calculated the next-token prediction loss on the chunks, and updated only the fully connected layers in the last quarter of the network. Then it generated new tokens. (Since inference used only the inner loop, it didn’t need the increased time required in the outer-loop training process, so processing time was constant regardless of the context length.)
Results: The authors compared TTT-E2E to a transformer with conventional attention as well as highly efficien
