---
title: "NEAR Lesson 1: AI Development Foundations"
type: lesson
difficulty: beginner
tags: [near, github, ide, api, tokens, context, fundamentals]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 1
---

# NEAR Lesson 1: AI Development Foundations

**Duration:** 2 hours · **Format:** theory + practice

## Lesson Goal

Get the five essentials every AI builder needs: **GitHub**, an **IDE**, **API keys**, **tokens**, and **context**. Everything else in this course builds on these.

## Part 1 — Where code lives: GitHub (15 min)

**GitHub** is cloud storage for code. Your code can be in three places:

| Where | What it is |
|---|---|
| **Locally** | a folder on your computer |
| **GitHub (remote)** | cloud code storage |
| **Synced** | both, via Git |

Why GitHub:
- **Backup** — code survives a broken computer
- **Version history** — roll back any version
- **Portfolio** — your public profile
- **Deployment** — services load code directly from GitHub

**Do:** create a free account at [github.com](https://github.com).

## Part 2 — What an IDE is (15 min)

An **IDE** (Integrated Development Environment) is a code editor with an AI assistant inside — like Google Docs for code. Examples: **Zed**, **Cursor**, **VS Code**.

You open a project, see files, and ask the AI inside the editor to write and change code. In this course you mostly won't write code by hand — you'll ask the AI.

**Do:** install one (Zed is fast and free: [zed.dev](https://zed.dev)).

## Part 3 — API keys (20 min)

An **API** is how two programs talk. An **API key** is the password that lets your tool use an AI's brain on your behalf.

- You get a key from an AI provider (OpenAI, DeepSeek, Google, NEAR AI …).
- You paste it into your IDE / agent once.
- **Never share it, never commit it to GitHub.**

**Do:** create a key at one provider (e.g. [platform.deepseek.com](https://platform.deepseek.com)), top up ~$2, copy the key somewhere safe.

> Security rule for the whole course: **secrets go in a `.env` file — never in code, never in chat.**

## Part 4 — Tokens & context (25 min)

A **token** is roughly a "word" for AI. You pay per token — input (what you send) and output (what the AI writes).

| Unit | ≈ tokens |
|---|---|
| 1 word | ~1.3 |
| 1 A4 page | ~500 |
| 1M tokens | ~3,000 pages |

**Context** is the AI's working memory — the max it can "see" at once (its *context window*). Every message, file and instruction eats into it. When it's full, the AI "forgets" the beginning.

Why it matters: you pay for the **whole context on every request**, not just your new message. So keep conversations lean, and put reusable rules in a file (e.g. `AGENTS.md`) instead of repeating them.

## Part 5 — Practice: your first project (30 min)

Use your IDE's AI to make a tiny project, then push it to GitHub — without writing code by hand.

1. In your IDE, open a projects folder.
2. Ask the AI:
   > "Create a simple calculator in one HTML file. Save it as `calculator.html`."
3. Open the file in a browser — it should work.
4. Ask the AI to push it to GitHub (it will run `git init`, `gh auth login`, commit, push) and give you the link.

## Homework

1. GitHub account + one IDE installed.
2. One API key created (and kept secret).
3. Your `calculator.html` pushed to GitHub — share the link in the group.

## Result

You understand where code lives, what an IDE and an API key are, what tokens/context cost you — and you've pushed your first project.

## Related

- [[near-lesson-02-deploy-agent-cloud]] — next: deploy your agent & the AI cloud
