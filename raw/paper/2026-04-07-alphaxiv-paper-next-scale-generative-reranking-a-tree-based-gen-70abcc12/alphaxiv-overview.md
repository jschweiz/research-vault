# Next-Scale Generative Reranking: A Tree-based Generative Rerank Method at Meituan

- alphaXiv: https://www.alphaxiv.org/abs/2604.05314
- Source paper: https://arxiv.org/abs/2604.05314

In the architecture of modern recommendation systems, providing a personalized experience to millions of users involves a sophisticated multi-stage pipeline. This "funnel" typically begins with a matching stage to retrieve a few thousand items, followed by a ranking stage that scores these items individually. The final, and arguably most critical, stage is reranking.

Reranking determines the final order of items presented to a user, considering not just the individual relevance of an item, but the mutual influences between items in the list and the impact of their specific positions. While traditional ranking models treat each item as an independent entity, reranking models analyze the list as a whole to maximize total utility, such as the total click-through rate (CTR) or gross merchandise value (GMV).

![Reranking Paradigms Comparison](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.05314v1/x1.png)
*Figure 1: Comparison of different generative reranking paradigms, highlighting the transition from sequential and one-step methods to the proposed tree-based hierarchical approach.*

Despite its importance, reranking faces a massive computational challenge: the combinatorial explosion of possible item permutations. For a list of 20 items, there are $20!$ (over 2 quintillion) possible orderings. Evaluating every single one in real-time is impossible. To navigate this, researchers have developed various generative paradigms, each with its own set of trade-offs between local detail and global perspective.

## The Challenges of Existing Reranking Paradigms

Current generative reranking methods generally follow one of three patterns:

1.  **Autoregressive paradigm:** Items are generated one by one. While this captures local interactions between adjacent items, it often lacks a global view of the entire list and is computationally slow because each step depends on the previous one.
2.  **One-step paradigm:** All positions in the list are determined simultaneously. This provides a global perspective and is fast, but it often struggles to capture the fine-grained, local interactions between specific items.
3.  **Multi-step paradigm:** This starts with an initial list and iteratively swaps items to find a better configuration. However, these methods can easily get stuck in "local optima," where a single swap might seem bad even if a series of swaps would lead to a much better list.

Furthermore, these methods often suffer from **goal inconsistency**. In a typical setup, a *generator* creates a list, and an *evaluator* scores it. The generator tries to find the best list, while the evaluator is trained to predict the utility of any given list. If the evaluator's feedback doesn't perfectly align with the generator's optimization goal, the system fails to reach its full potential.

## Introducing Next-Scale Generative Reranking (NSGR)

The NSGR framework addresses these limitations by introducing a tree-based, coarse-to-fine generative process. Instead of deciding positions one by one or all at once, it generates the list through a series of hierarchical splits. This structure allows the model to maintain a global context at the higher levels of the tree while refining local details at the lower levels.

The system consists of two primary modules: the **Multi-Scale Evaluator (MSE)** and the **Next-Scale Generator (NSG)**.

## The Multi-Scale Evaluator (MSE)

The role of the MSE is to accurately estimate the utility of a given list by looking at item interactions across different scales. To do this, it first extracts a user's global interests from their lifelong behavior history $H_u$, resulting in a semantic interest embedding $e_u$.

For each item in a candidate list $L_s$, the evaluator creates a semantic representation $x_{s_i}$ that combines item features, the user's recent short-term history, and their long-term global interest. To capture context, the MSE uses multiple self-attention layers that operate at different granularities—ranging from the full list to small neighboring pairs. For a list of size $m$, it captures $K = \log_2(m)$ scales of context.

The evaluator then predicts a position-aware CTR $\hat{y}_t$ for each item at position $t$ using its semantic embedding, its multi-scale context $x_{c_t}$, and a positional embedding $e_{p_t}$:

$$\hat{y}_L = \sum_{t=1}^m \text{MLP}(x_{s_t}, x_{c_t}, e_{p_t})$$

By summing these predictions, the MSE calculates the total list-wise value $\hat{y}_L$.

## The Next-Scale Generator (NSG)

The NSG produces the optimal list through a hierarchical expansion process, often described as a "one-generates-two, two-generates-four" pattern. At each step $k$, the model looks at a subset of items $S^{(k)}_{l:r}$ and decides how to split them into two smaller child subsets.

This decision is informed by three key factors:
*   **Item Priority:** A score $p^{(k)}_i$ indicating an item's individual relevance.
*   **Pairwise Relationships:** A classification of how two items interact (e.g., do they enhance each other or does one suppress the other?).
*   **Tree-to-Item Attention:** An anchor vector $\tilde{g}^{(k)}$ that provides global context from previous tree nodes, helping the model decide which items belong in the "front" half of the list versus the "back" half.

This recursive splitting continues until the final ranked list is formed. This hierarchical approach ensures that the generator always has access to both the broader context of the subset it is working with and the specific features of the items it is organizing.

## Solving Goal Inconsistency with Multi-Scale Neighbor Loss

The most significant technical hurdle in generative reranking is ensuring the generator actually listens to the evaluator's "advice." To solve this, NSGR introduces the **Multi-Scale Neighbor Loss (MSNL)**.

During training, the system doesn't just evaluate the list produced by the generator $L_g$. It also constructs several "neighboring" lists $L_o$ by swapping items within the generated list. The evaluator scores both the generated list ($r_g$) and the neighbors ($r_o$).

If a neighbor list has a higher utility than the generated list ($r_o > r_g$), the loss function "pulls" the generator's internal representations $g^{(k)}_o$ closer to the evaluator's context representations $e^{(k)}_o$. If the generated list is better, it "pushes" them away. This guidance happens at every scale of the tree structure:

$$L_G = -\sum_{o=1}^O \text{sign}(r_o - r_g) \exp\left(\frac{|r_o - r_g|}{\tau}\right) \sum_{k=1}^K \cos(g^{(k)}_o, e^{(k)}_o)$$

This scale-specific feedback provides the generator with a clear signal on how to improve the list structure at both coarse and fine levels.

## Experimental Results and Performance

The NSGR framework was tested on both public (Taobao Ad) and large-scale industrial (Meituan) datasets. In offline tests, it consistently outperformed existing reranking methods. On the Meituan dataset, it achieved an AUC (Area Under the Curve) of 0.8902, a significant improvement over standard evaluators.

In terms of generation quality, the model's "Hit Ratio" (how often it produces lists close to the theoretical optimum) was remarkably high. In a controlled test with 8 items—where the optimal list can be found by checking all 40,320 permutations—NSGR produced lists that were 97.8% as good as the absolute best possible ordering.

## Real-World Deployment at Meituan

The true test of such a system is its performance in a live production environment. NSGR was deployed on Meituan’s food delivery platform, serving real users.

When reranking a small set of 8 items, the gains were modest. However, when the candidate set was expanded to 20 items—where the combinatorial complexity is far greater—the advantages of the tree-based approach became evident. The online A/B tests showed:
*   **+2.89%** increase in Click-Through Rate (CTR)
*   **+0.58%** increase in Conversion Rate (CVR)
*   **+3.15%** increase in Gross Merchandise Value (GMV)

Crucially, these improvements were achieved with a slight reduction in computational latency compared to existing production baselines, proving that the hierarchical generation method is both effective and efficient enough for high-traffic industrial use.

## Conclusion

The Next-Scale Generative Reranking method provides a structured way to handle the complexity of list optimization in recommendation systems. By moving away from sequential generation and adopting a hierarchical, tree-based approach, it successfully balances global and local perspectives. Furthermore, by introducing a multi-scale loss function that aligns the generator and evaluator, it overcomes the goal inconsistency problem that has hampered previous generative models. Its successful deployment at Meituan demonstrates its potential for improving user experience and business outcomes in large-scale e-commerce and delivery platforms.

## Relevant Citations

- NLGR: Utilizing Neighbor Lists for Generative Rerank in Personalized Recommendation Systems: This paper is a direct and cited inspiration for the proposed multi-scale neighbor loss (MSNL), which is a core technical contribution of the NSGR framework designed to address the goal inconsistency between the generator and evaluator. NLGR is also used as a key baseline representing the multi-step generation paradigm.
- You Only Evaluate Once: A Tree-based Rerank Method at Meituan: The YOLOR model from this paper is the main state-of-the-art baseline used for the crucial online A/B testing, making it the primary point of comparison to demonstrate NSGR's real-world effectiveness. Its tree-based approach provides important context for NSGR's own architecture, showing an evolution of tree-based methods at Meituan.
- GRN: Generative Rerank Network for Context-wise Recommendation: This work is presented as a foundational example of the two-stage generative reranking framework and specifically represents the autoregressive paradigm. The authors of the main paper critique the limitations of this paradigm, and GRN serves as a significant baseline in the experiments to prove the superiority of their proposed next-scale approach.
- Non-autoregressive generative models for reranking recommendation: This paper, which introduces NAR4Rec, is used as a baseline to represent the one-step generative paradigm. The main paper contrasts its next-scale approach against the overly coarse generation process of one-step models, making this citation essential for understanding the specific trade-offs NSGR aims to resolve.
