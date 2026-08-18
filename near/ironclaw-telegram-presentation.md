---
marp: true
theme: default
paginate: true
size: 16:9
---

# IronClaw + Telegram
## NEAR Agent OS — Quick Start

**Noviciado × NEAR · Meetup of Interoperability**

---

## What is IronClaw?

- NEAR's **open-source Agent OS** — your own secure AI assistant
- Runs **locally**, encrypted, sandboxed (WASM)
- Multi-channel: **terminal · WebUI · Telegram · Slack**
- 25+ LLM providers (NEAR AI, Anthropic, OpenAI, Gemini, Ollama…)
- Self-expanding: builds its own tools, MCP, plugins

---

## Why it matters

- **Privacy** — your data stays yours, no telemetry
- **Security** — WASM sandbox, prompt-injection defense, encrypted secrets
- **Agentic economy** — everyone runs their own agent

> NEAR Foundation already runs IronClaw internally.

---

## Step 1 — Deploy (< 30 sec)

```bash
IRONCLAW_RELEASE_TAG=ironclaw-vX.Y.Z
curl --proto '=https' --tlsv1.2 -LsSf \
  "https://github.com/nearai/ironclaw/releases/download/${IRONCLAW_RELEASE_TAG}/ironclaw-installer.sh" | sh
```

```bash
ironclaw onboard   # pick provider + API key + model
ironclaw status    # → WebUI link
```

---

## Step 2 — Create a Telegram bot

1. Open **@BotFather**
2. `/newbot`
3. name + username (ends in `bot`)
4. copy the **token**

⚠️ The token is a full credential — never share it.

---

## Step 3 — Expose it (local installs)

Telegram only delivers to public HTTPS (443/80/88/8443):

```bash
ngrok http 3000
# or:  tailscale funnel 3000
# or:  cloudflared tunnel --url http://localhost:3000
```

---

## Step 4 — Configure Telegram

WebUI → **Admin → Configuration → Telegram deployment configuration**

1. Bot token
2. Webhook secret — `openssl rand -hex 32`
3. Public webhook URL — `https://<host>/webhooks/extensions/telegram/updates`
4. Bot username (no `@`)

Then **Extensions → install Telegram**.

---

## Step 5 — Pair & talk

- Open the **pairing panel** (link / QR), or send `/start` + code to the bot
- Pairing = only *you* act as you
- DM the bot → it replies

---

## One action to automate

> "Every morning at 09:00 send me the top NEAR headlines."

IronClaw builds the routine and runs it on schedule.

---

## Add a skill

- **WASM tools** — describe it, it builds it (sandboxed)
- **MCP servers** — plug in any Model Context Protocol server
- **Plugins** — drop in channels & tools without restarting

---

## Recap

✅ Deploy in < 30 sec
✅ Connect to Telegram
✅ Automate one action
✅ Add a skill

**Next → the NEAR course: build something real, present the results.**
