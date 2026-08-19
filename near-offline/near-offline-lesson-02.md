---
title: "NEAR Off-line Lesson 2: Product Owner — NEAR Ecosystem Research & Architecture"
type: lesson
difficulty: beginner
tags: [near, offline, architecture, specification, plan, research, product-owner, ai-agents, team, agent-near-ai, cloud-near-ai, nearbuilders]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 2
---

# NEAR Off-line Lesson 2: Product Owner — NEAR Ecosystem Research & Architecture

**Format:** Instructor-led classroom — screen sharing + hands-on practice

## How This Lesson Works

Same flow as Lesson 1: instructor explains → demonstrates on screen → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

---

## Prerequisites

From Lesson 1, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ Git and GitHub CLI working (`gh auth status`)
3. ✅ Context optimization skill installed
4. ✅ Global AGENTS.md in home folder
5. ✅ NEAR testnet account (`yourname.testnet`)
6. ✅ NEAR AI Cloud API key saved somewhere safe

---

## Part 1: You Are the Product Owner

In this lesson, your role changes. You are no longer just telling AI "make me a calculator." You are now a **Product Owner** — the person who decides WHAT to build.

**Your job:**
1. Explore the NEAR ecosystem with AI as your guide
2. Understand NEAR basics: accounts, testnet, gas
3. Describe your agent idea to AI
4. AI asks you clarifying questions
5. Based on your answers, AI creates architecture, specification, plan, and team structure
6. You review and approve
7. AI executes Phase 1 — the skeleton of your project

**You do NOT write code. You do NOT create documents. AI does everything.**

The product you design today will be built for real in Lessons 3-5: in Lesson 3 you deploy a ready-made secure agent (IronClaw), in Lesson 4 you build your own bot on NEAR AI Cloud, and in Lesson 5 you connect it to the blockchain. Today we lay the foundation.

---

## Part 2: Research the NEAR Ecosystem with AI

Before designing anything, you need to know the landscape. The NEAR ecosystem for AI builders has three pillars:

| Site | What It Is |
|------|-----------|
| **[agent.near.ai](https://agent.near.ai)** | NEAR AI Hub — deploy your own AI agent (IronClaw) in one click, get a web UI + URL |
| **[cloud.near.ai](https://cloud.near.ai)** | NEAR AI Cloud — private LLM API. Models run in sealed hardware (TEE), answers are cryptographically attested |
| **[nearbuilders.org](https://nearbuilders.org)** | NEAR Builders community — find collaborators, discover projects, ship in public |

In Zed's AI panel, paste:

```
Research the NEAR ecosystem for AI builders. I'm a beginner — explain
everything in simple language.

Look at these sources:
1. https://agent.near.ai — what is it, what can you deploy there, what is IronClaw
2. https://cloud.near.ai — what is NEAR AI Cloud, what makes it private/verifiable
3. https://nearbuilders.org — what is the NEAR Builders community
4. Search the web for "IronClaw nearai github" — what is IronClaw, its key
   security features, how it connects to Telegram

For each: what it is, who it's for, how much it costs for a beginner.

Then save a summary to RESEARCH.md in my project folder with:
- One section per site
- A table comparing agent.near.ai vs cloud.near.ai (what you'd use each for)
- Interesting facts I could use in my own project
```

> ⚠️ Note for the instructor: `agent.near.ai` is a JavaScript-heavy site — AI may not be able to read it directly and will use web search instead. That's fine and expected. If AI says the page is empty, tell it: "Use web search instead."

Open RESEARCH.md, read it together. This document is your map of the NEAR world.

**Chat drop:** Paste the prompt above. If AI can't open agent.near.ai — reply: `Use web search instead.` Read RESEARCH.md when done.

---

## Part 3: NEAR Basics in 15 Minutes

Ask AI to explain the fundamentals — the concepts every NEAR builder must know. In Zed's AI panel:

```
Explain NEAR blockchain basics in simple language for a complete beginner.
Use everyday analogies. Save to NEAR_BASICS.md in my project folder.

Cover:
1. What is a blockchain, in one paragraph
2. NEAR accounts — why they're human-readable (alice.near, alice.testnet)
   and how that differs from Bitcoin/Ethereum addresses
3. Testnet vs mainnet — why we develop on testnet (free, no real money)
4. Gas — what it is, who pays it, why it's cheap on NEAR
5. Public key vs private key (seed phrase) — which one you can share
6. Smart contracts — what they are, in one paragraph
7. What makes NEAR special for AI: TEEs, Intents, chain abstraction (1-2 lines each)

Keep the whole file under 300 lines. Tables are welcome.
```

**Chat drop:** Paste the prompt above. Read NEAR_BASICS.md. Quiz your neighbor: "Can you share your public key? Can you share your seed phrase?"

---

## Part 4: Describe Your Project to AI

Now the Product Owner moment. You will design **a Telegram assistant on NEAR** — but the details are yours.

Open your projects folder in Zed. In Zed's AI panel:

```
I want to build a project. Ask me questions to understand what I need.

Ask about:
- What the assistant does and who it's for
- Main features (what commands or help it offers)
- Which NEAR services it should use (agent.near.ai IronClaw, NEAR AI Cloud,
  or both)
- Any constraints (budget, time, platforms)

Ask one question at a time. Wait for my answer before asking the next.
After I answer all questions, you will create the project documents.
```

AI will start asking questions. Answer honestly — the more detail you give, the better the result.

**Chat drop:** Paste the prompt above. Answer AI's questions one at a time. No wrong answers — describe your dream assistant.

---

## Part 5: AI Creates Architecture, Specification, Plan, and Team

After you've answered all the questions, tell AI:

```
Based on my answers, create the following documents:

1. ARCHITECTURE.md — project architecture:
   - Structure: what parts the project consists of (bot, AI brain, blockchain)
   - Data: what is stored and where
   - External services: Telegram, NEAR AI Cloud, agent.near.ai, NEAR testnet

2. SPECIFICATION.md — detailed specification:
   - For each feature: what it does, example user messages, expected replies
   - Commands list (e.g. /help, /balance)
   - Error handling: what happens when something fails
   - Edge cases

3. PLAN.md — implementation plan:
   - Phase 1: project skeleton (this lesson)
   - Phase 2: deploy agent on NEAR (Lesson 3)
   - Phase 3: own bot on NEAR AI Cloud (Lesson 4)
   - Phase 4: blockchain connection via MCP (Lesson 5)
   - Phase 5: final polish and presentation (Lesson 6)
   - Task list with expected result for each phase

4. TEAM.md — AI agent team structure:
   - Team Lead — orchestration and delegation
   - Backend Developer — bot logic, APIs
   - Blockchain Developer — NEAR testnet integration
   - QA Tester — testing, bug hunting
   - Code Reviewer — security (especially secrets handling)
   - Rules: commit after every task, update PLAN.md, never commit .env,
     ask before any blockchain transaction

Save all four files in the project root.
```

Open each file in Zed and review. If something doesn't match your vision — tell AI:

```
In [FILENAME], change [specific thing] to [what you want].
```

**Chat drop:** Paste the prompt above. Review all four files. Fix anything you don't like with the correction prompt.

---

## Part 6: Launch Your AI Team — Phase 1

Now the exciting part. You have:
- ✅ RESEARCH.md — your map of the NEAR ecosystem
- ✅ NEAR_BASICS.md — the fundamentals
- ✅ ARCHITECTURE.md, SPECIFICATION.md, PLAN.md — the blueprint
- ✅ TEAM.md — your AI team defined

**You will now appoint AI as Team Lead and execute Phase 1** — the project skeleton.

In Zed's AI panel, from your project folder:

```
Read TEAM.md, ARCHITECTURE.md, SPECIFICATION.md, and PLAN.md.

You are the Team Lead. Execute Phase 1 from PLAN.md:

1. Create the project structure (folders and files as defined in ARCHITECTURE.md)
2. Create README.md describing the project (what it does, how to run it later)
3. Create .gitignore — make sure .env is listed
4. Create .env.example — a template of all future secrets, with empty values
   and comments (NEAR AI Cloud key, Telegram bot token, etc.)
5. Create a clean git repository with an initial commit
6. Update PLAN.md — mark Phase 1 tasks as done

Keep me updated on progress.
```

Then push to GitHub:

```
Create a GitHub repository for this project and push all files.
Commit message: "Phase 1 complete: [brief description of what was built]"
Give me the repository link.
```

**Chat drop:** Paste both prompts in order. Open the GitHub link when done — your project has a home.

---

## Homework

1. Read your RESEARCH.md again and mark 3 facts you find most useful
2. Explore [nearbuilders.org](https://nearbuilders.org) — find 2 NEAR projects that interest you, write them in the group chat
3. Ask AI to plan Phase 2 in more detail (the IronClaw deployment from Lesson 3)
4. Check your testnet account still has some testnet NEAR (or request more from the [faucet](https://docs.near.org/getting-started/faucet))
5. Push any changes to GitHub

---

## Troubleshooting

### AI Can't Read agent.near.ai

```
The site agent.near.ai looks empty to you. Use web search instead:
search for what agent.near.ai is, how to deploy an agent there,
and what IronClaw is. Cite your sources.
```

### AI Doesn't Ask Enough Questions

```
You asked me questions about my project, but I feel like you missed
important details. Ask 5 more deep questions about:
- Who exactly will use the assistant and when
- What happens when something goes wrong
- Future features and growth
```

### Architecture Doesn't Match My Vision

```
In ARCHITECTURE.md, the following doesn't match what I want:
[describe what's wrong].
Rewrite that section. Keep the rest.
```

### Team Lead Doesn't Delegate

```
TEAM.md is created but you're doing everything yourself
instead of delegating. Re-read TEAM.md and delegate each task
to the appropriate specialist. Report what each role did.
```

### I Don't Understand a NEAR Concept

```
Explain [gas / testnet / attestation / whatever] again, simpler.
Use an analogy from everyday life. Then ask me 2 questions to check
I understood.
```

---

## Related Materials

- [[near-offline-lesson-01]] — Previous lesson: setup and tools
- [[near-offline-lesson-03]] — Next lesson: deploy IronClaw on agent.near.ai + Telegram
- [[near-overview]] — The existing NEAR course (online variant)
- [[off-line-lesson-02]] — Original course Lesson 2 (same Product Owner method)
- [[near-lesson-02-deploy-agent-cloud]] — Deploy your agent + AI cloud (reference for Lesson 3)

## Result

After this lesson, each student has:
- RESEARCH.md — a beginner-friendly map of agent.near.ai, cloud.near.ai, nearbuilders.org, and IronClaw
- NEAR_BASICS.md — understanding of accounts, testnet/mainnet, gas, keys, contracts
- ARCHITECTURE.md, SPECIFICATION.md, PLAN.md — the complete blueprint of their NEAR assistant
- TEAM.md — their AI agent team with roles and rules
- Phase 1 executed: project skeleton, README, .gitignore, .env.example
- Everything pushed to GitHub
- Understanding of the Product Owner role and the NEAR ecosystem
