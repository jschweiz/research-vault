# PoM: A Linear-Time Replacement for Attention with the Polynomial Mixer

- alphaXiv: https://www.alphaxiv.org/abs/2604.06129
- Source paper: https://arxiv.org/abs/2604.06129

The Transformer architecture has become the standard for a wide array of artificial intelligence tasks, from large language models to high-resolution image generation. At its core is the Multi-Head Attention (MHA) mechanism, which allows models to weigh the importance of different parts of an input sequence relative to each other. However, MHA has a significant limitation: its computational and memory requirements grow quadratically with the length of the input sequence. This means that doubling the input length quadruples the resources required, making it difficult to process extremely long documents, high-resolution videos, or large 3D environments.

Research has increasingly focused on finding "sub-quadratic" alternatives that can approximate or replace attention without this scaling penalty. Existing approaches include State Space Models (SSMs) like Mamba, which offer constant-time inference but often struggle with non-sequential data like images, and various low-rank or local attention approximations that can sometimes sacrifice model expressivity. The Polynomial Mixer (PoM) is a token mixing mechanism designed to replace MHA with linear computational complexity while maintaining the high performance and theoretical generality associated with standard Transformers.

## The Architecture of the Polynomial Mixer (PoM)

The primary goal of PoM is to allow each token in a sequence to access global context without performing the pairwise comparisons that lead to quadratic complexity. In a standard attention mechanism, every token queries every other token. In contrast, PoM summarizes the entire sequence into a single, compact "shared state" and then allows each individual token to query this state.

Suppose we have an input sequence $X \in \mathbb{R}^{d \times n}$, where $n$ is the number of tokens and $d$ is the feature dimension of each token. The PoM operation involves two main steps: sequence aggregation and token-wise gating.

First, the model computes a shared state representation $H(X) \in \mathbb{R}^{D \times 1}$, where $D$ is an internal hidden dimension. This state is calculated using a learned polynomial function that aggregates information across all $n$ tokens:

$$
H(X) = \left[ \sum_{p=1}^{k} \alpha_p \odot (h(W_h X))^p \right] \mathbf{1} \in \mathbb{R}^{D \times 1}
$$

In this equation, $W_h \in \mathbb{R}^{D \times d}$ is a learnable weight matrix that projects tokens into the hidden space. The function $h$ is an activation function, and $(.)^p$ denotes an element-wise power operation. The learnable polynomial coefficients $\alpha_p \in \mathbb{R}^{D \times 1} \text{ for } p \in \{1, \dots, k\}$ allow the model to weight different orders of the polynomial up to a degree $k$. The final multiplication by $\mathbf{1} \in \mathbb{R}^{n \times 1}$ (a vector of ones) performs a summation across the sequence dimension, effectively compressing $n$ tokens into a single vector.

Second, the model uses this global summary to update each token. It computes a gating mask $S(X) = \sigma(W_s X) \in [0, 1]^{D \times n}$ using a sigmoid function $\sigma(.)$ and another weight matrix $W_s \in \mathbb{R}^{D \times d}$. This mask determines which parts of the shared global state are relevant to each specific token. The final output is then projected back to the original dimension $d$ using $W_o \in \mathbb{R}^{d \times D}$:

$$
\text{PoM}(X) = W_o [\sigma(W_s X) \odot H(X)] \in \mathbb{R}^{d \times n}
$$

Because both the aggregation and the gating steps involve operations that scale linearly with the number of tokens $n$, PoM achieves $O(n)$ complexity, making it significantly more efficient for long sequences than the $O(n^2)$ complexity of standard attention.

## Theoretical Expressivity and the PolyMorpher Block

A critical question for any attention replacement is whether it can still perform the complex reasoning required for modern AI. Theoretical analysis suggests that PoM-based models, referred to as PolyMorphers, retain several important properties of standard Transformers.

The PolyMorpher block is structured similarly to a Transformer block, using residual connections and feed-forward networks (FFN):

$$
P(X) = X + \text{PoM}(X) + \text{FF}(X + \text{PoM}(X))
$$

The authors demonstrate that PoM is permutation equivariant, meaning that if the order of the input tokens is shuffled, the output tokens will be shuffled in exactly the same way (provided no positional encodings are used). This property is a hallmark of self-attention and is vital for tasks where the spatial or temporal relationship between items must be learned rather than hard-coded.

More importantly, the research proves that PoM satisfies the "contextual mapping property." This property ensures that the mixer can map every token to a unique value that depends on the entire context of the sequence while still preserving the unique identity of the original token. Based on this, the PolyMorpher block is shown to be a universal sequence-to-sequence approximator. This means that, in theory, a network of PolyMorpher blocks can approximate any continuous function that maps one sequence to another, placing it on the same theoretical footing as the standard Transformer.

## Handling Causal Dependencies and Real-Time Inference

In natural language processing, models typically operate in a "causal" mode, where each token can only see tokens that came before it. While the basic PoM aggregates the entire sequence, it can be easily adapted for causal tasks.

In a causal setting, the shared state $H(X)$ is no longer a single vector for the whole sequence but becomes a sequence of states where each state $H(X)_t$ only includes information from tokens up to time $t$. This allows for very efficient autoregressive generation (e.g., predicting the next word in a sentence). The state can be updated iteratively:

$$
H(X)_t = H(X)_{t-1} + \sum_{p=1}^{k} \alpha_p \odot (h(W_h x_t))^p \in \mathbb{R}^{D \times 1}
$$

where $x_t \in \mathbb{R}^{d \times 1}$ is the token at the current time step. This recurrence means that during inference, the cost of generating a new token is $O(1)$—it does not depend on how many tokens have already been generated. This provides a massive advantage over standard Transformers, where the "KV cache" grows with sequence length and eventually slows down generation or exceeds memory limits.

## Efficiency Benchmarks and Computational Complexity

The transition from quadratic to linear complexity has practical implications for hardware performance. Standard attention implementations, even highly optimized ones like FlashAttention, eventually succumb to the quadratic cost as the sequence length $n$ grows.

PoM's computational cost is primarily determined by the hidden dimension $D$ and the polynomial degree $k$. The analysis shows that PoM starts to outperform MHA when the sequence length exceeds a relatively small threshold (often around 1,000 tokens for common model sizes). 

Empirical tests demonstrate this efficiency clearly:
- **Throughput:** In language modeling tasks with a sequence length of 32,000 tokens, PoM-based models achieved a throughput of approximately 447,500 tokens per second, while standard MHA models dropped to roughly 52,400 tokens per second.
- **Scaling:** Unlike attention, where doubling the resolution of an image leads to a fourfold increase in token-mixing time, PoM's scaling is direct. In image generation tasks at 1024x1024 resolution, PoM-based architectures were twice as fast as their attention-based counterparts.

Importantly, these speedups were achieved using high-level PyTorch code. The authors suggest that further optimizations using custom CUDA kernels could increase this advantage even further.

## Performance Across Modalities: From Text to 3D Points

To establish PoM as a general-purpose building block, it was evaluated across five distinct domains.

### Natural Language Processing
In language modeling, the researchers replaced the attention layers in a 125M parameter GPT-2 model with PoM. While a pure PoM model performed slightly worse than standard attention, a "Hybrid" version—which combined PoM with some local attention (attention restricted to a small window of nearby tokens)—matched the performance of the original GPT-2 on benchmarks like ARC and MMLU while remaining significantly faster at long context lengths.

### Image Generation
For class-conditional image generation (ImageNet 256x256), PoM was integrated into "Scalable Interpolant Transformers" (SiT). The PoM-based models produced images of comparable visual quality to the original attention-based models, as measured by Fréchet Inception Distance (FID), but with twice the inference speed.

### Optical Character Recognition (OCR)
On the task of reading handwritten text, PoM-based models achieved Character Error Rates (CER) comparable to state-of-the-art attention models. Notably, as the text grew from single lines to multi-line documents (increasing the sequence length), the efficiency gains of PoM became more pronounced.

### Earth Observation and 3D Vision
In 3D point cloud segmentation (ScanNet) and satellite image time-series analysis (PASTIS), PoM models matched the accuracy of standard Transformers. In satellite analysis, where temporal sequences can be quite long, the PoM-based version was over 300% faster than the attention-based baseline. In 3D vision, PoM allowed for processing entire large-scale point clouds in a single pass without the need to "chunk" the data into smaller pieces, which is a common requirement for $O(n^2)$ models.

## Conclusion

The Polynomial Mixer (PoM) offers a scalable alternative to self-attention that bypasses the quadratic complexity bottleneck. By summarizing sequence information into a shared polynomial state, it achieves linear scaling without sacrificing the theoretical expressivity or the practical performance of the Transformer architecture. Its versatility across text, images, 3D points, and satellite data suggests that it can serve as a robust, general-purpose component in the next generation of efficient, long-context AI models.

## Relevant Citations

- Attention is all you need: This is the foundational paper that introduced the Multi-Head Attention (MHA) mechanism and the Transformer architecture. The main paper's proposed Polynomial Mixer (PoM) is explicitly designed as a direct, linear-time replacement for MHA, making this the primary work that PoM aims to improve upon in terms of efficiency.
- Are transformers universal approximators of sequence-to-sequence functions?: This paper provides the theoretical framework for proving that Transformers are universal approximators, which hinges on the 'contextual mapping property' of attention. The PoM paper leverages this exact framework to prove that their proposed mixer also satisfies this property, thereby theoretically validating it as a powerful replacement for attention without sacrificing expressivity.
- FlashAttention: Fast and memory-efficient exact attention with io-awareness: A key claim of the main paper is the superior efficiency of PoM. FlashAttention is a highly optimized implementation of the standard attention mechanism that serves as a critical, state-of-the-art baseline. The paper repeatedly benchmarks PoM's performance against FlashAttention to demonstrate its practical speed advantages for long sequences.
- Efficiently modeling long sequences with structured state spaces: This paper is a foundational work on State Space Models (SSMs), which are presented as a major class of alternatives to attention for efficient sequence modeling. The PoM paper positions its work within this broader context, contrasting its approach with SSMs, making this citation important for understanding the landscape of competing architectures.
