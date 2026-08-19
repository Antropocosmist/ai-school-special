---
title: "NEAR Off-line Lesson 3: Deploy Your Agent — IronClaw on agent.near.ai + Telegram"
type: lesson
difficulty: intermediate
tags: [near, offline, ironclaw, agent, agent-near-ai, telegram, botfather, deployment, security, wasm]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 3
---

# NEAR Off-line Lesson 3: Deploy Your Agent — IronClaw on agent.near.ai + Telegram

**Format:** Instructor-led classroom — screen sharing + hands-on practice

## How This Lesson Works

Same flow: instructor explains → demonstrates on screen → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

---

## Prerequisites

From Lessons 1-2, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ NEAR testnet account (`yourname.testnet`)
3. ✅ Project blueprint on GitHub (ARCHITECTURE.md, SPECIFICATION.md, PLAN.md, TEAM.md)
4. ✅ A Telegram account
5. ✅ A bank card (the IronClaw Starter plan is free, but agent.near.ai asks to attach a card)

---

## Part 1: What Is an AI Agent — and What Is IronClaw

So far you've used AI in a chat window: you ask → it answers → conversation ends. An **agent** is different:

| AI Chat (Zed) | AI Agent |
|---------------|----------|
| Waits for your question | Works on its own, on schedule |
| One conversation at a time | Runs 24/7 in the cloud |
| No tools | Can use tools, browse, run tasks |
| You are the initiator | It initiates (sends you messages) |

**IronClaw** is NEAR's open-source **Agent OS** — "a secure personal AI assistant you run yourself." The source code is public ([github.com/nearai/ironclaw](https://github.com/nearai/ironclaw), written in Rust), and it's built around three ideas:

1. **Privacy** — your credentials are encrypted (AES-256-GCM). Even the hosting platform can't read them.
2. **Security** — tools run in an isolated **WASM sandbox** (each tool gets only the permissions it needs), with built-in **prompt-injection defense** (a malicious email can't trick your agent into leaking data).
3. **Extensibility** — you can add tools, skills, and connect other services (Telegram, Slack, MCP servers).

Today you deploy it on **agent.near.ai** — the NEAR AI Hub — in one click. No terminal, no Docker: in under a minute your agent is live on the internet with its own URL.

---

## Part 2: Create a Telegram Bot with BotFather

Your agent needs a "body" — Telegram. First we create a bot (a Telegram account run by code).

1. Open Telegram → search **@BotFather** (the official bot for creating bots)
2. Send `/newbot`
3. Answer: bot **name** (any name, e.g. "My IronClaw Assistant")
4. Answer: bot **username** (must end with `bot`, e.g. `my_ironclaw_bot`)
5. BotFather gives you a **token** — a long string like `123456:ABC-DEF1234gh...`

**Save this token.** It gives full control over your bot. Never share it, never commit it to GitHub.

**Chat drop:**
- Telegram → @BotFather → `/newbot`
- Name: anything. Username: must end with `bot`
- COPY THE TOKEN. Keep it secret.

---

## Part 3: Deploy IronClaw on agent.near.ai

Now the magic part. Instructor does it on screen first, then students repeat:

1. Go to [agent.near.ai](https://agent.near.ai) and sign in (any method you like)
2. Click **Deploy** → choose **IronClaw**
3. Choose the **Starter** plan — it's free, but you'll need to attach a card (nothing is charged)
4. Complete the sign-up transaction
5. Click **Generate and Download Access Key**
   - **Public SSH key** — this one is safe to share, it identifies your agent
   - **Private SSH key** — this one is the password to your agent. Download it, keep it secret, never share it
6. Accept that you downloaded the private key
7. Click **Activate Agent**

In under 30 seconds your agent is live at:

```
https://<your-agent>.agents.near.ai
```

The **admin panel** is at `https://<your-agent>.agents.near.ai/admin`. Your agent's address will have a random name (like `vast-fox-komoj`) — that's normal.

**Chat drop:**
- `agent.near.ai` → Deploy → IronClaw → Starter (free, card attached, nothing charged)
- Generate and Download Access Key → download BOTH keys
- Public key: shareable. Private key: NEVER share.
- Activate Agent → your URL: `https://<your-agent>.agents.near.ai`

---

## Part 4: Configure the Telegram Connection

Your agent is alive but has no body yet. Let's wire it to Telegram.

Open **Admin** (left sidebar of your agent's web UI) → **Configuration** → **"Telegram deployment configuration"**. Four fields to fill:

| Field | Value |
|---|---|
| **Bot token** | from BotFather (Part 2) |
| **Webhook secret token** | a random 32-character string — you invent it. Only letters, digits, `_`, `-` |
| **Public webhook URL** | `https://<your-agent>.agents.near.ai/webhooks/extensions/telegram/updates` (replace with YOUR agent address) |
| **Bot username** | your bot name **without** the `@` (e.g. `my_ironclaw_bot`) |

**Making the webhook secret:** the easiest way is to ask AI in Zed:

```
Give me a random 32-character string for a webhook secret.
Only letters, digits, underscore, and dash allowed.
```

(Or use a generator site: [generate-random.org/webhook-secrets](https://generate-random.org/webhook-secrets) — Count 1, Length 32, HMAC-SHA256, Hexadecimal.)

Click **Save configuration**.

**Chat drop:**
- Admin → Configuration → Telegram deployment configuration
- 4 fields: bot token · webhook secret (32 chars, `[A-Za-z0-9_-]` only) · webhook URL `https://<YOUR-AGENT>.agents.near.ai/webhooks/extensions/telegram/updates` · username WITHOUT `@`
- Save configuration

---

## Part 5: Install the Extension and Pair

1. Left sidebar → **Extensions** → search **Telegram** → click **Install**
2. A pairing window opens with a short **code** (8 letters/digits)
3. Either scan the QR code with your phone, or click **Open in Telegram**
4. Your bot chat opens → click **START** → send the code: `/start <code>`

Pairing stops strangers from talking to your agent as you — only you (the paired account) can use it.

**Chat drop:**
- Extensions → Telegram → Install → copy the 8-character code
- In Telegram: open your bot → START → send `/start <code>`
- The code goes into Telegram, NOT on the web page

---

## Part 6: First Conversation

Send your agent a message in Telegram:

- "Hi! Who are you and what can you do?"
- "What do you know about NEAR?"
- "Remember that my favorite color is blue." … then ask "What's my favorite color?"

Try the web UI too (same conversation, `https://<your-agent>.agents.near.ai`) — same brain, two bodies.

**Chat drop:** Try the three messages above. Confirm the agent remembers your favorite color. Show your neighbor.

---

## Part 7: Teach It a Routine — A Scheduled Task

Now make it *autonomous*. In Telegram (or the web UI), ask:

```
Every morning at 09:00 send me the top 5 NEAR ecosystem headlines.
```

IronClaw has a **Routines Engine** — it builds the tool and the schedule itself. Confirm you want it, and check the routine list in the web UI.

**Chat drop:** Send the routine request above. Confirm. Find where routines are listed in the web UI and show your neighbor.

---

## Part 8: Why Your Agent Is Secure (10-Minute Explanation)

You just deployed a machine that holds secrets and acts on your behalf. Why is IronClaw safe? Three layers:

| Layer | What It Does | Analogy |
|-------|-------------|---------|
| **WASM sandbox** | Every tool runs in an isolated box with only the permissions it needs | Each contractor works in a separate locked room, with only the keys to rooms they need |
| **Prompt-injection defense** | Malicious text (in emails, web pages) can't give your agent secret instructions | Your assistant won't follow instructions slipped into a letter from a stranger |
| **Encrypted credentials (AES-256-GCM)** | Your API keys are stored encrypted | Your passwords are in a safe, not on sticky notes |

**The SSH key pair from Part 3:**
- **Public key** = like your home address. Fine to share.
- **Private key** = like your house keys. Anyone with it enters as you.

**Golden rules for the whole course:**
1. Private keys, tokens, and API keys never go in code, never in chat, never on GitHub
2. On the web, only use official NEAR links (agent.near.ai, cloud.near.ai)
3. If something asks for your seed phrase — it's a scam. Legit services never ask.

**Chat drop:** Discussion questions: Which key can you share? What does the WASM sandbox protect against? What would you do if you accidentally posted your bot token in a public chat?

---

## Homework

1. Give your agent a personality: "From now on, always answer like a friendly librarian who loves NEAR. Keep replies under 3 sentences."
2. Add a second routine (e.g. a weekly Monday summary)
3. Try the web UI on your phone — same conversation as Telegram
4. Write down your agent's URL and bot username in your project README (ask AI in Zed to do it and commit)
5. Share one surprising thing your agent did in the group chat

---

## Troubleshooting

### "An administrator must configure the Telegram bot first"

You skipped Part 4. Go to Admin → Configuration → Telegram deployment configuration, fill all 4 fields, Save.

### Config Won't Save

The two classic culprits:
- **Bot username has a leading `@`** — remove it (`@MyBot` → `MyBot`)
- **Webhook secret has illegal characters** — only `[A-Za-z0-9_-]`, 1-256 characters. Use a freshly generated 32-char string

### Bot Never Replies

- Check the webhook URL matches YOUR agent address exactly (not the example from the screen)
- Re-check the bot token is copied completely (no missing characters)

### Works in Private Chat, Silent in Groups

Groups require mentioning the bot (`@your_bot question`), or disable privacy mode: BotFather → `/setprivacy` → Disable.

### Pairing Code Expired

The code lives ~3 minutes. Go to Extensions → Telegram → Connect again for a fresh code.

### The Agent Says It "Doesn't Accept a Bot Token Directly"

Ignore it — that's a failed tool talking, not the truth. The token IS required in Admin → Configuration.

### I Lost My Private SSH Key

If you still have access to the agent's admin panel, check for a way to regenerate the key; otherwise redeploy a fresh agent (Starter plan is free) and keep the new private key safe this time.

---

## Related Materials

- [[near-offline-lesson-02]] — Previous lesson: architecture & plan
- [[near-offline-lesson-04]] — Next lesson: NEAR AI Cloud + your own bot
- [[ironclaw-telegram-cheatsheet]] — IronClaw + Telegram quick reference
- [[How to get IronClaw in your Telegram in less than 30 seconds]] — Visual guide with screenshots
- [[near-lesson-02-deploy-agent-cloud]] — Online NEAR course variant of this lesson

## Result

After this lesson, each student has:
- A Telegram bot created via BotFather
- IronClaw deployed on agent.near.ai — live at `https://<your-agent>.agents.near.ai` (free Starter plan)
- Public + private SSH keys (private key stored safely)
- Telegram connected and paired — the agent works 24/7 in their pocket
- A scheduled routine (autonomous daily task)
- Understanding of agent security: WASM sandbox, prompt-injection defense, encrypted credentials
- The "no-code path" to a NEAR agent — a working fallback and reference for everything we build next
