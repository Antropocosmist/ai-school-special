---
title: "IronClaw + Telegram — Quick Start Cheatsheet"
type: guide
difficulty: beginner
tags: [near, ironclaw, telegram, agent, mcp, skills, meetup]
created: 2026-08-17
updated: 2026-08-17
---

# IronClaw + Telegram — Cheatsheet

**IronClaw** is NEAR's open-source Agent OS — a secure personal AI assistant you run yourself. Local, encrypted, sandboxed (WASM). Talk to it from the terminal, the web UI, Telegram or Slack.

> Sources: https://github.com/nearai/ironclaw · https://docs.ironclaw.com

There are **two ways** to run it:

- **NEAR AI Cloud** — hosted, one-click, zero terminal. Fastest for a meetup / first try.
- **Self-hosted** — install on your own machine, full control.

Both connect to Telegram the same way. The difference is only the deploy step and the webhook URL.

---

## 1. Quick deploy on NEAR AI Cloud (fastest — hosted)

No terminal, no Docker. You get a public `https://<your-agent>.agents.near.ai` URL with HTTPS already handled.

1. Open the **NEAR AI Agent Dashboard** → https://agent.near.ai
2. **Deploy** → pick **IronClaw** (Starter plan = 1 instance).
3. Wait for **"Your agent is ready"** → choose **"Open IronClaw"**.
4. Your agent is now live at `https://<your-agent>.agents.near.ai`.
   The admin panel is at `https://<your-agent>.agents.near.ai/admin`.

> ⚠️ Don't confuse with the **"Request dedicated deployment"** modal on `cloud.near.ai` — that's for booking dedicated GPUs. You don't need it to run an agent; the one-click deploy on `agent.near.ai` is enough.

---

## 2. Deploy self-hosted (your own machine)

Pick the latest `ironclaw-v*` tag from [Releases](https://github.com/nearai/ironclaw/releases/), then:

```bash
IRONCLAW_RELEASE_TAG=ironclaw-vX.Y.Z
curl --proto '=https' --tlsv1.2 -LsSf \
  "https://github.com/nearai/ironclaw/releases/download/${IRONCLAW_RELEASE_TAG}/ironclaw-installer.sh" | sh
```

Onboard (choose an LLM provider, paste its API key, accept the default model):

```bash
ironclaw onboard
```

Verify it's running and get the WebUI link:

```bash
ironclaw status
```

> Windows: start the WebUI in the foreground with `ironclaw serve` (the installer handles macOS/Linux as a background service).

---

## 3. Connect to Telegram

Works the same for both Cloud and self-hosted. Only the **Public webhook URL** differs.

### 3.1 Create the bot

1. Message [@BotFather](https://t.me/botfather) → `/newbot`.
2. Pick a name + a username ending in `bot`. Copy the **token**.

### 3.2 Configure the Telegram extension

Open **Admin → Configuration → "Telegram deployment configuration"** (status shows `Configuration required` until it's done). Fill 4 fields:

| Field | Value |
|---|---|
| Bot token | from BotFather |
| Webhook secret token | `openssl rand -hex 32` (you invent it — only letters, digits, `_`, `-`) |
| Public webhook URL | **Cloud:** `https://<your-agent>.agents.near.ai/webhooks/extensions/telegram/updates` · **Self-hosted:** `https://<host>/webhooks/extensions/telegram/updates` |
| Bot username | your bot name, **without** `@` |

Then **Save**.

> **Self-hosted only** — Telegram delivers to public HTTPS on ports 443/80/88/8443, so expose your local server first:
> ```bash
> ngrok http 3000                 # or: tailscale funnel 3000
>                                  # or: cloudflared tunnel --url http://localhost:3000
> ```
> On NEAR AI Cloud the HTTPS is already public — no tunnel needed.

### 3.3 Install + pair

1. **Admin → Extensions → Telegram → Connect** — this opens a pairing panel with a short **code** (e.g. `82N5X5WQ`).
2. In Telegram, send the bot **`/start <code>`** — the code goes into Telegram, *not* on the web page.
3. **Talk to it** — DM the bot. For groups: mention the bot (or `/setprivacy` off in BotFather).

Pairing stops strangers from talking to your agent as you.

---

## 4. Automate one action

Ask the agent in chat, e.g.:

> "Every morning at 09:00 send me the top 5 NEAR ecosystem headlines."

IronClaw builds the tool/routine itself (Dynamic Tool Building, Routines Engine).

---

## 5. Add a skill

Three ways to extend IronClaw:

- **Built-in / WASM tools** — describe what you need, it builds it as an isolated WASM tool.
- **MCP servers** — connect any Model Context Protocol server for extra capabilities.
- **Plugins / channels** — drop in new WASM tools and channels (Telegram, Slack, …) without restarting.

---

## Key commands (self-hosted only)

| Command | What it does |
|---|---|
| `ironclaw status` | service state + WebUI login link |
| `ironclaw onboard` | guided setup (provider, key, model) |
| `ironclaw serve` | start service in the foreground |
| `ironclaw repl` | interactive terminal chat |
| `ironclaw run --message "hi"` | run a single turn |
| `ironclaw models set-provider openai --model gpt-5-mini` | switch LLM |
| `ironclaw config set <key>` | set config (secrets are prompted, never echoed) |
| `ironclaw service restart` | apply a config change |

---

## Troubleshooting

- **Config won't save** → the two classic culprits:
  - **Bot username has a leading `@`** — remove it (`@IronClawBot` → `IronClawBot`).
  - **Webhook secret has illegal chars** — it accepts only `[A-Za-z0-9_-]` (1–256 chars). Use the output of `openssl rand -hex 32`.
- **The agent says "doesn't accept a bot token directly"** → ignore it. That's a failed tool, not the truth — the bot token **is** required in Admin → Configuration.
- **Bot never replies** → (self-hosted) tunnel is down, or the *Public webhook URL* hostname changed (free tunnels change on restart), or the port isn't 443/80/88/8443. (Cloud) check the webhook URL matches your `https://<your-agent>.agents.near.ai`.
- **Works in DM, silent in group** → mention the bot, or disable privacy mode via BotFather `/setprivacy`.
- **"An administrator must configure the Telegram bot first"** → fill all 4 fields in **Admin → Configuration** and save.
- **Pairing code expired** → the code is short-lived (~3 min). Open **Admin → Extensions → Telegram → Connect** again for a fresh one.
- **Activation fails after save** → check the token is exact, the secret is only `[A-Za-z0-9_-]`, the URL is the full `…/webhooks/extensions/telegram/updates`, and the username has no `@`.
