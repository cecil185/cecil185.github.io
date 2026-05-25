---
layout: single
title: "How I Eval the Prompts in my AI Reading Pipeline"
date: 2026-05-25
categories: Data
---
I set out to build a better reading process — one that used AI to find, filter, and synthesize technical articles against a specific learning goal.

## The problem with NotebookLM

NotebookLM is good at Q&A. It's not good at filtering. There's no mechanism to score an article against what you're actually trying to learn — it surfaces anything that pattern-matches the topic, and you drift without noticing. And if you change how you're filtering, you have no idea whether that made things better or worse.

## My approach

To fix these problems, I built a pipeline that reads Hacker News and various tech blogs, scores each article against a written `goal.md`, and auto-tickets the matches in Linear. `goal.md` is structured intent — not just a topic, but What I'm learning, Why, and explicit signals for what's high or low relevance. Every time I changed `goal.md`, I was guessing whether the change helped.

![Image](/images/blog/data/ai_reading_pipeline.png)

## The eval harness

I built a labelled eval harness. `labels.jsonl` holds real keep/drop decisions from Linear ticket history — kept ticket means keep, cancelled means drop. Real signal, not synthetic. Precision/Recall/F1 reports are committed to version control alongside the code.

I ran 6 prompt variants against the same label set. The finding wasn't in the prompt at all — it was in `goal.md`. One hard exclusion rule: "Research papers on model internals with no near-term application to coding workflows" was excluding articles I found valuable. Softening it shifted F1 from 0.357 to 0.508.

| Variant | F1 | Precision | Recall |
|---|---|---|---|
| v1 (original exclusion rule) | 0.357 | 0.455 | 0.294 |
| v6 (softer exclusion rule) | **0.508** | 0.682 | 0.405 |

*(5 other prompt variants were also tested)*

Now any change to `goal.md` produces a report. I know immediately whether it helped.

## I almost built a Q&A layer but...

From there, I built a wiki — chaining several prompts to synthesize my top 30 articles — and started asking questions against it. I briefly considered adding a RAG layer, but with summaries averaging ~1,000 tokens, 50 articles fit easily inside 25% of Sonnet's context window. RAG wasn't necessary.

Then I realized the Q&A layer was no better than NotebookLM for general questions — and for anything already in Claude's training data, a general-purpose LLM already knows it. The goal-aware filtering is the part that doesn't exist anywhere else. For now I dump my article URLs into NotebookLM for Q&A. I'm tempted to build a custom layer with paragraph-level citations to learn more about faithfulness evals and hallucination guardrails — but that's a future project.

### The broader takeaway
Without labeled evals, every prompt change is a guess. Measure first — then you can actually tell when your AI systems are improving.