---
title: "NEAR Lesson 2: Deploy Your Agent & the AI Cloud"
type: lesson
difficulty: beginner
tags: [near, agent.near.ai, cloud.near.ai, ironclaw, agent, telegram, ssh, tee, attestation]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 2
---

# NEAR Lesson 2: Deploy Your Agent & the AI Cloud

**Duration:** 2 hours
**Format:** 100% hands-on

## Lesson Goal

By the end of this lesson you will have **your own secure AI agent (IronClaw) running 24/7 in Telegram**, plus a **NEAR AI Cloud API key** and your first call to a private, verifiable LLM. No terminal, no Docker — mostly clicks and prompts.

## Prerequisites

1. ✅ Zed with DeepSeek connected (Lesson 1)
2. ✅ GitHub account (Lesson 1)
3. ✅ A Telegram account
4. ✅ A bank card (the IronClaw Starter plan is free, but agent.near.ai asks to attach one — nothing is charged)

---

## Part 1: What Is an Agent — and What Is IronClaw

So far you've used AI in a chat: you ask → it answers → conversation ends. An **agent** is different:

| AI Chat (Zed) | AI Agent |
|---|---|
| Waits for your question | Works on its own, on schedule |
| One conversation at a time | Runs 24/7 in the cloud |
| No tools | Can use tools, browse, run tasks |
| You are the initiator | It initiates (sends you messages) |

**IronClaw** is NEAR's open-source **Agent OS** — "a secure personal AI assistant you run yourself." The source is public ([github.com/nearai/ironclaw](https://github.com/nearai/ironclaw), written in Rust). It's built on three ideas:

1. **Privacy** — your credentials are encrypted (AES-256-GCM).
2. **Security** — tools run in an isolated **WASM sandbox**, with **prompt-injection defense** (a malicious email can't trick your agent into leaking data).
3. **Extensibility** — add tools, skills, MCP servers, and channels (Telegram, Slack).

Today you deploy it on **agent.near.ai** — one click, under a minute.

---

## Part 2: Create a Telegram Bot with BotFather

**Why:** your agent needs a "body" — a Telegram bot is a Telegram account run by code.

1. Open Telegram → search **@BotFather** (the official bot for creating bots)
2. Send `/newbot`
3. Answer: bot **name** (any name, e.g. "My IronClaw Assistant")
4. Answer: bot **username** (must end with `bot`, e.g. `my_ironclaw_bot`)
5. BotFather gives you a **token** — a long string like `123456:ABC-DEF1234gh...`

> **⚠️ Save this token. It gives full control over your bot. Never share it, never commit it to GitHub.**

---

## Part 3: Deploy IronClaw on agent.near.ai

1. Go to [agent.near.ai](https://agent.near.ai) and sign in (any method you like)
2. Click **Deploy** → choose **IronClaw**
3. Choose the **Starter** plan — free, but you'll attach a card (nothing is charged)
4. Complete the sign-up transaction
5. Click **Generate and Download Access Key**:
   - **Public SSH key** — safe to share; it identifies your agent
   - **Private SSH key** — the actual key to your agent. **Download it, keep it secret, never share it.**
6. Accept that you downloaded the private key
7. Click **Activate Agent**

In under 30 seconds your agent is live at:

```
https://<your-agent>.agents.near.ai
```

The name is random (like `vast-fox-komoj`) — that's normal. The **admin panel** is at `https://<your-agent>.agents.near.ai/admin`.

---

## Part 4: Connect Telegram

Your agent is alive but has no body yet. Open **Admin** → **Configuration** → **"Telegram deployment configuration"**. Four fields:

| Field | Value |
|---|---|
| **Bot token** | from BotFather (Part 2) |
| **Webhook secret token** | a random 32-char string — letters, digits, `_`, `-` only |
| **Public webhook URL** | `https://<your-agent>.agents.near.ai/webhooks/extensions/telegram/updates` |
| **Bot username** | your bot name **without** the `@` (e.g. `my_ironclaw_bot`) |

**Making the webhook secret:** ask Zed's AI panel:

```
Give me a random 32-character string for a webhook secret.
Only letters, digits, underscore, and dash allowed.
```

(Or use [generate-random.org/webhook-secrets](https://generate-random.org/webhook-secrets): Count 1, Length 32, Format Hexadecimal, extra options off.)

Click **Save configuration**.

### Install the extension and pair

1. Left sidebar → **Extensions** → search **Telegram** → click **Install**
2. A pairing window opens with a short **code** (8 letters/digits)
3. Scan the QR code with your phone, or click **Open in Telegram**
4. Your bot chat opens → click **START** → send `/start <code>`

> The code goes **into Telegram**, not on the web page.

**Verify:** send your bot a message in Telegram. It should reply. 🎉 You now have a 24/7 agent.

---

## Part 5: First Conversation and a Routine

**Why a routine:** this is what makes an agent *autonomous* — it acts on a schedule, not just when you message it.

Send your agent:

```
Every morning at 09:00 send me the top 5 NEAR ecosystem headlines.
```

IronClaw's **Routines Engine** builds the tool and the schedule itself. Confirm when asked.

**Also try:**
- "Hi! Who are you and what can you do?"
- "Remember that my favorite color is blue." … then "What's my favorite color?"

---

## Part 6: NEAR AI Cloud — the Private LLM API

**Why this matters:** until now you've used ready-made agents. **cloud.near.ai** is the raw building block — an LLM API you call from your own code, with a privacy guarantee you can *verify*.

**The big idea.** Normally, when you send a prompt to an AI API, the server operator *could* read your prompts. NEAR AI Cloud runs models inside **TEEs** (Trusted Execution Environments) — hardware enclaves (Intel TDX + NVIDIA GPU TEE) that even the operator can't look inside. Every response carries an **attestation** — a cryptographic proof of which model ran, on which hardware. **You don't have to trust NEAR — your code checks.**

**It's OpenAI-compatible.** The API speaks the same language as OpenAI's, so almost any OpenAI code works by changing the URL and the key.

### Get your key

1. Go to [cloud.near.ai](https://cloud.near.ai) → sign in
2. Add ~$2 of credits
3. Find **API Keys** → create a key → save it (it's usually passed as `NEAR_AI_KEY`)

### Make your first call

**Why:** one script that talks to a private AI is the foundation for everything you'll build later (Lesson 5).

In Zed's AI panel, paste:

```
Create a Python script called hello_near_ai.py in my project.

It should:
1. Load the NEAR AI Cloud API key from a .env file (variable NEAR_AI_KEY)
2. Use the OpenAI-compatible API:
   - base URL: https://cloud-api.near.ai/v1
   - endpoint: POST /chat/completions
   - use the standard "openai" Python library pointed at this base URL
3. Ask the model: "Explain NEAR testnet to a beginner in 3 sentences."
4. Print the reply

Also:
- Create .env with NEAR_AI_KEY=PASTE_YOUR_KEY_HERE (I'll paste my real key myself)
- Make sure .env is in .gitignore
- Tell me exactly which line to replace with my real key
```

Paste your real key into `.env`, then:

```
Run hello_near_ai.py. If something fails, diagnose and fix.
```

**Verify:** you should see a friendly 3-sentence explanation of testnet. You just called a private, attested AI from your own code.

---

## Part 7: Why Your Agent Is Secure

You deployed a machine that holds secrets and acts for you. Three layers keep it safe:

| Layer | What it does | Analogy |
|---|---|---|
| **WASM sandbox** | every tool runs isolated, with only the permissions it needs | each contractor in a separate locked room |
| **Prompt-injection defense** | malicious text in emails/pages can't give the agent secret instructions | your assistant ignores orders slipped into a stranger's letter |
| **Encrypted credentials** | API keys stored encrypted (AES-256-GCM) | passwords in a safe, not on sticky notes |

**Golden rules for the whole course:**
1. Private keys, tokens, API keys — never in code, never in chat, never on GitHub
2. Only use official NEAR links (agent.near.ai, cloud.near.ai)
3. If something asks for your seed phrase — it's a scam

---

## Homework

1. Give your agent a personality: "Answer like a friendly librarian who loves NEAR. Keep replies under 3 sentences."
2. Add a second routine (e.g. a weekly Monday summary)
3. Run `hello_near_ai.py` and confirm the reply
4. Write your agent's URL and bot username into your project README (ask Zed to do it and commit)
5. Share one surprising thing your agent did in the group chat

---

## Troubleshooting

### "An administrator must configure the Telegram bot first"

You skipped Part 4. Go to Admin → Configuration → Telegram deployment configuration, fill all 4 fields, Save.

### Config won't save

Two classic culprits:
- **Bot username has a leading `@`** — remove it (`@MyBot` → `MyBot`)
- **Webhook secret has illegal characters** — only `[A-Za-z0-9_-]`, 1–256 chars

### Bot never replies

- Check the webhook URL matches **your** agent address exactly
- Re-check the bot token is copied completely (no missing characters)

### The agent says it "doesn't accept a bot token directly"

Ignore it — that's a failed tool talking. The token **is** required in Admin → Configuration.

### Pairing code expired

The code lives ~3 minutes. Go to Extensions → Telegram → Connect for a fresh one.

### `hello_near_ai.py` returns 401 / "Invalid API key"

```
My NEAR AI Cloud call returns 401. Check:
1. Is NEAR_AI_KEY in .env correct (no spaces)?
2. Do I have credits on cloud.near.ai?
Diagnose and fix.
```

### I lost my private SSH key

If you still have admin access, check for a way to regenerate it; otherwise redeploy a fresh agent (Starter is free) and keep the new private key safe.

---

## Related Materials

- [[near-lesson-01-ai-foundations]] — Previous lesson
- [[near-lesson-03-wallet-intents]] — Next lesson: wallet & Intents
- [[ironclaw-telegram-cheatsheet]] — IronClaw + Telegram quick reference
- [[How to get IronClaw in your Telegram in less than 30 seconds]] — visual walkthrough with screenshots

## Result

After this lesson you have:
- A Telegram bot created via BotFather
- IronClaw deployed on agent.near.ai, live at `https://<your-agent>.agents.near.ai` (free)
- Public + private SSH keys (private stored safely)
- Telegram connected and paired — the agent works 24/7 in your pocket
- A scheduled routine (autonomous daily task)
- A NEAR AI Cloud key + your first call to a private, attested LLM
- Understanding of agent security (WASM sandbox, prompt-injection defense, encryption)
