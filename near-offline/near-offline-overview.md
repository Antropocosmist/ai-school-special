---
title: "NEAR Off-line Course Overview"
type: synthesis
difficulty: beginner
tags: [near, offline, overview, course, lessons, ironclaw, agent, mcp, cloud]
created: 2026-08-19
updated: 2026-08-19
---

# Novicado AI School × NEAR — Off-line Course Overview

Six hands-on classroom lessons where you build real products on **NEAR** using AI. No coding skills required — you describe what you want, AI builds it. Each lesson is instructor-led in a classroom: you watch the big screen, copy prompts from the chat, and repeat on your own laptop.

The three pillars of the course:

- **agent.near.ai** — the NEAR AI Hub. Deploy your own secure AI agent (**IronClaw**) in one click and connect it to Telegram.
- **cloud.near.ai** — NEAR AI Cloud. Private LLM API: models run inside hardware-sealed enclaves (TEE), every answer is cryptographically attested.
- **NEAR MCP + skills** — connect AI (Zed) to the NEAR blockchain, and teach your agent new abilities with SKILL.md files.

---

## Lesson 1: Setup — GitHub, Zed, DeepSeek & NEAR Accounts

In Lesson 1 we set up your entire workspace. We install **Zed** — an AI-powered code editor — and connect it to the **DeepSeek API** (about $2 for months of use). macOS users install **Homebrew**. We install **Git** and **GitHub CLI**, then create our first project — a working calculator — without writing a single line of code, and push it to GitHub. We create an **AGENTS.md** rules file that tells AI exactly how to behave. Finally, we create our NEAR identity: a **NEAR testnet account** and a **NEAR AI Cloud API key** — the two credentials every future lesson uses.

---

## Lesson 2: Product Owner — NEAR Ecosystem Research & Architecture

In Lesson 2 we become Product Owners. We explore the NEAR ecosystem with AI as our guide: **agent.near.ai** (deploy agents), **cloud.near.ai** (private AI models), **nearbuilders.org** (community and projects). Then we describe our agent idea to AI, and it asks clarifying questions — then creates **ARCHITECTURE.md**, **SPECIFICATION.md**, **PLAN.md**, and **TEAM.md** — the complete blueprint for our product. We understand NEAR basics: human-readable accounts (`alice.near`, `alice.testnet`), testnet vs mainnet, and gas.

---

## Lesson 3: Deploy Your Agent — IronClaw on agent.near.ai + Telegram

In Lesson 3 we deploy our first real AI agent. On **agent.near.ai** we deploy **IronClaw** — NEAR's secure, open-source Agent OS — with the free Starter plan. In under a minute our agent is live with its own web UI. We connect it to **Telegram** via BotFather so it becomes our 24/7 assistant. We teach it a **routine** (a scheduled task), and we understand what makes it secure: WASM sandbox for tools, prompt-injection defense, and encrypted credentials.

---

## Lesson 4: NEAR AI Cloud — Private LLM API + Your Own Bot

In Lesson 4 we go under the hood. We sign up at **cloud.near.ai**, add credits, and get an API key. We learn that NEAR AI Cloud is an **OpenAI-compatible API** — but every response carries a hardware-signed **attestation** proving the model ran inside a sealed enclave (TEE), so nobody — not even NEAR — could see your prompts. We write a **Python Telegram bot** whose brain is NEAR AI Cloud, keep all secrets in `.env`, and verify an attestation with code.

---

## Lesson 5: NEAR MCP, Skills & the Blockchain

In Lesson 5 we connect AI directly to the blockchain. We install **NEAR MCP** (`@nearai/near-mcp`) into Zed — from now on AI can manage NEAR accounts, check balances, and send transactions with plain-language prompts. We create a testnet account, get testnet NEAR from a faucet, check the balance, and send our first transaction — all via prompts. Then we teach our agent a new ability: we write a **SKILL.md** file and add it to IronClaw.

---

## Lesson 6: Final Project — NEAR Wallet Assistant & Presentation

In Lesson 6 we build our diploma project: a **NEAR Wallet Assistant** — a Telegram bot that reports our NEAR balance, sends testnet tokens on command, and answers questions about NEAR, powered by NEAR AI Cloud + NEAR MCP. Then we prepare the defense: AI creates a product analysis, a 7-slide presentation, a 5-minute pitch script, and prepared answers to questions. Slides are generated via **NotebookLM**. We rehearse with AI as the investor, then present to the group.

---

**After this course you can:**
- Set up a complete AI development environment (GitHub, Zed, API keys, AGENTS.md)
- Deploy a secure AI agent (IronClaw) on NEAR and run it 24/7 via Telegram
- Use the NEAR AI Cloud private LLM API from your own code
- Control the NEAR blockchain through MCP with plain-language prompts
- Teach your agent new skills with SKILL.md files
- Build, ship, and present a real NEAR product
- All without writing a single line of code by hand
