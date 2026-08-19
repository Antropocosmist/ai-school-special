---
title: "NEAR Lesson 1: AI Development Foundations"
type: lesson
difficulty: beginner
tags: [near, github, ide, api, tokens, context, zed, deepseek, fundamentals]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 1
---

# NEAR Lesson 1: AI Development Foundations

**Duration:** 2 hours
**Format:** Theory + Practice

## Lesson Goal

By the end of this lesson you will have a **complete AI development environment**: a GitHub account, the Zed editor connected to the DeepSeek API, Git installed, your first project pushed to GitHub — and you'll understand **tokens** and **context**, the two concepts that decide how much AI costs you. Everything in this course builds on this setup.

## Prerequisites

1. **A computer** (Windows / Mac / Linux)
2. **A GitHub account** — sign up at [github.com](https://github.com) (free)
3. **A Gmail account** — for registrations
4. **~$2 on a bank card** — to top up the DeepSeek API (lasts for months)
5. **A Telegram account** — you'll use it from Lesson 2

---

## Part 1: Where Code Lives — GitHub

**Why you need to understand this first:** every project in this course ends up on GitHub. It's where code is stored, backed up, and shared.

Your code can be in three places:

| Where | What it is | Example |
|---|---|---|
| **Locally** | a folder on your computer | `~/projects/my-app` |
| **GitHub (remote)** | cloud code storage | `github.com/yourname/my-app` |
| **Synced** | both, via Git | the normal way of working |

```
Your computer ←——— Git ———→ GitHub (cloud)
```

**Why GitHub:**
- **Backup** — code survives a broken computer
- **Version history** — roll back any version
- **Portfolio** — your public profile
- **Deployment** — many services (including NEAR) load code directly from GitHub

**Do it now:** create a free account at [github.com](https://github.com) if you haven't already.

---

## Part 2: The Tool We Install — Zed

**Why Zed:** you need an AI assistant that can *do* things (create files, run commands, push to GitHub), not just chat. Zed is a code editor with an AI assistant built in — like Google Docs for code.

**What it is:** you open a project, see your files, and an AI panel sits next to your code. You describe what you want in plain language — AI writes and changes the files.

**How you talk to it:** press `Ctrl+Shift+A` (Mac: `Cmd+Shift+A`) to open the AI panel.

### Install Zed

1. Go to [zed.dev/download](https://zed.dev/download)
2. Download the version for your OS
3. Install it like any normal program

Open Zed once, then close it — we'll configure it next.

---

## Part 3: Get a DeepSeek API Key

**Why:** an **API key** is a password that lets your tools use an AI's brain on your behalf. Zed without a key is just an editor; with a key, it's an editor with a brain.

DeepSeek is the cheapest solid provider — $2 lasts for months.

1. Go to [platform.deepseek.com](https://platform.deepseek.com)
2. Sign up (you can use your Google account)
3. **Billing** → top up $2
4. **API Keys** → create a new key → name it `zed`
5. Copy the key — it looks like `sk-…` (a long string)

> **⚠️ Save the key somewhere safe. Never share it, never put it on GitHub.** It gives access to AI on your behalf.

---

## Part 4: Connect DeepSeek to Zed

1. Open Zed
2. Open the AI panel: `Ctrl+Shift+A` (Mac: `Cmd+Shift+A`)
3. Click the model name at the bottom → **Configure** / **Add Provider**
4. Paste your DeepSeek key when asked

**If DeepSeek doesn't appear directly,** ask the AI to do it. In the AI panel, paste:

```
Help me connect the DeepSeek API to Zed.
My key: sk-...
Add the DeepSeek provider to settings (~/.zed/settings.json).
Explain what you're doing.
```

**Verify:** type this in the AI panel:

```
Hi! Explain in one sentence what you can do and how I work with you.
```

If it replies — you're connected. 🎉

---

## Part 5: Install Git and GitHub CLI

**Why:** Git is how code moves between your computer and GitHub. GitHub CLI (`gh`) lets the AI log in and create repositories for you. We'll install both by asking the AI.

In Zed's AI panel, paste:

```
Install Git and GitHub CLI (gh) on my computer.

My OS: [Windows / Mac / Linux].

If macOS — use Homebrew (install Homebrew first if needed:
brew install git gh).
If Git is already installed — just check the version (git --version).

After installing, verify:
1. git --version
2. gh --version

Then help me authenticate: run "gh auth login".
I'll choose: GitHub.com → HTTPS → authenticate via browser.
After that, verify with "gh auth status".
```

A browser window opens — click **Authorize**. When `gh auth status` shows your username, you're in.

> **⚠️ Windows users:** run PowerShell **as administrator** (right-click → Run as administrator) so installed tools are available globally.

---

## Part 6: Your First Project — a Calculator

**Why:** to experience the core workflow of this whole course — *you speak, AI builds*. You won't write a single line of code.

Open a projects folder in Zed (create `~/projects` on Mac/Linux, `C:\Projects` on Windows), then in the AI panel paste:

```
Create a simple calculator web app in a new folder called "calculator".

Use plain HTML, CSS, and JavaScript — no frameworks, no build tools.

Features:
- Buttons for digits 0-9 and operations + - * /
- A display showing the current input and result
- "C" button to clear, "=" to calculate
- Nice clean design

Create all files in the calculator folder. Explain what you created.
```

**Verify:** open `calculator/index.html` in a browser (double-click it). Test `7 + 8 = 15`. ✅

---

## Part 7: Push to GitHub

**Why:** code on your computer is only visible to you. On GitHub it's saved, shareable, and portable.

In Zed's AI panel, paste:

```
Create a GitHub repository called "calculator" and push my calculator
project to it. Then give me the repository link.
```

**Verify:** open the link the AI gives you — your project is on the internet.

---

## Part 8: Tokens and Context — What You're Actually Paying For

**Why this matters:** every lesson you'll paste prompts into Zed. If you understand tokens and context, you'll spend $2 over months instead of days.

### A token is a "word" for AI

You don't pay per question — you pay per **token** (a piece of text the AI reads or writes).

| Unit | ≈ tokens |
|---|---|
| 1 English word | ~1.3 |
| 1 A4 page | ~500 |
| 1M tokens | ~3,000 pages |

You pay for **input** (what you send) **and output** (what the AI writes).

### Context is the AI's working memory

Every model has a **context window** — the max it can "see" at once. DeepSeek V4: ~1M tokens. When the window fills up, the AI "forgets" the beginning of the conversation.

**Why it costs money:** on every request you pay for the **whole conversation again**, not just the new message. A long chat with big files pasted in = expensive and forgetful.

### Keep it cheap: AGENTS.md

**Why:** instead of repeating "be concise, don't waste words" every time, you write it once in a file that every AI reads automatically.

In Zed's AI panel, paste:

```
Create an AGENTS.md file in my projects folder.

It should contain rules for AI agents:
1. Be concise — no fluff, no "Sure, I can help with that"
2. Result first, then explanation
3. Never put secrets (API keys, tokens) in code or commits
4. If something is unclear, ask instead of guessing
5. After completing a task, summarize what was done in 2-3 lines

Keep it short.
```

**Verify:** open AGENTS.md and read it. From now on, your AI is cheaper and more focused.

---

## Homework

1. Make sure `gh auth status` works and your calculator is on GitHub
2. Ask AI to add **one** feature to the calculator (e.g. a decimal point or a `%` button) and push the change
3. Re-read your AGENTS.md — anything you'd add?
4. Share your calculator repo link in the group chat

---

## Troubleshooting

All problems are solved the same way: **copy the prompt → paste into Zed → AI fixes it.**

### Zed Doesn't See DeepSeek

```
DeepSeek doesn't appear as a provider in Zed.
Check my settings and fix it. Explain what you're changing.
```

### Git Won't Install

```
Git installation failed. Here's the error: [paste error]
Diagnose and give me the exact next step for my OS: [Windows / Mac / Linux].
```

### Can't Push to GitHub

```
I can't push to GitHub. The error is: [paste error]
Check gh auth status, fix authentication if needed, then push.
```

### Accidentally Pushed a Secret to GitHub

If an API key ever lands on GitHub — **revoke it immediately** in the provider dashboard, then:

```
I accidentally committed a secret to GitHub.
1. Tell me how to revoke the key
2. Remove the secret from git history
3. Make sure .gitignore and .env are set up so it never happens again
```

---

## Related Materials

- [[near-lesson-02-deploy-agent-cloud]] — Next lesson: deploy your agent
- [[lesson-01-github-ide-ai]] — Original Lesson 1 (full version, same setup)
- [[lesson-02-free-tokens-optimization]] — Original Lesson 2 (deep dive on tokens)
- [[tool-zed]] — More about Zed
- [[link-deepseek]] — DeepSeek API

## Result

After this lesson you can:
- Explain where code lives (locally vs GitHub) and why GitHub matters
- Use Zed with DeepSeek connected
- Install tools (Git, GitHub CLI) by pasting prompts
- Create a project and push it to GitHub — without writing code
- Understand tokens, context, and why AGENTS.md saves money
