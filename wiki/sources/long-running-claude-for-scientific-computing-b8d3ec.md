---
id: page:2026-03-23-anthropic-research-long-running-claude-for-scientific-computing-20a930ae
page_type: source-note
title: Long-running Claude for scientific computing
aliases:
- Long-running Claude for scientific computing
source_refs:
- 2026-03-23-anthropic-research-long-running-claude-for-scientific-computing-20a930ae
backlinks:
- page:2025-12-18-anthropic-research-project-vend-phase-two-6d9cb3ea
- page:2026-03-31-anthropic-research-how-australia-uses-claude-findings-from-the-anth-8bdd4935
- page:2026-04-01-openai-website-gradient-labs-gives-every-bank-customer-an-ai-ac-a0904673
- page:2026-04-08-openai-website-the-next-phase-of-enterprise-ai-7bcd68b5
- page:2026-04-09-tldr-email-anthropic-launches-claude-managed-agents-for-bus-bf42c0c8
- topic:ai-agents
- topic:boltzmann-solvers
- topic:claude
- topic:jax
updated_at: '2026-04-09T16:35:04.589881Z'
managed: true
---
# Long-running Claude for scientific computing

System-generated source note. Build higher-order synthesis pages around it instead of editing the raw document.

## Metadata

- Source: Anthropic Research
- Canonical URL: https://www.anthropic.com/research/long-running-Claude
- Document kind: blog-post
- Published at: 2026-03-23T00:00:00+00:00
- Authors: Siddharth Mishra-Sharma
- Tags: anthropic, official, research, website, blog-post, ai agents, scientific computing, claude, boltzmann solvers, jax
- Topics: [Agents](../topics/agents.md), [Ai Agents](../topics/ai-agents.md), [Anthropic](../topics/anthropic.md), [Boltzmann Solvers](../topics/boltzmann-solvers.md), [Claude](../topics/claude.md), [Jax](../topics/jax.md)
- Trend score: 155.17
- Novelty score: 4.80

## Summary

The post details applying multi-day agentic coding workflows to scientific computing tasks, using Claude to implement a differentiable version of a cosmological Boltzmann solver.

## Topic Map

- [Agents](../topics/agents.md)
- [Ai Agents](../topics/ai-agents.md)
- [Anthropic](../topics/anthropic.md)
- [Boltzmann Solvers](../topics/boltzmann-solvers.md)
- [Claude](../topics/claude.md)
- [Jax](../topics/jax.md)

## Related Research

- [Anthropic launches Claude Managed Agents for businesses](anthropic-launches-claude-managed-agents-for-businesses-184163.md) (shared topics: Agents, Ai Agents, Anthropic, Claude)
- [How Australia Uses Claude: Findings from the Anthropic Economic Index](how-australia-uses-claude-findings-from-the-anthropic-economic-i-147fc4.md) (shared topics: Anthropic, Claude)
- [Project Vend: Phase two](project-vend-phase-two-818878.md) (shared topics: Ai Agents, Anthropic)
- [The 2-Sigma Problem: The 1:1 Tutor](the-2-sigma-problem-the-1-1-tutor-9725b7.md) (shared topics: Anthropic)
- [Scaling LangGraph Agents: Parallelization, Subgraphs, and Map-Reduce Trade-Offs](scaling-langgraph-agents-parallelization-subgraphs-and-map-reduc-940f52.md) (shared topics: Agents)
- [Building an Agentic Deep-Thinking RAG Pipeline to Solve Complex Queries](building-an-agentic-deep-thinking-rag-pipeline-to-solve-complex--58c4bb.md) (shared topics: Agents)

## Radar

- [Rising Topics](../trends/rising-topics.md)
- [Global AI Research](../maps/global-ai-research.md)

## Source Excerpt

Subscribe to Anthropic Science
Features on AI-assisted discoveries, practical workflows, and field notes across the sciences.
In this post, Siddharth Mishra-Sharma, a researcher on the Discovery team, explains how to apply multi-day agentic coding workflows—test oracles, persistent memory, and orchestration patterns—to scientific computing tasks even outside of one’s domain.
Most scientists currently using AI agents work in a conversational loop, managing each step of the process on a tight leash. As models have become [significantly better at long-horizon tasks](https://metr.org/time-horizons/) over the last year or so, a new way of working emerged: rather than getting involved with every detail, we can specify the high-level objective and set a team of agents loose to work autonomously. This makes it possible to complete projects in mere hours that might otherwise take us days, weeks, or even months. Certain types of scientific tasks fit well within this model, e.g., reimplementing a numerical solver, converting legacy scientific software written in an old Fortran dialect to a modern language, and debugging a large codebase against a reference implementation. These are tasks where the work is well-scoped, the success criteria are clear, and human oversight can be occasional rather than continuous.
Anthropic’s [C compiler project](https://www.anthropic.com/engineering/building-c-compiler) demonstrated a version of this, where Claude worked across roughly 2,000 sessions to build a C compiler capable of compiling the Linux kernel. This post describes how to set up a similar pattern for scientific computing tasks using Claude Code, with a typical academic lab in mind. As a concrete example, I will walk through using Claude Opus 4.6 to [implement a differentiable version of a cosmological Boltzmann solver](https://github.com/smsharma/clax). This is numerical code that predicts the statistical properties of the afterglow of the Big Bang—the Cosmic Microwave Background, or CMB. It does this by evolving coupled equations for photons, baryons, neutrinos, and dark matter through the early universe.
Boltzmann solvers like [CLASS](http://class-code.net/) and [CAMB](https://camb.info/) are core pieces of scientific infrastructure in cosmology, allowing us to constrain cosmological models using data from surveys like Planck and the Simons Observatory. A differentiable version—one that can propagate gradients through the full solver—enables the use of gradient-based inference methods, dramatically speeding up parameter estimation. Writing it in JAX is a natural fit here, since it gives us automatic differentiation and compatibility with accelerators (e.g., GPUs) essentially for free.
Notably, the task isn’t in my core scientific domain—I have a high-level familiarity with the tools and the science, but don’t have the expertise to complete it myself in any reasonable time frame. Groups who do have that expertise have built [differentiable](https://arxiv.org/abs/2311.03291) [solvers](https://arxiv.org/abs/2602.15104) in JAX with a subset of the features present in CLASS. These efforts typically represent months to years of researcher-time. The point here was to see if an agent could go further with minimal steering from a non-domain expert.
This kind of task is structurally different from the C compiler project, which can be farmed out to a large number of parallel agents. A Boltzmann solver, on the other hand, is a deeply coupled pipeline—a small numerical error or poor approximation in modeling how the early universe recombines can subtly shift everything downstream. It thus requires a different set of agent skills. Debugging requires tracing causally through the entire chain and drawing from domain knowledge, which may be better suited to a single agent working sequentially, spawning subagents as needed, and using the reference implementation to bisect discrepancies.
We'll use an HPC cluster running the SLURM job scheduler as our compute
