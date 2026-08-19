---
title: "NEAR Off-line Lesson 1: Setup — GitHub, Zed, DeepSeek & NEAR Accounts"
type: lesson
difficulty: beginner
tags: [near, offline, github, zed, deepseek, api, homebrew, context, agents-md, near-account, testnet]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 1
---

# NEAR Off-line Lesson 1: Setup — GitHub, Zed, DeepSeek & NEAR Accounts

**Format:** Instructor-led classroom — screen sharing + hands-on practice

## How This Lesson Works

The instructor stands at a desk with a laptop connected to a big screen. Students sit at their desks with their own laptops.

**Flow for each section:**
1. Instructor explains what we're about to do and why
2. Instructor does it on screen — students watch
3. Instructor drops the prompt/link in the common chat
4. Students copy from chat, paste, and repeat on their own machines
5. We wait until everyone succeeds
6. Instructor answers questions if any
7. Move to the next section

**Common chat:** All prompts, links, and guides are dropped there. Students copy-paste — no typing from memory.

---

## Prerequisites

Before the lesson, every student should have:

1. **A computer** (Windows / Mac / Linux)
2. **A GitHub account** — [github.com](https://github.com) (free, sign up beforehand)
3. **A Gmail account** — needed for registrations
4. **~$2 on a bank card** — to top up DeepSeek API balance (lasts for months)
5. **A Telegram account** — we'll use it from Lesson 3 for our agent
6. **Access to the common chat** (Telegram / WhatsApp / Discord)

---

## Part 1: Understanding Where Code Lives

**Three places your code can be:**

| Where | What It Is | Example |
|-------|-----------|---------|
| **Locally** | A folder on your computer | `C:\Projects\my-app` (Windows) or `~/projects/my-app` (Mac/Linux) |
| **GitHub (remote)** | Cloud code storage | `github.com/yourname/my-app` |
| **Synced** | Both places — via Git | Most common: you work locally, save to GitHub |

```
Your computer ←——— Git ———→ GitHub (cloud)
```

**Why GitHub:**
- Backup — code won't disappear if your computer breaks
- Version history — roll back any version
- Portfolio — your public profile for future employers
- Deployment — many services load code directly from GitHub (including NEAR agents later in this course)

**Chat drop:** `GitHub: https://github.com` — register if you haven't yet. Free account is all you need.

---

## Part 2: The Tool We're Installing — Zed

Today we install **Zed** — your AI-powered code editor. It's where you'll do all your work.

**What Zed is:** A code editor with an AI assistant built right inside. You open a project, see your files, and the AI panel lives next to your code. You describe what you want — AI writes and changes code for you. Like Google Docs, but for programming — with an AI copilot that never leaves your side.

**How you interact:** Press `Ctrl+Shift+A` (Mac: `Cmd+Shift+A`) — the AI panel opens. Type what you need, AI responds and edits files directly in the editor.

**Zed connects to the DeepSeek API** — that's the "brain" powering the AI. We'll set that up next. (Later in the course we'll also plug the **NEAR AI Cloud** API and the **NEAR MCP** server into Zed — that's the NEAR-specific part.)

---

## Part 3: Install Zed

1. Open browser → go to [zed.dev/download](https://zed.dev/download)
2. Download the right version for your OS
3. Install like any normal program

**Chat drop:** `Zed download: https://zed.dev/download` — install and open it once.

---

## Part 4: Get a DeepSeek API Key

**What is an API key?** It's a password that lets Zed connect to DeepSeek's AI brain. Without a key, Zed is just a text editor. With a key — it's an editor with an AI assistant built in.

**Cost:** You need to top up $2. This is cheaper than a cup of coffee and lasts for months. DeepSeek is the cheapest AI provider.

1. Open browser → go to [platform.deepseek.com](https://platform.deepseek.com)
2. Sign up (can use Google account)
3. Go to **Billing** → Top up with $2
4. Go to **API Keys** → Create new key → name it `zed`
5. Copy the key — it looks like: `sk-a1b2c3d4e5f6...`

**IMPORTANT:** Save the key somewhere safe. Never share it. It gives access to AI on your behalf.

**Chat drop:**
- `DeepSeek platform: https://platform.deepseek.com`
- Sign up (Google) → Top up $2 → API Keys → Create key named "zed" → Copy it
- SAVE THE KEY. Do not share.

---

## Part 5: Connect DeepSeek to Zed

1. Open Zed
2. Open the AI panel: **`Ctrl+Shift+A`** (Mac: **`Cmd+Shift+A`**)
3. At the bottom of the AI panel, click the model name
4. Select "Configure" or "Add Provider"
5. Zed will ask for an API key — paste your DeepSeek key

**If Zed doesn't offer DeepSeek directly** — we'll use AI to help us. Type in the AI panel:

```
Help me connect the DeepSeek API to Zed.
My key: sk-...
Add the DeepSeek provider to settings (~/.zed/settings.json).
Explain what you're doing.
```

After this, DeepSeek will appear as a model option in Zed.

**Chat drop:** In Zed AI panel (`Ctrl+Shift+A` / `Cmd+Shift+A`) → click model name → Add Provider → paste your DeepSeek key. If DeepSeek doesn't appear, paste the prompt above.

---

## Part 6: Homebrew for macOS + Install Git

Before we install anything, macOS users need **Homebrew** — a package manager. Without it, AI has a very hard time installing programs on Mac. Think of Homebrew as an "App Store for the terminal" — it lets AI install tools with simple commands.

Windows users can skip this — they'll use PowerShell as Administrator instead.

### macOS: Install Homebrew

**Instructor shows on screen:**

1. Open **Terminal** (Finder → Applications → Utilities → Terminal)
2. Go to [brew.sh](https://brew.sh) — copy the install command
3. Paste into terminal and run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

4. Follow the on-screen instructions — you'll need to enter your Mac password
5. After installation, the terminal will show "Next steps" — two lines to run:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

6. Verify: `brew --version` — should show a version number

**Chat drop (macOS only):**
- Open Terminal → copy install command from https://brew.sh → paste and run
- Enter your Mac password when asked
- Run the two "Next steps" lines shown at the end
- Verify: `brew --version`
- Windows users: skip this, use PowerShell as Administrator instead

### Now Install Git (all platforms)

**Create folder:**
- **Windows:** Open File Explorer → create `C:\Projects`
- **Mac/Linux:** Open Finder/Terminal → create `~/projects`

**Open it in Zed:** Zed → Open Project → select the `Projects` folder.

**Now ask AI to install Git.** In Zed's AI panel:

```
Install Git on my computer.

My OS: [Windows / Mac / Linux].

If macOS — use Homebrew: brew install git
If Git is already installed — check the version (git --version).
If not — give me the install command and explain what to press.

After installation, verify that Git works.
```

**Chat drop:**
- Create folder: Windows `C:\Projects`, Mac/Linux `~/projects`
- Open in Zed → Open Project → select the folder
- In Zed AI panel, paste the Git install prompt above
- ⚠️ Windows: Right-click PowerShell → Run as administrator first!

---

## Part 7: Install GitHub CLI

**GitHub CLI (`gh`)** is a tool that connects your computer to GitHub from the terminal. AI uses it to create repositories and push code for you.

Ask AI in Zed's AI panel:

```
Install GitHub CLI (gh) on my computer.

My OS: [Windows / Mac / Linux].

Install it. Verify it works: gh --version

Then help me authenticate with GitHub:
Run "gh auth login" and guide me through it step by step.
I'll choose: GitHub.com → HTTPS → authenticate via browser.

After that, verify: gh auth status
```

**Chat drop:** Paste the prompt above. When `gh auth login` asks — GitHub.com → HTTPS → browser. Confirm in browser. Then `gh auth status` should show your username.

---

## Part 8: First Project — Calculator

Now the fun part. We create a working calculator **without writing a single line of code**.

In Zed's AI panel (your `Projects` folder is open):

```
Create a simple calculator web app in a new folder called "calculator".

Use plain HTML, CSS, and JavaScript — no frameworks, no build tools.

Features:
- Buttons for digits 0-9 and operations + - * /
- A display showing the current input and result
- "C" button to clear
- "=" button to calculate
- Nice clean design

Create all files in the calculator folder. Explain what you created.
```

AI creates the files. Open `calculator/index.html` in the browser by double-clicking it. Test: 7 + 8 = 15. ✅

**Chat drop:** Paste the prompt above. Then double-click `index.html` in the calculator folder and try 7 + 8 = 15.

---

## Part 9: Push to GitHub

Let's save our calculator to the cloud. In Zed's AI panel:

```
Create a GitHub repository called "calculator" and push my calculator project to it.
Then give me the repository link.
```

**Chat drop:** Paste the prompt. Open the GitHub link AI gives you — your calculator is now on the internet.

---

## Part 10: What Are Tokens and Why Should You Care

A quick but important concept — **tokens** are the "currency" of AI:

| Concept | What It Means |
|---------|---------------|
| **Token** | A piece of text AI reads/writes (~0.75 of an English word) |
| **Context window** | How many tokens AI can "remember" in one conversation |
| **API cost** | You pay per token — more tokens = more money |
| **Context optimization** | Keeping the conversation short so AI stays focused and cheap |

**Why this matters for this course:** Every lesson you'll paste prompts into Zed. If you paste a whole 500-line file into the chat every time, AI gets slow, expensive, and forgetful. The skill in the next part fixes that.

---

## Part 11: Context Optimization Skill

We install a **skill** — a reusable set of instructions that makes AI work better. Skills will come back throughout this course: in Lesson 5 we write our own SKILL.md for the NEAR agent.

Ask AI in Zed's AI panel:

```
Install the "context-optimization" skill for this agent.

Find the skill at: ~/.agents/skills/context-optimization/SKILL.md
If it exists, read it and start following its rules.
If it doesn't exist, explain how to install skills and guide me.
```

**Chat drop:** Paste the prompt above. After installation, ask: `Explain what context optimization means and why it saves money.` Share the answer with your neighbor.

---

## Part 12: AGENTS.md — Rules for AI

Now we create **AGENTS.md** — a rules file. It's a note to every AI that works in your projects: "here's how to behave." Think of it as a job description you write once, and every AI agent reads automatically.

In Zed's AI panel:

```
Create an AGENTS.md file in my Projects folder.

It should contain rules for AI agents:

1. Language: always reply in [English/Russian]
2. Code style: simple, readable, with comments explaining non-obvious parts
3. Before making changes, explain what you're about to do in 1-2 sentences
4. Never push to GitHub without my explicit request
5. Never put secrets (API keys, tokens, passwords) in code or commits
6. After completing a task, summarize what was done and what to check
7. If something is unclear, ask me instead of guessing

Keep it short and clear.
```

Review the file, edit anything you want.

**Chat drop:** Paste the prompt above. Open AGENTS.md in Zed, read it, adjust to your taste.

---

## Part 13: Your Own Project

Time to repeat the full cycle on your own project. In Zed's AI panel:

```
I want to build my own small project. Ask me questions about what I want
to build (one question at a time). Based on my answers:
1. Create the project folder with all files
2. Test that it works
3. Create a GitHub repo and push it

Keep it simple — this is a warm-up project.
```

Ideas if you're stuck: a to-do list, a password generator, a unit converter, a quote-of-the-day page.

**Chat drop:** Paste the prompt. Answer AI's questions. Push to GitHub when AI suggests it.

---

## Part 14: Create Your NEAR Testnet Account

Now the NEAR-specific part. NEAR is the blockchain we'll build on. To develop without spending real money, we use **testnet** — a free, separate copy of the NEAR network where tokens are worthless and mistakes cost nothing.

**Two facts to understand right now:**

| Term | Meaning |
|------|---------|
| **Account** | Your address on NEAR. Human-readable: `alice.testnet` (test) or `alice.near` (real). No long crypto addresses. |
| **Seed phrase** | 12 words that are the ONLY way to recover your account. Write them on paper. Anyone with them controls your account. |

**Create the account:**

1. Go to [wallet.near.org](https://wallet.near.org) and choose any wallet from the curated list (e.g. MyNearWallet)
2. Find **testnet** mode (the wallet should let you switch network to testnet — look for a network switcher; on MyNearWallet open `testnet.mynearwallet.com`)
3. Create a new account with a name you like: `yourname.testnet`
4. **Write down the seed phrase on paper. Never type it into a chat, never send it to anyone.**
5. Done — you own `yourname.testnet`

**Get free testnet NEAR (optional, 1 minute):**

1. Open the [NEAR docs faucet](https://docs.near.org/getting-started/faucet)
2. Enter your account ID (`yourname.testnet`)
3. Click **Request Tokens** — a small amount of testnet NEAR arrives

> If the built-in faucet is out of tokens, the official docs list alternatives: the external faucet at [near-faucet.io](https://near-faucet.io) and testnet Ref Finance at [testnet.ref.finance](https://testnet.ref.finance). We'll use these more in Lesson 5.

**Chat drop:**
- `Wallet list: https://wallet.near.org` → pick a wallet → switch to testnet → create `yourname.testnet`
- WRITE THE SEED PHRASE ON PAPER. Do not photograph it, do not type it in chat.
- Free testnet NEAR: https://docs.near.org/getting-started/faucet → enter your account → Request Tokens

---

## Part 15: Get a NEAR AI Cloud API Key

One more key, and it's a big one for this course. **NEAR AI Cloud** (cloud.near.ai) is NEAR's private LLM API — AI models running inside sealed, verifiable hardware. In Lesson 4 we'll build a bot whose brain is this API. Today we just create the key.

1. Go to [cloud.near.ai](https://cloud.near.ai)
2. Sign in (Google or email)
3. Top up a small amount of credits (~$2 — enough for all the experiments in this course)
4. Find the **API Keys** section and create a new key
5. Copy and save it (the key is typically passed to the API as `NEAR_AI_KEY`)

**Why this matters:** this key lets your code talk to AI models that run inside **TEEs** (hardware enclaves). Even the server operator can't see your prompts. Every answer comes with a cryptographic **attestation** — proof of what ran and where. We'll verify this with code in Lesson 4.

**Chat drop:**
- `NEAR AI Cloud: https://cloud.near.ai` → sign in → add ~$2 credits → API Keys → create key
- SAVE THE KEY. This one is for Lesson 4.

---

## Homework

1. Make sure `gh auth status` works and your two projects are on GitHub
2. Ask AI to improve your own project from Part 13 (one new feature)
3. Check your testnet account balance on the [explorer](https://testnet.nearblocks.io) — search your account ID
4. Re-read your AGENTS.md — would you add anything after today?
5. Share your testnet account name in the group chat

---

## Troubleshooting

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

### Homebrew Won't Install (macOS)

```
Homebrew install failed. Here's the error: [paste error]
Diagnose and guide me through fixing it.
```

### Can't Push to GitHub

```
I can't push to GitHub. The error is: [paste error]
Check gh auth status, fix authentication if needed, then push.
```

### Accidentally Pushed Secrets to GitHub

If an API key ever lands on GitHub — revoke it immediately and tell AI:

```
I accidentally committed a secret to GitHub.
1. Tell me how to revoke the key
2. Remove the secret from git history
3. Make sure .gitignore and .env are set up so it never happens again
```

### Wallet Won't Create a Testnet Account

```
The NEAR wallet shows only mainnet. How do I switch to testnet
in [your wallet name]? Walk me through creating a .testnet account.
```

---

## Related Materials

- [[near-offline-overview]] — Full course overview
- [[near-offline-lesson-02]] — Next lesson: NEAR ecosystem research & architecture
- [[off-line-lesson-01]] — Original course Lesson 1 (same setup, general track)
- [[near-lesson-01-ai-foundations]] — NEAR course foundations (online variant)

## Result

After this lesson, each student has:
- Zed installed with DeepSeek connected
- Git and GitHub CLI working (`gh auth status`)
- Homebrew (macOS)
- First project — calculator — created by AI and pushed to GitHub
- A second project of their own on GitHub
- Context optimization skill installed
- AGENTS.md with rules for AI
- A NEAR testnet account (`yourname.testnet`) with seed phrase on paper
- A NEAR AI Cloud API key
- Understanding of tokens, context, and why secrets never go in code
