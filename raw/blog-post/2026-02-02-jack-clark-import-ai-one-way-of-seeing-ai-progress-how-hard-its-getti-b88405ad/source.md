---
id: 2026-02-02-jack-clark-import-ai-one-way-of-seeing-ai-progress-how-hard-its-getti-b88405ad
kind: blog-post
title: One way of seeing AI progress – how hard it’s getting to design technical interviews
source_url: https://www.anthropic.com/engineering/AI-resistant-technical-evaluations
source_name: Import AI
authors:
- Anthropic
published_at: '2026-02-02T13:31:18Z'
ingested_at: '2026-04-09T20:16:59.224182Z'
content_hash: 016b748cb635703396fe006e132e644b31e5ca16a5d01854e0aa33b84f8eb458
identity_hash: b7de6c31ccc1b718de869d049c2f51dab4fd95f58317843aeb92083b1764ea48
tags:
- newsletter
- ai
- analysis
- policy
- website
- blog-post
- technical interviews
- evaluation
- testing
- human skills
status: active
asset_paths: []
source_id: jack-clark-import-ai
source_pipeline_id: jack-clark-import-ai
external_key: https://jack-clark.net/2026/02/02/import-ai-443-into-the-mist-moltbook-agent-ecologies-and-the-internet-in-transition::story::3:https://www.anthropic.com/engineering/AI-resistant-technical-evaluations
canonical_url: https://www.anthropic.com/engineering/AI-resistant-technical-evaluations
doc_role: derived
parent_id: 2026-02-02-jack-clark-import-ai-import-ai-443-into-the-mist-moltbook-agent-ecolo-cf919aa0
index_visibility: visible
fetched_at: '2026-04-09T20:16:59.224187Z'
short_summary: Anthropic is redesigning its technical interviews and take-home tests because advanced AI systems are now capable of outperforming human candidates. They are exploring ways to design tests that leverage uniquely human skills to evaluate candidates.
lightweight_enrichment_status: succeeded
lightweight_enriched_at: '2026-04-09T22:01:42.898145Z'
lightweight_enrichment_model: gemma4:e2b
lightweight_enrichment_input_hash: 66cd8ae2a2d473deaf82fa8be4e14af14fe5b0c8b4e3f6c58c5a6e9d437ebb3e
lightweight_enrichment_error: null
lightweight_scoring_model: gemma4:e2b
lightweight_scoring_input_hash: 90a2b0d21ff206ca9d6ebe6859c4639f836cbf2ffee397994e9cdbca1dae0e72
lightweight_score:
  relevance_score: 0.75
  source_fit_score: 0.6
  topic_fit_score: 1.0
  author_fit_score: 1.0
  evidence_fit_score: 1.0
  confidence_score: 1.0
  bucket_hint: must_read
  reason: The document directly addresses evaluation methods and the distinction between human and AI capabilities, which aligns perfectly with the user's favorite topics of evaluation and reasoning in LLMs.
  evidence_quotes:
  - Anthropic is redesigning its technical interviews and take-home tests because advanced AI systems are now capable of outperforming human candidates.
  - 'When given the same time limit, Claude Opus 4 outperformed most human applicants. That still allowed us to distinguish the strongest candidates—but then Claude '
  - In a sense, this is an attempt to go ‘off distribution’ to outsmart an AI, while still having a test that holds signal for evaluating human applicants.
---
# One way of seeing AI progress – how hard it’s getting to design technical interviews

Source newsletter: Import AI 443: Into the mist: Moltbook, agent ecologies, and the internet in transition
Source issue: https://jack-clark.net/2026/02/02/import-ai-443-into-the-mist-moltbook-agent-ecologies-and-the-internet-in-transition
Published At: 2026-02-02T13:31:18+00:00
Canonical URL: https://www.anthropic.com/engineering/AI-resistant-technical-evaluations

## Newsletter Context

…Anthropic shares details on how its own AI systems are breaking its favorite technical interview questions… When it comes to technical recruiting, AI companies are caught in a red queen race with their own systems – recruiters and those who design interviews are having to work harder and harder just to keep pace (and ideally exceed) the capabilities of modern AI systems.

Anthropic is no different – in a new blog the company shares how the ceaseless march forward in AI capabilities has repeatedly broken and necessitated the redesign of one of its hardest technical interviews. “Since early 2024, our performance engineering team has used a take-home test where candidates optimize code for a simulated accelerator. Over 1,000 candidates have completed it, and dozens now work here, including engineers who brought up our Trainium cluster and shipped every model since Claude 3 Opus,” Anthropic writes. “But each new Claude model has forced us to redesign the test. When given the same time limit, Claude Opus 4 outperformed most human applicants. That still allowed us to distinguish the strongest candidates—but then Claude Opus 4.5 matched even those. Humans can still outperform models when given unlimited time, but under the constraints of the take-home test, we no longer had a way to distinguish between the output of our top candidates and our most capable model.”

Why this matters – AI may help us identify uniquely human skills that leverage AI: In Anthropic’s case, it found a way to keep outrunning its systems by designing a much weirder take-home test loosely inspired by programming puzzle games from Zachtronics. In a sense, this is an attempt to go ‘off distribution’ to outsmart an AI, while still having a test that holds signal for evaluating human applicants. My instinct is this may itself serve in the future as an amazing aggregate dataset for figuring out where human comparative advantage is – where here, implicitly, this test is leveraging the strong generalization advantage humans hold over AIs. What would it be like to collect 1,000 hard-for-AI tests from all the different companies dealing with this same problem? What might we learn from this about ourselves and what makes us unique relative to the machines? Tantalizing stuff! Read more : Designing AI-resistant technical evaluations (Anthropic Engineering blog) .
