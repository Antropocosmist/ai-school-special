---
title: "NEAR Lesson 2: Deploy Your Agent & the AI Cloud"
type: lesson
difficulty: beginner
tags: [near, agent.near.ai, cloud.near.ai, ironclaw, agent, telegram, ssh]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 2
---

# NEAR Lesson 2: Deploy Your Agent & the AI Cloud

**Duration:** 2 hours · **Format:** 100% hands-on

## Lesson Goal

Deploy your own secure AI agent (**IronClaw**) on **agent.near.ai**, connect it to Telegram, and understand **cloud.near.ai** — the cloud it runs on. No terminal, no install.

## Prerequisites

- A browser + a Telegram account
- (optional) the API key from Lesson 1

---

## Part 1 — Deploy IronClaw (10 min)

1. Go to **https://agent.near.ai** and sign in the way you prefer.
2. **Deploy** → choose **IronClaw** → **Starter** plan.
3. Attach a card (the Starter plan is **free**).
4. Click **Generate and Download Access Key** — you get a **Public SSH key** (shareable) and a **Private SSH key** (keep secret).
5. Accept, then click **Activate Agent**.

In less than 30 seconds your agent is live at `https://<your-agent>.agents.near.ai`. Click **Open IronClaw**.

> No `curl`, no installer, no Docker — this is the point. (A self-hosted install still exists for power users, but you don't need it here.)

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

## Part 3 — Where your agent lives: cloud.near.ai (25 min)

Now that your agent is running, here's the cloud behind it.

**agent.near.ai vs cloud.near.ai:**

| | **agent.near.ai** | **cloud.near.ai** |
|---|---|---|
| What it is | the AI **Agent Hub** | NEAR **AI Cloud** (compute) |
| What you do | deploy an agent in one click | request dedicated compute / GPU |
| For | running a personal agent quickly | agents/services that need dedicated resources |

**Do:**

1. Open **https://cloud.near.ai** and sign in.
2. Look at the dashboard and the **organizations** section.
3. Find **"Request dedicated deployment"** — that's the flow for booking dedicated GPUs. You don't need it for a Starter agent, but it's good to know where it is.

## Part 4 — SSH keys: your access to the cloud (15 min)

When you deployed, NEAR generated an **SSH key pair**:

- **Public key** — shareable; it identifies you / your agent.
- **Private key** — **never share it**. It's the actual key to your agent/cloud resources.

Think of SSH keys like a lock (public) and its key (private). You hand out the lock freely; only the key opens it.

**Do:** find where your private key was downloaded, and keep it somewhere safe. If you lose it, you can't easily recover access.

**Rule of thumb:** a personal agent answering DMs → agent.near.ai is enough. Heavy traffic, custom models, or GPU jobs → cloud.near.ai.

## Part 5 — Automate one action (15 min)

Ask your agent in chat:

> "Every morning at 09:00 send me the top 5 NEAR ecosystem headlines."

It builds the routine and runs it on schedule.

---

## Homework

1. Deploy IronClaw and connect Telegram.
2. Send 3 messages to your agent.
3. Set up one automated action.
4. In 3 sentences, explain the difference between agent.near.ai and cloud.near.ai.

## Troubleshooting

- **Config won't save** → Bot username has a leading `@` (remove it), or the webhook secret has illegal characters (use letters/digits/`_`/`-` only).
- **Agent says "doesn't accept a bot token"** → ignore it; the token **is** required — fill all 4 fields and save.
- **Pairing code expired** → open Extensions → Telegram → Connect again for a fresh one (the code is short-lived).

## Result

A running IronClaw agent on NEAR's cloud, connected to Telegram, with one automated task — and you understand the cloud it runs on.

## Related

- [[How to get IronClaw in your Telegram in less than 30 seconds]] — screenshot walkthrough
- [[ironclaw-telegram-cheatsheet]] — full reference
- [[near-lesson-03-wallet-intents]] — next: wallet & Intents
