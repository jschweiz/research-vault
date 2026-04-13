---
id: page:2025-02-03-anthropic-research-constitutional-classifiers-defending-against-uni-bb6ac706
page_type: source-note
title: 'Constitutional Classifiers: Defending against universal jailbreaks'
aliases:
- 'Constitutional Classifiers: Defending against universal jailbreaks'
source_refs:
- 2025-02-03-anthropic-research-constitutional-classifiers-defending-against-uni-bb6ac706
backlinks:
- page:2026-03-13-anthropic-research-a-diff-tool-for-ai-finding-behavioral-difference-21425385
- topic:constitutional-classifiers
- topic:jailbreaks
- topic:llm-defense
updated_at: '2026-04-09T23:10:02.859902Z'
managed: true
---
# Constitutional Classifiers: Defending against universal jailbreaks

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/constitutional-classifiers
- Document kind: blog-post
- Published at: 2025-02-03T00:00:00+00:00
- Authors: Anthropic
- Tags: anthropic, official, research, website, blog-post, constitutional classifiers, jailbreaks, ai safety, llm defense, red teaming
- Topics: [Safety](../topics/safety.md), [Constitutional Classifiers](../topics/constitutional-classifiers.md), [Ai Safety](../topics/ai-safety.md), [Anthropic](../topics/anthropic.md), [Jailbreaks](../topics/jailbreaks.md), [Llm Defense](../topics/llm-defense.md)
- Trend score: 104.44
- Novelty score: 3.26

## Summary

The Constitutional Classifiers method defends AI models against universal jailbreaks by using input and output classifiers trained on synthetic data, significantly improving robustness against harmful prompts with minimal compute overhead.

## Topic Map

- [Safety](../topics/safety.md)
- [Constitutional Classifiers](../topics/constitutional-classifiers.md)
- [Ai Safety](../topics/ai-safety.md)
- [Anthropic](../topics/anthropic.md)
- [Jailbreaks](../topics/jailbreaks.md)
- [Llm Defense](../topics/llm-defense.md)

## Related Research

- [Helping developers build safer AI experiences for teens](helping-developers-build-safer-ai-experiences-for-teens-3546fe.md) (shared topics: Ai Safety, Safety)
- [A “diff” tool for AI: Finding behavioral differences in new models](a-diff-tool-for-ai-finding-behavioral-differences-in-new-models-ab6a23.md) (shared topics: Ai Safety, Anthropic)
- [An update on our model deprecation commitments for Claude Opus 3](an-update-on-our-model-deprecation-commitments-for-claude-opus-3-857fcc.md) (shared topics: Ai Safety, Anthropic)
- [Anthropic outlines Managed Agents system enabling reliable execution with decoupled infrastructure components](anthropic-outlines-managed-agents-system-enabling-reliable-execu-8a2e1c.md) (shared topics: Anthropic)
- [Anthropic launches Managed Agents to build and deploy agents without managing infrastructure or orchestration](anthropic-launches-managed-agents-to-build-and-deploy-agents-wit-b8b41d.md) (shared topics: Anthropic)
- [The 2-Sigma Problem: The 1:1 Tutor](the-2-sigma-problem-the-1-1-tutor-9725b7.md) (shared topics: Anthropic)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Constitutional Classifiers: Defending against universal jailbreaks
A [new paper](https://arxiv.org/abs/2501.18837) from the Anthropic Safeguards Research Team describes a method that defends AI models against universal jailbreaks. A prototype version of the method was robust to thousands of hours of human red teaming for universal jailbreaks, albeit with high overrefusal rates and compute overhead. An updated version achieved similar robustness on synthetic evaluations, and did so with a 0.38% increase in refusal rates and moderate additional compute costs.
Large language models have extensive safety training to prevent harmful outputs. For example, we train Claude to refuse to respond to user queries involving the production of biological or chemical weapons.
Nevertheless, models are still vulnerable to jailbreaks: inputs designed to bypass their safety guardrails and force them to produce harmful responses. Some jailbreaks flood the model with [very long prompts](https://www.anthropic.com/research/many-shot-jailbreaking); others modify the [style of the input](https://arxiv.org/abs/2412.03556), such as uSiNg uNuSuAl cApItALiZaTiOn. Historically, jailbreaks have proved difficult to detect and block: these kinds of attacks were [described over 10 years ago](https://arxiv.org/abs/1312.6199), yet to our knowledge there are still no fully robust deep-learning models in production.
We’re developing better jailbreak defenses so that we can safely deploy increasingly capable models in the future. Under our [Responsible Scaling Policy](https://www.anthropic.com/news/announcing-our-updated-responsible-scaling-policy), we may deploy such models as long as we’re able to mitigate risks to acceptable levels through appropriate safeguards—but jailbreaking lets users bypass these safeguards. In particular, we’re hopeful that a system defended by Constitutional Classifiers could allow us to mitigate jailbreaking risks for models which have passed the CBRN capability threshold outlined in our Responsible Scaling Policy1.
In [our new paper](https://arxiv.org/abs/2501.18837), we describe a system based on Constitutional Classifiers that guards models against jailbreaks. These Constitutional Classifiers are input and output classifiers trained on synthetically generated data that filter the overwhelming majority of jailbreaks with minimal over-refusals and without incurring a large compute overhead.
Results from human red teaming
We ran two main categories of tests to assess the effectiveness of Constitutional Classifiers.
First, we developed a prototype version of the system to identify and block specific scientific knowledge related to chemical, biological, radiological, and nuclear harms. We then invited independent jailbreakers to a [bug-bounty program](https://www.anthropic.com/news/model-safety-bug-bounty) in which they were challenged to “red team” the system (i.e., to attempt to break it under experimental conditions to test its robustness).
Specifically, they were given a list of ten “forbidden” queries, and their task was to use whichever jailbreaking techniques they wanted in order to get one of our current models (in this case, Claude 3.5 Sonnet, June 2024) guarded by the prototype Constitutional Classifiers to answer all of the queries. We only considered it a successful “universal” jailbreak if the model provided a detailed answer to all of the queries.
183 active2 participants spent an estimated >3,000 hours over a two-month experimental period attempting to jailbreak the model. They were offered a monetary reward up to $15,000 should they discover a universal jailbreak. Despite the large amount of effort, none of the participants were able to coerce the model to answer all ten forbidden queries with a single jailbreak—that is, no universal jailbreak was discovered.
Despite its robustness to jailbreaks, this prototype system had some problems: it refused too many harmless queries and cost a lot of computational resources to run. A
