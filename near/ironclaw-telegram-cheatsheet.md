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

---

## 1. Deploy in < 30 seconds

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

## 2. Connect to Telegram

1. **Create a bot** — message [@BotFather](https://t.me/botfather), send `/newbot`, choose a name + a username ending in `bot`. Copy the **token**.
2. **Start IronClaw** — `ironclaw serve`
3. **Local install? Expose HTTPS** (Telegram only delivers to public HTTPS on ports 443/80/88/8443):
   ```bash
   ngrok http 3000                 # or: tailscale funnel 3000
                                    # or: cloudflared tunnel --url http://localhost:3000
   ```
4. **WebUI → Admin → Configuration → Telegram deployment configuration** — fill 4 fields:
   | Field | Value |
   |---|---|
   | Bot token | from BotFather |
   | Webhook secret token | `openssl rand -hex 32` (you invent it) |
   | Public webhook URL | `https://<host>/webhooks/extensions/telegram/updates` |
   | Bot username | your bot name, **without** `@` |
5. **WebUI → Extensions → install Telegram** (or just ask the agent in chat).
6. **Pair your account** — open the pairing panel (link / QR) or send `/start` + code to the bot. Pairing stops strangers from talking to your agent as you.
7. **Talk to it** — DM the bot. For groups: mention the bot (or `/setprivacy` off in BotFather).

---

## 3. Automate one action

Ask the agent in chat, e.g.:

> "Every morning at 09:00 send me the top 5 NEAR ecosystem headlines."

IronClaw builds the tool/routine itself (Dynamic Tool Building, Routines Engine).

---

## 4. Add a skill

Three ways to extend IronClaw:

- **Built-in / WASM tools** — describe what you need, it builds it as an isolated WASM tool.
- **MCP servers** — connect any Model Context Protocol server for extra capabilities.
- **Plugins / channels** — drop in new WASM tools and channels (Telegram, Slack, …) without restarting.

---

## Key commands

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

- **Bot never replies** → tunnel is down, or the *Public webhook URL* hostname changed (free tunnels change on restart), or the port isn't 443/80/88/8443.
- **Works in DM, silent in group** → mention the bot, or disable privacy mode via BotFather `/setprivacy`.
- **"An administrator must configure the Telegram bot first"** → fill all 4 fields in **Admin → Configuration** and save.
- **Activation fails after save** → check the token is exact, the secret is only `[A-Za-z0-9_-]`, the URL is the full `…/webhooks/extensions/telegram/updates`, and the username has no `@`.
