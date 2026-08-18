---
title: "NEAR Lesson 3: NEAR AI Cloud"
type: lesson
difficulty: beginner
tags: [near, cloud.near.ai, gpu, compute, ssh, deployment]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 3
---

# NEAR Lesson 3: NEAR AI Cloud

**Duration:** 1.5 hours · **Format:** concept talk + exploration

## Lesson Goal

Understand **cloud.near.ai** — NEAR's cloud for running AI agents and services — and how it relates to the one-click deploy you did in Lesson 2.

## Part 1 — agent.near.ai vs cloud.near.ai (15 min)

Two different things, often confused:

| | **agent.near.ai** | **cloud.near.ai** |
|---|---|---|
| What it is | the AI **Agent Hub** | NEAR **AI Cloud** (compute) |
| What you do | deploy an agent in one click | request dedicated compute / GPU |
| For | running a personal agent quickly | agents/services that need dedicated resources |

**agent.near.ai** is where you deploy a ready-made agent (like IronClaw in Lesson 2). **cloud.near.ai** is the underlying cloud — when your agent needs dedicated GPUs or more serious infrastructure, that's where you go.

## Part 2 — Explore cloud.near.ai (30 min)

1. Open **https://cloud.near.ai** and sign in.
2. Look at the dashboard and the **organizations** section.
3. Find **"Request dedicated deployment"** — this is the flow for booking dedicated GPUs. You don't need it for a Starter agent, but it's good to know where it is.

## Part 3 — SSH keys: your access to the cloud (20 min)

When you deployed in Lesson 2, NEAR generated an **SSH key pair**:

- **Public key** — shareable; it identifies you / your agent.
- **Private key** — **never share it**. It's the actual key to your agent/cloud resources.

Think of SSH keys like a lock (public) and its key (private). You hand out the lock freely; only the key opens it.

**Do:** find where your private key was downloaded, and keep it somewhere safe. If you lose it, you can't easily recover access.

## Part 4 — When do you need dedicated compute? (10 min)

- A personal agent answering DMs → **agent.near.ai** is enough.
- A service with heavy traffic, custom models, or long-running GPU jobs → **cloud.near.ai**.

## Homework

1. Open cloud.near.ai and describe (3 sentences) the difference between it and agent.near.ai.
2. Locate your SSH key pair from Lesson 2 and confirm your private key is stored safely.

## Result

You can explain the difference between the Agent Hub and the Cloud, and you understand SSH keys — the building block of secure access to NEAR.

## Related

- [[near-lesson-02-deploy-agent]] — previous lesson
- [[near-lesson-04-wallet-intents]] — next: wallet & Intents
