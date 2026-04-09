---
id: 2026-03-06-the-batch-research-googles-aletheia-uses-gemini-3-deep-think-to-fin-7faeaab3
kind: blog-post
title: Google’s Aletheia Uses Gemini 3 Deep Think to Find Original Mathematics Solutions
source_url: https://www.deeplearning.ai/the-batch/googles-aletheia-uses-gemini-3-deep-think-to-find-original-mathematics-solutions
source_name: The Batch Research
authors:
- Tony Feng
- Quoc V. Le
- Thang Luong
published_at: '2026-03-06T07:50:04-08:00'
ingested_at: '2026-04-09T20:54:41.002830Z'
content_hash: 4522f2ba865da3f67cc3c30013918ecc2b20d1499f840131f7e5052d008e9cb1
identity_hash: 1e796257b6e2b282dba4fca91cadf1c0ee026b4ea471a45eb4564613202c4253
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- llms
- math
- agentic_systems
- gemini
- deep_think
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/googles-aletheia-uses-gemini-3-deep-think-to-find-original-mathematics-solutions
canonical_url: https://www.deeplearning.ai/the-batch/googles-aletheia-uses-gemini-3-deep-think-to-find-original-mathematics-solutions
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-09T21:59:41.064651Z'
short_summary: Google introduced Aletheia, an agentic system using Gemini 3 Deep Think to generate, verify, and revise solutions to unsolved math problems. Researchers found Aletheia solved 212 of Paul Erdős's unsolved problems.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T20:59:31.612594Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 18408c29d26fd2badd201bb239ad98f14bb4c3af4c4de2401ed7b94ae93f73dd
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
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
- The authors examined the 13 correct answers to evaluate their novelty. The problem had already been solved in 9 of them: Aletheia either identified the solution from existing research or solved a problem that had a solution in existing research.
- The remaining four solutions were novel.
Behind the news: AI-assisted proofs have had limited but real success. In most [previous](https://arxiv.org/abs/2510.23513?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) [work](https://arxiv.org/abs/2512.14575?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX), researchers used an LLM to help them prove a given theorem, as opposed to building a generalist system like Aletheia. Most similar would be Google’s [AlphaEvolve](https://www.deeplearning.ai/the-batch/googles-alphaevolve-uses-llms-and-evolutionary-code-to-solve-complex-math-and-speed-up-gemini-training/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX), an agentic system that improved algorithms for scheduling compute usage in a data center and multiplying matrices.
Why it matters: Agentic systems are becoming useful mathematical tools that can work with mathematicians to help generate new methods, roadmaps, and the like. If, like Aletheia, an agent’s strength is its breadth of knowledge, it may accelerate research into problems that touch on knowledge from many subfields, while human specialists continue to dive into their favorite fields.
We’re thinking: Erdős proposed nearly 1,200 problems between the early 1930s and his death in 1996. Fewer than 500 have been solved, but AI models have [helped](https://github.com/teorth/erdosproblems/wiki/AI-contributions-to-Erd%C5%91s-problems?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-__PLGlWst6ErppMVsgt5XeNmlrvvBPZnQ4ZW6YCtaQ-ifMXNEgKyU1jQoozrmdTu5PemqX) to solve around 100 of them in the past six months alone!
