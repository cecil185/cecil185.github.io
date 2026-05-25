---
layout: single
title: "Data Engineering Mistakes I Learned From"
date: 2026-03-18
categories: Data
---

I recently came across [GiveWell](https://www.givewell.org/about/our-mistakes), a charity evaluator, which publicly documents their mistakes on their website. I really admire their transparency and accountability, so this post is my attempt to do the same. These are real mistakes from my data engineering career — how I messed up and what I learned.

<details markdown="block">
<summary><strong>Mistake: Being dogmatic about code style at the wrong time</strong></summary>

I once worked with a lead engineer who had strong, well-reasoned opinions about how code should be written. He won me over quickly. Eventually our code was indistinguishable from each other's. It was beautiful — a singular, consistently styled codebase rather than a patchwork of individual preferences.

The mistake came when I moved to a new team and tried to push functional programming and local Docker development on teammates who had no interest in either. A senior engineer eventually asked me to stop refactoring existing code and start shipping features.

**What I changed:** I learned that a new team member's job is to adapt first, improve later. You earn trust first by being useful and understanding why the team works the way it does. I maintained my strong opinions, but I held onto them less tightly. Later on, I was able to suggest improvements more effectively.

</details>

<details markdown="block">
<summary><strong>Mistake: Insufficient data validation</strong></summary>

I built a data product that evolved from data ingestion to a full data modeling layer, embedding business logic so the dataset represented real-world business concepts. We moved too fast and didn't add enough validation before onboarding customers. Some customers found data quality issues and churned.

**What I changed:** We added many more validation checks, but the damage was done. In data work, trust is everything. Build processes that catch problems before customers do.

</details>

<details markdown="block">
<summary><strong>Mistake: Pushing the wrong logic into the wrong layer</strong></summary>

While designing schemas for a Power BI dashboard product, I pushed complex aggregation metrics into the ETL pipeline — mainly because I was much more comfortable writing SQL than Power BI logic.

That worked at first, but by the second or third dashboard it became clear that I was solving the wrong problem in the wrong place. Aggregations happen at many levels: daily, weekly, monthly, and more. Once you collapse the granularity too early, you cannot recover it later. You cannot go from a monthly sum back to a weekly one.

My fix made things worse. I added more tables at various aggregation levels, which harmed dashboard speed as they pulled in increasingly large datasets.

**What I changed:** The right solution was to move aggregations into Power BI. The broader lesson: use the right tool for the job, not the most familiar one. Now I ask myself — where should this logic live, given the capabilities and constraints of the whole system?

</details>

<details markdown="block">
<summary><strong>Mistake: Adding CDC too early</strong></summary>

While building an MVP for a new data product, the architect and I assumed customers would want change data capture (CDC). If a value changed, they would want to see its full history, so we built CDC into both the ETL and reverse ETL pipelines.

Technically it worked, but it came at a cost:

- Greater code complexity
- 10× slower, more expensive backfills

Meanwhile, the product itself was evolving rapidly. Ironically, none of our early customers had asked for CDC.

I raised concerns about removing it several times, but by then the system was in production and the team prioritized new features over refactoring. It stayed that way for months until a new team member was brought in to untangle it.

**What I changed:** I should have been louder and helped my teammates understand the technical complexity of CDC earlier on before we committed to it in the product.

MVPs must be easy to change. Any feature that slows iteration — especially one customers haven't asked for — deserves heavy scrutiny before you build it in.

</details>
