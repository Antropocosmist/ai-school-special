---
title: "NEAR Lesson 4: Confidential Intents"
type: lesson
difficulty: beginner
tags: [near, confidential-intents, privacy, zcash, intents]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 4
---

# NEAR Lesson 4: Confidential Intents

**Duration:** 1.5 hours
**Format:** reading + concept talk + discussion

## Lesson Goal

By the end of this lesson you can **explain what confidential Intents are, why privacy matters for money, and why the NEAR × ZCash connection is significant** — grounded in the official NEAR blog post.

## Prerequisites

1. ✅ Lesson 3 done (you understand regular Intents)
2. ✅ A browser for reading

---

## Part 1: Read the Source

**Why read the source yourself:** you're about to learn a concept people often misstate. Go straight to the official post:

**https://www.near.org/blog/confidential-intents**

Read it once through, then once more slowly. If any term is unclear, paste it into Zed's AI panel:

```
Explain this term from a NEAR blog post in simple language: [term].
Use an everyday analogy.
```

---

## Part 2: Recap — What Regular Intents Do

**Why:** confidential Intents build directly on regular Intents (Lesson 3). If that's fuzzy, re-read the Lesson 3 summary first.

Regular Intents let you say **what** you want ("swap USDC for NEAR") and solvers settle it cross-chain. That's convenient — but your **amounts** and **identity** can still be observed on-chain.

---

## Part 3: What "Confidential" Adds

**The key difference:** confidential Intents add **privacy** to the swap. The *what* and the *who* of your transaction aren't revealed.

The core idea, in one line from the post:

> **"Confidential Intents create private money."**

Think of it as:
- **Regular Intent** = a bank transfer (the bank can see who paid whom and how much)
- **Confidential Intent** = cash in an envelope (the value moves, but the details stay private)

**Why it matters:** money is not just about moving value — it's about not exposing your whole financial life to anyone who can read a blockchain.

---

## Part 4: NEAR × ZCash

**Why this is a big deal:** ZCash is a privacy-focused cryptocurrency. NEAR Intents unlocked it — the two are now closely tied.

A concrete, verifiable example: the **ZCash token address** viewed on CoinGecko is a **NEAR smart-contract address**. In other words, a privacy currency is now integrated *through* NEAR — a textbook case of **chain abstraction**.

Ask Zed's AI panel to ground this for you:

```
What is ZCash and how does it relate to NEAR Intents and confidential
Intents? Use the NEAR blog post "confidential-intents" as a source.
Explain the privacy mechanics in simple terms.
```

---

## Part 5: Group Discussion

Discuss (in the group chat or with a neighbor):

1. Why does privacy matter for real-world money?
2. What trade-offs does privacy bring? (think: regulation, usability, trust)
3. If you could make **one** everyday payment private, what would it be — and why?

Write your answers down — you'll reference them in the final project.

---

## Homework

1. Summarize the blog post in **5 sentences** (in your own words)
2. Write down **one concrete use case** where confidential Intents would matter to a real person
3. Ask Zed's AI: "What's the difference between confidentiality and anonymity?" — and write the answer in 2 lines
4. Share your 5-sentence summary in the group chat

---

## Troubleshooting

### The blog post is unclear

```
Summarize this NEAR blog post in simple language for a beginner:
https://www.near.org/blog/confidential-intents
Focus on: what confidential Intents are, and what ZCash has to do with it.
```

### I can't tell confidentiality from anonymity

```
Explain the difference between confidentiality and anonymity with
2 everyday examples. Keep it under 100 words.
```

---

## Related Materials

- [[near-lesson-03-wallet-intents]] — Previous lesson: wallet & Intents
- [[near-lesson-05-build-present]] — Next lesson: build something real
- https://www.near.org/blog/confidential-intents — the source

## Result

After this lesson you can:
- Explain regular Intents vs confidential Intents in plain language
- Say why "confidential Intents create private money"
- Explain the NEAR × ZCash connection and what chain abstraction means
- Give a real-world use case for private money
