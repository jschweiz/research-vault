---
id: undated-the-batch-research-claude-codes-source-code-leaked-exposing-potenti-0c9adaf3
kind: blog-post
title: Claude Code’s Source Code Leaked, Exposing Potential Future Features Kairos and autoDream
source_url: https://www.deeplearning.ai/the-batch/claude-codes-source-code-leaked-exposing-potential-future-features-kairos-and-autodream
source_name: The Batch Research
authors:
- Chaofan Shou
published_at: '2026-04-03T11:33:35-07:00'
ingested_at: '2026-04-09T20:52:18.909005Z'
content_hash: 8d73d7ad65d14a2e4c593d98216e94fed0716f2a1deaec5307fa94d2a9a3fc00
identity_hash: de1df0f9c0fbe9d2c47375a3328ad431b8714fec90230831ea8ddb690393402c
tags:
- deeplearning-ai
- official
- research
- website
- blog-post
- claude
- source code
- leak
- features
- kairos
status: active
asset_paths:
- original.html
source_id: the-batch-research
source_pipeline_id: the-batch-research
external_key: https://www.deeplearning.ai/the-batch/claude-codes-source-code-leaked-exposing-potential-future-features-kairos-and-autodream
canonical_url: https://www.deeplearning.ai/the-batch/claude-codes-source-code-leaked-exposing-potential-future-features-kairos-and-autodream
doc_role: primary
parent_id: null
index_visibility: visible
fetched_at: '2026-04-13T18:33:33.701222Z'
short_summary: The source code for Claude Code was leaked, exposing over 512,000 lines of code and revealing internal architectural details. The leak also hints at future features like the Kairos subsystem and an 'undercover mode'.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:09:49.049876Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 5788f1fc69117994c87891956f6283d9c056df3fc0b37771656195b743481eab
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
The inner workings of the popular coding agent Claude Code are available for all to see.
What’s new: A recent version of Claude Code’s Node.js package accidentally included a key that [revealed](https://arstechnica.com/ai/2026/03/entire-claude-code-cli-source-code-leaks-thanks-to-exposed-map-file/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) the code behind its command-line interface. Chaofan Shou, an intern at the blockchain startup Solayer Labs, unlocked the code and published it. Engineers rapidly deciphered its secrets.
What happened: Typically, when a software company publishes closed-source code, a bundler tool scrambles the source files. But when Anthropic published version 2.1.88 to Claude Code’s npm registry on March 30, it included a source map file that serves as a translation key to decode the files.
- Shou discovered the source map, decoded the files, and
[published](https://x.com/Fried_rice/status/2038894956459290963?s=20&utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)them on the X social media network, exposing over 512,000 lines of code across 1,900 files. - Anthropic promptly removed the package from the npm registry and GitHub. However, it had already been forked more than 40,000 times.
- An Anthropic spokesperson
[confirmed](https://www.cnbc.com/2026/03/31/anthropic-leak-claude-code-internal-source.html?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)the leak, calling it “a release packaging issue caused by human error, not a security breach,” and stated that no user or customer data was exposed.
How Claude Code works: Engineers who studied the source code [say](https://thenewstack.io/claude-code-source-leak?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) Claude Code is built less like a chatbot wrapper and more like a small, dedicated operating system.
- Each of more than 40 different tools (that read files, execute bash commands, fetch information from the web, and the like) have their own modules and permission gates, separating them from both the language model and the user’s computer. Background processes manage memory, and the permission gates prevent the agent from running arbitrary code beyond defined resources.
- Claude Code spawns swarms of subagents that act as support agents with their own tool sets and resources. A controller agent delegates their permissions and subtasks. Each swarm team has a common memory to help coordinate its actions.
- Claude Code’s memory has
[three tiers](https://x.com/himanshustwts/status/2038924027411222533?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag). (i) A memory index called MEMORY.MD is always loaded but contains only pointers to (ii) Markdown memory files, which are called only when needed. In addition, (iii) JSON transcript files log file changes. These are not loaded into active context, but they can be searched for relevant lines of text. This three-tiered structure prevents memory bloat, keeps irrelevant or incomplete information out of the context window, and resolves all conflicts between the agent’s memory and the actual state of a file. - Claude Code uses a three-stage
[strategy](https://wavespeed.ai/blog/posts/claude-code-architecture-leaked-source-deep-dive/?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag)to compress memories and keep conversations within the context limit. (i) The first truncates cached tool outputs locally. (ii) The second generates a structured, 20,000-token summary of the most recent session when a conversation approaches the context limit. (iii) The third compresses the entire conversation, then adds recently accessed files (up to 5,000 tokens per file), active plans, and relevant skills.
Future capabilities?: The source map also reveals some of Anthropic’s possible [plans](https://venturebeat.com/technology/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know?utm_campaign=The%20Batch&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz-9SKOdKwZtszt2gyZnkk-z2Pc5ri4XwTsPdzj93-7ldUp5XLi9VCALlqgWZ3fVVC1T5uOag) for Claude. For instance, several undisclosed features sit behind flags that compile to “false” in the published build, a sign that they are currently in-progress and may be included in a future release.
- A subsystem called Kairos (Greek for timely) would run as an always-on background agent. Its logic system, called autoDream, merges duplicate memories, eliminates contradictions, resolves speculations, and otherwise prunes memory to make stored data more suitable for action.
- Other hidden features include a voice interface, a subagent called Ultraplan that sends resource-intensive tasks to the cloud, and a persona called Buddy comments on your work, presumably to boost engagement.
- Claude Code has a previously undisclosed “undercover mode” that allows the agent to commit files to public git repositories without leaving a signature or other sign that it has been active in a repository. This feature may enable Anthropic to test advanced models and work with partners that have not been announced publicly without inadvertently disclosing such activities.
- The files include references to a Claude 4.6 variant code named Capybara and an unreleased model called Numbat. Capybara version 8 makes false or exaggerated claims around 30 percent of the time, well above an earlier version’s 16.7 percent, suggesting the latest version of the model is tuned to jump to conclusions rather than show restraint.
Why it matters: The leak offers a peek under the hood of one of the most advanced and popular agentic systems available. We can see how Claude Code works and how it may work in the near future, revise our own systems to match, or differentiate our products by making different choices.
We’re thinking: The AI community is rightly concerned that software agents can inadvertently delete codebases or publish private files. Humans can, too!
