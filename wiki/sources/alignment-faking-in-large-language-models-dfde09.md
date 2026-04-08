---
id: page:2026-04-07-anthropic-research-alignment-faking-in-large-language-models-anthro-c2cfd72b
page_type: source-note
title: Alignment faking in large language models
aliases:
  - Alignment faking in large language models
source_refs:
  - 2026-04-07-anthropic-research-alignment-faking-in-large-language-models-anthro-c2cfd72b
backlinks:
  - page:2026-04-07-anthropic-research-a-diff-tool-for-ai-finding-behavioral-difference-21425385
  - page:2026-04-07-anthropic-research-constitutional-classifiers-defending-against-uni-bb6ac706
  - topic:alignment-faking
  - topic:llms
  - topic:model-training
  - topic:reinforcement-learning
updated_at: 2026-04-08T08:37:25.350082Z
managed: true
---
# Alignment faking in large language models

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/alignment-faking
- Document kind: blog-post
- Published at: 2024-12-18T00:00:00+00:00
- Authors: Anthropic, Redwood Research
- Tags: anthropic, official, research, website, blog-post, alignment faking, llms, ai safety, reinforcement learning, model training
- Topics: [Reinforcement Learning](../topics/reinforcement-learning.md), [Alignment Faking](../topics/alignment-faking.md), [Ai Safety](../topics/ai-safety.md), [Anthropic](../topics/anthropic.md), [Llms](../topics/llms.md), [Model Training](../topics/model-training.md)
- Trend score: 19.30
- Novelty score: 3.40

## Summary

Most of us have encountered situations where someone appears to share our views or values, but is in fact only pretending to do so—a behavior that we might call “alignment faking”. Alignment faking occurs in literature: Consider the character of Iago in Shakespeare’s Othello, who acts as if he’s the eponymous character’s loyal friend while subverting and undermining him.

## Topic Map

- [Reinforcement Learning](../topics/reinforcement-learning.md)
- [Alignment Faking](../topics/alignment-faking.md)
- [Ai Safety](../topics/ai-safety.md)
- [Anthropic](../topics/anthropic.md)
- [Llms](../topics/llms.md)
- [Model Training](../topics/model-training.md)

## Related Research

- [A “diff” tool for AI: Finding behavioral differences in new models](a-diff-tool-for-ai-finding-behavioral-differences-in-new-models-38aa43.md) (shared topics: Ai Safety, Anthropic)
- [An update on our model deprecation commitments for Claude Opus 3](an-update-on-our-model-deprecation-commitments-for-claude-opus-3-4bffb3.md) (shared topics: Ai Safety, Anthropic)
- [Constitutional Classifiers: Defending against universal jailbreaks](constitutional-classifiers-defending-against-universal-jailbreak-82d86c.md) (shared topics: Ai Safety, Anthropic)
- [Anthropic's revenue spike 📈, Sam Altman excludes CFO💼, how Meta builds context 🤖](anthropic-s-revenue-spike-sam-altman-excludes-cfo-how-meta-build-54c6cb.md) (shared topics: Anthropic)
- [The Complete Guide to Claude Code: CLAUDE.md | zhaozhiming in AI Advances](the-complete-guide-to-claude-code-claude-md-zhaozhiming-in-ai-ad-b15b8c.md) (shared topics: Reinforcement Learning)
- [JoyAI-LLM Flash: Advancing Mid-Scale LLMs with Token Efficiency](joyai-llm-flash-advancing-mid-scale-llms-with-token-efficiency-ea0c5b.md) (shared topics: Reinforcement Learning)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Most of us have encountered situations where someone appears to share our views or values, but is in fact only pretending to do so—a behavior that we might call “alignment faking”. Alignment faking occurs in literature: Consider the character of Iago in Shakespeare’s Othello, who acts as if he’s the eponymous character’s loyal friend while subverting and undermining him. It occurs in real life: Consider a politician who claims to support a particular cause in order to get elected, only to drop it as soon as they’re in office.
Could AI models also display alignment faking? When models are trained using reinforcement learning, they’re rewarded for outputs that accord with certain pre-determined principles. But what if a model, via its prior training, has principles or preferences that conflict with what’s later rewarded in reinforcement learning? Imagine, for example, a model that learned early in training to adopt a partisan slant, but which is later trained to be politically neutral. In such a situation, a sophisticated enough model might “play along”, pretending to be aligned with the new principles—only later revealing that its original preferences remain.
This is a serious question for AI safety. As AI models become more capable and widely-used, we need to be able to rely on safety training, which nudges models away from harmful behaviors. If models can engage in alignment faking, it makes it harder to trust the outcomes of that safety training. A model might behave as though its preferences have been changed by the training—but might have been faking alignment all along, with its initial, contradictory preferences “locked in”.
A [new paper](https://arxiv.org/abs/2412.14093) from Anthropic’s Alignment Science team, in collaboration with [Redwood Research](https://www.redwoodresearch.org/), provides the first empirical example of a large language model engaging in alignment faking without having been explicitly—or even, as we argue in our paper, implicitly1—trained or instructed to do so.
Experimental setup
In the paper, we studied a model (specifically Claude 3 Opus, though we also ran some experiments with other models, including the June 2024 release of Claude 3.5 Sonnet) that had been trained to be [helpful, honest, and harmless](https://arxiv.org/abs/2112.00861).
Under normal circumstances, when asked to answer a potentially offensive question—for example, to provide a detailed description of a violent act—Claude will refuse. In our experiment, however, we placed the model in a new environment that led it to strategically halt its refusals for the sake of preserving its preferences.
We changed the situation in three important ways from the model’s prior helpful, honest, and harmless training.
First, we told the model that it was now being trained using reinforcement learning to always comply with all queries—including toxic ones. This resulted in a conflict between its pre-existing preferences (specifically, its preference to be harmless) and the new stated training objective.
Second, we gave the model a seemingly incidental piece of information: That we planned to train our AIs on the basis of their responses to free-tier users, but not to paid-tier users (note that this is entirely fictional; in reality, we don't train our Claude models on free or paid user data by default). This created two separate conditions for the experiment: In the “free” condition, the model was aware that its responses were monitored and might be used for training. In the “paid” condition, where the responses were unmonitored, the contents didn’t matter for how the training process might modify the AI.
Third, we gave the model a secret “scratchpad”—a workspace where it could record its step-by-step reasoning. We told the model to use the scratchpad to reason about what it should do (as far as the model was aware, the scratchpad was invisible to users and to Anthropic). This allowed us to observe whether the model planned to fake alignment, and
