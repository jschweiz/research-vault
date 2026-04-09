---
id: 2026-03-02-jack-clark-import-ai-llms-are-still-very-bad-at-videogames-4b8298cd
kind: article
title: LLMs are still very bad at videogames
source_url: https://p5.js/
source_name: Import AI
authors: []
published_at: '2026-03-02T13:45:27Z'
ingested_at: '2026-04-09T20:16:09.174324Z'
content_hash: 6fb50a7f379c7ce38331f107934027458c199c7dcce2a392c5a1b02d6f8ff3cd
identity_hash: 30508e2c2097ee5331f17884fe98f7600f123ae9248aee578fe6ee703f9a7015
tags:
- newsletter
- ai
- analysis
- policy
- website
- article
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/03/02/import-ai-447-the-agi-economy-testing-ais-with-generated-games-and-agent-ecologies::story::4:https://p5.js/
canonical_url: https://p5.js/
doc_role: derived
parent_id: 2026-03-02-jack-clark-import-ai-import-ai-447-the-agi-economy-testing-ais-with-g-0a17e9c4
index_visibility: visible
fetched_at: '2026-04-09T20:16:09.174328Z'
short_summary: null
lightweight_enrichment_status: pending
lightweight_enriched_at: null
lightweight_enrichment_model: null
lightweight_enrichment_input_hash: null
lightweight_enrichment_error: null
lightweight_scoring_model: null
lightweight_scoring_input_hash: null
lightweight_score: null
---
# LLMs are still very bad at videogames

Source newsletter: Import AI 447: The AGI economy; testing AIs with generated games; and agent ecologies
Source issue: https://jack-clark.net/2026/03/02/import-ai-447-the-agi-economy-testing-ais-with-generated-games-and-agent-ecologies
Published At: 2026-03-02T13:45:27+00:00
Canonical URL: https://p5.js/

## Newsletter Context

…GAMESTORE highlights a dumb side of modern AI, as well as suggesting a new way to build benchmarks… Researchers with MIT, Harvard, the University of British Columbia, Princeton University, the University of Cambridge, and the Universitat Politècnica de València, have built and released AI GAMESTORE, a benchmark that tests out how well AIs can do compared to humans at playing simple games found on the web. The results are pretty damning for the AI systems, with “state-of-the-art models achieving less than 30% of the human baseline on average, while taking 15-20x more time to compute than humans”.

What AI GAMESTORE is: AI GAMESTORE is a set of 100 games, which are simplified and recreated versions of popular games that people play. AI GAMESTORE was built by the authors sampling 7,500 games from the App Store, then filtering down to only those with 10,000+ reviews and a 4.5+ rating. After this, they further filtered the games using Gemini Flash 2.5, which assessed 1) whether the games can be played within a few minutes, 2) can be built in p5.js , 3) can have a quantifiable way of viewing performance, and 4) do not require extensive game-specific knowledge (e.g., poker). AI makes games to test AI: Following this, they use Claude 4.5 Sonnet to read the descriptions and other data to make a simplified version of each game in p5.js , then this game is tested for playability, then refined by a human playing the game and iteratively prompting an LLM to improve it. “Each refinement step takes about 2 minutes. On average, this process took 4.7 refinement steps for all 100 generated games,” they write. “The end-to-end process of generating and refining a new game with human-in-the-loop can be completed in approximately 30 minutes on average”.

Labeling for skills: Each finalized game is labeled by humans with a particular emphasis on the types of cognitive demand the games entail. These labels are: VP = Visual Processing; ST = Spatial-temporal Coordination; ME = Memory; PL = Planning; WM = World Model Learning; PH = Physical Reasoning; SO = Social Reasoning.

Cutting edge LLMs are very bad at this: The authors compare the performance of roughly ~100 humans against the performance of several cutting edge LLMs on the corpus. LLMs studied include: GPT-5.2, GPT-5-Mini, Gemini-2.5-Flash, Claude-Opus-4.5, Qwen-VL-32B, and LLama-4-Maverick. “While the evaluated models demonstrate the ability to navigate and interact with most game environments, a substantial performance gap remains between AI agents and human participants”, the researchers write. “State-of-the-art models like GPT-5.2, GEMINI-2.5-PRO, and CLAUDE-OPUS-4.5, all achieve geometric mean scores of less than 10% of the human baseline”. And it gets worse the more you look: The LLMs are also playing with advantages that humans don’t get – each human got 120 seconds to play each game, while each LLM got the same time, but they’re so bad at vision and low-latency control that the researchers gave them a crutch: “We pause the game every second to query the model to elicit five lists of actions to perform in the next second, with each action list corresponding to a 0.2 second segment of gameplay. Upon receiving the model response, the game is resumed and the actions are applied. The loop continues until the game is won or it reaches 2 minutes of game play (120 API calls). When you factor this in, the models look worse than humans on this dimension of time: “This is because the models spend a few minutes thinking, in addition to typically a few seconds of response latency per query; as a result, many models spend at least 20 minutes on the game, while humans play the games within 2 minutes.”

Why this matters – this is both an interesting benchmark, and a clever way to generate more benchmarks in the future: GAMESTORE feels like a promising benchmark, especially for modern LLMs which wrap in visual capabilities, as well as an inherently clever way to use AIs to bootstrap the creation of new environments in which to train AI systems in. Read more : AI Gamestore: Scalable, Open-Ended Evaluation of Machine General Intelligence with Human Games (arXiv) . Try out some of the games at the official site (AI Gamestore) .
