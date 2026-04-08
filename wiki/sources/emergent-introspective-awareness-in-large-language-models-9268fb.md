---
id: page:2026-04-07-anthropic-research-emergent-introspective-awareness-in-large-langua-9bf6ddc3
page_type: source-note
title: Emergent introspective awareness in large language models
aliases:
  - Emergent introspective awareness in large language models
source_refs:
  - 2026-04-07-anthropic-research-emergent-introspective-awareness-in-large-langua-9bf6ddc3
backlinks:
  - page:2026-04-07-anthropic-research-how-australia-uses-claude-findings-from-the-anth-8bdd4935
  - page:2026-04-07-anthropic-research-long-running-claude-for-scientific-computing-ant-20a930ae
  - topic:ai-research
  - topic:claude
  - topic:introspection
  - topic:large-language-models
updated_at: 2026-04-08T08:37:25.353342Z
managed: true
---
# Emergent introspective awareness in large language models

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/introspection
- Document kind: blog-post
- Published at: 2025-10-29T00:00:00+00:00
- Authors: Anthropic
- Tags: anthropic, official, research, website, blog-post, introspection, large language models, ai research, claude, transparency
- Topics: [Ai Research](../topics/ai-research.md), [Anthropic](../topics/anthropic.md), [Claude](../topics/claude.md), [Introspection](../topics/introspection.md), [Large Language Models](../topics/large-language-models.md), [Official](../topics/official.md)
- Trend score: 58.29
- Novelty score: 0.60

## Summary

Have you ever asked an AI model what’s on its mind? Or to explain how it came up with its responses?

## Topic Map

- [Ai Research](../topics/ai-research.md)
- [Anthropic](../topics/anthropic.md)
- [Claude](../topics/claude.md)
- [Introspection](../topics/introspection.md)
- [Large Language Models](../topics/large-language-models.md)
- [Official](../topics/official.md)

## Related Research

- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-0b98d0.md) (shared topics: Anthropic, Claude, Official)
- [Long-running Claude for scientific computing](long-running-claude-for-scientific-computing-0fdf5f.md) (shared topics: Anthropic, Claude, Official)
- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-e4fef4.md) (shared topics: Anthropic, Official)
- [Anthropic Economic Index report: Learning curves](anthropic-economic-index-report-learning-curves-e5dad7.md) (shared topics: Anthropic, Official)
- [Vibe physics: The AI grad student](vibe-physics-the-ai-grad-student-50a654.md) (shared topics: Anthropic, Official)
- [Introducing our Science Blog](introducing-our-science-blog-adf36e.md) (shared topics: Anthropic, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Have you ever asked an AI model what’s on its mind? Or to explain how it came up with its responses? Models will sometimes answer questions like these, but it’s hard to know what to make of their answers. Can AI systems really introspect—that is, can they consider their own thoughts? Or do they just make up plausible-sounding answers when they’re asked to do so?
Understanding whether AI systems can truly introspect has important implications for their transparency and reliability. If models can accurately report on their own internal mechanisms, this could help us understand their reasoning and debug behavioral issues. Beyond these immediate practical considerations, probing for high-level cognitive capabilities like introspection can shape our understanding of what these systems are and how they work. Using interpretability techniques, we’ve started to investigate this question scientifically, and found some surprising results.
Our [new research](https://transformer-circuits.pub/2025/introspection/index.html) provides evidence for some degree of introspective awareness in our current Claude models, as well as a degree of control over their own internal states. We stress that this introspective capability is still highly unreliable and limited in scope: we do not have evidence that current models can introspect in the same way, or to the same extent, that humans do. Nevertheless, these findings challenge some common intuitions about what language models are capable of—and since we found that the most capable models we tested (Claude Opus 4 and 4.1) performed the best on our tests of introspection, we think it’s likely that AI models’ introspective capabilities will continue to grow more sophisticated in the future.
What does it mean for an AI to introspect?
Before explaining our results, we should take a moment to consider what it means for an AI model to introspect. What could they even be introspecting on? Language models like Claude process text (and image) inputs and produce text outputs. Along the way, they perform complex internal computations in order to decide what to say. These internal processes remain largely mysterious, but we know that models use their internal neural activity to [represent abstract concepts](https://www.anthropic.com/research/mapping-mind-language-model). For instance, prior research has shown that language models use specific neural patterns to distinguish [known vs. unknown people](https://arxiv.org/abs/2411.14257), evaluate the [truthfulness of statements](https://arxiv.org/abs/2310.06824), encode [spatiotemporal coordinates](https://arxiv.org/abs/2310.02207), store [planned future outputs](https://transformer-circuits.pub/2025/attribution-graphs/biology.html#dives-poems), and [represent their own personality traits](https://www.anthropic.com/research/persona-vectors). Models use these internal representations to [perform computations and make decisions about what to say](https://www.anthropic.com/research/tracing-thoughts-language-model).
You might wonder, then, whether AI models know about these internal representations, in a way that’s analogous to a human, say, telling you how they worked their way through a math problem. If we ask a model what it’s thinking, will it accurately report the concepts that it’s representing internally? If a model can correctly identify its own private internal states, then we can conclude it is capable of introspection (though see our full paper for a full discussion of all the nuances).
Testing introspection with concept injection
In order to test whether a model can introspect, we need to compare the model’s self-reported “thoughts” to its actual internal states.
To do so, we can use an experimental trick we call concept injection. First, we find neural activity patterns whose meanings we know, by recording the model’s activations in specific contexts. Then we inject these activity patterns into the model in an unrelated context, where we ask the model wheth
