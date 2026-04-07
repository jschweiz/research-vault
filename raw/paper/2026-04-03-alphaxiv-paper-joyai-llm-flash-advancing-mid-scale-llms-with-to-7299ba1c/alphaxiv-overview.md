# JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency

- alphaXiv: https://www.alphaxiv.org/abs/2604.03044
- Source paper: https://arxiv.org/abs/2604.03044

In the current landscape of Large Language Models (LLMs), a significant challenge has emerged: the tension between high-quality reasoning and computational efficiency. While scaling models to hundreds of billions of parameters often yields better performance, it typically results in higher latency and increased token consumption during inference. JoyAI-LLM Flash addresses this by focusing on the sub-$50\text{B}$ parameter regime, prioritizing token efficiency—the ability of a model to produce accurate outputs while minimizing the total number of tokens generated.

## Introduction to JoyAI-LLM Flash

JoyAI-LLM Flash is a mid-scale language model designed to maximize reasoning capabilities and agentic performance while maintaining high inference throughput. At its core, the model utilizes a sparse Mixture-of-Experts (MoE) architecture with a total of $48.9\text{B}$ parameters. However, by activating only a fraction of these parameters during each forward pass—approximately $3.28\text{B}$ active parameters per token—it achieves computational costs comparable to much smaller dense models while retaining the knowledge capacity of a larger system.

![Model Performance vs. Token Consumption](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03044v1/x1.png)
*Figure 1: Comparison of model performance against token consumption across various benchmarks. JoyAI-LLM Flash occupies the upper-left region, indicating high accuracy with low token usage.*

The development of JoyAI-LLM Flash is characterized by a "co-design" philosophy that integrates architectural sparsity, large-scale data curation, and a novel reinforcement learning (RL) algorithm. By focusing on intrinsic efficiency rather than post-hoc optimizations alone, the model establishes a new baseline for what is achievable in the sub-$50\text{B}$ parameter class.

## Architectural Design and Sparse Scaling

The architecture of JoyAI-LLM Flash is built on a sparse MoE framework consisting of 40 Transformer layers. While the initial layer is a dense feed-forward network, the subsequent 39 layers utilize a sophisticated MoE module. This module features 256 total experts, with 8 routed experts dynamically selected via a Top-8 gating mechanism and one dedicated shared expert that is always active. Of the $3.28\text{B}$ active parameters per token, $2.7\text{B}$ come from these routed experts, while $0.58\text{B}$ reside in the embedding and shared layers.

To improve attention efficiency and long-context handling, the model incorporates Multi-head Latent Attention (MLA), which compresses KV (Key-Value) cache requirements without sacrificing performance. Other architectural choices include RMSNorm for layer normalization, RoPE for positional encoding, and SwiGLU activation functions.

A notable departure from traditional LLM training is the use of the Muon optimizer. Muon uses matrix orthogonalization for Newton-style updates, which has been shown to improve sample efficiency and accelerate convergence compared to standard Adam-based optimizers. Furthermore, the model includes a lightweight, single-layer dense Multi-Token Prediction (MTP) head. This head serves a dual purpose: during training, it provides additional learning signals by predicting multiple subsequent tokens; during inference, it enables speculative decoding, allowing the model to verify and output multiple tokens in a single step, thereby increasing throughput.

## Large-Scale Data Curation and Pretraining

The foundation of JoyAI-LLM Flash is a pretraining corpus of $20.7\text{T}$ high-quality tokens. The data strategy was multi-pronged, focusing on web content, code, academic knowledge, and synthetic reasoning trajectories.

*   **Web and Code Data:** The team utilized frameworks like Datatrove for rule-based cleaning and MinHash-LSH for deduplication. Code data from sources like The Stack v2 was processed using language-specific dependency graphs to construct long-context sequences (up to $128\text{K}$ tokens).
*   **Academic Knowledge Extraction:** To capture complex STEM and medical knowledge, the researchers used DeepSeek-OCR and MinerU to extract text from millions of PDF documents, ensuring that hierarchical structures and mathematical formulas were preserved.
*   **Synthetic Reasoning and Agentic Data:** Synthetic data played a critical role in eliciting advanced reasoning. The team used advanced LLMs to reformulate factual knowledge into QA pairs and to generate agentic trajectories where models simulate interactions with environments. These trajectories were filtered through an LLM-based evaluator to ensure only high-quality, successful problem-solving paths were included.

The pretraining followed a phased strategy, moving from foundational learning to code-math enhancement, and finally to context extension, allowing the model to handle windows of up to $128\text{K}$ tokens.

## Post-Training and Tool-Integrated Reasoning

To align the model with human intent and enhance its autonomy, a rigorous post-training pipeline was implemented. This began with Supervised Fine-Tuning (SFT), where the model was exposed to diverse instruction-following data, including science, creative writing, and safety protocols.

A significant focus of SFT was Tool-Integrated Reasoning (TIR). By training on datasets that involve interacting with Python interpreters, search engines, and terminal environments, the model developed the ability to solve problems by executing code or searching for information. This is particularly relevant for Software Engineering (SWE) tasks, where the model must navigate GitHub issues, pull requests, and commits within a verifiable environment.

Following SFT, Direct Preference Optimization (DPO) was used to refine response quality. DPO contrasts high-quality "chosen" responses with rejection-sampled "rejected" examples, providing a signal that penalizes hallucinations and undesirable behaviors before the model undergoes large-scale Reinforcement Learning.

## Multi-Scale Stability with FiberPO

A central contribution of this work is the introduction of FiberPO, a novel Reinforcement Learning (RL) algorithm designed to address the instabilities often encountered during RLHF (Reinforcement Learning from Human Feedback). Traditional RL methods like PPO (Proximal Policy Optimization) can suffer from multi-scale instability: token-level stochasticity, trajectory-level drift, and system-level heterogeneity.

FiberPO is inspired by fiber bundle theory (fibration). It decomposes the trust-region maintenance—essentially the mechanism that prevents the model from diverging too far from its original state—into two components: a global trajectory-level base weight and a local token-level gated residual. 

Consider the importance ratio for a token $t$ in a trajectory:
$$r_t = \frac{\pi_\theta(a_t|s_t)}{\pi_{\text{old}}(a_t|s_t)}$$
In standard RL, this ratio is used to calculate the gradient. FiberPO factorizes this ratio so that it can control the trajectory-level drift $w_\tau^{\text{base}}$ independently of local token deviations. This prevents global preference biases (like a preference for longer or shorter answers) from overwhelming the learning signals at the token level. 

The global base weight is calculated as:
$$w_\tau^{\text{base}} = \exp\left(\frac{1}{T} \sum_{t=1}^T g^{\text{agg}}(\log r_t)\right)$$
where $g^{\text{agg}}$ is a piecewise gating function. By managing the ratio $\tilde{r}_t = r_t / w_\tau^{\text{base}}$, FiberPO maintains policy entropy (preventing the model from becoming too repetitive) and ensures stable, monotonic improvement in both training rewards and validation accuracy.

## Inference Optimization and Quantization

Efficiency in JoyAI-LLM Flash is not just architectural; it is also achieved through optimized deployment. The model supports various quantization formats to reduce memory footprint and increase speed.
*   **Quantization-Aware Training (QAT):** The model was trained with simulated INT4 precision to stabilize RL and ensure robustness during deployment.
*   **Low-Bit Formats:** The researchers evaluated the model using BF16, FP8, and a specialized W4AFP8 format. The FP8 variant achieved a $17\%$ throughput gain with negligible accuracy loss, while the W4AFP8 model provided a $28\%$ gain over the BF16 baseline.
*   **Speculative Decoding:** By utilizing the MTP head, the model achieved a speedup of $1.87\times$ on benchmarks. When combined with quantization, this speedup reached $1.96\times$ for certain configurations, demonstrating the synergy between structural efficiency and inference-time acceleration.

## Results and Token Efficiency

The primary evaluation of JoyAI-LLM Flash centered on its ability to match the performance of much larger models while using fewer tokens.

On **LiveCodeBench v6**, a challenging coding benchmark, JoyAI-LLM Flash achieved $65.6\%$ accuracy using an average of 7,300 tokens. In comparison, GLM-4.7-Flash-Thinking achieved $64.0\%$ accuracy but required 53,600 tokens—an $85\%$ reduction in token consumption for the Flash model. Similarly, on **MMLU-Pro**, the model matched the $81.6\%$ accuracy of Qwen3.5-35B-A3B while using $77\%$ fewer tokens (900 vs. 4,000).

![Token Efficiency Metrics](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03044v1/x12.png)
*Figure 2: Performance breakdown across math and reasoning benchmarks, highlighting the significant reduction in tokens required to reach state-of-the-art accuracy.*

These results indicate that the model's reasoning paths are more direct. Through the combination of FiberPO and rigorous agentic training, the model learns to solve complex problems with more concise "thinking" processes, directly translating to lower operational costs for end-users.

## Conclusion

JoyAI-LLM Flash demonstrates that mid-scale models in the sub-$50\text{B}$ parameter range can achieve top-tier performance by prioritizing token efficiency and architectural sparsity. By integrating a sparse MoE design with the novel FiberPO algorithm and extensive inference optimizations like MTP and QAT, the model offers a compelling alternative to larger, more computationally expensive systems. The release of the model checkpoints and quantization formats marks a contribution to the open-source community, providing a robust platform for further research into efficient LLM alignment and agentic autonomy.

## Relevant Citations

- Fibration policy optimization: This citation is paramount as it provides the complete theoretical foundation for FiberPO, the novel reinforcement learning algorithm that is a central contribution of the JoyAI-LLM Flash paper. The main paper introduces FiberPO and explicitly defers to this reference for the detailed derivations and proofs underpinning its multi-scale stability control.
- Deepseek-v3 technical report: The JoyAI-LLM Flash paper explicitly states its micro-architecture and Multi-Token Prediction (MTP) head draw direct inspiration from DeepSeek-V3. This makes the DeepSeek-V3 technical report a foundational reference for understanding the model's core architectural design and inference efficiency strategies.
- Kimi k2: Open agentic intelligence: This paper is cited as a key source of inspiration for the micro-architecture of JoyAI-LLM Flash, alongside DeepSeek-V3. It is also referenced for its use of the Muon optimizer, which the JoyAI-LLM paper adopts to enhance training stability and accelerate convergence, making it crucial for understanding the model's design and training process.
- Deepseekmath: Pushing the limits of mathematical reasoning in open language models: This paper introduced the GRPO algorithm, which is used as a primary baseline in the empirical evaluation of the novel FiberPO algorithm. The direct comparison and analysis of GRPO's failure modes serve to validate the structural advantages and superior performance of FiberPO, which is a core claim of the main paper.
