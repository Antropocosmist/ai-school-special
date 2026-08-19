---
title: "NEAR Lesson 5: Extend & Build Something Real"
type: lesson
difficulty: intermediate
tags: [near, mcp, skills, build, project, presentation, ironclaw]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 5
---

# NEAR Lesson 5: Extend & Build Something Real

**Duration:** 2 × 1.5 hours
**Format:** guided project + live demos

## Lesson Goal

By the end of this lesson you will have **extended your IronClaw agent** with a skill and an MCP server, then **built and presented a real project** that combines your agent + NEAR. This is the payoff of the whole course.

## Prerequisites

1. ✅ Lessons 1–4 done (agent on Telegram + NEAR AI Cloud key + wallet + Intents)
2. ✅ Your project folder from Lesson 1 on GitHub

---

## Part 1: What Is MCP — in Plain Language

**Why:** MCP is how you make your agent *do* things, not just chat.

**MCP (Model Context Protocol)** is a standard "plug" that connects AI to outside tools — like USB connects devices to your computer.

| Without MCP | With MCP |
|---|---|
| AI can only chat | AI calls tools: read files, check balances, send transactions |
| You copy-paste data in | AI fetches live data itself |
| You do the action, AI describes it | AI does the action (with your permission) |

The **NEAR MCP** server ([github.com/nearai/near-mcp](https://github.com/nearai/near-mcp), package `@nearai/near-mcp`) connects an AI to the NEAR blockchain — so it can check balances, create accounts, and send transactions from plain-language prompts.

---

## Part 2: What Is a Skill

**Why:** a skill is a reusable ability you teach an agent once and keep forever.

A **skill** is a `SKILL.md` file — plain-text instructions + metadata that teach an agent how to handle a certain kind of request. IronClaw supports skills, and it can also build a **WASM tool** on the fly when you describe what you want.

Two ways to extend your IronClaw agent:

1. **Describe it, it builds it** (fastest). In Telegram, message your agent:
   ```
   Build me a tool that checks the current NEAR gas price and reports it in USD.
   ```
   It writes the tool as an isolated WASM tool (sandboxed).

2. **Write a SKILL.md** (more control). Ask Zed's AI to draft one:
   ```
   Create a SKILL.md file for my NEAR assistant. It teaches the agent
   a new ability: "NEAR Expert Mode".

   Content:
   1. Frontmatter: name: near-expert, description: one sentence
   2. When to use: when the user asks about NEAR (blockchain, accounts,
      testnet, gas, IronClaw, NEAR AI Cloud)
   3. How to answer: simple language, no jargon without explanation,
      mention testnet vs mainnet, never ask for seed phrases or keys
   4. Include 3 example Q&A pairs

   Save it in my project as SKILL.md.
   ```

---

## Part 3: Pick a Project

Choose one, or bring your own idea. **Start with the smallest version that works end-to-end.**

| Project | What it does |
|---|---|
| **NEAR price/gas bot** | `/near` → current NEAR price + gas, via a skill you built |
| **Balance alert** | agent watches your NEAR wallet and pings you on deposits/withdrawals |
| **NEAR news digest** | daily agent briefing of NEAR headlines (routine) |
| **NEAR wallet assistant** | combine `/balance`, `/ask`, and a scheduled digest |

---

## Part 4: Build It

**The loop is the same as always — you prompt, AI builds:**

1. Write the goal in one sentence (what "done" means)
2. Message your agent (or Zed) the build prompt
3. Test it — run it once for real
4. Iterate — fix, simplify, extend

Example build prompt (to your IronClaw agent):

```
I want a NEAR price bot. When I send /near, reply with:
1. The current NEAR price in USD
2. The current gas fee
3. One line about the market (up/down today)

Build the tool for this. Then test it with a /near message.
```

---

## Part 5: Prepare a 3-Minute Demo

**Why:** you built something real — now tell the story.

Structure your demo:

1. **What it does** — one sentence
2. **Live demo** — run it (not slides, the real thing)
3. **How it's built** — agent + NEAR + the skill/MCP you used
4. **What was hard** — one obstacle and how you solved it
5. **What's next** — one idea to extend it

---

## Part 6: Present

Present to the group (5 minutes each). Demo first, explain second. Keep a screenshot as backup in case something breaks live.

---

## Homework

1. Finish the smallest working version of your project and screenshot it
2. Push any code (SKILL.md, scripts) to GitHub and share the link
3. Write a 5-line project summary for the group
4. Add one future feature to your project's plan (e.g. price alerts, mainnet mode)

---

## Troubleshooting

### The agent's tool fails

```
The tool I asked you to build failed with: [paste error].
Diagnose and fix. If it needs a capability grant (HTTP access),
tell me how to allow it in the admin UI.
```

### MCP server won't load

```
The MCP server won't connect. Here's the address/config: [paste].
Check the URL, credentials, and the IronClaw MCP docs. Diagnose.
```

### The IronClaw admin UI has no "Skills" section

Interfaces change. Ask your agent: "Where do I add skills or MCP servers in the current version? Check docs.ironclaw.com."

### Stuck on scope

Shrink it: one action, one notification, one screen. You can always add more after it works.

---

## Related Materials

- [[near-lesson-04-confidential-intents]] — Previous lesson
- [[near-overview]] — Back to the course overview
- [[ironclaw-telegram-cheatsheet]] — IronClaw reference (skills & MCP)

## Result

After this lesson you have:
- An agent extended with a skill (or WASM tool) and an MCP server
- A working project that combines your agent + NEAR
- A 3-minute live demo you've presented to the group
- A real, shippable artifact — built from zero with AI
