---
title: "NEAR Lesson 4: Build Something Real"
type: lesson
difficulty: intermediate
tags: [near, ironclaw, build, project, dapp]
created: 2026-08-17
updated: 2026-08-17
lesson_number: 4
---

# NEAR Lesson 4: Build Something Real

**Duration:** 2 hours · **Format:** guided project

## Lesson Goal

Ship a small but **real** project that combines your agent (IronClaw) and NEAR. You build during the lesson, not just watch.

## Prerequisites

- NEAR Lessons 1–3 done (agent + Telegram + MCP/skill + a NEAR wallet)

---

## Part 1 — Pick a project (10 min)

Choose one, or bring your own idea:

| Project | What it does |
|---|---|
| **Portfolio watcher** | agent pings you in Telegram when a NEAR token moves X% |
| **Balance alert** | agent watches your NEAR wallet and notifies you of deposits/withdrawals |
| **NEAR news digest** | daily agent briefing of NEAR ecosystem headlines |
| **Gas/price bot** | `/near` command → current NEAR gas + price via a skill |
| **Mini dApp UI** | an AI-generated landing page for a NEAR idea |

Start with the **smallest** version that works end-to-end.

## Part 2 — Build with your agent

Use IronClaw as your co-builder:

1. Write the goal in chat (one sentence + what "done" means).
2. Let the agent generate the tool/skill/code.
3. Test it — ask the agent to run it and show the result.
4. Iterate: fix, simplify, extend.

## Part 3 — Wire in NEAR

Connect the NEAR side:

- **Wallet / account** — the project reads or acts on your NEAR account.
- **Intents** — if it's a swap/transfer, use Intents.
- **An MCP or skill** — the bridge between your agent and NEAR data/actions.

## Part 4 — Make it repeatable

- Save the tool/skill so it survives restart.
- If it's a Routine, schedule it.
- Push any code to GitHub.

---

## Homework

1. Finish the smallest working version of your project.
2. Run it once for real and capture a screenshot.
3. Prepare a 3-minute demo for the next lesson.

## Troubleshooting

- **Stuck on scope** → shrink it: one action, one notification, one screen.
- **NEAR part unclear** → reuse what you did in Lesson 2 (wallet + Intents); ask your agent to explain the error.

## Result

A working project: your agent + NEAR, doing something real.

## Related

- [[near-lesson-03-mcp-skills]] — previous lesson
- [[near-lesson-05-final-presentation]] — next: present it
