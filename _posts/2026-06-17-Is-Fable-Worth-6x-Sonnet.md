---
layout: single
title: "Is Fable Worth 6x Sonnet? A Model Bakeoff"
date: 2026-06-17
categories: Data
---

Claude's new Fable model is supposedly the best, but it's ~6x the cost of Sonnet and ~3x Opus. Someone at work asked me: is Fable worth the money?

So I ran a bakeoff on a task where I'd expect a cheaper model to fall short — the **planning step of a code refactor**. Refactors are hard. A weaker model should miss context or logic and plan poorly, which makes it a good place to look for a real difference.

## The setup

Three terminals, same starting prompt — *refactor this module and make sure it does X, Y, Z* — one model each: Sonnet, Opus, Fable. Each wrote its plan to a separate markdown file (A, B, C). Then I ran a Claude skill that does **not** know which model wrote which plan. Two parts:

- **Objective checks** — every time a plan cites a function, class, or module, the skill searches the codebase to confirm the citation exists and does what the plan claims. True or false, easy to compare.
- **Compare and contrast** — where the plans agree (common ground), where they diverge (unique contributions, different approaches — e.g. Redis vs. SQS for a queue), and any assumptions or claims I need to verify myself.

The human is still the best judge in the loop. I'm not asking the skill to crown a winner — I'm using LLMs for what they're good at: chewing through a lot of text faster than I can and surfacing the differences so I can decide.

![Image](/images/blog/data/model_bakeoff.png)

## What I found

Groundedness was a wash — A, B, and C were all 100% correct in their code citations. The interesting part was where the plans diverged. The photo above (A=Sonnet, B=Opus, C=Fable) shows red underlines where I preferred a model's decision — and **Sonnet still won on some of them**. The expensive model didn't dominate.

Different models make different decisions. Some of that may be vague prompting on my part, but the divergence itself is the value — it's where I'm forced to actually think about the design.

## The takeaway

**For this task, Fable wasn't clearly worth 6x Sonnet or 3x Opus.** The win wasn't "buy the best model" — it was "compare two plans and review where they disagree." A Sonnet + Opus dual-plan with a human resolving the forks would likely beat Fable alone, and cost less. I suspect a cross-vendor pair (e.g. Gemini Pro + Opus) would be more robust still, since two different model families disagree in more interesting ways than two Claude models.

My takeaway: given a human in the loop, reviewing the *diff* between two cheaper model outputs will provide better results at a lower cost than running one expensive model.
