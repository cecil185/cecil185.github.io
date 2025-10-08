---
layout: single
title: "Data: Process Map to Code Better"
date: 2023-06-20
categories: Data
header:
  teaser: /images/blog/data/muffin_factory.png
---

My team lead asked me to help a junior engineer plan a complex data ingestion project. The project involved moving data from our cloud to a client’s BigQuery environment. I quickly noticed that the junior engineer was thinking about the small details, like what python libraries to use, but ignoring some bigger questions like how to ingest new data to the client’s BigQuery project without introducing duplicates. Hoping to refocus us on the big picture, I suggested that we map the process in Figma. We began by mapping the process in just two boxes, then iteratively added more detail. Where multiple options existed to perform some step, we listed all feasible options without evaluating them (see color-coded circles)

![photo](/images/blog/data/process_map_example.png)

Using this diagram, we brainstormed with our team lead and agree on the best path forward. Then we got into the details of coding this. We added to the diagram until we had one box per function or method. We color-coding each box to indicate who would build it, and started working in parallel. It was crystal clear who was working on what and how our pieces would fit together in the end. We delivered the project successfully, and we used a process diagram to explain to the client what they were receiving. 

I love process diagraming. I developed the skill through seven years of industrial engineering and process improvement consulting which included working in this muffin factory:

![photo](/images/blog/data/muffin_factory.png)

Process diagramming, both in factories and in software, helps with these two things:

1. Internal collaboration - generating ideas & planning projects
2. External communication

My view is that engineers underuse process diagrams and overuse architecture diagrams.
Here’s an architecture diagram.

![photo](/images/blog/data/architecture_diagram.png)

… and here is a process diagram (it’s for the process of process mapping, which I made to present these ideas to the company-wide engineering group):

![photo](/images/blog/data/process_map_to_process_map.png)

- Architecture diagrams show *what* connects; process diagrams show *how* work flows. The first is about *nouns*, while the latter is about *verbs.*
- Architecture diagrams often look cluttered, full of crossing lines and two-way arrows, while process diagrams flow cleanly from left to right like an Airflow DAG which I’ve found makes them easier for non-engineers to understand.
- Architecture diagrams impede brainstorming alternative options because they show what exists, not what could exist—they lock you into structure instead of encouraging “what-if” thinking.
- Process diagrams make hidden assumptions visible—like timing, dependencies, or handoffs that architecture diagrams often ignore.
- Process diagrams naturally translate into implementation plans, API workflows, or Airflow DAGs.

That said, architecture diagrams have their strengths:

- They’re great for tracing how failures propagate across services or APIs.
- They help communicate security boundaries and permissioning between systems.

Of course, the two diagrams complement each other, but process diagrams feel under-appreciated to me, and they can make the difference between a project that looks good on paper and one that actually delivers.