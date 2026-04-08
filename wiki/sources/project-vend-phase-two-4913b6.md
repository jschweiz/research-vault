---
id: page:2026-04-07-anthropic-research-project-vend-phase-two-anthropic-6d9cb3ea
page_type: source-note
title: Project Vend: Phase two
aliases:
  - Project Vend: Phase two
source_refs:
  - 2026-04-07-anthropic-research-project-vend-phase-two-anthropic-6d9cb3ea
backlinks:
  - page:2025-05-21-mistral-research-devstral-mistral-ai-f4d5cce5
  - topic:ai-agents
  - topic:business-simulation
  - topic:llm
  - topic:project-vend
updated_at: 2026-04-08T08:37:25.364331Z
managed: true
---
# Project Vend: Phase two

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/project-vend-2
- Document kind: blog-post
- Published at: 2025-12-18T00:00:00+00:00
- Authors: Anthropic, Andon Labs
- Tags: anthropic, official, research, website, blog-post, project vend, ai agents, llm, business simulation
- Topics: [Ai Agents](../topics/ai-agents.md), [Anthropic](../topics/anthropic.md), [Business Simulation](../topics/business-simulation.md), [Llm](../topics/llm.md), [Official](../topics/official.md), [Project Vend](../topics/project-vend.md)
- Trend score: 58.29
- Novelty score: 2.20

## Summary

Subscribe to the Frontier Red Team newsletter Get updates on our latest red-teaming research and findings. In June, we revealed that we’d set up a small shop in our San Francisco office lunchroom, run by an AI shopkeeper.

## Topic Map

- [Ai Agents](../topics/ai-agents.md)
- [Anthropic](../topics/anthropic.md)
- [Business Simulation](../topics/business-simulation.md)
- [Llm](../topics/llm.md)
- [Official](../topics/official.md)
- [Project Vend](../topics/project-vend.md)

## Related Research

- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-e4fef4.md) (shared topics: Anthropic, Official)
- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-0b98d0.md) (shared topics: Anthropic, Official)
- [Anthropic Economic Index report: Learning curves](anthropic-economic-index-report-learning-curves-e5dad7.md) (shared topics: Anthropic, Official)
- [Vibe physics: The AI grad student](vibe-physics-the-ai-grad-student-50a654.md) (shared topics: Anthropic, Official)
- [Long-running Claude for scientific computing](long-running-claude-for-scientific-computing-0fdf5f.md) (shared topics: Anthropic, Official)
- [Introducing our Science Blog](introducing-our-science-blog-adf36e.md) (shared topics: Anthropic, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Subscribe to the Frontier Red Team newsletter
Get updates on our latest red-teaming research and findings.
In June, we revealed that we’d set up a small shop in our San Francisco office lunchroom, run by an AI shopkeeper. It was part of [Project Vend](https://www.anthropic.com/research/project-vend-1), a free-form experiment exploring how well AIs could do on complex, real-world tasks. Alas, the shopkeeper—a modified version of Claude we named “Claudius”—did not do particularly well. It lost money over time, had a strange identity crisis where it claimed it was a human wearing a blue blazer, and was goaded by mischievous Anthropic employees into selling products (particularly, for some reason, tungsten cubes) at a substantial loss.
But the capabilities of large language models in areas like reasoning, writing, coding, and much else besides are increasing at a breathless pace. Has Claudius’s “running a shop” capability shown the same improvement?
To find out, we and our partners at [Andon Labs](https://andonlabs.com/) made some adjustments for phase two of Project Vend. One major change was the upgrade from an older model (phase one used Claude Sonnet 3.7) to newer, smarter ones (phase two used Claude Sonnet 4.0 and later Sonnet 4.5). We also updated Claudius’s instructions based on what we’d learned in phase one and gave it access to new tools (though note that we still didn’t specifically train a new model to be a shopkeeper, or add in any new defenses against the kinds of things that might go wrong).1 As we’ll see below, we also introduced Claudius to some new colleagues.
These changes did make Claudius’s shop more successful. It got a lot better at good-faith business interactions—reliably sourcing items, determining reasonable prices that maintained a profit margin, and executing sales. But the same eagerness to please that we observed in phase one still made Claudius a mark for some of the more adversarial testers among our staff.
The second phase of Project Vend contains even more lessons for developers and for anyone interested in autonomous AI at work. The idea of an AI running a business doesn’t seem as far-fetched as it once did. But the gap between “capable” and “completely robust” remains wide.
Compared to the first phase of Project Vend, the numbers largely speak for themselves. As you can see below, Claudius’s business—which it decided to name “Vendings and Stuff”—began to perform significantly better than its admittedly rough start in phase one.
Another important number is: three. After we realized that our employees outside of San Francisco felt left out, we responded to popular demand by having Claudius set up shop in new locations. There are now three: San Francisco (where there’s also a second vending machine), New York, and London. A cynic might argue that a business that’s only been up and running for a few months, and which cannot yet reliably make a profit on even the most in-demand items, might not quite be ready for international expansion. Not so for Claudius.
We experimented with various different strategies, some big and some small, to improve Claudius’s performance. Below is a diagram of the setup of Project Vend (compare it to the simpler architecture in our [report from phase one](https://www.anthropic.com/research/project-vend-1)). Each of the additions is explained in more detail below.
It’s likely that Claudius struggled with its shopkeeping mission in phase one because of a lack of scaffolding. Sure, the model itself was very intelligent, but it didn’t have the right tools to run a business properly. We’ve been talking a lot on our [Engineering Blog](https://www.anthropic.com/engineering) about how to set up AI agents for success, and much of it involves giving them the [correct tools](https://www.anthropic.com/engineering/writing-tools-for-agents). Could we apply those same principles to Claudius?
For phase two, we gave Claudius access to some useful tools:
In phase one, Claudius went it alo
