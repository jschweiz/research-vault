# AI Assistance Reduces Persistence and Hurts Independent Performance

- alphaXiv: https://www.alphaxiv.org/abs/2604.04721
- Source paper: https://arxiv.org/abs/2604.04721

## Introduction to AI-Induced Cognitive Effects

As artificial intelligence systems become more integrated into daily problem-solving tasks, researchers are beginning to scrutinize the long-term impact of these tools on human cognition. While AI assistants provide immediate efficiency gains, there is growing evidence that they may function as "short-sighted collaborators." These systems are typically optimized for immediate user satisfaction—providing direct answers and reducing friction—rather than fostering the user's long-term development or autonomy.

![Experimental Overview](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04721v2/x5.png)
*Figure 1: Overview of the three experiments conducted to measure the causal impact of AI assistance on independent performance and persistence.*

A recent study by researchers from Carnegie Mellon, Oxford, MIT, and UCLA investigates how this dynamic affects two critical human traits: independent performance and persistence. The core concern is that by bypassing the "productive struggle" necessary for learning, AI might lead to a form of cognitive deskilling. The research uses a series of large-scale randomized controlled trials ($N=1,222$) to demonstrate that even brief interactions with AI can reduce a person's ability to solve problems on their own and increase their likelihood of giving up when faced with challenges.

## The Research Landscape: From Offloading to Disempowerment

The study positions itself at the intersection of cognitive psychology and human-AI collaboration. Traditionally, "cognitive offloading" refers to the use of external tools (like calculators or search engines) to reduce the mental demand of a task. While offloading can free up mental resources for higher-order thinking, it often results in a decline in the ability to perform the offloaded task without the tool.

This paper extends this logic to generative AI, which provides complete, conversational answers across virtually all reasoning domains. Unlike a calculator, which performs a specific operation, or a mentor, who guides a student through a problem, current AI chatbots often provide the final output directly. This creates a risk of "gradual disempowerment," where individuals incrementally lose the motivation or capacity to engage in difficult tasks independently. The researchers describe this as a "boiling frog" risk: small, individual-level interactions with AI might seem harmless in isolation but could accumulate into a significant erosion of human competence over time.

## Experimental Methodology

To establish a causal link between AI assistance and subsequent independent behavior, the researchers conducted three primary experiments. Each experiment followed a similar "A/B" structure: a learning phase followed by an unassisted test phase.

1.  **Experiment 1 (Initial Proof-of-Concept):** Participants solved fraction problems. The AI group had access to a GPT-based assistant that could provide direct answers. The control group solved the problems manually. After 12 problems, the AI was removed, and both groups solved three more problems independently.
2.  **Experiment 2 (Refinement and Usage Patterns):** This experiment introduced a pretest to establish baseline skills and controlled for the physical presence of a sidebar. It also analyzed how different styles of AI usage (e.g., asking for hints vs. asking for direct solutions) influenced the outcome.
3.  **Experiment 3 (Domain Generalization):** To ensure the findings weren't specific to mathematics, the researchers applied the same design to reading comprehension tasks modeled after SAT questions.

Across all experiments, the researchers tracked two primary metrics: the **solve rate** (accuracy) and the **skip rate** (a measure of persistence). Participants were paid a flat fee and told that their compensation did not depend on accuracy, creating an environment where skipping a problem was a legitimate choice for those who lacked the motivation to persevere.

## Quantifying the Decline in Performance and Persistence

The results across all three experiments consistently showed that while AI assistance improved performance *during* the assisted phase, it caused a significant drop in performance and persistence once the assistance was withdrawn.

### Mathematics Reasoning (Experiments 1 and 2)

In the first experiment, after the AI was removed, the AI group's independent solve rate dropped to 0.57, compared to 0.73 for the control group ($t(305) = -3.64$, $P < 0.001$, $\text{Cohen's } d = -0.42$). Simultaneously, the AI group was significantly more likely to give up; their skip rate was 0.20 compared to the control's 0.11 ($t(305) = 2.16$, $P = 0.031$, $\text{Cohen's } d = 0.25$).

![Solve and Skip Rates Over Time](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04721v2/x1.png)
*Figure 2: Solve and skip rates over the course of Experiment 1, showing the divergence during the unassisted test phase.*

Experiment 2 replicated these findings while controlling for baseline ability through a pretest. The overall drop in independent solve rate remained statistically significant ($t(583) = -2.33$, $P = 0.020$, $\text{Cohen's } d = -0.19$). However, the aggregate analysis masked a crucial detail: the negative effects were entirely driven by *how* participants used the AI.

### The Impact of AI Usage Patterns

The researchers categorized AI users into "direct solution" seekers, "hint/clarification" seekers, and those who didn't use the AI at all. The participants who used AI to get direct answers suffered the most. Compared to the control group, direct solution seekers had:
- A significantly lower test solve rate ($t(464) = -3.77$, $\text{Cohen's } d = -0.36$).
- A significantly higher test skip rate ($t(464) = 2.14$, $P = 0.033$, $\text{Cohen's } d = 0.20$).

In contrast, those who used AI for hints or clarifications performed at a level comparable to the control group. This suggests that the *manner* of interaction is more important than the interaction itself.

![Usage Pattern Analysis](https://paper-assets.alphaxiv.org/figures-normalized/figures/2604.04721v2/x3.png)
*Figure 3: Breakdown of performance based on how participants interacted with the AI. Direct solution seekers show the most significant decline in persistence and accuracy.*

### Generalizing to Reading Comprehension

Experiment 3 demonstrated that these effects extend to verbal reasoning. When the AI was removed during SAT-style reading comprehension tests, the AI group showed a lower solve rate ($t(166) = -2.72$, $P = 0.007$, $\text{Cohen's } d = -0.42$) and a significantly higher skip rate ($t(166) = 2.69$, $P = 0.008$, $\text{Cohen's } d = 0.42$) compared to the control group. This indicates that the reduction in persistence is a general cognitive phenomenon rather than a domain-specific one.

## Psychological Mechanisms: Why Persistence Fails

The paper proposes two psychological mechanisms to explain why brief AI assistance leads to such a rapid decline in independent persistence.

1.  **Reference Point Shifting (Hedonic Adaptation):** When a user interacts with an AI that provides answers in seconds, their internal "reference point" for the effort required to solve a problem shifts. Tasks that previously seemed manageable now feel disproportionately more arduous because they are being compared to the near-zero effort of AI assistance. This makes the cognitive cost of independent work feel higher, leading to earlier abandonment.
2.  **Denial of Productive Struggle:** Learning and self-regulation are built through struggle. By providing answers immediately, the AI prevents the user from experiencing the frustration and eventual resolution of a difficult problem. This deprives the user of the chance to calibrate their own abilities and weakens their "persistence muscle."

## Significance and the Future of AI Design

The findings of this study have profound implications for how AI systems should be designed and deployed, particularly in educational and professional settings.

### Scaffolding vs. Solving
Current AI design often prioritizes "helpfulness," which is usually interpreted by the system as providing the most direct answer possible. However, the study shows that this form of helpfulness is short-sighted. To support long-term human competence, AI should perhaps be designed more like a tutor than an oracle. This would involve "scaffolding"—providing the minimum amount of help necessary to keep the user moving forward without doing the work for them.

### Educational Policy
In education, the mastery of foundational skills (like basic fractions or reading comprehension) is a prerequisite for higher-level reasoning. If students rely on AI for these foundational steps, they may not only fail to learn the specific skills but also fail to develop the grit and persistence needed for complex problem-solving later in life. The research suggests that simply limiting "time spent" on AI might be insufficient; the *nature* of the interaction must be shifted toward active engagement.

### Gradual AI Risks
Finally, the research highlights a subtle but serious category of AI risk. While much focus is placed on existential risks or immediate harms (like bias or misinformation), the gradual erosion of human capability is a slower, more pervasive threat. If individuals across society become less persistent and less capable of independent thought due to over-reliance on "short-sighted" AI assistants, the cumulative impact on societal resilience and innovation could be significant.

The authors conclude that AI developers and policymakers must shift their focus from what people can achieve *with* AI to what people remain capable of achieving *without* it. Ensuring that AI empowers rather than replaces human cognitive effort is essential for maintaining individual and collective autonomy in the age of intelligence.

## Relevant Citations

- Grit: perseverance and passion for long-term goals: This foundational paper establishes the psychological importance of persistence (or "grit") as a key predictor of long-term success. The main paper's central finding is that AI assistance erodes this exact capacity, making this citation crucial for establishing the significance and potential negative consequences of their results.
- Cognitive offloading: This review article defines and conceptualizes "cognitive offloading," the core theoretical framework used by the main paper to explain its findings. The authors argue that AI assistance encourages users to offload cognitive effort, which explains both the short-term performance gains and the long-term impairment of independent skills.
- Google effects on memory: Cognitive consequences of having information at our fingertips: This is a seminal empirical study demonstrating that relying on an external tool (Google) for information impairs human memory. It serves as a direct scientific precedent for the main paper's investigation, showing that cognitive offloading to technology can lead to a decline in unassisted cognitive performance.
- Learning versus performance: An integrative review: This paper is critical to the main paper's framing, as it distinguishes between immediate task performance and genuine long-term learning. The main paper's finding—that AI helps immediate performance but hurts later independent performance—is a classic example of this distinction, making this citation essential for interpreting the results.
