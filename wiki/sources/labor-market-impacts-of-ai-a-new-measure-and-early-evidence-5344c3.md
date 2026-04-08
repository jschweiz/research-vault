---
id: page:2026-04-07-anthropic-research-labor-market-impacts-of-ai-a-new-measure-and-ear-24d6782b
page_type: source-note
title: Labor market impacts of AI: A new measure and early evidence
aliases:
  - Labor market impacts of AI: A new measure and early evidence
source_refs:
  - 2026-04-07-anthropic-research-labor-market-impacts-of-ai-a-new-measure-and-ear-24d6782b
backlinks:
  - page:2026-04-07-anthropic-research-anthropic-economic-index-report-learning-curves--490c7dff
  - page:2026-04-07-anthropic-research-emotion-concepts-and-their-function-in-a-large-l-2f22c4fb
  - topic:employment
  - topic:exposure
  - topic:labor-market
  - topic:occupational-change
updated_at: 2026-04-08T08:37:25.358926Z
managed: true
---
# Labor market impacts of AI: A new measure and early evidence

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/labor-market-impacts
- Document kind: blog-post
- Published at: 2026-03-05T00:00:00+00:00
- Authors: Anthropic
- Tags: anthropic, official, research, website, blog-post, ai, labor market, exposure, occupational change, employment
- Topics: [Anthropic](../topics/anthropic.md), [Employment](../topics/employment.md), [Exposure](../topics/exposure.md), [Labor Market](../topics/labor-market.md), [Occupational Change](../topics/occupational-change.md), [Official](../topics/official.md)
- Trend score: 58.29
- Novelty score: 0.40

## Summary

Key findings - We introduce a new measure of AI displacement risk, observed exposure, that combines theoretical LLM capability and real-world usage data, weighting automated (rather than augmentative) and work-related uses more heavily - AI is far from reaching its theoretical capability: actual coverage remains a fraction of what's feasible - Occupations with higher observed exposure are projected by the BLS to grow less through 2034 - Workers in the most exposed professions are more likely to

## Topic Map

- [Anthropic](../topics/anthropic.md)
- [Employment](../topics/employment.md)
- [Exposure](../topics/exposure.md)
- [Labor Market](../topics/labor-market.md)
- [Occupational Change](../topics/occupational-change.md)
- [Official](../topics/official.md)

## Related Research

- [Anthropic Economic Index report: Learning curves](anthropic-economic-index-report-learning-curves-e5dad7.md) (shared topics: Anthropic, Labor Market, Official)
- [Emotion concepts and their function in a large language model](emotion-concepts-and-their-function-in-a-large-language-model-e4fef4.md) (shared topics: Anthropic, Official)
- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-0b98d0.md) (shared topics: Anthropic, Official)
- [Vibe physics: The AI grad student](vibe-physics-the-ai-grad-student-50a654.md) (shared topics: Anthropic, Official)
- [Long-running Claude for scientific computing](long-running-claude-for-scientific-computing-0fdf5f.md) (shared topics: Anthropic, Official)
- [Introducing our Science Blog](introducing-our-science-blog-adf36e.md) (shared topics: Anthropic, Official)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Key findings
- We introduce a new measure of AI displacement risk, observed exposure, that combines theoretical LLM capability and real-world usage data, weighting automated (rather than augmentative) and work-related uses more heavily
- AI is far from reaching its theoretical capability: actual coverage remains a fraction of what's feasible
- Occupations with higher observed exposure are projected by the BLS to grow less through 2034
- Workers in the most exposed professions are more likely to be older, female, more educated, and higher-paid
- We find no systematic increase in unemployment for highly exposed workers since late 2022, though we find suggestive evidence that hiring of younger workers has slowed in exposed occupations
Introduction
The rapid diffusion of AI is generating a wave of research measuring and forecasting its impacts on labor markets. But the track record of past approaches gives reason for humility.
For example, a prominent attempt to measure job offshorability identified roughly a quarter of US jobs as vulnerable, but a decade on, most of those jobs maintained healthy employment growth. The government’s own occupational growth forecasts, while directionally correct, have added little predictive value beyond linear extrapolation of past trends. Even in hindsight, the impact of major economic disruptions on the labor market is often unclear. Studies on the employment effects of industrial robots reach opposing conclusions, and the scale of job losses attributed to the China trade shock continues to be debated.1
In this paper, we present a new framework for understanding AI’s labor market impacts, and test it against early data, finding limited evidence that AI has affected employment to date. Our goal is to establish an approach for measuring how AI is affecting employment, and to revisit these analyses periodically. This approach won't capture every channel through which AI could reshape the labor market, but by laying this groundwork now, before meaningful effects have emerged, we hope future findings will more reliably identify economic disruption than post-hoc analyses.
It is possible that the impacts of AI will be unmistakable. This framework is most useful when the effects are ambiguous—and could help identify the most vulnerable jobs before displacement is visible.
Counterfactuals
Causal inference is easier when the effects are large and sudden. The COVID-19 pandemic and accompanying policy measures caused economic disruption so stark that sophisticated statistical approaches were unnecessary for many questions. For example, unemployment jumped sharply in the early weeks of the pandemic, leaving little room for alternative explanations.
The impacts of AI, however, might be less like COVID and more like the internet or trade with China. The effects may not be immediately clear from aggregate unemployment data; factors like trade policy and the business cycle could cloud interpretations of trend lines.
One common approach is to compare outcomes between more or less AI-exposed workers, firms, or industries, in order to isolate the effect of AI from confounding forces.2 Exposure is typically defined at the task level: AI can grade homework but not manage a classroom, for example, so teachers are considered less exposed than workers whose entire job can be performed remotely.
Our work follows this task-based approach, incorporating measures of theoretical AI capability and real-world usage, before aggregating to occupations.3
Measuring exposure
Our approach combines data from three sources.
- The
[O*NET database](https://www.onetcenter.org/database.html), which enumerates tasks associated with around 800 unique occupations in the US. - Our own usage data (as measured in the
[Anthropic Economic Index](https://www.anthropic.com/economic-index)). - Task-level exposure estimates from Eloundou et al. (2023), which measure whether it is theoretically possible for an LLM to make a task at least twice as fast.
