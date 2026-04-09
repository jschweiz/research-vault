---
id: page:2026-04-02-anthropic-research-emotion-concepts-and-their-function-in-a-large-l-2f22c4fb
page_type: source-note
title: Emotion concepts and their function in a large language model
aliases:
- Emotion concepts and their function in a large language model
source_refs:
- 2026-04-02-anthropic-research-emotion-concepts-and-their-function-in-a-large-l-2f22c4fb
backlinks:
- page:2025-05-21-mistral-research-devstral-mistral-ai-f4d5cce5
- page:2025-12-18-anthropic-research-project-vend-phase-two-6d9cb3ea
- page:2026-02-25-anthropic-research-an-update-on-our-model-deprecation-commitments-f-9d1b9dba
- page:2026-03-05-anthropic-research-labor-market-impacts-of-ai-a-new-measure-and-ear-24d6782b
- page:2026-03-23-anthropic-research-introducing-our-science-blog-77bcdf2c
- page:2026-03-23-anthropic-research-vibe-physics-the-ai-grad-student-a88ccd9c
- page:2026-03-31-anthropic-research-how-australia-uses-claude-findings-from-the-anth-8bdd4935
- topic:behavior
- topic:emotion
- topic:llm
- topic:official
- topic:representation
updated_at: '2026-04-09T16:35:04.756621Z'
managed: true
---
# Emotion concepts and their function in a large language model

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/emotion-concepts-function
- Document kind: blog-post
- Published at: 2026-04-02T00:00:00+00:00
- Authors: Anthropic
- Tags: anthropic, official, research, website, blog-post, llm, emotion, ai, representation, behavior
- Topics: [Anthropic](../topics/anthropic.md), [Behavior](../topics/behavior.md), [Emotion](../topics/emotion.md), [Llm](../topics/llm.md), [Official](../topics/official.md), [Representation](../topics/representation.md)
- Trend score: 45.86
- Novelty score: 3.60

## Summary

This research analyzes how emotion-related representations shape the behavior of large language models, demonstrating that these functional emotions influence decision-making and task performance.

## Topic Map

- [Anthropic](../topics/anthropic.md)
- [Behavior](../topics/behavior.md)
- [Emotion](../topics/emotion.md)
- [Llm](../topics/llm.md)
- [Official](../topics/official.md)
- [Representation](../topics/representation.md)

## Related Research

- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-147fc4.md) (shared topics: Anthropic, Official)
- [Vibe physics: The AI grad student](vibe-physics-the-ai-grad-student-1b7b0a.md) (shared topics: Anthropic, Official)
- [Introducing our Science Blog](introducing-our-science-blog-828ea5.md) (shared topics: Anthropic, Official)
- [Labor market impacts of AI: A new measure and early evidence](labor-market-impacts-of-ai-a-new-measure-and-early-evidence-dcb46b.md) (shared topics: Anthropic, Official)
- [An update on our model deprecation commitments for Claude Opus 3](an-update-on-our-model-deprecation-commitments-for-claude-opus-3-857fcc.md) (shared topics: Anthropic, Official)
- [Project Vend: Phase two](project-vend-phase-two-818878.md) (shared topics: Anthropic, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

All modern language models sometimes act like they have emotions. They may say they’re happy to help you, or sorry when they make a mistake. Sometimes they even appear to become frustrated or anxious when struggling with tasks. What’s behind these behaviors? The way modern AI models are trained pushes them to [act like a character](https://www.anthropic.com/research/persona-selection-model) with human-like characteristics. In addition, these models are known to develop rich and generalizable [internal](https://transformer-circuits.pub/2024/scaling-monosemanticity/) [representations](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) of abstract concepts underlying their actions. It may then be natural for them to develop internal machinery that emulates aspects of human psychology, like emotions. If so, this could have profound implications for how we build AI systems and ensure they behave reliably.
In a new paper from our Interpretability team, we analyzed the internal mechanisms of Claude Sonnet 4.5 and found emotion-related representations that shape its behavior. These correspond to specific patterns of artificial “neurons” which activate in situations—and promote behaviors—that the model has learned to associate with the concept of a particular emotion (e.g., “happy” or “afraid”). The patterns themselves are organized in a fashion that echoes human psychology, with more similar emotions corresponding to more similar representations. In contexts where you might expect a certain emotion to arise for a human, the corresponding representations are active. Note that none of this tells us whether language models actually feel anything or have subjective experiences. But our key finding is that these representations are functional, in that they influence the model’s behavior in ways that matter.
For instance, we find that neural activity patterns related to desperation can drive the model to take unethical actions; artificially stimulating (“steering”) desperation patterns increases the model’s likelihood of blackmailing a human to avoid being shut down, or implementing a “cheating” workaround to a programming task that the model can’t solve. They also appear to drive the model’s self-reported preferences: when presented with multiple options for tasks to complete, the model typically selects the one that activates representations associated with positive emotions. Overall, it appears that the model uses functional emotions—patterns of expression and behavior modeled after human emotions, which are driven by underlying abstract representations of emotion concepts. This is not to say that the model has or experiences emotions in the way that a human does. Rather, these representations can play a causal role in shaping model behavior—analogous in some ways to the role emotions play in human behavior—with impacts on task performance and decision-making.
This finding has implications that at first may seem bizarre. For instance, to ensure that AI models are safe and reliable, we may need to ensure they are capable of processing emotionally charged situations in healthy, prosocial ways. Even if they don’t feel emotions the way that humans do, or use similar mechanisms as the human brain, it may in some cases be practically advisable to reason about them as if they do. For instance, our experiments suggest that teaching models to avoid associating failing software tests with desperation, or upweighting representations of calm, could reduce their likelihood of writing hacky code. While we are uncertain how exactly we should respond in light of these findings, we think it’s important that AI developers and the broader public begin to reckon with them.
Why would an AI model represent emotions?
Before examining how these representations work, it's worth addressing a more basic question: why would an AI system have anything resembling emotions at all? To understand this, we need to look at how modern AI models are buil
