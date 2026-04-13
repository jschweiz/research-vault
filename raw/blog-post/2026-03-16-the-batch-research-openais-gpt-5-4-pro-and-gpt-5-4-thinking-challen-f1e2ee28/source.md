---
id: 2026-03-16-the-batch-research-openais-gpt-5-4-pro-and-gpt-5-4-thinking-challen-f1e2ee28
kind: blog-post
title: OpenAI’s GPT-5.4 Pro and GPT-5.4 Thinking Challenge Google’s Gemini 3.1 Pro Preview as Best All-Around AI Model
source_url: https://www.deeplearning.ai/the-batch/openais-gpt-5-4-pro-and-gpt-5-4-thinking-challenge-googles-gemini-3-1-pro-preview-as-best-all-around-ai-model
source_name: The Batch Research
authors:
- OpenAI
published_at: '2026-03-16T08:27:57-07:00'
ingested_at: '2026-04-09T20:54:35.481910Z'
content_hash: 2817bd7ac8faf73423a72101e3a18d87f7ebca84fea56af855742bdf6f355b9e
identity_hash: d7febdf2113e923e75f32764319e5ade08572c0c20f3bb9e8e47c686e366aa2e
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- gpt-5.4
- gemini
- ai-models
- tool-use
- performance
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/openais-gpt-5-4-pro-and-gpt-5-4-thinking-challenge-googles-gemini-3-1-pro-preview-as-best-all-around-ai-model
canonical_url: https://www.deeplearning.ai/the-batch/openais-gpt-5-4-pro-and-gpt-5-4-thinking-challenge-googles-gemini-3-1-pro-preview-as-best-all-around-ai-model
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:33:51.750314Z'
short_summary: OpenAI's GPT-5.4 models, including the Pro variant, have achieved state-of-the-art performance on various benchmarks, challenging Google's Gemini models. The models are designed to enhance tool use and reasoning, showing strong performance in tasks related to knowledge work and computer use.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:48.279748Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 46f229605d4f75892b5dc4d2d2de84e616cbb6ad6f276b54447226053572579f
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
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
Why it matters: OpenAI’s GPT 5.4 has vaulted over Anthropic’s Claude — for the moment — to challenge Google’s Gemini for the top spot. OpenAI touts the GPT-5.4 family’s improved performance per token, but it still requires twice as many tokens as Gemini 3.1 Pro Preview to match the latter’s performance, and its higher efficiency is largely negated by its higher price. GPT-5.4 Pro is a state-of-the art coding model, and costs less than Claude Opus 4.6 to complete coding tasks. But Google’s ability to keep Gemini 3.1 Preview’s price low and overall intelligence high, along with its ability to process audio and video, remains a formidable obstacle for any AI company that aims to become the undisputed leader.
We’re thinking: GPT-5.4 ranks highest on benchmarks developed internally by OpenAI, as you would expect. But these metrics show that the models are built to solve hard problems in automating office work. GPT-5.4 Pro turned in impressive performance on [GDPval](https://openai.com/index/gdpval/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes) (83 percent win or tie rate against professionals across knowledge-work tasks like writing legal briefs and customer-support conversations) and [OSWorld-Verified](https://xlang.ai/blog/osworld-verified?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9JC4D-W5UcjdQ8rV37QH0gl9Mg2LEqt0aAgHOHo4FxPDoSs6tsWv62X4V9mcrBXuP6xOes) (75 percent success rate on computer use tasks like navigating websites and updating spreadsheets from files, above the 72.4 percent human baseline). Given the high human costs of this work, GPT-5.4 Pro, even at xhigh reasoning, may turn out to be a bargain.
