# Hierarchical Planning with Latent World Models

- alphaXiv: https://www.alphaxiv.org/abs/2604.03208
- Source paper: https://arxiv.org/abs/2604.03208

In the field of robotics and embodied artificial intelligence, the ability to plan actions over long periods remains a core objective. One effective method for achieving this is through "world models," which are internal simulations that allow an agent to predict the outcomes of its actions. By "imagining" future states, an agent can select the best sequence of movements to reach a goal. However, these models often face two major hurdles: prediction errors that accumulate over time (compounding errors) and the overwhelming number of possible action sequences to explore as the planning time increases (the search space problem).

The research paper "Hierarchical Planning with Latent World Models" introduces a framework called HWM to address these issues. Instead of planning a single, long sequence of fine-grained actions, HWM utilizes a temporal hierarchy. A high-level planner identifies a sequence of "macro-actions" to set intermediate subgoals, while a low-level planner finds the specific motor commands to reach those subgoals. Crucially, HWM operates entirely within a learned "latent space"—a compressed numerical representation of the environment—rather than directly on raw pixels. This approach allows the system to achieve long-horizon control on real robots and in complex simulations without requiring task-specific training or human-defined rewards.

![HWM Success Rate and Planning Efficiency](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03208v1/x6.png)
*Figure 1: Comparison between Hierarchical World Models (HWM) and standard Flat World Models. HWM consistently achieves higher success rates across different tasks (Franka, Maze, Push-T) while requiring significantly less computation time per plan.*

## The Challenges of Long-Horizon Control

Planning over extended periods is difficult because every small error in a world model's prediction becomes the starting point for the next prediction. After dozens of steps, the model’s "imagination" might drift so far from reality that the plan becomes useless. This is known as compounding error. In high-dimensional environments, such as those where a robot perceives the world through a camera, these errors are even more pronounced.

Furthermore, if a robot needs to plan 100 steps ahead and has 10 possible actions at each step, the total number of paths to evaluate is $10^{100}$. This exponential growth makes it impossible to find an optimal path using standard search techniques. Traditional "flat" planners try to solve this by looking ahead only a short distance, but this "greedy" behavior often fails in tasks requiring non-greedy actions. For instance, to open a drawer, a robot might first have to move its arm *away* from the drawer handle to get a better grip—an action that a greedy planner, focused only on getting closer to the handle, might never choose.

## Hierarchical Latent World Models

HWM overcomes these challenges by splitting the planning process into two distinct temporal scales. Both scales operate in a shared latent space created by an encoder $E$ that translates raw observations $s_t$ (like images) into compact latent states $z_t$.

1.  **Low-Level Model ($P^{(1)}$):** This model is responsible for short-term, fine-grained transitions. It predicts the next latent state $p(z_{t+1} | z_t, a_t)$ given the current state and a primitive action (like a small motor command). It is highly accurate over short distances but prone to drift over long sequences.
2.  **High-Level Model ($P^{(2)}$):** Instead of primitive actions, this model uses "latent macro-actions" $l_{t_k}$. It predicts where the agent will be several steps in the future, effectively jumping over many low-level steps at once. This reduces the number of prediction steps needed to reach a distant goal, thereby mitigating compounding errors.

By using these two models together, HWM can "think" globally while "acting" locally.

## Latent Macro-Actions

A key contribution of this work is the method for representing high-level actions. Standard hierarchical methods often use simple "delta-poses" (e.g., the change in position between two points) as macro-actions. However, the authors argue that these simple representations are insufficient for complex tasks like grasping or navigating around obstacles.

HWM instead learns a dedicated action encoder $A_{\psi}$ during the training phase. This encoder takes a sequence of raw actions $a_{t_k:t_{k+1}}$ from offline datasets and compresses them into a fixed-length latent macro-action $l_{t_k}$. The high-level world model $P^{(2)}_{\phi}$ is then trained to predict the next waypoint representation $\hat{z}_{t_{k+1}}$ based on these learned macro-actions and the history of previous states $(l_{t_i}, z_t{_i})_{i \leq k}$.

![High-Level World Model Architecture](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03208v1/x7.png)
*Figure 2: The architecture of the High-Level World Model. An action encoder compresses a sequence of primitive actions into a latent macro-action, which the high-level model then uses to predict future waypoints in the latent space.*

Using learned latent actions allows the high-level planner to reason about complex behaviors. For example, a single macro-action might represent the entire process of "approaching and grasping a cup," which the high-level planner can treat as a single step toward the goal of "moving the cup to the box."

## The Hierarchical Planning Strategy

HWM performs planning at inference time using a top-down strategy. When given a current observation $s_1$ and a goal image $s_g$, the process follows these steps:

1.  **Goal Encoding:** Both images are converted into latent states $z_1 = E(s_1)$ and $z_g = E(s_g)$.
2.  **High-Level Plan Optimization:** A high-level planner (using algorithms like CEM or MPPI) searches for a sequence of $H$ macro-actions $\hat{l}_{1:H}$ that minimizes the distance between the predicted final state and the goal. This is defined by a high-level energy function:
    $$E_2(\hat{l}_{1:H}; z_1, z_g) \triangleq \|z_g - P^{(2)}(\hat{l}_{1:H}; z_1)\|_1$$
3.  **Subgoal Selection:** The first predicted state from this high-level sequence is extracted and used as an immediate latent subgoal $\tilde{z}_1$.
4.  **Low-Level Plan Optimization:** The low-level planner then finds a short sequence of $h$ primitive actions $\hat{a}_{1:h}$ to reach this subgoal by minimizing:
    $$E_1(\hat{a}_{1:h}; z_1, \tilde{z}_1) \triangleq \|\tilde{z}_1 - P^{(1)}(\hat{a}_{1:h}; z_1)\|_1$$
5.  **Execution and Re-planning:** The robot executes the first action of the low-level plan. Every $k$ steps, the entire hierarchy is re-evaluated to adjust for any unexpected changes in the environment.

## Performance on Real-World and Simulated Tasks

The researchers tested HWM across three distinct environments, each designed to highlight different aspects of long-horizon reasoning.

### Real-Robot Manipulation (Franka Arm)
The most significant result was the robot's ability to perform "non-greedy" tasks. In the "pick-and-place" task, the robot had to pick up a cup and place it on a box. A standard flat planner would often get stuck because it only tries to move toward the box directly, failing to realize it must first move to pick up the cup. HWM, however, achieved a 70% success rate on this task. It also succeeded in a drawer-opening task (70% success) where it correctly planned to approach the handle, grasp it, and pull—all from a single goal image and no prior task-specific instructions.

### Complex Object Manipulation (Push-T)
In the Push-T task, a robot must push a T-shaped object into a specific location and orientation. This requires long-term planning, as the object can only be moved in certain ways. As the difficulty of the task increased (longer horizons), the performance of flat planners dropped significantly. At a horizon of $d=75$ steps, HWM maintained a 61% success rate, while the flat planner dropped to 17%.

![Push-T Subgoals](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03208v1/x11.png)
*Figure 3: Visualization of subgoals in the Push-T environment. The hierarchical planner sets intermediate subgoals (red dashed boxes) that guide the agent toward the final T-shape goal (solid red box), enabling completion of long-horizon sequences.*

### Navigation (Diverse Maze)
The framework was also tested in a point-maze navigation task. HWM successfully navigated mazes that were larger and more complex than those seen during training. In the hardest mazes, HWM achieved an 83% success rate, nearly doubling the 44% success rate of the flat planner.

![Maze Navigation Trajectories](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.03208v1/x16.png)
*Figure 4: Point-maze navigation trajectories. The high-level planner (pink) provides a coarse path, while the flat planner (mint) often fails to navigate the complex turns required to reach the goal (star).*

## Efficiency and Modularity

Beyond improving success rates, HWM is notably more efficient. Because the high-level planner reduces the effective search horizon, the system requires less total computation at inference time. In the Maze and Push-T tasks, HWM achieved better results while using 3 to 4 times less compute than the flat baseline.

HWM is also designed to be model-agnostic. The authors demonstrated this by successfully integrating the HWM abstraction with three different state-of-the-art world model architectures (VJEPA2-AC, DINO-WM, and PLDM). In each case, adding the hierarchical layer improved the model's ability to handle long-term tasks without changing the underlying training objective of the base model.

## Conclusion

Hierarchical Planning with Latent World Models (HWM) addresses the fundamental scalability issues of planning in learned world models. By combining high-level macro-action reasoning with low-level precision, the framework mitigates compounding errors and manages the computational explosion of long-horizon search.

The experiments demonstrate that this approach enables zero-shot execution of complex, multi-stage tasks on real hardware—a significant step for autonomous systems that must operate in the real world using only raw sensory data. By providing a modular "plug-in" abstraction for existing world models, HWM offers a path toward more efficient and capable embodied agents that can reason about the future at multiple scales.

## Relevant Citations

- V-jepa 2: Self-supervised video models enable understanding, prediction and planning: The HWM framework is applied directly on top of the VJEPA2-AC model for the real-world robotic manipulation experiments. The paper demonstrates a dramatic improvement from 0% to 70% success on pick-and-place tasks, making this baseline critical for validating the proposed hierarchical approach.
- Dino-wm: World models on pre-trained visual features enable zero-shot planning: DINO-WM serves as another key backbone model for the paper's experiments, specifically in the Push-T simulated environment. The comparison against the original 'flat' DINO-WM planner showcases HWM's ability to improve long-horizon reasoning and computational efficiency.
- Learning from reward-free offline data: A case for planning with latent dynamics models: This paper introduces PLDM, the third latent world model that HWM is built upon for the maze navigation experiments. The results demonstrate that HWM is a model-agnostic abstraction that consistently improves zero-shot generalization and performance on out-of-distribution tasks compared to the flat PLDM planner.
- World models: This is a foundational paper that popularized the concept of learning predictive latent-space models of an environment for planning and control. The current work directly builds on this paradigm, proposing a hierarchical extension to address the long-horizon planning limitations inherent in standard world models.
