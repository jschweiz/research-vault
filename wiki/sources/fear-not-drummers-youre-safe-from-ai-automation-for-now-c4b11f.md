---
id: page:2026-03-30-jack-clark-import-ai-fear-not-drummers-youre-safe-from-ai-automation--8ee69b4a
page_type: source-note
title: Fear not, drummers, you’re safe from AI automation for now
aliases:
- Fear not, drummers, you’re safe from AI automation for now
source_refs:
- 2026-03-30-jack-clark-import-ai-fear-not-drummers-youre-safe-from-ai-automation--8ee69b4a
backlinks:
- page:2026-02-02-jack-clark-import-ai-fauna-robotics-launches-a-friendly-programmable--c0269582
- page:2026-02-02-jack-clark-import-ai-russian-researchers-plot-hand-controlled-drones-fe8f4370
- page:2026-03-02-jack-clark-import-ai-physical-intelligence-shows-off-some-of-its-robo-b58b416c
- topic:dexdrummer
- topic:reinforcement-learning
- topic:robot-hands
updated_at: '2026-04-09T23:10:02.997369Z'
managed: true
---
# Fear not, drummers, you’re safe from AI automation for now

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Import AI
- Canonical URL: https://arxiv.org/abs/2603.22263
- Document kind: paper
- Published at: 2026-03-30T12:28:13+00:00
- Tags: newsletter, ai, analysis, policy, website, paper, robotics, dexdrummer, reinforcement learning, robot hands, sub-document
- Topics: [Robotics](../topics/robotics.md), [Reinforcement Learning](../topics/reinforcement-learning.md), [Dexdrummer](../topics/dexdrummer.md), [Newsletter](../topics/newsletter.md), [Policy](../topics/policy.md), [Robot Hands](../topics/robot-hands.md)
- Trend score: 655.21
- Novelty score: 6.80

## Summary

The paper details the development of DexDrummer, a hierarchical policy for teaching robot hands to play drums, focusing on dexterous control and real-world testing.

## Topic Map

- [Robotics](../topics/robotics.md)
- [Reinforcement Learning](../topics/reinforcement-learning.md)
- [Dexdrummer](../topics/dexdrummer.md)
- [Newsletter](../topics/newsletter.md)
- [Policy](../topics/policy.md)
- [Robot Hands](../topics/robot-hands.md)

## Related Research

- [Physical Intelligence shows off some of its robot deployments](physical-intelligence-shows-off-some-of-its-robot-deployments-3977c5.md) (shared topics: Newsletter, Policy, Robotics)
- [Russian researchers plot hand-controlled drones](russian-researchers-plot-hand-controlled-drones-ae7390.md) (shared topics: Newsletter, Policy, Robotics)
- [Fauna Robotics launches a friendly, programmable human robot](fauna-robotics-launches-a-friendly-programmable-human-robot-c57b2d.md) (shared topics: Newsletter, Policy, Robotics)
- [OpenAI #16: A History and a Proposal](openai-16-a-history-and-a-proposal-a6e162.md) (shared topics: Newsletter, Policy)
- [From folding boxes to fixing vacuums, GEN-1 robotics model hits 99% reliability](from-folding-boxes-to-fixing-vacuums-gen-1-robotics-model-hits-9-8d579f.md) (shared topics: Newsletter, Robotics)
- [Uh oh, there’s a scaling war for cyberattacks as well!](uh-oh-theres-a-scaling-war-for-cyberattacks-as-well-81eae4.md) (shared topics: Newsletter, Policy)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

# Fear not, drummers, you’re safe from AI automation for now

Source newsletter: Import AI 451: Political superintelligence; Google’s society of minds, and a robot drummer
Source issue: https://jack-clark.net/2026/03/30/import-ai-451-political-superintelligence-googles-society-of-minds-and-a-robot-drummer
Published At: 2026-03-30T12:28:13+00:00
Canonical URL: https://arxiv.org/abs/2603.22263

## Newsletter Context

…DexDrummer tackles a fiendishly hard robot hand problem… Whenever I get a bit worried about the pace of AI progress I toggle over to the ‘robotics’ sub-section of arXiv, read some papers, and feel a huge sense of relief. Robots, as everyone knows, are extremely hard to do well, with reality tending to screw up even the most advanced techniques. An even harder version of robotics is fine-grained low-latency dexterous control, where you need to get a robot hand to do something. So it’s with a combination of amusement and empathy that I read DexDrummer, a paper testing out how well contemporary AI approaches can get a robot hand to play the drums. The short answer is: robot hands are pretty terrible drummers!

What they did: They built DexDrummer “a hierarchical, two-stage policy for drumming” which has a high-level RL policy, as well as a low-level dexterous policy. They train their system in a simulated environment that contains a bimanual robot setup and a full drum set (snare, tom, ride, hi-hat, and crash). The main system generates a stick trajectory in task space, then a low-level system which tries to control the hand – this part is complex and involves encouraging the thumb and index finger to grasp the center of the drumstick paired with an “arm penalty constraint, which reduces excessive arm movements”. There is also work shaping rewards to ensure the robot is able to chain multiple drumhits together – this is achieved via a “contact curriculum” which allows the agent to practice trajectory following in free space while following the trajectory reward.

Real world testing: They test out the trained policy in reality on two 7-DOF Franka Panda arms and two 20-DOF Tesollo DG-5F hands. This is an area where I’d strongly encourage people to view the videos online to get some calibration about just how fiendishly hard this task is – the robots are able to hit the drums, but it’s painfully awkward to watch, and my sense is it’ll be quite a while till a human drummer has to look over their proverbial shoulder.

Why this matters – robotics as the last eval: Robotics in anything approximating a dynamic, rapidly changing environment (for instance, improvising drums with a live band) feels like one of the last frontiers for AI – and as this research shows, much like with modern computer vision research, getting AI to perform well requires the crafting of highly complicated artisanal policies. We’re a very long way from the generality of pretrained language models here. Read more: DexDrummer: In-Hand, Contact-Rich, and Long-Horizon Dexterous Robot Drumming (arXiv) . Please, I am begging you, check out the videos for a good time : DexDrummer site .
