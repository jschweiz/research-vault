# Test-Time Scaling Makes Overtraining Compute-Optimal

- alphaXiv: https://www.alphaxiv.org/abs/2604.01411
- Source paper: https://arxiv.org/abs/2604.01411

## The Convergence of Pretraining and Test-Time Scaling

The development of large language models (LLMs) has historically been governed by two distinct sets of "scaling laws." On one side, pretraining scaling laws—most notably the Chinchilla laws—prescribe how to balance model size and the amount of training data to achieve the lowest possible loss for a given training budget. On the other side, test-time scaling strategies focus on how to allocate computational resources during deployment, often by generating multiple candidate responses and selecting the best one to improve performance on difficult tasks.

![Train-to-Test (T2) scaling framework](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01411v1/x1.png)
*Figure 1: The Train-to-Test ($T^2$) scaling framework unifies pretraining compute (Chinchilla) and inference compute (Pass@k) to find a global optimum for model development.*

This research identifies a significant disconnect between these two phases. Traditional pretraining laws optimize for a "single-pass" scenario, where the model generates exactly one response. However, modern high-stakes applications frequently use repeated sampling, where the cost of inference scales linearly with both the model's size and the number of samples taken. This work introduces "Train-to-Test" ($T^2$) scaling laws, a unified framework that jointly optimizes model size $N$, training data $D$, and the number of inference samples $k$. The primary finding is that when a test-time budget is factored into the initial training plan, the "compute-optimal" strategy shifts significantly: it becomes more efficient to train smaller models for much longer than previously recommended—a state known as "overtraining."

## Bridging the Pretraining-Inference Gap

The motivation for this study stems from the practical reality of LLM deployment. Existing scaling laws like Chinchilla assume the goal is to minimize the final pretraining loss. This results in a "rule of thumb" where models are trained on roughly 20 tokens per parameter. However, many successful models in the industry, such as Llama-3 or Gemma, are trained on far more data than this ratio suggests. These models are deliberately overtrained to make them more capable for their size, thereby reducing the per-query cost during inference.

While practitioners intuitively understood this trade-off, there was no formal mathematical framework to quantify it. Specifically, the benefit of taking multiple samples—often measured by the $\text{pass@k}$ metric—is non-linear. A model that is slightly better on a per-sample basis might require significantly fewer samples to reach a target accuracy, or it might achieve a much higher accuracy for the same number of samples. By ignoring this interaction, traditional scaling laws provide an incomplete picture of the total cost of ownership for an AI system.

## The Train-to-Test ($T^2$) Framework

The authors propose two mathematical approaches to unify these costs. Both approaches assume a total compute budget that considers training cost $C_{\text{train}} = 6ND$ and inference cost $C_{\text{inf}} = 2Nk$.

### Approach 1: Parametric Model of Task Loss
This approach extends the standard Chinchilla power law. The original Chinchilla law is defined as:

$$L(N, D) = E + A N^{-\alpha} + B D^{-\beta}$$

Where $E$ is the irreducible loss, and the other terms represent the reducible loss as parameters $N$ and tokens $D$ increase. The $T^2$ version adds a third term to account for the number of samples $k$:

$$L(N, D, k) = E + A N^{-\alpha} + B D^{-\beta} + G k^{-\gamma}$$

To make this compatible with standard evaluation metrics, the authors define a negative log-likelihood (NLL) based on the probability of success. If $p_i$ is the probability the model solves problem $i$ in one try, the NLL for $\text{pass@k}$ is:

$$\mathbb{E}_{i \sim \mathcal{D}_{\text{task}}} [-\log(1 - (1 - p_i)^k)]$$

This formula captures how the "loss" on a task decreases as more samples are taken.

### Approach 2: Parametric Model of Task Accuracy
While Approach 1 is mathematically elegant, practitioners often care more about direct accuracy. However, simply using the average accuracy is misleading because $\text{pass@k}$ is a concave function—the benefit of more samples depends on how hard individual questions are. 

To solve this, the authors model the distribution of per-question accuracies using a Beta distribution, $\text{Beta}(a_{N,D}, b_{N,D})$. They then relate the parameters of this distribution to the Chinchilla loss. Specifically, they model the mean $\mu_{N,D}$ and the "sample size" $\nu_{N,D}$ (which controls the variance) as functions of the pretraining loss. The final accuracy for $k$ samples is then derived from the properties of the Beta function:

$$\text{Acc}(N, D, k) = 1 - \frac{B(a_{N,D}, b_{N,D} + k)}{B(a_{N,D}, b_{N,D})}$$

This allows the framework to predict exactly how much accuracy will improve if you change the model size or the number of samples.

## Why Overtraining Becomes the Optimal Strategy

The most significant finding of the $T^2$ laws is that the optimal "recipe" for a model changes when you know it will be used with repeated sampling. In the standard Chinchilla regime, the number of tokens per parameter stays relatively constant as you increase the compute budget. Under $T^2$ scaling, the optimal model size $N$ grows much more slowly, while the number of training tokens $D$ and the tokens-per-parameter ratio increase dramatically.

![Scaling optimal N and D](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01411v1/x2.png)
*Figure 2: Optimal parameters ($N$), tokens ($D$), and the tokens-per-parameter ratio as a function of compute. $T^2$ models (red and blue) favor much smaller models trained on far more data than Chinchilla (black).*

The reason for this shift is the "inference correction." For a fixed inference budget $C_{\text{inf}}$, a smaller model can afford more samples $k$ because each sample is cheaper. Specifically, the relationship is $k = \frac{C_{\text{inf}}}{2N}$. When this is substituted into the $T^2$ equations, the math reveals that it is often better to have a smaller, "smarter" (overtrained) model that can take many shots at a problem, rather than a larger model that only gets one or two shots. 

For example, at high compute levels ($10^{25}$ FLOPs), Chinchilla might recommend a massive model. In contrast, $T^2$ scaling suggests that the optimal model might be orders of magnitude smaller but trained on an enormous amount of data to maximize its per-sample efficiency.

## Empirical Validation and Extrapolation

To ensure these mathematical models aren't just theoretical artifacts, the authors conducted extensive experiments. They utilized a testbed of over 100 model checkpoints, including 21 new "overtrained" checkpoints specifically created for this study. These models ranged from 5 million to 901 million parameters and were evaluated on eight diverse tasks, including reasoning, knowledge recall, and linguistic benchmarks.

The results confirmed that $T^2$ scaling laws accurately predict the performance of overtrained models. When the models were fitted on standard Chinchilla-style checkpoints and used to predict the performance of the new overtrained checkpoints, the error rate was remarkably low (2.8% for Approach 1 and 8.4% for Approach 2). 

![Extrapolation to overtrained checkpoints](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.01411v1/x4.png)
*Figure 3: $T^2$ scaling laws accurately predict the performance (NLL and Accuracy) of overtrained checkpoints (green dots) even when trained mostly on standard checkpoints (gray dots).*

In head-to-head comparisons at a fixed total budget, the $T^2$-optimal models consistently outperformed Chinchilla-optimal models. For instance, on the LAMBADA task, an overtrained 37M parameter model achieved nearly double the accuracy of a 455M parameter Chinchilla-optimal model when both were given the same inference budget.

## Stability Through Post-Training

A common question in scaling research is whether the patterns observed in base models hold after they undergo fine-tuning or other post-training refinements. To address this, the authors applied both standard fine-tuning (FT) and supervised fine-tuning (SFT) to three real-world benchmarks (ARC-Easy, SciQ, and OpenBookQA).

The findings showed that the $T^2$ scaling laws are resilient. While fine-tuning generally shifts the performance curves upward (improving accuracy for everyone), the *relative* benefit of overtraining remains the same. The optimal strategy still favors smaller, overtrained models that leverage repeated sampling. Interestingly, the degree of optimal overtraining was slightly less aggressive for fine-tuned models compared to base models, suggesting that while overtrained models are more efficient for inference, they may be slightly less flexible during the fine-tuning process. However, this effect was minor and did not change the overall conclusion: overtraining remains the compute-optimal path for systems using test-time scaling.

## Practical Guidance for Model Developers

This research provides a concrete roadmap for organizations developing LLMs. The traditional approach of training a model until it reaches a "compute-optimal" point on a loss curve is only optimal if that model is used for a single generation. If the intended use case involves techniques like self-consistency, majority voting, or best-of-$k$ sampling, the training strategy must change.

1.  **Plan for the inference budget:** Before starting pretraining, developers should estimate the expected inference load and the test-time scaling strategy.
2.  **Shift toward overtraining:** If repeated sampling is planned, resources should be shifted from making the model larger to training a smaller model on more data. This makes each inference step cheaper, allowing for more samples within the same budget.
3.  **Use $T^2$ to find the "sweet spot":** The provided formulas can help identify the exact parameter count and token count that will maximize accuracy for a given combined training and inference budget.

By unifying these two previously separate fields of research, the $T^2$ framework offers a more realistic and economically sound approach to scaling AI. It validates the current industry trend toward smaller, highly-capable models and provides the mathematical foundation needed to refine these strategies for the next generation of LLMs.

## Relevant Citations

- Training compute-optimal large language models: This paper introduced the 'Chinchilla' scaling laws, which are the primary point of comparison and the foundation that the main paper seeks to modernize. The T2 scaling laws are presented as a direct extension to Chinchilla, incorporating test-time inference costs that Hoffmann et al. did not consider.
- Scaling laws for neural language models: This is the foundational paper that established the existence of predictable power-law scaling in language models, creating the research field that the main paper operates in. The concepts introduced here are the bedrock upon which Chinchilla and, subsequently, the T2 scaling laws are built.
- Scaling llm test-time compute optimally can be more effective than scaling model parameters: This work provides the empirical motivation for the main paper's research by showing that increasing inference-time compute for smaller models can outperform larger models. The main paper formalizes this trade-off into a predictive scaling law that jointly optimizes training and inference.
- Beyond chinchilla-optimal: Accounting for inference in language model scaling laws: This is a direct and important predecessor that first attempted to integrate inference costs into pretraining scaling laws. The main paper explicitly builds on and extends this work by considering the more complex scenario of repeated sampling (pass@k) instead of just single-pass serving volume.
