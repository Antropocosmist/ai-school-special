---
title: "NEAR Lesson 3: Agents + MCP + Skills"
type: lesson
difficulty: beginner
tags: [near, ironclaw, mcp, skills, agents, wasm]
created: 2026-08-17
updated: 2026-08-17
lesson_number: 3
---

# NEAR Lesson 3: Agents + MCP + Skills

**Duration:** 1.5 hours · **Format:** hands-on

## Lesson Goal

Extend your IronClaw agent beyond chat: add a **skill**, connect an **MCP server**, and understand how the agent "grows" its own tools.

## Prerequisites

- NEAR Lesson 1 done (running IronClaw, Telegram connected)

---

## Part 1 — What is MCP? (10 min)

**MCP (Model Context Protocol)** is an open standard that lets AI agents connect to tools and data — like a universal plug for AI.

- One agent → many servers (files, databases, wallets, browsers, APIs).
- Instead of coding every integration, you connect a ready-made MCP server.

## Part 2 — Add a skill to IronClaw

IronClaw is **self-expanding**:

1. **Describe it, it builds it** — ask the agent in chat:
   > "Build me a tool that checks the current NEAR gas price and reports it in USD."
   IronClaw writes it as an isolated **WASM tool** (sandboxed, capability-gated).
2. **Skills from the IronClaw repo** — browse the skills available in the IronClaw repo / WebUI and add one.
3. **Code your own** — write a WASM tool or drop in a plugin.

## Part 3 — Connect an MCP server

1. Find an MCP server you want (e.g. a NEAR/blockchain MCP, a search MCP, a database MCP).
2. Add it in the IronClaw WebUI (see the IronClaw docs → MCP) or via config.
3. Ask the agent to use it:
   > "Using the MCP server, look up …"

The agent now has that server's tools in every conversation.

## Part 4 — Routines & triggers (bonus)

Turn a capability into automation: a **Routine** runs on a cron schedule, an event, or a webhook — so your agent proactively does work, not only replies.

---

## Homework

1. Add one skill to your agent (built-in or from the repo).
2. Connect one MCP server and ask the agent to use it.
3. Write down: what's the difference between a skill and an MCP server? (one line each)

## Troubleshooting

- **MCP server won't load** → check its address/credentials; see the IronClaw MCP docs.
- **Tool fails** → the WASM tool needs an explicit capability grant (HTTP/secret); check the allowlist.

## Result

An agent with a custom skill and a connected MCP server — your agent now does real work.

## Related

- [[near-lesson-02-near-intents]] — previous lesson
- [[near-lesson-04-build-project]] — next: build something real
