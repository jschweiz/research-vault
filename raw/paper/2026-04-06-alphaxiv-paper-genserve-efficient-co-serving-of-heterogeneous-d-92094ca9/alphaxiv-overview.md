# GENSERVE: Efficient Co-Serving of Heterogeneous Diffusion Model Workloads

- alphaXiv: https://www.alphaxiv.org/abs/2604.04335
- Source paper: https://arxiv.org/abs/2604.04335

The rapid evolution of generative AI has shifted focus from text-to-image (T2I) generation toward more computationally demanding tasks like text-to-video (T2V). While these models often share a common architecture—specifically the Diffusion Transformer (DiT) backbone—the resource requirements for serving them are vastly different. T2V requests often require an order of magnitude more computation and memory bandwidth than T2I requests. For example, generating a single $720p$ video can take up to $20\times$ longer than generating a high-resolution image.

When production clusters attempt to serve these heterogeneous workloads together, conventional scheduling policies often fall short. Simple First-In-First-Out (FIFO) scheduling leads to head-of-line (HOL) blocking, where a long-running video request traps numerous latency-sensitive image requests in the queue, causing them to miss their Service Level Objectives (SLOs). Conversely, prioritizing short jobs (SJF) can lead to the starvation of video tasks. GENSERVE is a co-serving system designed to navigate these trade-offs by exploiting the unique execution characteristics of diffusion models.

![Comparison of scheduling policies: FIFO vs. HeteroFusion (GENSERVE)](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04335v1/x1.png)
*Figure 1: Comparison between standard FIFO scheduling and GENSERVE (HeteroFusion). While FIFO suffers from head-of-line blocking, GENSERVE utilizes video preemption, batching, and dynamic parallelism to ensure all requests meet their deadlines.*

## The Challenge of Heterogeneous Diffusion Workloads

The transition from traditional U-Net architectures to Diffusion Transformers (DiTs) has unified the underlying mathematical framework for images and videos. As shown in Figure 2, both modalities follow an iterative denoising process where a latent tensor is refined over a fixed number of steps. Despite this architectural similarity, the serving requirements are highly asymmetric.

![Diffusion Transformer (DiT) inference pipeline](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04335v1/x2.png)
*Figure 2: The generic inference pipeline for DiT-based models. The iterative denoising loop (T to 0) allows for natural break points at each step.*

The fundamental problem in co-serving arises from three factors:
1.  **Latency Sensitivity**: Image requests typically have strict, sub-second or low-second latency targets to maintain user interactivity. Video requests, while allowing for longer turnaround times, still have deadlines that are difficult to hit if resources are fragmented.
2.  **Computational Intensity**: A $720p$ video denoising step is significantly more expensive than a $256p$ or $480p$ image step.
3.  **Resource Staticity**: Existing systems often fix the degree of parallelism (e.g., how many GPUs work on one video) and the batch size at startup. If the workload shifts from mostly images to mostly videos, these static configurations become highly inefficient.

## Leveraging Predictability and Preemptibility

Unlike Large Language Models (LLMs), where the runtime is unpredictable because the model might generate five words or five hundred, diffusion models are remarkably predictable. They perform a pre-defined number of denoising steps (e.g., 20 or 50 steps), and each step has a nearly identical execution time for a given resolution. This predictability allows a system to calculate the exact remaining time for any in-flight request.

GENSERVE also exploits the "step-level preemptibility" of these models. Because the inference is a loop of sequential steps, the system can pause a video task at the boundary of any step. The only state that needs to be preserved is the latent tensor. Unlike the KV cache in LLMs, which can grow to gigabytes, the latent tensor for even high-definition videos is relatively small (often tens of megabytes). This makes preemption—pausing a long video to let a quick image "sneak through"—extremely low-overhead.

## System Architecture

The GENSERVE architecture consists of a centralized control plane and a distributed data plane of GPU workers. The workflow is orchestrated by several key components:

*   **Profiler**: An offline component that measures the latency of different model operations across various resolutions, batch sizes, and degrees of Sequence Parallelism (SP). This data allows the system to predict the cost of future actions accurately.
*   **Scheduler & Solver**: The "brain" of the system. It maintains a global view of all pending requests and active GPU states. It uses a specialized algorithm to decide which tasks to run, which to batch, and which to preempt.
*   **Allocator & Controller**: These components translate the high-level scheduling decisions into low-level GPU commands, such as adjusting the NCCL communication groups for parallel tasks or dispatching new batches.

![GENSERVE System Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04335v1/x7.png)
*Figure 3: Overview of the GENSERVE system architecture, highlighting the interaction between the central scheduler, the profiler, and the GPU workers.*

## Intelligent Video Preemption and Elastic Allocation

One of GENSERVE’s core innovations is its approach to "Slack." Slack is defined as the difference between the request's deadline and its projected completion time:

$$ \text{Slack} = \text{Deadline} - (\text{CurrentTime} + \text{RemainingSteps} \times \text{Latency}_{\text{step}}) $$

When image requests start piling up, the system identifies video tasks with the most positive slack—these are the "safest victims." By preempting these videos, the system frees up GPUs to clear the image queue without causing the video tasks to miss their own deadlines. Once the image "burst" is handled, the videos are resumed.

### Elastic Sequence Parallelism (SP)
Sequence Parallelism splits the spatial or temporal dimensions of a tensor across multiple GPUs. GENSERVE implements *Elastic SP*, which allows a video's parallelism degree to change during execution. If the cluster is idle, a video might scale up to use 8 GPUs (SP=8) to finish faster. If a flurry of image requests arrives, the system can "downgrade" that video to SP=2, releasing 6 GPUs for image processing without stopping the video entirely.

### SLO-aware Batching
For image tasks, throughput is often improved by batching multiple requests together. However, batching increases the latency of each individual request in the batch. GENSERVE’s scheduler only forms a batch if every request in that batch is still projected to meet its deadline despite the increased processing time.

## The SLO-aware Joint Scheduler

The scheduler solves a optimization problem: how to allocate $N$ GPUs among $G$ video groups and a set of image requests to maximize the number of satisfied SLOs.

$$ \text{Maximize} \sum_{i \in \mathcal{R}} \mathbb{1}(\text{Completion}_i \leq \text{Deadline}_i) $$

To solve this in real-time (under 2ms), GENSERVE uses a Knapsack-style dynamic programming (DP) algorithm. It treats each video as a "group" and each possible allocation (preempt, continue at SP=2, scale to SP=4, etc.) as an "item" within that group. The DP algorithm finds the combination of choices across all videos that leaves the optimal amount of GPU resources for image batches, ensuring the maximum total number of requests (both image and video) hit their deadlines. The complexity of this solver is $O(G \cdot N \cdot \bar{K})$, where $\bar{K}$ is the average number of allocation candidates per video.

## Performance and Evaluation

GENSERVE was evaluated against several baselines, including FCFS and Shortest Remaining Time First (SRTF), using high-end NVIDIA GPUs and state-of-the-art models like Stable Diffusion 3.5 and Wan2.2.

### SLO Attainment
In scenarios with mixed image and video traffic, GENSERVE achieved an overall SLO Attainment Rate (SAR) of $78\%$, significantly outperforming SRTF ($71\%$) and FCFS ($59\%$). Notably, GENSERVE was able to maintain a $100\%$ success rate for image requests while still meeting the deadlines for $56\%$ of video requests—a task where SRTF failed by being too aggressive with preemptions.

![SLO Attainment across different scales](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04335v1/x10.png)
*Figure 4: SLO satisfaction rates across varying SLO strictness (represented by $\sigma$). GENSERVE consistently maintains a higher SAR than conventional scheduling policies.*

### Tail Latency Reduction
For image requests, GENSERVE reduced the $p90$ tail latency by $3.1\times$ compared to FCFS. By eliminating the head-of-line blocking caused by videos, the system ensures that image users receive their results with consistently low delay. For videos, the use of dynamic SP allowed the system to reduce the median turnaround time by $41\%$, as shown by the comparison between $52$ seconds (GENSERVE) and $89$ seconds (FCFS).

### Ablation and Robustness
The ablation study (Figure 5) demonstrates the necessity of each component. Adding simple preemption to a baseline FCFS system improves image performance but hurts video. The addition of the DP Solver recovers the video performance by making preemption "smarter," and Elastic SP provides the final boost by allowing for more granular resource adjustments.

![Ablation study of GENSERVE components](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04335v1/x14.png)
*Figure 5: Incremental performance gains from adding preemption, the DP scheduler, and elastic SP switching.*

The system also showed remarkable efficiency. The memory overhead for storing paused video states was found to be less than $27.2\text{ MB}$ per video, which is negligible on a $96\text{ GB}$ GPU. Furthermore, the time taken by the scheduler to make a decision was typically less than $0.5$ ms, ensuring that the system spends its time generating content rather than debating how to schedule it.

## Conclusion

GENSERVE addresses the growing complexity of serving modern generative models by treating T2I and T2V as a unified, heterogeneous resource management problem. By leveraging the inherent predictability and preemptibility of diffusion models, it moves away from static, modality-specific deployments toward a fluid, SLO-aware co-serving model. The result is a system that can handle the high-throughput demands of image generation while still reliably delivering high-quality video content on shared infrastructure. This approach not only improves user experience by hitting more deadlines but also maximizes the economic efficiency of expensive GPU clusters.

## Relevant Citations

- xdit: an inference engine for diffusion transformers (dits) with massive parallelism: This paper is a key baseline as GENSERVE is implemented using its sequence parallelism library (xFuser). GENSERVE directly addresses the limitations of xDiT's static parallelism and fixed scheduling strategies, which are shown to be inefficient for dynamic, mixed workloads of images and videos.
- Tetriserve: Efficiently serving mixed dit workloads: TetriServe is a direct conceptual predecessor that introduced step-level resource management and dynamic sequence parallelism for homogeneous diffusion model workloads. GENSERVE extends this core idea by developing coordinated preemption and scheduling mechanisms specifically for the challenges of co-serving heterogeneous text-to-image and text-to-video requests.
- Tridentserve: A stage-level serving system for diffusion pipelines: This work represents an alternative design for diffusion model serving that decomposes the pipeline into coarse-grained stages for resource allocation. It is a relevant citation because it contrasts with GENSERVE's finer-grained, step-level approach, which enables more agile scheduling decisions like preemption and dynamic batching within the main denoising loop.
- vllm-omni: Fully disaggregated serving for any-to-any multimodal models: This paper is cited as important related work in hybrid serving systems, focusing on disaggregating multimodal LLM pipelines. It is relevant because it tackles the general problem of serving heterogeneous models, but its approach is tailored to LLMs, highlighting the novelty of GENSERVE's techniques (e.g., step-level preemption) which are specifically designed by exploiting the unique predictable and iterative structure of diffusion models.
