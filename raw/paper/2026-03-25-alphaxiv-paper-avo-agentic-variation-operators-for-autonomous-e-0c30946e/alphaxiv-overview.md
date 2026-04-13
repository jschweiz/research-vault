# AVO: Agentic Variation Operators for Autonomous Evolutionary Search

- alphaXiv: https://www.alphaxiv.org/abs/2603.24517
- Source paper: https://arxiv.org/abs/2603.24517

## Autonomous Optimization via Agentic Variation

Traditional evolutionary search frameworks for code optimization typically rely on a fixed, algorithmic pipeline. In these systems, a host framework handles task management—such as sampling parent solutions and evaluating new candidates—while a Large Language Model (LLM) is used as a constrained "generator" within a single-turn workflow. While effective for basic programming tasks, this rigid "LLM-in-the-loop" structure often fails to address the deep, iterative engineering required for performance-critical targets, such as GPU kernels. Optimizing for modern hardware like the NVIDIA Blackwell architecture necessitates a sustained cycle of documentation review, profiling, debugging, and micro-architectural refinement.

![Evolutionary Search Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24517v1/x1.png)
*Figure 1: Comparison between classical evolutionary search (EVO) and Agentic Variation Operators (AVO). While classical EVO uses LLMs in a single-turn or fixed workflow, AVO elevates the LLM to an autonomous agent capable of multi-step planning, tool use, and iterative debugging.*

Agentic Variation Operators (AVO) represent a shift toward an "LLM-as-the-loop" paradigm. Instead of being confined to a single generation step, the LLM is integrated into an autonomous agent equipped with persistent memory and professional engineering tools. This allows the agent to act as a self-directed variation operator that can explore hundreds of optimization directions, interpret hardware-specific profiler feedback, and autonomously revise its implementation before committing a candidate to the population. This method has demonstrated the ability to discover attention kernels that surpass the performance of highly optimized, expert-engineered libraries like cuDNN and FlashAttention-4 on the NVIDIA B200 GPU.

## The AVO Framework and Methodology

The fundamental difference in AVO lies in the mathematical formulation of the variation process. In traditional LLM-augmented evolutionary search, the variation step is typically defined as a single function call:

$$
Vary(P_t) = \text{Generate}(\text{Sample}(P_t))
$$

Here, the framework selects parents from the current population $P_t$ and asks the LLM to generate a descendant. In contrast, AVO defines the variation step as a complete autonomous agent run:

$$
Vary(P_t) = \text{Agent}(P_t, K, f) \to (x_{t+1}, f(x_{t+1}))
$$

In this formulation, $P_t$ is the accumulated lineage of solutions:

$$
P_t = \{(x_1, f(x_1)), \dots, (x_t, f(x_t))\}
$$

where each $x_i$ is a candidate implementation and $f(x_i)$ is its corresponding score. The agent also has access to a domain-specific knowledge base $K$, which contains hardware specifications (e.g., NVIDIA Blackwell PTX ISA) and reference codebases. The scoring function $f$ evaluates both the numerical correctness and the hardware throughput of a solution. The scoring is n-dimensional, $f(x_i) = (f_1(x_i), \dots, f_n(x_i))$, representing performance across different test configurations $j$.

![AVO Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24517v1/x2.png)
*Figure 2: The AVO main agent loop and its interaction with the population $P_t$, knowledge base $K$, and scoring function $f$. A supervisor agent monitors for stagnation and intervenes to steer the exploration.*

The agent operates in a continuous loop. For each variation step, it performs internal iterations of planning, implementation, and evaluation. It can consult prior versions in $P_t$ to analyze why certain optimizations worked or failed. If a candidate fails a correctness check or shows a regression in throughput, the agent diagnoses the error using compiler output or profiling data and revises the code. Only once a candidate meets the performance and correctness criteria is it committed back to the persistent lineage. To prevent the search from getting stuck in local optima, a "Supervisor Agent" monitors the trajectory and provides high-level guidance if it detects stagnation over multiple attempts.

## Optimization of Attention Kernels on NVIDIA Blackwell

The effectiveness of AVO was evaluated by optimizing Multi-Head Attention (MHA) and Grouped-Query Attention (GQA) kernels on the NVIDIA Blackwell B200 GPU. Attention kernels are critical components of Transformer-based AI models, and their performance directly impacts the speed of large language model inference and training. These kernels are typically optimized by hand by hardware experts over several months.

The optimization space for these kernels is vast and involves managing registers, shared memory, and warp-level synchronization. For the AVO agent, the starting point was a seed implementation $x_0$. The agent's goal was to maximize the throughput (measured in TFLOPS) while maintaining strict numerical correctness against a reference implementation.

![MHA Performance Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24517v1/x3.png)
*Figure 3: Throughput results for Multi-Head Attention (MHA) on the B200 GPU. AVO-discovered kernels outperform both cuDNN and FlashAttention-4 (FA4) across various sequence lengths.*

The results indicate that AVO successfully discovered micro-architectural optimizations that human experts and existing automated tools had not combined. For causal attention, AVO achieved throughput gains of up to 3.5% over cuDNN and 10.5% over FlashAttention-4. The peak performance reached 1668 TFLOPS at BF16 precision.

## Transferability to Grouped-Query Attention

A significant test of an optimization's value is its generalizability. To assess this, the AVO agent was tasked with adapting the highly optimized MHA kernel it had evolved into a Grouped-Query Attention (GQA) kernel. GQA is a variant of attention used in models like Qwen3 to reduce memory bandwidth requirements by sharing Key and Value heads across multiple Query heads.

![GQA Performance Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24517v1/x4.png)
*Figure 4: Throughput for Grouped-Query Attention (GQA). The agent adapted the evolved MHA kernel to GQA in 30 minutes, achieving up to 7% gains over cuDNN.*

The agent completed this adaptation autonomously in approximately 30 minutes. The resulting GQA kernel outperformed both cuDNN and FlashAttention-4 baselines, with gains of up to 7.0% and 9.3% respectively. This demonstrates that the micro-architectural insights discovered by the agent—such as improved instruction scheduling and memory management—were not specific to the MHA layout but represented fundamental hardware-level improvements.

## Analysis of the Evolutionary Trajectory

The optimization process spanned seven days of continuous autonomous evolution. During this time, the agent explored over 500 internal candidate directions, resulting in 40 committed versions that improved the running best performance.

![Causal Evolution Trajectory](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24517v1/x5.png)
*Figure 5: The evolution trajectory for causal attention shows distinct jumps in performance corresponding to specific micro-architectural breakthroughs.*

The trajectory reveals that performance gains were not linear. Instead, the agent discovered major architectural changes that led to significant jumps in throughput, followed by periods of fine-tuning. Notable milestones included:
- $v8$: Introduction of QK-PV interleaving and bitmask causal masking.
- $v13$: Restructuring the softmax operation into a single pass.
- $v20$: Implementation of branchless accumulator rescaling.
- $v30$: Overlapping the correction and MMA pipelines.
- $v33$: Manual rebalancing of registers across different warp groups.

![Non-Causal Evolution Trajectory](https://paper-assets.alphaxiv.org/figures-normalized/figures/2603.24517v1/x6.png)
*Figure 6: The evolution trajectory for non-causal attention. While the initial versions showed rapid gains, later versions focused on cycle-level scheduling and resource allocation.*

The agent transitioned from coarse-grained algorithmic changes (like changing how masks are applied) in the early versions ($v1$ to $v20$) to fine-grained, cycle-level tuning (like register allocation) in the later stages ($v21$ to $v40$). This mimicry of a human expert's workflow—starting with the "big ideas" and ending with "squeezing out the last bits of performance"—highlights the sophisticated planning capabilities of the AVO agent.

## Deep Hardware-Level Reasoning: Case Studies

The performance gains achieved by AVO were the result of genuine hardware-level reasoning rather than simple code refactoring. Three specific optimizations found by the agent illustrate this depth:

### Branchless Accumulator Rescaling
In version $v19$ to $v20$, the agent identified a bottleneck in the online softmax algorithm. Traditional implementations use a conditional branch to decide whether to rescale the output accumulator. This branch causes warp divergence and requires heavy synchronization. The agent replaced this with a branchless "speculative" path where the rescale factor is always calculated, and a predicate is used to select the value. This change allowed for a lighter, non-blocking memory fence, resulting in a 8.1% geomean throughput increase for non-causal attention.

### Correction and MMA Pipeline Overlap
Between $v29$ and $v30$, the agent analyzed the dual-stage attention pipeline. It noticed that the "correction" warps (responsible for normalization) were idling while waiting for the second Matrix-Multiply-Accumulate (MMA) stage to finish. The agent restructured the code to allow the correction warps to begin processing the results of the first stage immediately, overlapping their work with the ongoing second MMA stage. This improved throughput by approximately 1.1%.

### Register Rebalancing
In version $v33$, the agent diagnosed a "spilling" issue. Some warps were running out of their allocated registers, causing data to be swapped to slow local memory, while other warps had unused capacity. The agent manually redistributed the register budget—taking 8 registers from the underutilized softmax group and giving them to the critical correction group. This rebalancing (shifting from an allocation of 192/80/48 to 184/88/56) removed the bottleneck and increased performance by 2.1%.

## Significance of the AVO Approach

The development of Agentic Variation Operators signifies a shift in how AI can be used for software engineering. By providing an LLM with the autonomy to act as an agent—complete with tools, memory, and a feedback loop—the search process moves from simple "code generation" to "autonomous engineering."

The ability to surpass expert-tuned libraries in a domain as competitive as GPU kernels suggests that the bottleneck in many optimization tasks is not a lack of hardware knowledge, but the human bandwidth required to iteratively test and refine hundreds of micro-architectural hypotheses. AVO provides a scalable way to automate this process, enabling continuous, 24/7 optimization that can keep pace with the rapid evolution of AI hardware architectures. This framework is not limited to attention kernels and could potentially be applied to a wide range of performance-critical software systems across different hardware platforms.

## Relevant Citations

- Mathematical discoveries from program search with large language models: This paper introduces FunSearch, a flagship system for evolutionary search using large language models. The AVO paper frequently cites and contrasts its agentic approach with FunSearch's 'LLM-in-the-loop' pipeline, where the LLM is confined to a fixed candidate generation step, making this a foundational work that highlights the limitations AVO aims to overcome.
- Alphaevolve: A coding agent for scientific and algorithmic discovery: Similar to FunSearch, AlphaEvolve is presented as a key example of prior art in LLM-augmented evolutionary search. The AVO paper explicitly uses it to illustrate the standard, rigid framework of sampling, generation, and evaluation that its own autonomous agent-based variation operator replaces, making it a critical point of comparison for AVO's novel methodology.
- Flashattention: Fast and memory-efficient exact attention with io-awareness: This paper introduced the highly efficient, I/O-aware attention algorithm that became the standard for high-performance implementations. It establishes the fundamental problem domain and algorithmic context for the AVO paper's experiments, as AVO's goal is to autonomously discover further optimizations on top of this already advanced foundation.
- Flashattention-4: Algorithm and kernel pipelining co-design for asymmetric hardware scaling: This paper presents the latest version of FlashAttention, specifically optimized for the NVIDIA Blackwell architecture used in the AVO study. It serves as the primary state-of-the-art performance baseline, and outperforming this expert-engineered kernel is the main empirical result used to demonstrate the effectiveness of the AVO approach.
