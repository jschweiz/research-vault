---
id: 2026-04-03-the-batch-research-test-time-training-end-to-end-ttt-e2e-retrains-m-87b314e7
kind: blog-post
title: Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs
source_url: https://www.deeplearning.ai/the-batch/test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to-handle-long-inputs
source_name: The Batch Research
authors:
- Arnuv Tandon
- Karan Dalal
published_at: '2026-04-03T11:44:06-07:00'
ingested_at: '2026-04-09T20:51:32.641740Z'
content_hash: 5db0fa403789fbe7e62b808327c9dd0171848da9e0a0103e3a8c05755b0ecd8d
identity_hash: 338b1180e73a655a6f0935396ce1c6278f29baccfeb7f7d784b61e8193a767a9
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- llm
- test-time training
- transformer
- inference
- context length
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to-handle-long-inputs
canonical_url: https://www.deeplearning.ai/the-batch/test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to-handle-long-inputs
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T20:51:32.641745Z'
short_summary: The authors introduced Test-Time Training End-to-End (TTT-E2E), a method that compresses context into transformer weights by training during inference to maintain stable accuracy and constant inference time as context grows. This approach demonstrated faster inference for long contexts, though training was more complex.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T20:59:31.869196Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: df1560d2eb08fb847429e16270620aed8c9efb548e89779c352ba87b313f2f2c
lightweight_enrichment_error: null
lightweight_scoring_model: heuristic:profile-fallback
lightweight_scoring_input_hash: f9db2e627baa59e39acf6c55a77304560fca7a3b3b8cd9481a1777175db68d89
lightweight_score:
  relevance_score: 0.517
  source_fit_score: 0.55
  topic_fit_score: 0.4
  author_fit_score: 0.18
  evidence_fit_score: 1.0
  confidence_score: 0.45
  bucket_hint: worth_a_skim
  reason: Heuristic fallback based on 1 favorite-topic match.
  evidence_quotes:
  - The authors introduced Test-Time Training End-to-End (TTT-E2E), a method that compresses context into transformer weights by training during inference to mainta
---
Large language models typically become less accurate and slower when they process longer contexts, but researchers enabled an LLM to keep accuracy stable and inference time constant as its context grew.
What’s new: Arnuv Tandon, Karan Dalal, and colleagues at the nonprofit Astera Institute, Nvidia, Stanford, UC Berkeley, and UC San Diego introduced [Test-Time Training, End-to-End](https://arxiv.org/abs/2512.23675?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) (TTT-E2E), a method that compresses context into a transformer’s weights by training it during inference.
Key insight: LLMs built on the transformer architecture attend to the entire context (all tokens input and output so far) to generate the next output token. Thus, generating each new output token takes more processing than the last, potentially making inference expensive and slow. Instead of attending to the entire context, a transformer can restrict attention to a smaller window of fixed size — which keeps the time required to generate each output token constant — and learn from the context by updating its weights.
How it works: The authors built a 3 billion-parameter transformer that implemented [sliding-window attention](https://arxiv.org/abs/2004.05150?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag), which restricted attention to a fixed window of 8,000 tokens. They pretrained the model on sequences of 8,000 tokens — 164 billion tokens total — drawn from a filtered [dataset](https://arxiv.org/abs/2406.11794?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) of text scraped from the web. To enable it to track longer contexts, they fine-tuned it on sequences of up to 128,000 tokens drawn from the Books subset of [The Pile](https://arxiv.org/abs/2101.00027?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag). The authors used a form of meta-learning, or learning how to learn; in this case, the model learns how to learn from input provided at inference time.
- Training and fine-tuning took place in two loops, one (which we’ll call the inner loop) encompassed by the other (the outer loop). The inner loop simulated learning a chunk of context at inference, and the outer cycle evaluated how well the model would perform after that learning and adjusted the weights accordingly.
- The inner loop took a training sequence and split it into consecutive chunks of 1,000 tokens. For each chunk, the model used sliding-window attention to (i) predict each token in turn, (ii) compute a typical next-token prediction loss, and (iii) use the loss to compute how the weights should change in the fully connected layers of the last quarter of the network. The result was a sequence of weight updates, one for every 1,000 tokens.
- The outer loop used these weight updates to compute the average next-token prediction loss after the simulated weight updates. It backpropagated through the sequence of simulated weight updates and updated the entire model’s weights. (This process increased training time, because it required computing gradients of gradients.)
- During inference, the model followed the inner loop. It split the input context into chunks, calculated the next-token prediction loss on the chunks, and updated only the fully connected layers in the last quarter of the network. Then it generated new tokens. (Since inference used only the inner loop, it didn’t need the increased time required in the outer-loop training process, so processing time was constant regardless of the context length.)
Results: The authors compared TTT-E2E to a transformer with conventional attention as well as highly efficient architectures such as [Mamba 2](https://arxiv.org/abs/2312.00752?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) (a recurrent neural network-style model) and [Gated DeltaNet](https://arxiv.org/abs/2412.06464?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) (which uses a custom form of linear attention). Its accuracy slightly exceeded that of the transformer over long contexts — except on Needle-in-a-Haystack, which involves recovering a short target string from a long context — and it generated output tokens as rapidly as the more-efficient architectures as context grew. Its exceptional inference speed came at the cost of slower and more complex training.
- TTT-E2E demonstrated very slightly higher performance than a vanilla transformer from short to long contexts, judging by next-token prediction loss. The vanilla transformer had an average loss of 0.015 higher across context lengths from 8,000 to 128,000 tokens. Mamba 2’s and Gated DeltaNet’s losses were still 0.03 higher. TTT-E2E matched those models on Needle-in-a-Haystack (NIAH) when processing shorter contexts, but its performance dropped dramatically after 8,000 tokens. For example, at 128,000 tokens, TTT-E2E (6 percent) fell below Mamba 2 (7 percent) and Gated DeltaNet (7 percent), and far below the vanilla transformer (99 percent).
- TTT-E2E processed long contexts faster than the vanilla transformer, roughly on par with Mamba 2 and Gated DeltaNet. Running on an H100 GPU, TTT-E2E’s time to generate its first token increased linearly by 25 milliseconds per 1,000 tokens as the context increased from 8,000 to 128,000 tokens. The vanilla transformer’s time to first token increased from 12 to 70 milliseconds per 1,000 tokens from 8,000 to 128,000 tokens.
- TTT-E2E’s training latency, or the time it took to process and execute model updates per 1,000 training tokens, exceeded that of Mamba 2 and Gated DeltaNet. TTT-E2E’s training latency rose from about 0.25 seconds given 8,000 training tokens to around 0.33 seconds given 128,000 training tokens. In contrast, Mamba 2 and Gated DeltaNet remained roughly constant at about 0.06 seconds. Given 8,000 training tokens, the vanilla transformer (0.08 seconds) trained four times faster. At 128,000 tokens that relationship flipped: vanilla transformer (0.39 seconds) trained about 1.2 times slower.
Why it matters: Learning at inference offers an approach to processing long contexts that’s simpler than designing custom attention mechanisms or recurrent architectures. This work reframes the problem as a trade-off between training and inference: Processing at inference is less expensive and more consistent per token, but training is slower.
We’re thinking: This model took it to heart when we said: Keep learning!
