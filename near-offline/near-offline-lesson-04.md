---
title: "NEAR Off-line Lesson 4: NEAR AI Cloud — Private LLM API + Your Own Bot"
type: lesson
difficulty: intermediate
tags: [near, offline, cloud-near-ai, tee, attestation, telegram, python, api, env, privacy]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 4
---

# NEAR Off-line Lesson 4: NEAR AI Cloud — Private LLM API + Your Own Bot

**Format:** Instructor-led classroom — screen sharing + hands-on practice

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students repeat → wait for all → questions → next section.

---

## Prerequisites

From Lessons 1-3, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ NEAR AI Cloud API key (from Lesson 1, Part 15)
3. ✅ Project skeleton on GitHub with `.env.example` (from Lesson 2)
4. ✅ Telegram account
5. ✅ IronClaw agent running from Lesson 3 (as reference — we now build our own)

---

## Part 1: What Is NEAR AI Cloud — and Why It's Different

In Lesson 3 you used a ready-made agent. Now we go **under the hood** and build our own bot whose brain is **NEAR AI Cloud** ([cloud.near.ai](https://cloud.near.ai)).

**Three AI services you now know — what's the difference?**

| Service | What It Is | You Use It For |
|---------|-----------|----------------|
| **DeepSeek API** (Lesson 1) | Cheap general-purpose LLM API | Zed's brain, everyday coding |
| **agent.near.ai** (Lesson 3) | One-click hosted agent (IronClaw) | A ready assistant with web UI + Telegram, no code |
| **NEAR AI Cloud** (today) | Private LLM API — OpenAI-compatible | Your OWN code calls it. Models run in sealed hardware |

**The big idea — privacy you can verify.** Normally, when you send a prompt to an AI API, the server operator *could* read your prompts. NEAR AI Cloud runs models inside **TEEs** (Trusted Execution Environments) — hardware enclaves (Intel TDX + NVIDIA GPU TEE) that even the server operator cannot look inside. And here's the amazing part: **every response carries an attestation** — a cryptographic proof of which model ran, on which hardware. You can verify it with code. You don't have to trust NEAR — you check.

**It's OpenAI-compatible.** The API speaks the same language as OpenAI's: base URL `https://cloud-api.near.ai/v1`, endpoint `/chat/completions`. Almost any code that works with OpenAI works with NEAR AI Cloud by changing two lines: the URL and the key.

---

## Part 2: Sign Up and Get Your Key

You already created the key in Lesson 1. Quick check:

1. Go to [cloud.near.ai](https://cloud.near.ai) → sign in
2. Make sure you have a little credit (~$2 is plenty for this course)
3. Find your API key in the API Keys section (create one if you lost it)
4. The key is passed to the API as `NEAR_AI_KEY` — save it

**Chat drop:**
- `cloud.near.ai` → sign in → check credits → API Keys → copy your key
- This key will live in `.env` — NEVER in code, NEVER on GitHub

---

## Part 3: First Call — Hello, Private AI

Let's make our first call to the API. We'll let AI write the code — but first, understand what we're about to do:

1. We create a small Python file
2. It reads the API key from `.env` (not from the code!)
3. It sends a prompt to `https://cloud-api.near.ai/v1/chat/completions`
4. It prints the answer

Open your project folder in Zed. In Zed's AI panel:

```
Create a Python script called hello_near_ai.py in my project.

It should:
1. Load the NEAR AI Cloud API key from a .env file (variable NEAR_AI_KEY)
2. Use the OpenAI-compatible API:
   - base URL: https://cloud-api.near.ai/v1
   - endpoint: POST /chat/completions
   - Use the standard "openai" Python library pointed at this base URL
3. Ask the model: "Explain NEAR testnet to a complete beginner in 3 sentences."
4. Print the reply

Also:
- Create .env with NEAR_AI_KEY=PASTE_YOUR_KEY_HERE (I'll paste my real key myself)
- Make sure .env is in .gitignore (it should be from Lesson 2)
- Tell me exactly which line I need to replace with my real key
```

Paste your real key into `.env`, then ask AI to run it:

```
Run hello_near_ai.py. If something fails, diagnose and fix.
```

**You should see a friendly 3-sentence explanation of testnet.** You just called a private, attested AI from your own code. 🎉

**Chat drop:**
- Paste the script prompt → replace the key in `.env` with your real NEAR AI Cloud key
- Paste the run prompt → celebrate when the answer appears

---

## Part 4: Verify the Attestation — Proof You Can Check

Now the part that makes NEAR AI Cloud special. Every response carries a **hardware attestation** — a signed certificate proving the model ran inside a TEE on specific hardware.

In Zed's AI panel:

```
Explain to me how attestation works in NEAR AI Cloud, in simple language.

Then check: what is the current recommended way to verify an attestation
in Python? The NEAR AI SDK reportedly exposes something like
response.verify_attestation().

If there's a Python SDK for NEAR AI Cloud — install it, modify
hello_near_ai.py to verify the attestation of the response, and print
a clear result: "✅ Attestation verified" or "❌ Verification failed".

If no SDK is available, explain exactly what fields to check manually
and why they prove the model ran in a TEE.
```

**The concept in one line:** you don't trust NEAR's promise that your data was private — your code checks the cryptographic proof instead. That's "verify, don't trust."

**Chat drop:** Paste the prompt above. Show your neighbor the "✅ Attestation verified" output.

---

## Part 5: Create a Fresh Telegram Bot

We now build our own bot — the "body" for our own AI. Create a NEW bot (keep the Lesson 3 one):

1. Telegram → **@BotFather** → `/newbot`
2. Name: e.g. "My Private Assistant"
3. Username: must end with `bot`, must be unique
4. Copy the **token**

Also get your numeric Telegram user ID: message **@userinfobot** → it replies with your ID. Save both.

**Chat drop:**
- @BotFather → /newbot → new name + username → COPY TOKEN
- @userinfobot → send any message → COPY YOUR NUMERIC ID

---

## Part 6: Build Your Bot — AI Does the Coding

Now the main build. In Zed's AI panel:

```
Build a Telegram bot in Python, in my project folder.

Architecture:
- Brain: NEAR AI Cloud (OpenAI-compatible, base URL
  https://cloud-api.near.ai/v1, key from .env NEAR_AI_KEY)
- Body: Telegram via the python-telegram-bot library
- Secrets: all in .env (NEAR_AI_KEY, TELEGRAM_BOT_TOKEN, ALLOWED_USER_ID)

Behavior:
1. Only respond to messages from ALLOWED_USER_ID (my ID) — ignore others
2. Commands:
   /start — friendly welcome, explain what the bot can do
   /ask <question> — send the question to NEAR AI Cloud, reply with the answer
   /help — list commands
3. Any other message — remind me of the commands
4. If the API fails — reply with a friendly error, log details to the terminal

Use a plain "openai" client pointed at the NEAR AI Cloud base URL.
Add a requirements.txt with all dependencies.

Explain how to run it, then test: run it and wait for my message in Telegram.
```

**The instructor shows the bot working on screen: `/start`, `/ask What is NEAR?`**

**Chat drop:** Paste the build prompt → when AI says it's running, send `/start` and `/ask What is NEAR?` to your bot.

---

## Part 7: Push to GitHub — Without the Secrets

In Zed's AI panel:

```
Commit and push my project to GitHub.
Before pushing:
1. Verify .env is in .gitignore
2. Verify no real secrets are in any committed file
   (only .env.example with empty values)
3. Show me what files will be committed
Commit message: "Lesson 4: own Telegram bot on NEAR AI Cloud"
```

**Chat drop:** Paste the prompt. Open the GitHub repo — confirm `.env` is NOT there.

---

## Part 8: Running 24/7 — What Are Your Options?

Right now the bot lives on your laptop — it works only while your computer is on. What are the options for "always on"?

| Option | Effort | Cost | When to Use |
|--------|--------|------|-------------|
| **Keep it local** (today) | zero | free | Learning, testing |
| **IronClaw on agent.near.ai** (Lesson 3) | zero | free Starter | You want an always-on assistant NOW — it can do much of what this bot does, and it can connect MCP servers too |
| **A small VPS / fly.io** (later) | medium | ~free tier | Your custom bot in production |

**For this course:** the custom bot you built today teaches you the fundamentals — and your Lesson 3 IronClaw agent gives you 24/7 availability for free. In Lesson 5 we connect the blockchain to both.

**Chat drop:** Discussion: which option would you choose for a bot that must run while you sleep? Why?

---

## Homework

1. Add a `/summarize` command: paste a long text → bot returns a 3-bullet summary
2. Ask AI to add a second allowed user (a classmate) — test that strangers still get ignored
3. Verify the attestation again from a fresh conversation
4. Push your changes to GitHub
5. Compare: ask the same question to your custom bot and your IronClaw agent — write the funniest difference in the group chat

---

## Troubleshooting

### 401 / "Invalid API key"

- The key in `.env` is wrong or has extra spaces. Open `.env`, fix, restart the bot
- Check you have credits on cloud.near.ai

### Bot Doesn't Reply

```
My Telegram bot doesn't reply. Here's the terminal output: [paste]
Diagnose and fix. Also check the bot token in .env is complete.
```

### `.env` Accidentally Committed

If `.env` ever lands on GitHub: **revoke the keys immediately** (BotFather `/revoke` for the bot token; cloud.near.ai for the API key), then ask AI to remove the file from git history.

### ModuleNotFoundError

```
I get "ModuleNotFoundError" when running the bot. Install the missing
dependencies from requirements.txt and explain how to run it properly.
```

### Attestation Verification Fails

```
Attestation verification failed. Show me the raw response fields,
explain what each proves, and check whether my verification code
is checking the right fields.
```

---

## Related Materials

- [[near-offline-lesson-03]] — Previous lesson: IronClaw on agent.near.ai
- [[near-offline-lesson-05]] — Next lesson: NEAR MCP, skills & the blockchain
- [[off-line-lesson-04]] — Original course Lesson 4 (same bot pattern, DeepSeek brain)
- [[near-lesson-02-deploy-agent-cloud]] — Online variant covering agent.near.ai + cloud.near.ai
- [[ironclaw-telegram-cheatsheet]] — IronClaw reference (for the always-on option)

## Result

After this lesson, each student has:
- A NEAR AI Cloud account with credits and API key
- hello_near_ai.py — first direct call to the private LLM API
- Attestation verification — proof the model ran in a TEE, checked by their own code
- Their OWN Telegram bot in Python: NEAR AI Cloud as the brain, Telegram as the body
- Secrets managed properly: `.env` local, `.env.example` template, `.gitignore` enforced
- Everything pushed to GitHub (without secrets)
- Understanding of privacy-by-verification and the options for 24/7 operation
