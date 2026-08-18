---
title: "NEAR Lesson 2: Deploy Your First AI Agent"
type: lesson
difficulty: beginner
tags: [near, agent.near.ai, ironclaw, agent, telegram]
created: 2026-08-17
updated: 2026-08-19
lesson_number: 2
---

# NEAR Lesson 2: Deploy Your First AI Agent

**Duration:** 1.5 hours · **Format:** 100% hands-on

## Lesson Goal

Deploy your own secure AI agent (**IronClaw**) on **agent.near.ai** and connect it to Telegram. No terminal, no install — the whole thing is clicks in the browser. By the end you message **your** agent and it replies.

## Prerequisites

- A browser + a Telegram account
- (optional) the API key from Lesson 1

---

## Part 1 — Deploy IronClaw (10 min)

1. Go to **https://agent.near.ai** and sign in the way you prefer.
2. Click **Deploy** → choose **IronClaw** → **Starter** plan.
3. Attach a card (the Starter plan is **free**).
4. Click **Generate and Download Access Key** — you get a **Public SSH key** (shareable) and a **Private SSH key** (keep secret).
5. Accept, then click **Activate Agent**.

In less than 30 seconds your agent is live at `https://<your-agent>.agents.near.ai`. Click **Open IronClaw**.

> No `curl`, no installer, no Docker — this is the point. A self-hosted install (installer + `ironclaw onboard` + a tunnel) still exists for power users, but you don't need it here.

## Part 2 — Connect Telegram (30 min)

1. **Create a bot** — [@BotFather](https://t.me/botfather) → `/newbot` → name + username ending in `bot` → copy the **token**.
2. In IronClaw, go to **Admin → Configuration → Telegram deployment configuration** and fill 4 fields:

   | Field | Value |
   |---|---|
   | Bot token | from BotFather |
   | Webhook secret token | `openssl rand -hex 32` (any 32-char random string of letters/digits) |
   | Public webhook URL | `https://<your-agent>.agents.near.ai/webhooks/extensions/telegram/updates` |
   | Bot username | your bot name, **without** `@` |

3. Click **Save configuration**.
4. Go to **Admin → Extensions → Telegram → Connect** — copy the 8-char **code**.
5. In Telegram, send the bot **`/start <code>`**.

Done — DM your bot and it replies.

## Part 3 — Automate one action (15 min)

Ask your agent in chat:

> "Every morning at 09:00 send me the top 5 NEAR ecosystem headlines."

It builds the routine and runs it on schedule.

---

## Homework

1. Deploy IronClaw and connect Telegram.
2. Pair your account and send 3 messages.
3. Set up one automated action.
4. Share a screenshot of your agent replying.

## Troubleshooting

- **Config won't save** → Bot username has a leading `@` (remove it), or the webhook secret has illegal characters (use letters/digits/`_`/`-` only).
- **Agent says "doesn't accept a bot token"** → ignore it; the token **is** required — fill all 4 fields and save.
- **Pairing code expired** → open Extensions → Telegram → Connect again for a fresh one (the code is short-lived).

## Result

A running IronClaw agent, connected to Telegram, with one automated task.

## Related

- [[How to get IronClaw in your Telegram in less than 30 seconds]] — screenshot walkthrough
- [[ironclaw-telegram-cheatsheet]] — full reference
- [[near-lesson-03-near-ai-cloud]] — next: NEAR AI Cloud
