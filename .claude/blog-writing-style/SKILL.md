---
name: blog-writing-style
description: >
  Documents Cecil's personal blog writing voice and structure for cecil185.github.io.
  Use when drafting, editing, or reviewing a blog post for this site.
when_to_use: >
  Trigger when the user says "write a blog post", "draft a post for my blog", "edit this
  post in my style", "make this sound like my blog", or works on any file under _posts/.
paths: "_posts/**, _drafts/**"
---

# Cecil's Blog Writing Style

A guide to writing posts for cecil185.github.io that match Cecil's voice. Two post
families share one voice: **RAK** (personal reflections on kindness/service) and
**Data** (technical essays on data engineering, AI, and software collaboration).

---

## Frontmatter

Jekyll front matter, always `layout: single`. Two categories: `RAK` or `Data`.

```yaml
---
layout: single
title: "data: Why Interesting Data Reports Are Not Good Enough"
date: 2023-06-20
categories: Data
header:
  teaser: /images/blog/data/whoop_v_oura.jpg
---
```

- **Title:** Older Data posts prefix with `"data: "`; the two most recent (2026) dropped
  the prefix and use a plain descriptive title. RAK posts use `"RAK #N: Title"`.
- **Teaser image** under `header:` was standard through 2024, then dropped in 2026 posts.
  When in doubt, omit it unless the user has a teaser image ready.
- Images inline as `![alt text](/images/blog/{rak,data}/filename.ext)`.

## Length

~500 words. Tight, scannable, headers + bullets.

**Prefer shorter and punchier**. Default to concise unless the piece is a
narrative reflection that needs room to breathe.

## Voice

First person, reflective, warm, and notably humble. Cecil admits mistakes, contradictions,
and uncertainty rather than posturing as an expert. The reader is a companion, not a student.

- **Honest and self-deprecating** — "my accounting skills are less than subpar", "My fix
  made things worse", admits when he received contradictory feedback.
- **Concrete and specific** — real numbers and names earn trust: "100 eggs", "60 people",
  "F1 from 0.357 to 0.508", "30 dev deployments", named tools (`goal.md`, `make test`),
  named people (Logan, Mariah, chef Darren).
- **Curious, not preachy** — poses questions, explores, then offers a takeaway.
- **References outside thinkers** — Ram Dass, Jay Shetty, Robert Cecil Martin's *Clean Code*,
  GiveWell, psychology studies. Use these as lenses, not name-drops.

## The signature structure (analogy-driven essay)

Cecil's strongest move, especially in Data posts, is pairing a **personal experience** with
a **professional lesson** so each illuminates the other:

- Watercolor painting with his mom ↔ teaching dbt to a new engineer.
- Oura vs. Whoop fitness apps ↔ what makes a data dashboard actually useful.

When the topic allows, open with the personal/relatable thread, weave the technical thread
through it, and let the lesson emerge from the parallel.

## Openings

Hook on the first line. Common patterns:
- **A question** — "How would you like your body to be handled after you die?"
- **In medias res scene** — "Today, I helped someone, a stranger in fact, move..."
- **A stated tension or goal** — "I set out to build a better reading process..."

Avoid throat-clearing. Never open with "In this post I will..." — though a one-sentence
"In this essay, I..." roadmap near the *end* of the opening paragraph is on-brand for Data essays.

## Endings

Close with a distilled lesson, then often an invitation or forward look.

- **Data** ends with a crisp, quotable takeaway: "And even interesting isn't good enough.",
  "Measure first — then you can actually tell when your AI systems are improving."
- **Acknowledgment footnotes** are common: "Thank you to Mariah for the editorial support",
  "Thank you to my teammate Christine Gaudet for helping me generate the main ideas."
- Neutral **disclosure notes** when relevant: "I have no personal connection to either Whoop
  or Oura that would bias this post."

## Formatting by post type

**Data essay (2023 style):** Optional `##` headers (Introduction, Background, named sections,
Take Aways). Long-form prose carrying one big analogy.

**Data how-to / list (2024+ style):** `##`/`###` headers, numbered principles
("Three Core Principles"), bullet lists, inline `code`, occasional bold lead-ins. Scannable.

**Special structures Cecil has used — reach for these when they fit:**
- **Collapsible sections** for a list of independent items (the "Mistakes" post):
  ```markdown
  <details markdown="block">
  <summary><strong>Mistake: Adding CDC too early</strong></summary>

  ...narrative of what happened...

  **What I changed:** ...the lesson...
  </details>
  ```
- **Tables** for comparing variants/results (the "Eval Prompts" post).
- **Bold lead-in labels** like `**What I changed:**` to separate story from lesson.

## Quality checklist before delivering a draft

- [ ] Correct frontmatter (layout, title convention for the category, date, category, teaser if applicable)
- [ ] Opens with a hook (question / scene / tension), no throat-clearing
- [ ] Concrete specifics — real numbers, names, tools — not vague generalities
- [ ] A clear lesson/takeaway, distilled into a memorable closing line
- [ ] Quotable takeaway
- [ ] Humble, first-person, conversational tone throughout
- [ ] Length matches the type (lean toward concise)
- [ ] Acknowledgment footnote if anyone helped; disclosure note if there's a conflict of interest
