---
title: "NEAR Lesson 2: Wallet, Intents & Privacy"
type: lesson
difficulty: beginner
tags: [near, wallet, intents, confidential-intents, zcash, privacy]
created: 2026-08-17
updated: 2026-08-17
lesson_number: 2
---

# NEAR Lesson 2: Wallet, Intents & Privacy

**Duration:** 1.5 hours · **Format:** hands-on + short concept talk

## Lesson Goal

Understand the NEAR wallet, deposit a token, and grasp **Intents** (cross-chain swaps) and **confidential Intents** (private money, the NEAR × ZCash story).

## Prerequisites

- NEAR Lesson 1 done (or just a browser + a NEAR wallet)

---

## Part 1 — What NEAR is (5 min)

NEAR is a fast, cheap layer-1 blockchain built for mainstream usability — human-readable account names (e.g. `alice.near`), and a strong focus on **chain abstraction**: NEAR makes other chains usable from one place.

## Part 2 — Create a wallet & deposit

1. Go to **near.com** (or a NEAR wallet of your choice).
2. Create an account (pick a human-readable name).
3. Deposit a token of your choice.

## Part 3 — NEAR Intents (cross-chain swaps)

**Intents** = you express *what you want* ("swap USDC for NEAR"), and solvers compete to fulfill it — no manual bridging, no wrapping tokens.

- Cross-chain by design: assets from many chains settle through Intents.
- You don't hold wrapped tokens; the solver settles on the destination chain.

## Part 4 — Confidential Intents (private money)

**Confidential Intents** add privacy: your amounts and identity aren't revealed during the swap.

- "Confidential Intents create private money."
- **NEAR × ZCash**: NEAR Intents unlocked ZCash — they are now closely tied (the ZCash token address viewed on CoinGecko is a NEAR smart-contract address).

## Part 5 — Try it

1. Visit the NEAR Intents app (linked from near.com / near-intents.org).
2. Do a small cross-chain swap via Intents.
3. Explore shielding (confidential Intents) — deposit into a private balance.

---

## Homework

1. Create a NEAR wallet and deposit a small amount.
2. Complete one Intents swap.
3. Write 3 sentences: what's the difference between a normal swap and a confidential Intent?

## Troubleshooting

- **Swap slow** → Intents are solver-matched; give it a minute and check the explorer.
- **Can't find confidential Intents** → it's rolling out; use the links on near.com / the official NEAR blog for the current access point.

## Result

A funded NEAR wallet + you can explain Intents and confidential Intents in one sentence.

## Related

- [[near-lesson-01-ironclaw-agent]] — previous lesson
- [[near-lesson-03-mcp-skills]] — next: agents + MCP + skills
