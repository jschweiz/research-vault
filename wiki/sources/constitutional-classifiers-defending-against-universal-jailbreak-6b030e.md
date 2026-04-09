---
id: page:2025-02-03-anthropic-research-constitutional-classifiers-defending-against-uni-bb6ac706
page_type: source-note
title: 'Constitutional Classifiers: Defending against universal jailbreaks'
aliases:
- 'Constitutional Classifiers: Defending against universal jailbreaks'
source_refs:
- 2025-02-03-anthropic-research-constitutional-classifiers-defending-against-uni-bb6ac706
backlinks:
- page:2026-02-25-anthropic-research-an-update-on-our-model-deprecation-commitments-f-9d1b9dba
- page:2026-03-31-anthropic-research-how-australia-uses-claude-findings-from-the-anth-8bdd4935
- topic:alignment
- topic:constitutional-classifiers
updated_at: '2026-04-09T12:15:42.542400Z'
managed: true
---
# Constitutional Classifiers: Defending against universal jailbreaks

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/constitutional-classifiers
- Document kind: blog-post
- Published at: 2025-02-03T00:00:00+00:00
- Tags: anthropic, official, research, website, blog-post
- Topics: [Safety](../topics/safety.md), [Anthropic](../topics/anthropic.md), [Official](../topics/official.md), [Website](../topics/website.md), [Alignment](../topics/alignment.md), [Constitutional Classifiers](../topics/constitutional-classifiers.md)
- Trend score: 56.46
- Novelty score: 3.60

## Topic Map

- [Safety](../topics/safety.md)
- [Anthropic](../topics/anthropic.md)
- [Official](../topics/official.md)
- [Website](../topics/website.md)
- [Alignment](../topics/alignment.md)
- [Constitutional Classifiers](../topics/constitutional-classifiers.md)

## Related Research

- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-147fc4.md) (shared topics: Anthropic, Official, Safety, Website)
- [An update on our model deprecation commitments for Claude Opus 3](an-update-on-our-model-deprecation-commitments-for-claude-opus-3-857fcc.md) (shared topics: Anthropic, Official, Safety, Website)
- [Introducing the Child Safety Blueprint](introducing-the-child-safety-blueprint-be6078.md) (shared topics: Official, Safety, Website)
- [Announcing the OpenAI Safety Fellowship](announcing-the-openai-safety-fellowship-8b56c7.md) (shared topics: Official, Safety, Website)
- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-9e1ca2.md) (shared topics: Anthropic, Official, Website)
- [Inside our approach to the Model Spec](inside-our-approach-to-the-model-spec-aad9dd.md) (shared topics: Official, Safety, Website)

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
