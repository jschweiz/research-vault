---
id: page:2026-03-06-the-batch-research-googles-aletheia-uses-gemini-3-deep-think-to-fin-7faeaab3
page_type: source-note
title: Google’s Aletheia Uses Gemini 3 Deep Think to Find Original Mathematics Solutions
aliases:
- Google’s Aletheia Uses Gemini 3 Deep Think to Find Original Mathematics Solutions
source_refs:
- 2026-03-06-the-batch-research-googles-aletheia-uses-gemini-3-deep-think-to-fin-7faeaab3
backlinks:
- page:2026-03-16-the-batch-research-openais-gpt-5-4-pro-and-gpt-5-4-thinking-challen-f1e2ee28
- topic:agentic-systems
- topic:deep-think
- topic:gemini
- topic:math
updated_at: '2026-04-09T23:10:02.702491Z'
managed: true
---
# Google’s Aletheia Uses Gemini 3 Deep Think to Find Original Mathematics Solutions

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: The Batch Research
- Canonical URL: https://www.deeplearning.ai/the-batch/googles-aletheia-uses-gemini-3-deep-think-to-find-original-mathematics-solutions
- Document kind: blog-post
- Published at: 2026-03-06T07:50:04-08:00
- Authors: Tony Feng, Quoc V. Le, Thang Luong
- Tags: deeplearning-ai, official, research, website, blog-post, llms, math, agentic_systems, gemini, deep_think
- Topics: [Agentic Systems](../topics/agentic-systems.md), [Deep Think](../topics/deep-think.md), [Deeplearning Ai](../topics/deeplearning-ai.md), [Gemini](../topics/gemini.md), [Llms](../topics/llms.md), [Math](../topics/math.md)
- Trend score: 25.71
- Novelty score: 2.20

## Summary

Google introduced Aletheia, an agentic system using Gemini 3 Deep Think to generate, verify, and revise solutions to unsolved math problems. Researchers found Aletheia solved 212 of Paul Erdős's unsolved problems.

## Topic Map

- [Agentic Systems](../topics/agentic-systems.md)
- [Deep Think](../topics/deep-think.md)
- [Deeplearning Ai](../topics/deeplearning-ai.md)
- [Gemini](../topics/gemini.md)
- [Llms](../topics/llms.md)
- [Math](../topics/math.md)

## Related Research

- [OpenAI’s GPT-5.4 Pro and GPT-5.4 Thinking Challenge Google’s Gemini 3.1 Pro Preview as Best All-Around AI Model](openais-gpt-5-4-pro-and-gpt-5-4-thinking-challenge-googles-gemin-00277e.md) (shared topics: Deeplearning Ai, Gemini)
- [Nano Banana 2, aka Gemini 3.1 Flash Image, Makes Edits Easier and Faster](nano-banana-2-aka-gemini-3-1-flash-image-makes-edits-easier-and--52d417.md) (shared topics: Deeplearning Ai, Gemini)
- [Google introduces notebooks to reduce repeated prompts by maintaining context and files within a single workspace](google-introduces-notebooks-to-reduce-repeated-prompts-by-mainta-de3cec.md) (shared topics: Gemini)
- [Meta's Superintelligence Lab unveils its first public model, Muse Spark](meta-s-superintelligence-lab-unveils-its-first-public-model-muse-5c1dbe.md) (shared topics: Agentic Systems)
- [Good Taste the Only Real Moat Left](good-taste-the-only-real-moat-left-825f84.md) (shared topics: Llms)
- [Test-Time Training End-to-End (TTT-E2E) Retrains Model Weights to Handle Long Inputs](test-time-training-end-to-end-ttt-e2e-retrains-model-weights-to--b1f1bd.md) (shared topics: Deeplearning Ai)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

LLMs have achieved gold-medal performance in math competitions. An agentic system showed strength in mathematical research as well.
What’s new: Tony Feng, Quoc V. Le, Thang Luong, and colleagues at Google introduced [Aletheia](https://arxiv.org/abs/2602.10177?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX), an agent that generated, verified, and revised solutions to previously unsolved math problems. Aletheia is an agentic workflow for math research that uses the latest update of Gemini 3 Deep Think, a specialized reasoning mode of the Gemini 3 Pro model for subscribers to the company’s top-tier AI service. Concurrently, Google made Gemini 3 Deep Think more widely available via API.
Gemini 3 Deep Think: Google bills Deep Think as its most advanced reasoning mode, geared toward multi-step tasks in math, science, and engineering. It generates multiple chains of reasoning in parallel, considers them, and revises or combines them to produce final output.
- Input/output: Text, image, video, audio, pdf in (up to 1 million tokens); text out (up to 65,000 tokens)
- Performance: Achieved state of the art on HLE (48.4 percent without tools), ARC-AGI-2 (84.6 percent), Codeforces (3455 Elo), GPQA Diamond (93.8 percent)
- Availability: Via Gemini app with Google AI Ultra subscription ($250/month), via API with
[early access](https://forms.gle/eEF5natXTQimPhYH9?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) - Features: web search, code execution
- Undisclosed: Google has disclosed little information about how it built Gemini 3 Pro and the Deep Think capability
How it works: Aletheia is an agentic workflow with three parts — generator, verifier, and reviser — all powered by Gemini 3 Deep Think.
- Given a problem, the generator produces an initial solution.
- The verifier checks that solution and marks it either as complete, in need of fixes, or critically flawed.
- If the solution needs fixes, the reviser takes the problem and solution, and generates a modified version of the solution, which it feeds back to the verifier.
- If the solution is critically flawed, the generator takes the problem again and generates a new solution.
- The process repeats until the verifier marks a problem as solved or an author-set number of model calls occurs.
Results: Researchers have used Aletheia in six published papers to date: two in which Aletheia did essentially all the work, two in which both humans and Aletheia contributed significantly, and two in which humans did most of the work and Aletheia helped a little. The authors note that Aletheia works well in situations where broad knowledge across subfields of math is helpful, but it doesn’t have as much depth within subfields as a human specialist.
- One of the papers offers four novel solutions to unsolved Erdős problems, a set of difficult-to-solve mathematical conjectures proposed by the mathematician
[Paul Erdős](https://en.wikipedia.org/wiki/Paul_Erd%C5%91s?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX). Of the remaining[700](https://erdosproblems.com/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX)unsolved Erdős problems, Aletheia said it found solutions to 212 of them. - Mathematicians examined the 212 solutions and found them correct or incorrect in 200 cases. (For the other 12, the problem or solution was ambiguous.) Of the 200, 137 (68.5%) were incorrect, 63 (31.5%) were technically correct under some interpretation of the problem, and 13 (6.5%) were correct under the intended interpretation.
- The authors examined the 13 correct answers to evaluate their novelty. The problem had already been solv
