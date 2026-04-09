---
id: page:2025-12-18-anthropic-research-project-vend-phase-two-6d9cb3ea
page_type: source-note
title: 'Project Vend: Phase two'
aliases:
- 'Project Vend: Phase two'
source_refs:
- 2025-12-18-anthropic-research-project-vend-phase-two-6d9cb3ea
backlinks:
- page:2026-03-17-openai-website-introducing-gpt-5-4-mini-and-nano-8afdb503
- page:2026-03-23-anthropic-research-long-running-claude-for-scientific-computing-20a930ae
- page:2026-03-23-anthropic-research-vibe-physics-the-ai-grad-student-a88ccd9c
updated_at: '2026-04-09T12:15:42.196383Z'
managed: true
---
# Project Vend: Phase two

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/project-vend-2
- Document kind: blog-post
- Published at: 2025-12-18T00:00:00+00:00
- Tags: anthropic, official, research, website, blog-post
- Topics: [Anthropic](../topics/anthropic.md), [Official](../topics/official.md), [Website](../topics/website.md), [Agents](../topics/agents.md), [Reasoning](../topics/reasoning.md), [Tool Use](../topics/tool-use.md)
- Trend score: 249.90
- Novelty score: 4.80

## Topic Map

- [Anthropic](../topics/anthropic.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Agents](../topics/agents.md)
- [Reasoning](../topics/reasoning.md)
- [Tool Use](../topics/tool-use.md)

## Related Research

- [Vibe physics: The AI grad student](vibe-physics-the-ai-grad-student-1b7b0a.md) (shared topics: Agents, Anthropic, Official, Website)
- [Long-running Claude for scientific computing](long-running-claude-for-scientific-computing-b8d3ec.md) (shared topics: Agents, Anthropic, Official, Website)
- [Introducing GPT-5.4 mini and nano](introducing-gpt-5-4-mini-and-nano-2054cd.md) (shared topics: Agents, Official, Reasoning, Website)
- [The next phase of enterprise AI](the-next-phase-of-enterprise-ai-00c367.md) (shared topics: Agents, Official, Website)
- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-9e1ca2.md) (shared topics: Anthropic, Official, Website)
- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-147fc4.md) (shared topics: Anthropic, Official, Website)

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
