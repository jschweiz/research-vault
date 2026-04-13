---
id: page:2026-03-16-the-batch-research-openais-gpt-5-4-pro-and-gpt-5-4-thinking-challen-f1e2ee28
page_type: source-note
title: OpenAI’s GPT-5.4 Pro and GPT-5.4 Thinking Challenge Google’s Gemini 3.1 Pro Preview as Best All-Around AI Model
aliases:
- OpenAI’s GPT-5.4 Pro and GPT-5.4 Thinking Challenge Google’s Gemini 3.1 Pro Preview as Best All-Around AI Model
source_refs:
- 2026-03-16-the-batch-research-openais-gpt-5-4-pro-and-gpt-5-4-thinking-challen-f1e2ee28
backlinks:
- page:2026-03-06-the-batch-research-googles-aletheia-uses-gemini-3-deep-think-to-fin-7faeaab3
- topic:ai-models
- topic:gemini
- topic:gpt-5-4
- topic:reasoning
- topic:tool-use
updated_at: '2026-04-09T23:08:05.794255Z'
managed: true
---
# OpenAI’s GPT-5.4 Pro and GPT-5.4 Thinking Challenge Google’s Gemini 3.1 Pro Preview as Best All-Around AI Model

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/openais-gpt-5-4-pro-and-gpt-5-4-thinking-challenge-googles-gemini-3-1-pro-preview-as-best-all-around-ai-model
- Document kind: blog-post
- Published at: 2026-03-16T08:27:57-07:00
- Authors: OpenAI
- Tags: deeplearning-ai, official, research, website, blog-post, gpt-5.4, gemini, ai-models, tool-use, performance
- Topics: [Tool Use](../topics/tool-use.md), [Reasoning](../topics/reasoning.md), [Ai Models](../topics/ai-models.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Gemini](../topics/gemini.md), [Gpt 5 4](../topics/gpt-5-4.md)
- Trend score: 30.85
- Novelty score: 6.80

## Summary

OpenAI's GPT-5.4 models, including the Pro variant, have achieved state-of-the-art performance on various benchmarks, challenging Google's Gemini models. The models are designed to enhance tool use and reasoning, showing strong performance in tasks related to knowledge work and computer use.

## Topic Map

- [Tool Use](../topics/tool-use.md)
- [Reasoning](../topics/reasoning.md)
- [Ai Models](../topics/ai-models.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Gemini](../topics/gemini.md)
- [Gpt 5 4](../topics/gpt-5-4.md)

## Related Research

- [Google’s Aletheia Uses Gemini 3 Deep Think to Find Original Mathematics Solutions](googles-aletheia-uses-gemini-3-deep-think-to-find-original-mathe-ded24a.md) (shared topics: Deeplearning Ai, Gemini)
- [Nano Banana 2, aka Gemini 3.1 Flash Image, Makes Edits Easier and Faster](nano-banana-2-aka-gemini-3-1-flash-image-makes-edits-easier-and--52d417.md) (shared topics: Deeplearning Ai, Gemini)
- [Meta debuts Muse Spark combining multimodal inputs, tool use, and agent orchestration in one system](meta-debuts-muse-spark-combining-multimodal-inputs-tool-use-and--acb2ab.md) (shared topics: Tool Use)
- [Google introduces notebooks to reduce repeated prompts by maintaining context and files within a single workspace](google-introduces-notebooks-to-reduce-repeated-prompts-by-mainta-de3cec.md) (shared topics: Gemini)
- [AI Assistance Reduces Persistence and Hurts Independent Performance](ai-assistance-reduces-persistence-and-hurts-independent-performa-21bf42.md) (shared topics: Reasoning)
- [Eight years of wanting, three months of building with AI](eight-years-of-wanting-three-months-of-building-with-ai-11c063.md) (shared topics: Tool Use)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

OpenAI updated its flagship models, extending the ability to use tools and setting the state of the art on a handful of benchmarks, and priced them at the top of the market. Its coding and agentic abilities have enabled Codex, OpenAI’s competitor to Anthropic’s Claude Code, to leap ahead.
What’s new: GPT-5.4 comes in two variants, Thinking and Pro, both with an expanded context window relative to GPT-5.2. (Only two days elapsed between the launch of GPT-5.3 and GPT-5.4, and OpenAI offered no explanation.) GPT-5.4 models are trained to use computers natively and help agents find and use tools more efficiently, a capability called tool search.
- Input/output: Text, images in (up to 1,050,000 tokens), text out (up to 128,000 tokens)
- Architecture: Mixture-of-experts transformer
- Features: Tool use (Google search, Python code execution, file search, function calling), tool search, computer use, adjustable reasoning (low, medium, high, xhigh)
- Performance: In independent tests, GPT-5.4 Pro with xhigh reasoning achieved state of the art on GDP-Val-AA, BrowseComp, Terminal-Bench-Hard, SWE-Bench-Pro, and MCP Atlas; it’s just behind Gemini 3.1 Pro Preview on MMMU-Pro and Humanity’s Last Exam (without tools) and just behind Gemini 3 Deep Think on ARC-AGI-1 and ARC-AGI-2
- Availability/price: GPT-5.4 is available in ChatGPT via subscription at Plus, Team, and Pro tiers. Via API, GPT-5.4 is available for $2.50/$0.25/$15 per 1 million input/cached/output tokens, and GPT-5.4 Pro is priced at $30/$180 per 1 million input/output tokens.
- Knowledge cutoff: August 2025
- Undisclosed: Parameter count, architecture details, training methods
How it works: As is typical of closed models, OpenAI disclosed few details about how it built GPT-5.4 and GPT-5.4 Pro. The model is a sparse mixture-of-experts transformer pretrained on text, code, and images scraped from the web alongside licensed materials, user data, and synthetic data. It was fine-tuned via reinforcement learning on datasets that covered multi-step reasoning, solving problems, and proving theorems.
Performance: GPT-5.4 Pro leaped over GPT-5.2 Pro and Claude 4.6 Opus to achieve a number of state-of-the-art metrics in independent tests by Artificial Analysis. But even in OpenAI’s own tests, it underperformed Gemini 3.1 Pro Preview in several tasks and cost more to run the same tests.
- On the Artificial Analysis
[Intelligence Index](https://artificialanalysis.ai/models/gpt-5-4?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes), a weighted average of 10 benchmarks that focus on economically useful work, GPT-5.4 Pro set to xhigh reasoning nearly tied Gemini 3.1 Pro Preview with reasoning (57 points at a cost of $2,950 vs. 57.2 points at a cost of $892), but outperformed Claude Opus 4.6 set to max reasoning (53 points, $2,486), GPT-5.3 Codex set to xhigh reasoning (54 points, $1,650), and the open-weights GLM-5 (50 points, $547). It led three of the index’s 10 component benchmarks. - GPT-5.4 Pro set to xhigh topped Artificial Analysis’ Coding and Agentic indices (subsets of the Intelligence Index devoted to each broad category), with scores of 57 and 69 points, topping Gemini 3.1 Pro Preview (56 points) and Claude Opus 4.6 (68 points).
- On
[ARC-AGI-2](https://arcprize.org/leaderboard?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes)visual logic puzzles, GPT-5.4 Pro set to xhigh (83.3 percent) came in ahead of Gemini 3.1 Pro Preview (74.0 percent) and fractionally behind Gemini 3 Deep Think (84.6 percent).
Why it matters: OpenAI’s GPT 5.4 has vaulted over Anthropic’s Claude — for the moment — to challenge Google’s Gemini for the top spot. OpenAI touts the GPT-5.4 family’s improved performance per token, but it still requires twice as many tokens as Gemini 3.1 Pro Preview to match the latter’s perf
