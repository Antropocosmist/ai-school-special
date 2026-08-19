---
title: "NEAR Lesson 5: Extend & Build Something Real"
type: lesson
difficulty: intermediate
tags: [near, mcp, skills, build, project, presentation]
created: 2026-08-17
updated: 2026-08-19
lesson_number: 5
---

# NEAR Lesson 5: Extend & Build Something Real

**Duration:** 2 × 1.5 hours · **Format:** guided project + demos

## Lesson Goal

Extend your agent with a **skill** or **MCP server**, then ship a small real project that combines your agent and NEAR — and present it.

## Prerequisites

- Lessons 1–4 done (agent + Telegram + wallet + Intents)

---

## Part 1 — Extend your agent (30 min)

Two ways to make your agent do more:

- **Skill** — a reusable capability. In IronClaw, describe what you want and it builds it (as an isolated WASM tool):
  > "Build me a tool that checks the current NEAR gas price and reports it in USD."
- **MCP server** — an open standard that plugs tools/data into your agent (files, databases, wallets, browsers, APIs). Connect one in the WebUI (Admin → Extensions / MCP).

## Part 2 — Pick a project (10 min)

Choose one, or bring your own:

| Project | What it does |
|---|---|
| Portfolio watcher | agent pings you in Telegram when a NEAR token moves X% |
| Balance alert | agent watches your NEAR wallet, notifies you of deposits |
| NEAR news digest | daily agent briefing of NEAR headlines |
| Gas/price bot | `/near` → current NEAR gas + price via a skill |

Start with the **smallest** version that works end-to-end.

## Part 3 — Build (45 min)

1. Write the goal in one sentence (what "done" means).
2. Let the agent generate the tool/skill/code.
3. Test it — ask the agent to run it and show the result.
4. Iterate: fix, simplify, extend.

## Part 4 — Present (5 min each)

1. **What it does** — one sentence.
2. **Live demo** — run it.
3. **How it's built** — agent + NEAR + the skill/MCP you used.
4. **What was hard** — one obstacle and how you solved it.
5. **What's next** — one idea.

## Homework

1. Finish the smallest working version and screenshot it.
2. Push any code to GitHub and share the link.
3. Write a 5-line project summary.

## Result

You've shipped and presented a real agent + NEAR project. You're a builder now.

## Related

- [[near-lesson-04-confidential-intents]] — previous lesson
- [[near-overview]] — back to the overview
