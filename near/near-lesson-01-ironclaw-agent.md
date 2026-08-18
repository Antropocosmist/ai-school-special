---
title: "NEAR Lesson 1: Deploy Your Own AI Agent (IronClaw)"
type: lesson
difficulty: beginner
tags: [near, ironclaw, agent, telegram]
created: 2026-08-17
updated: 2026-08-17
lesson_number: 1
---

# NEAR Lesson 1: Deploy Your Own AI Agent (IronClaw)

**Duration:** 1.5 hours · **Format:** 100% hands-on

## Lesson Goal

Run your own secure AI agent (IronClaw) and connect it to Telegram. By the end, you message **your** agent and it replies — and it automates one task for you.

## Prerequisites

- A computer (macOS / Linux / Windows)
- A Telegram account
- An LLM API key (NEAR AI, OpenAI, Gemini, DeepSeek — any)

---

## Part 1 — Install (< 30 seconds)

Pick the latest `ironclaw-v*` tag from the [Releases](https://github.com/nearai/ironclaw/releases/) page, then run:

```bash
IRONCLAW_RELEASE_TAG=ironclaw-vX.Y.Z
curl --proto '=https' --tlsv1.2 -LsSf \
  "https://github.com/nearai/ironclaw/releases/download/${IRONCLAW_RELEASE_TAG}/ironclaw-installer.sh" | sh
```

## Part 2 — Onboard (choose your model)

```bash
ironclaw onboard
```

- Pick a provider, paste its API key (hidden prompt), accept the default model.
- IronClaw writes its local config, encrypted credential store, and WebUI token.

Check it's running:

```bash
ironclaw status     # prints the WebUI login link
```

## Part 3 — Connect Telegram

1. **Create a bot** — [@BotFather](https://t.me/botfather) → `/newbot` → name + username ending in `bot` → copy the **token**.
2. **Start** — `ironclaw serve`
3. **Local? Expose HTTPS** (Telegram needs public HTTPS on ports 443/80/88/8443):
   ```bash
   ngrok http 3000     # or: tailscale funnel 3000 / cloudflared tunnel --url http://localhost:3000
   ```
4. **WebUI → Admin → Configuration → Telegram deployment configuration** — fill:
   - **Bot token** — from BotFather
   - **Webhook secret token** — `openssl rand -hex 32`
   - **Public webhook URL** — `https://<your-host>/webhooks/extensions/telegram/updates`
   - **Bot username** — without the `@`
5. **WebUI → Extensions → install Telegram** (or ask the agent in chat).
6. **Pair your account** — pairing panel (link/QR) or `/start` + code.
7. **DM the bot** — it replies.

## Part 4 — Automate one action

Ask your agent in chat:

> "Every morning at 09:00 send me the top 5 NEAR ecosystem headlines."

It builds the routine and runs it on schedule.

---

## Homework

1. Deploy IronClaw and connect it to Telegram.
2. Pair your account and send 3 messages.
3. Set up one automated action (schedule or trigger).
4. Share in the group chat: a screenshot of your agent replying.

## Troubleshooting

- **Bot never replies** → tunnel down or webhook URL hostname changed.
- **"Administrator must configure the Telegram bot first"** → fill all 4 fields in Admin → Configuration and save.
- **`ironclaw` not found** → reopen your terminal (PATH refresh), or re-run the installer.

## Result

A running IronClaw agent, connected to Telegram, with one automated task.

## Related

- [[ironclaw-telegram-cheatsheet]] — full reference
- [[near-lesson-02-near-intents]] — next: NEAR wallet & Intents
