---
title: "NEAR Off-line Lesson 6: Final Project — NEAR Wallet Assistant & Presentation"
type: lesson
difficulty: advanced
tags: [near, offline, final-project, diploma, presentation, pitch, telegram, near-mcp, notebooklm]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 6
---

# NEAR Off-line Lesson 6: Final Project — NEAR Wallet Assistant & Presentation

**Format:** Instructor-led classroom — screen sharing + hands-on practice + final presentations

## How This Lesson Works

**First half:** All students build the final project and prepare their presentations simultaneously with AI assistance.
**Second half:** Each student presents their product to the group (5-7 minutes each).

---

## Prerequisites

Every student must have:
1. ✅ Zed with DeepSeek + NEAR MCP connected
2. ✅ Own Telegram bot from Lesson 4 (NEAR AI Cloud brain)
3. ✅ Testnet account(s) with some testnet NEAR
4. ✅ IronClaw agent from Lesson 3 (as backup / comparison)
5. ✅ Project on GitHub

---

## Part 0: What We're Doing Today

Today you build the diploma project — a **NEAR Wallet Assistant**: a Telegram bot that

- reports your NEAR testnet balance (`/balance`)
- sends testnet tokens to a friend (`/send 0.1 alice.testnet`)
- answers questions about NEAR (`/ask What is gas?`)

**Architecture:**

```
You ←→ Telegram ←→ Your Bot (Python)
                      ├── Brain: NEAR AI Cloud (private, attested LLM)
                      ├── Blockchain: NEAR testnet (reads & sends)
                      └── Dev tools: NEAR MCP in Zed (verify & test)
```

Then you prepare the defense: product analysis, 7-slide presentation, 5-minute pitch, Q&A prep, NotebookLM slides, rehearsal — and present to the group.

**You don't write code or documents yourself.** You tell AI what you need — it creates everything.

---

## Part 1: Build the NEAR Wallet Assistant

Open your project from Lesson 4 in Zed. In Zed's AI panel:

```
Extend my Telegram bot into a NEAR Wallet Assistant.

Add these commands:
/balance — show the balance of my testnet account(s)
/send <amount> <account.testnet> — send testnet NEAR to a friend.
  Ask me to confirm before sending. Max 1 NEAR per send.
/ask <question> — answer any NEAR question via NEAR AI Cloud
/help — list all commands

Implementation notes:
- Brain stays NEAR AI Cloud (OpenAI-compatible, base URL
  https://cloud-api.near.ai/v1, key NEAR_AI_KEY in .env)
- Blockchain actions: use the NEAR testnet RPC (rpc.testnet.near.org)
  with a NEAR library you install (e.g. py-near). The account's private
  key goes in .env as NEAR_ACCOUNT_PRIVATE_KEY — never in code.
- If I don't have the private key handy, generate a fresh keypair for a
  new account via NEAR MCP, or tell me how to export it from my wallet.
- All secrets in .env, .env in .gitignore
- Keep the ALLOWED_USER_ID guard from Lesson 4

Use NEAR MCP tools to verify your work as you go:
- create/import the account
- check balances match what the bot reports
- after a test /send, show the transaction on the explorer

Then run the bot and guide me through testing all four commands.
```

**Test everything:** `/balance`, `/ask What is gas?`, `/send 0.1 <neighbor>` (confirm + check on [testnet.nearblocks.io](https://testnet.nearblocks.io)), `/help`.

**Chat drop:** Paste the build prompt → test all four commands → show your neighbor the `/send` transaction on the explorer.

---

## Part 2: Push and Document

In Zed's AI panel:

```
Commit and push the Wallet Assistant.
1. Verify no secrets are committed (.env only in .gitignore)
2. Update README.md: what the bot does, the 4 commands, how to run it,
   architecture diagram in text form
3. Commit message: "Final project: NEAR Wallet Assistant"
Give me the repository link.
```

**Chat drop:** Paste the prompt. Save the repo link — you'll need it for the presentation.

---

## Part 3: Product Analysis

In Zed's AI panel, from your project folder:

```
Analyze my product.

Repository: [GitHub link]
Live bot: [@your_bot_username] on Telegram

Tasks:
1. Study the code and architecture
2. Identify key features (the 5 most important ones)
3. List all technologies used (NEAR AI Cloud, NEAR testnet, MCP, Telegram…)
4. Highlight unique solutions or clever implementations
5. Note what security measures are in place (why is my bot safe?)

Save the analysis to PRODUCT_ANALYSIS.md
```

---

## Part 4: Create the Presentation

In Zed's AI panel:

```
Create a presentation of my product.

Use PRODUCT_ANALYSIS.md as reference.

Format: Markdown
It will be used for creating a visual presentation with an AI service.

Structure (7 slides):

1. Title slide — product name, my name, date
2. Problem — what problem the product solves (why would anyone
   want a wallet assistant in Telegram?)
3. Solution — what the product does, how it solves the problem
4. Demo — the 4 commands with example replies, user scenario step by step
5. Technologies — Brain (NEAR AI Cloud), Blockchain (NEAR testnet),
   Body (Telegram), Tools (NEAR MCP, Zed, GitHub)
6. Architecture — component diagram described in text (what connects to what)
7. Conclusion — summary, future plans for the product

Add speaker notes under each slide (what to say, key points).

Save to PRODUCT_PRESENTATION.md
```

---

## Part 5: Pitch Script

In Zed's AI panel:

```
Write a 5-minute pitch script for my product.

Use PRODUCT_ANALYSIS.md and PRODUCT_PRESENTATION.md.

Tone: confident but simple. I'm presenting to a friendly group of
fellow students — not investors.

Structure:
- Hook (first 15 seconds — make them curious)
- Problem → Solution
- Live demo moment (I'll show the bot on my phone — write what I say)
- What I built it with (technologies, one sentence each)
- What was hard and how I solved it
- Closing (what's next)

Save to PITCH_SCRIPT.md
```

---

## Part 6: Q&A Preparation

In Zed's AI panel:

```
Prepare me for questions after my presentation.

Based on my product, generate 10 likely questions from the audience.
For each:
- The question
- A short, confident answer I can give
- A one-line "deeper" fact in case someone pushes further

Include at least one hard question about security and one about
"why not just use ChatGPT instead?"

Save to Q&A.md
```

---

## Part 7: Beautiful Slides via NotebookLM

[NotebookLM](https://notebooklm.google.com) turns documents into visuals. Feed it your presentation:

1. Open NotebookLM → create a new notebook
2. Upload `PRODUCT_PRESENTATION.md` (and `PRODUCT_ANALYSIS.md` if you like)
3. Use its presentation/slides feature to generate visual slides
4. Compare with your markdown — keep the better version, or mix
5. Download the slides as PDF/PPTX

If NotebookLM's slides don't match — tell AI in Zed:

```
The generated slides missed [what's missing]. Update
PRODUCT_PRESENTATION.md so NotebookLM produces a better result,
emphasizing [what matters].
```

**Chat drop:** NotebookLM: https://notebooklm.google.com → new notebook → upload presentation → generate slides → download.

---

## Part 8: Rehearse with AI

Practice makes the pitch. In Zed's AI panel:

```
You are a friendly but skeptical audience member at my final
presentation. I will present my pitch to you.

After I paste my script, you:
1. Ask me 3 questions (the hardest ones first)
2. Point out the weakest part of my story
3. Suggest how to make the demo moment more memorable
4. Grade my pitch: clarity, structure, confidence — out of 10

Here is my script:
[Paste PITCH_SCRIPT.md content]
```

**Chat drop:** Paste the rehearsal prompt → answer the 3 questions → fix your script with AI → rehearse once more.

---

## Part 9: Presentation Day — The Defense

**Each student presents (5-7 minutes):**
1. Title + one-sentence idea
2. Problem → Solution (2 slides)
3. **Live demo** — open Telegram on your phone, show `/balance`, `/ask`, `/send` live
4. Technologies (1 slide)
5. What was hard + what's next
6. Audience questions (use your Q&A.md!)

**While others present:** note one thing you'd steal for your own project.

---

## Homework

1. Push final versions of all documents (PRODUCT_ANALYSIS.md, PRODUCT_PRESENTATION.md, PITCH_SCRIPT.md, Q&A.md) to GitHub
2. Add one future feature to PLAN.md (e.g. price alerts, mainnet mode with safety guard)
3. Share your repository and bot in the group chat
4. Celebrate — you built a blockchain product with AI. From zero.

---

## Troubleshooting

### The Bot Can't Send (Signature Errors)

```
The /send command fails with: [paste error]. Diagnose it.
Check that the account's private key in .env matches the account ID
and that the account has enough balance for amount + gas.
```

### RPC Timeouts

```
NEAR RPC calls sometimes time out. Add retry logic (2 retries,
1 second apart) and a friendly error message. Explain what you changed.
```

### Bot Forgot a Command

```
The /ask answers are too slow for Telegram. Add a "typing…" indicator
and keep replies under ~4 sentences by adding a system prompt that
says: answer briefly.
```

### NotebookLM Won't Accept My File

Export `PRODUCT_PRESENTATION.md` as a text/PDF file first, or paste the content into a Google Doc and link that. Ask AI to help convert.

### I'm Nervous About Presenting

```
Act as my presentation coach. Give me 5 practical tips for a 5-minute
demo presentation to a friendly student audience, and one relaxation
technique to use right before I start.
```

---

## Related Materials

- [[near-offline-lesson-05]] — Previous lesson: NEAR MCP & skills
- [[near-offline-overview]] — Full course overview
- [[off-line-lesson-06]] — Original course final lesson (same defense format)
- [[near-lesson-05-build-present]] — Online variant: build & present
- [[ironclaw-telegram-cheatsheet]] — IronClaw reference (your always-on backup)

## Result

After this lesson, each student has:
- **NEAR Wallet Assistant** — a working Telegram bot: `/balance`, `/send`, `/ask`, `/help`
- Brain on NEAR AI Cloud, transactions on NEAR testnet, secrets in `.env`
- PRODUCT_ANALYSIS.md — structured product analysis
- PRODUCT_PRESENTATION.md — 7-slide presentation with speaker notes
- PITCH_SCRIPT.md — 5-minute pitch
- Q&A.md — 10 prepared answers
- Visual slides generated via NotebookLM
- Rehearsal with AI as the audience
- A live 5-7 minute defense presented to the group
- **A complete NEAR product, built from zero with AI tools**
