# Tune to Learn: How Controller Gains Shape Robot Policy Learning

- alphaXiv: https://www.alphaxiv.org/abs/2604.02523
- Source paper: https://arxiv.org/abs/2604.02523

## The Role of Controller Gains in Modern Robot Learning

Position-controlled robots rely on a foundational control loop to track commanded trajectories. In this paradigm, a high-level policy outputs a target joint configuration $q_d$, and a low-level proportional-derivative (PD) controller generates the actual joint torques $\tau$ required to reach that target. This relationship is typically governed by the equation:

$$\tau = K_p(q_d - q) - K_d\dot{q} + \tau_{ff}$$

where $q$ and $\dot{q}$ represent the current joint position and velocity, $\tau_{ff}$ is a feed-forward term (often for gravity compensation), and the proportional gain $K_p$ and derivative gain $K_d$ are parameters that determine the controller's stiffness and damping, respectively.

![Overview of the study: tuning controller gains for learnability rather than task-level behavior.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02523v1/main-figure-gain-setting-2.png)
*Caption: Position controller gains ($K_p$ and $K_d$) are often selected based on desired task compliance, but this research suggests they should instead be optimized to improve policy learnability.*

Historically, roboticists have selected these gains using heuristics based on the task at hand. For tasks requiring precision, such as high-speed assembly, "stiff" gains (high $K_p$) are used to ensure the robot tracks its targets as closely as possible. For contact-rich manipulation, such as opening a door or cleaning a surface, "compliant" gains (low $K_p$) are preferred to allow the robot to yield under external forces, preventing damage.

However, modern robot learning shifts the burden of defining behavior from the controller to a state-conditioned policy. When a policy is reactive—meaning it updates its commands based on the robot's current state—the effective behavior of the system is no longer determined by the gains alone. Instead, it emerges from the interaction between the policy's response and the control dynamics. This work investigates how these gains function as an *inductive bias* that shapes the learnability, training stability, and transferability of learned policies.

## Decoupling Low-Level Gains from High-Level Behavior

A central claim of this research is that the effective stiffness of a robot is decoupled from its low-level controller gains when it is governed by a reactive policy. In classical control, if a robot has low $K_p$ gains, it will necessarily be "soft" or compliant to external disturbances. This research demonstrates that a learned policy can override this default behavior.

By training a reinforcement learning (RL) policy with compliant gains to maintain a rigid pose despite external forces, the authors show that the policy learns to compensate for its own compliance by outputting aggressive, counteractive target positions. Conversely, a policy trained with stiff gains can be incentivized to act compliantly by learning to move its targets in the direction of an external force.

![Quantifying the emergence of task-level stiffness across different gain regimes.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02523v1/existence_proof_quant.png)
*Caption: Effective Cartesian stiffness is not strictly tied to low-level joint gains. Policies can learn to be stiff even with compliant controller gains (orange line) or compliant with stiff gains (blue line).*

The effective stiffness $K_{eff}$ is measured by the relationship between a displacement $\Delta x$ and the resulting force $\Delta F$:

$$K_{eff} = -\frac{\Delta F}{\Delta x} \text{ [N/m]}$$

The results confirm that $K_{eff}$ is an emergent property. This finding is significant because it suggests that we do not need to choose gains to "match" the task's mechanical requirements. Instead, we are free to choose gains that make the policy easier to learn or more robust to real-world errors.

## Behavior Cloning: Why Compliant Gains Improve Learnability

Behavior cloning (BC) is the process of learning a policy by imitating an expert's actions. A major challenge in BC is the compounding of errors: small mistakes by the policy lead the robot to states it never saw during training, causing even larger subsequent mistakes.

The authors investigated how gains affect this error propagation. To do this fairly, they developed a technique called **Torque-to-Position Retargeting (TPR)**. This allows them to take a single set of expert torque demonstrations and convert them into target position actions for any arbitrary $(K_p, K_d)$ gain setting. This ensures that the only difference between training scenarios is the gain setting, while the physical motion remains identical.

![A robot performing a dish unloading task, one of the contact-rich manipulation environments used to evaluate behavior cloning.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02523v1/dishrack-unload.png)
*Caption: Manipulation tasks like unloading a dishrack provide a complex environment for evaluating how controller gains influence imitation learning performance.*

The experiments revealed a consistent trend: **compliant and overdamped gains (low $K_p$, high $K_d$) lead to significantly higher success rates in BC.** 

This might seem counterintuitive because stiff gains result in lower training error (the robot follows the expert's path more accurately in simulation). However, the compliant/overdamped regime is more "forgiving." If the policy outputs a slightly incorrect target $q_d$, a compliant controller generates less torque, resulting in a smaller physical deviation. Simultaneously, high damping $K_d$ prevents the robot from oscillating after a perturbation. This "error attenuation" property prevents small policy errors from spiraling into catastrophic task failures.

## Teleoperation and the Human Element

If compliant gains are better for learning, does using them make it harder for humans to provide demonstrations? High-gain, stiff robots feel responsive, while low-gain robots can feel "mushy" or laggy to a human operator.

To address this, the authors conducted a user study where participants teleoperated a robot to push a box into a target zone. For each gain setting, the users were allowed to adjust an **input mapper** $\phi(u, x) \to x_{des}$, which translates their raw control inputs $u$ (from a 3D mouse) into desired target positions $x_{des}$.

![Users adjusting input mapping parameters during the teleoperation study.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02523v1/output3.png)
*Caption: The teleoperation setup allowed users to customize how their inputs mapped to robot motion, ensuring that comparisons between gain settings were fair to the human operator.*

The study found that when users were given the opportunity to tune their individual input mapping parameters, they performed just as well with compliant gains as they did with stiff gains. In fact, many users found the compliant settings easier to handle in contact-rich tasks because the robot was less likely to jerk or stall when hitting the box. This implies that robot learning practitioners can safely adopt compliant gain regimes for data collection without sacrificing the quality or speed of human demonstrations.

## Reinforcement Learning: Adaptability and Optimization Landscapes

Unlike behavior cloning, reinforcement learning (RL) allows the robot to explore and learn from its own mistakes. The authors tested whether the same gain-dependent trends held for RL across tasks ranging from cube lifting to bimanual handovers.

![System identification results showing the fit between real robot data and simulated joint trajectories.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02523v1/sysid_final_with_markers.png)
*Caption: System identification ensures that the simulation environments used for reinforcement learning accurately reflect the specific dynamics of each gain configuration.*

The key finding for RL is its high degree of **adaptability**. Successful policies could be discovered for nearly every gain setting, provided that the training hyperparameters (like action scaling) were re-tuned for each specific configuration. While the "ease of discovery" (how many hyperparameter settings lead to success) varied depending on the task and gain, no single gain regime was a universal winner.

This suggests that for RL-based workflows, the specific choice of gain is less critical for the final performance of the policy, as the RL algorithm naturally adapts its reactive behavior to the underlying hardware dynamics. However, the choice of gains still influences how sensitive the training process is to hyperparameter selection.

## The Sim-to-Real Paradox: Accuracy vs. Robustness

One of the most surprising findings of the research involves the transition from simulation to the real world. To prepare for this transfer, researchers perform **System Identification (SysID)** to make the simulation as accurate as possible.

The authors found that stiff gain settings yielded the most accurate system models. Because stiff controllers dominate the robot's unmodeled nonlinearities (like joint friction or slight arm flex), the simulated robot was a very close match to the real one.

![Real-world joint tracking showing high-frequency jitter when using stiff controller gains.](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.02523v1/joint_7_achieved_only.png)
*Caption: Stiff gain settings are prone to high-frequency oscillations and jitter during zero-shot sim-to-real transfer, despite appearing highly accurate in offline modeling.*

However, this accuracy did not translate to successful transfer. When policies were deployed on the real robot, **stiff gain settings often failed due to high-frequency oscillations (jitter).** This happens because stiff controllers are highly sensitive to small discrepancies between sim and real observations. A tiny modeling error can cause the policy to react aggressively, which the stiff controller immediately translates into a large torque, leading to instability.

In contrast, compliant and overdamped gains proved much more robust. They inherently "smooth out" the policy's reactions to modeling gaps. Furthermore, the authors found that lowering the policy's update frequency (e.g., running the policy at $10$ Hz or $20$ Hz instead of $100$ Hz) was an effective way to mitigate jitter, as it gives the robot's physical joints more time to settle between discrete commands.

## Practical Recommendations for Robot Learning

This systematic investigation provides a set of data-driven guidelines for researchers and engineers in robot learning:

1.  **For Behavior Cloning:** Use compliant and overdamped gains (low $K_p$, high $K_d$). This regime attenuates the compounding errors that often degrade imitation learning performance.
2.  **For Data Collection:** Do not be afraid to use compliant gains for human teleoperation. Provided the input mapping is tuned, humans are highly adaptable, and the resulting data will be better suited for learning.
3.  **For Reinforcement Learning:** RL is versatile, but ensure you re-tune your action scales and other environment hyperparameters whenever you change controller gains.
4.  **For Sim-to-Real:** Do not rely solely on modeling accuracy as a metric for transferability. Stiff gains might look better in simulation but often fail on hardware due to unmodeled dynamics. Consider compliant/overdamped gains and lower policy frequencies to achieve stable zero-shot transfer.

By viewing controller gains as an inductive bias rather than a fixed mechanical property, this work provides a framework for designing robot control interfaces that are optimized for learning rather than just traditional tracking.

## Relevant Citations

- A new feedback method for dynamic control of manipulators: This foundational paper established the global asymptotic stability of the PD control law with gravity compensation. This control law is the fundamental interface between the policy and the robot that is analyzed throughout the main paper.
- Action space design in reinforcement learning for robot motor skills: This work is cited for framing action space selection as an inductive bias, a core perspective that the main paper explicitly extends to the selection of controller gains. This provides the key conceptual lens for the paper's investigation.
- Soft-mimic: Learning compliant whole-body control from examples: This paper's key observation—that a learned policy's compliance is dictated by its training incentives, not the underlying controller gains—provides the central motivation for the main paper's study. It justifies the need to analyze gains from a 'learnability' perspective rather than a 'task behavior' one.
- Sim-to-real transfer of robotic control with dynamics randomization: This is a seminal paper on using dynamics randomization to bridge the sim-to-real gap, a standard practice that often includes randomizing PD gains. The main paper's investigation into how the nominal gain settings affect sim-to-real transfer provides crucial context and guidance for this established technique.
