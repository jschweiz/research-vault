# Muon Dynamics as a Spectral Wasserstein Flow

- alphaXiv: https://www.alphaxiv.org/abs/2604.04891
- Source paper: https://arxiv.org/abs/2604.04891

Modern deep learning relies heavily on gradient normalization to stabilize the training of large-scale models. When parameters are grouped into matrices—such as the weights of a linear layer or the attention blocks in a transformer—these normalization schemes often take a "spectral" form, accounting for the underlying matrix geometry. A prominent example is the Muon optimizer, which uses a specific matrix-normalized gradient update to achieve faster convergence and better scaling properties compared to standard stochastic gradient descent.

While Muon and similar methods are empirically successful, their theoretical foundations have remained relatively unexplored. This research addresses this gap by introducing a mathematical framework that interprets these optimization dynamics as gradient flows in a new family of geometries known as Spectral Wasserstein distances. By viewing neural network parameters through a "mean-field" lens—where an arbitrarily large number of neurons are represented by a probability distribution—the study provides a unified geometric language for understanding how different normalization choices reshape the path to convergence.

![MMD trajectories](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04891v1/mmd_trajectories_three.png)
*Figure 1: Comparison of particle trajectories for MMD gradient flows using trace ($p=1$), Frobenius ($p=2$), and operator ($p=\infty$) Schatten norms. The operator norm flow, corresponding to Muon, exhibits globally coordinated particle movements.*

## The Spectral Wasserstein Distance

The classical quadratic Wasserstein distance, denoted as $W_2$, is a cornerstone of optimal transport. It measures the minimum effort required to transform one probability distribution into another by considering the sum of squared distances between individual points. Mathematically, it is defined as:

$$W_2(\mu, \nu)^2 = \inf_{\pi \in \Pi(\mu, \nu)} \int \|x-y\|^2 d\pi(x, y)$$

where $\mu$ and $\nu$ are probability measures, and $\pi$ is a "coupling" that describes how mass is moved from $x$ to $y$. 

The core contribution of this work is to generalize this concept by replacing the Euclidean distance with a cost function based on matrix norms. Specifically, the paper introduces the Spectral Wasserstein distance $W_\gamma$, defined as:

$$W_\gamma(\mu, \nu)^2 = \inf_{\pi \in \Pi(\mu, \nu)} \gamma\left( \int (x-y)(x-y)^T d\pi(x, y) \right)$$

In this definition, $\gamma$ is a norm acting on $d \times d$ positive semidefinite matrices. Instead of summing the squared distances, we compute the covariance matrix of the displacements $(x-y)$ and then measure the "size" of that covariance matrix using $\gamma$.

## Schatten Norms and Interpolation

The choice of the norm $\gamma$ allows the framework to cover a continuous range of geometries. The paper focuses on Schatten $p$-norms, denoted as $\gamma_p$, which act on the singular values of a matrix. Three cases are particularly important:

1.  **Trace Norm ($p=1$):** When $\gamma$ is the trace norm, $W_\gamma$ exactly recovers the classical $W_2$ distance. This is because the trace of the displacement covariance matrix is exactly the integral of $\|x-y\|^2$. This geometry corresponds to standard gradient descent.
2.  **Operator Norm ($p=\infty$):** This norm measures only the largest singular value of the covariance matrix. This choice corresponds to the Muon geometry, where gradients are normalized such that only the most significant directions of change are penalized.
3.  **Frobenius Norm ($p=2$):** This provides an interpolation between the local, point-wise focus of $W_2$ and the global, spectral focus of Muon.

By varying $p$, researchers can smoothly transition between standard optimization and the more coordinated, spectral updates used in modern practice.

## Robust Transport and Admissible Costs

A powerful way to understand $W_\gamma$ is through its "dual" representation. The paper proves that $W_\gamma$ can be viewed as a "robust" or "adversarial" version of optimal transport. For any norm $\gamma$, there exists a set of admissible cost matrices $K_\gamma$. The distance can be rewritten as:

$$W_\gamma(\mu, \nu)^2 = \max_{Q \in K_\gamma} W_Q(\mu, \nu)^2$$

In this formulation, $W_Q$ is a Mahalanobis-type Wasserstein distance where the cost of moving from $x$ to $y$ is weighted by a matrix $Q$, defined as $(x-y)^T Q (x-y)$. The Spectral Wasserstein distance effectively searches for the "worst-case" matrix $Q$ in the set $K_\gamma$ that maximizes the transportation cost.

This perspective reveals that Muon ($p=\infty$) is equivalent to finding the single direction in space along which the two distributions are hardest to align. Conversely, $W_2$ ($p=1$) assumes that all directions contribute equally to the total cost.

![Static matchings](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04891v1/static_matchings_three.png)
*Figure 2: Static optimal matchings between two point clouds for different Spectral Wasserstein geometries. As $p$ increases, the matching becomes less sensitive to individual outliers and more focused on the global alignment of the distributions.*

## From Static Metrics to Optimization Dynamics

While the static distance helps characterize the geometry, optimization is a dynamic process. The paper establishes a bridge between the static cost and the continuous evolution of parameters by proving an equivalence with the Benamou-Brenier formulation.

For certain norms (known as monotone norms), the distance between two measures is equal to the minimum "energy" required to flow from one to the other along a path $\mu_t$ with velocity $v_t$:

$$W_{BB}^\gamma(\mu_0, \mu_1)^2 = \inf_{(\mu_t, v_t)} \int_0^1 \gamma\left( \int v_t(x)v_t(x)^T d\mu_t(x) \right) dt$$

This energy integral is subject to the continuity equation, $\partial_t \mu_t + \nabla \cdot (\mu_t v_t) = 0$, which ensures mass is conserved. This result is significant because it allows us to define "Spectral Wasserstein Gradient Flows." These are the steepest-descent paths a distribution would take to minimize a functional (like a loss function) under the $W_\gamma$ metric.

## Finite-Particle Gradient Flows and Muon

In practice, we don't optimize continuous distributions; we optimize $n$ discrete particles (or neurons). The paper shows that the continuum spectral flow translates directly into a concrete update rule for a parameter matrix $X_t \in \mathbb{R}^{d \times n}$.

If we want to minimize a loss function $F_n(X_t)$, the "spectral" update rule is:

$$\dot{X}_t = - \Xi_p(\nabla F_n(X_t))$$

where $\Xi_p$ is a normalization operator that depends on the Schatten norm $p$. For a gradient matrix $G$, let its singular value decomposition be $G = U \text{diag}(\sigma) V^T$. The normalization is given by:

$$\Xi_p(G) = \frac{U \text{diag}(\sigma^{q-1}) V^T}{\|\sigma\|_q^{q-2}}$$

where $q$ is the conjugate exponent such that $1/p + 1/q = 1$.

-   **When $p=1$ (Standard GD):** The operator $\Xi_1$ is just a constant scaling, and we recover standard gradient descent.
-   **When $p=\infty$ (Muon):** The operator $\Xi_\infty$ performs a "whitening" operation, $G (G^T G)^{-1/2}$, effectively making all non-zero singular values equal to 1. This is exactly the core update used in the Muon optimizer.
-   **When $p=2$ (Frobenius):** The operator $\Xi_2$ simply divides the gradient by its Frobenius norm, $G / \|G\|_F$, which is a common form of global gradient clipping.

## Geodesic Convexity and Global Convergence

A major question in optimization is whether a local descent method will find a global minimum. In optimal transport, this is often linked to "geodesic convexity"—the idea that the loss function looks "bowl-shaped" along the shortest paths (geodesics) in the chosen geometry.

The paper analyzes when a functional $F(\mu)$ is convex relative to $W_\gamma$. For linear functionals of the form $F_h(\mu) = \int h(x) d\mu(x)$, the study finds that they are convex if and only if the underlying function $h$ is convex. More specifically, for a smooth function $h$, the condition for "curvature" $\kappa$ is:

$$\nabla^2 h(z) \succeq \kappa Q \text{ for all } Q \in K_\gamma$$

For the Muon geometry ($p=\infty$), this requirement is quite stringent: it implies that $h$ must be convex in every possible direction simultaneously. This provides a theoretical lens to evaluate how normalization affects the "flatness" or "sharpness" of the optimization landscape.

## Significance for Neural Networks

The researchers apply this framework to mean-field models of two-layer Multilayer Perceptrons (MLPs). In these models, neurons are often assumed to be "homogeneous"—meaning if you scale the weights, the output scales predictably.

The paper demonstrates that for such models, the Spectral Wasserstein flow in the high-dimensional weight space can be reduced to a specific type of "unbalanced transport" on the sphere $S^{d-1}$. This finding is significant because it suggests that Muon and its relatives are not just normalizing the size of the updates, but are fundamentally changing how the *directions* of the neurons evolve on the unit sphere. 

While classical $W_2$ flows on the sphere lead to the well-known Wasserstein-Fisher-Rao geometry, spectral flows lead to a new, broader class of spherical geometries that prioritize global alignment over individual neuron movement.

## Conclusion

By grounding spectral normalization in the theory of optimal transport, this work moves beyond heuristic explanations for optimizers like Muon. It establishes that these methods are not merely "tricks" to speed up training, but are the natural gradient flows associated with a rigorous family of matrix-aware metrics.

The Spectral Wasserstein framework provides a unified map of the optimization landscape, showing how different norms—from trace to operator—allow practitioners to choose between local, Euclidean updates and global, spectral updates. As neural networks continue to grow in complexity, these geometric insights offer a principled way to design and analyze the next generation of deep learning optimizers.

## Relevant Citations

- Muon: An optimizer for hidden layers in neural networks: This work introduces the Muon optimizer, which serves as the primary motivating application for the main paper. The paper's central goal is to provide a theoretical foundation for Muon and similar spectral normalization methods by framing them as gradient flows within a novel 'Spectral Wasserstein' geometry.
- On the global convergence of gradient descent for over-parameterized models using optimal transport: This paper is a key predecessor that established the connection between the mean-field limit of training neural networks and gradient flows in the classical Wasserstein space. The current paper builds directly upon this paradigm by replacing the standard Wasserstein geometry with its new family of Spectral Wasserstein geometries to account for matrix-based spectral normalizations.
- A computational fluid mechanics solution to the Monge–Kantorovich mass transfer problem: This is the foundational paper for the dynamic (fluid mechanical) formulation of optimal transport. The main paper heavily relies on and extends this framework in Section 3 to prove that its static Spectral Wasserstein cost is equivalent to a dynamic formulation, which is crucial for establishing that it is a genuine metric and for characterizing its geodesics.
- Subspace robust wasserstein distances: The main paper explicitly identifies this work as the 'closest antecedent' to its approach. Paty and Cuturi's work robustifies the Wasserstein distance by maximizing the transport cost over a family of projected quadratic costs, which is conceptually very similar to the max-min representation of the Spectral Wasserstein distance derived in Theorem 2.10.
