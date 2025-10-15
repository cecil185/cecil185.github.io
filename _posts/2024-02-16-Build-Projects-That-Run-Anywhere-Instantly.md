---
layout: single
title: "data: Build Projects That Run Anywhere, Instantly"
date: 2024-02-16
categories: Data
header:
  teaser: /images/blog/data/muffin_factory.png
---

As I've moved between engineering teams throughout my career, I’ve been struck by how drastically the local development experience can differ. Some projects take a full day to set up, with README instructions that omit crucial steps and ultimately require a video call with the original developer. Other projects I can have running in fifteen minutes. When new engineers join my projects, I challenge myself to get them running locally in five minutes and deploying code on day one.

## Why This Matters

Projects where only a handful of long-tenured engineers can contribute to the code are bad for everyone. The knowledge concentration is risky for the business. The projects are stressful for new team members; and ironically, stressful for the long-tenured engineers when they are under pressure to deliver and can’t quickly onboard new teammates to help them.

### The Hidden Work Behind “Run the Code”

Before contributing, every engineer must:

- Install dependencies
- Database schema changes
- Run code & tests
- Containerize environments
- Reproduce bugs locally
- Document their work
- Integrating new code & tests with existing code

If any of these steps are confusing, progress stalls.

## The Three Foundations

After many painful experiences, both as the onboarder and the onboarded, I landed on three principles that significantly increased developer confidence on my projects:

### 1. Encode setup logic, don't document it

Aggressively minimize README instructions. Instead encode these steps in Docker Compose and Makefiles. Configuring environments in a README is like listing every pip install < package > manually rather than using poetry. If a database needs to be running before a project is run, chain those commands together in a Makefile so developers don't need to memorize steps.

Have a  `make build` to build the docker image, a `make sql` to interact with your database, and a `make test` to run your test suite.

In Robert Cecil Martin's foundational text Clean Code, he argues that comments are crutches—failures to write expressive code. Comments should only exist when code cannot possibly express its intent clearly. I would say that READMEs are similar. They should only contain what cannot be reliably encoded in a Makefile or docker-compose.yaml.

### 2. Develop in containers from day one

When you develop in containers, you develop in the same environment that runs in production. First, this helps immensely when replicating production bugs locally, and second, this fundamentally shifts where you catch issues when developing.

When I deploy to the cloud, I expect to only surface orchestration problems. I expect to encounter and fix all other problems—missing packages, incorrect dependencies, broken database connections—during local development. I witnessed this difference starkly when I switched projects: my usual workflow required one dev deployment to validate a feature. My new feature on the new project, which no one could run locally, required thirty deployments to dev. Eventually other developers messaged me asking when I'd stop monopolizing the shared Airflow instance—which leads directly to the third principle.

### 3. Minimize collisions between developers

Run your entire stack locally: database, Redis, message queues, whatever your architecture requires. The critical insight is that because it's local, developers can freely drop tables, delete data, and experiment without fear of impacting teammates.

![Image](/images/blog/data/destroy-local-database.png)

## In Short

Your goal isn’t just to make the code run—it’s to make it run for anyone, immediately, with confidence. The more seamlessly you enable local development, the faster your team scales, collaborates, and ships.