---
title: "NEAR Lesson 3: Wallet & Intents"
type: lesson
difficulty: beginner
tags: [near, wallet, intents, cross-chain, near.com, testnet]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 3
---

# NEAR Lesson 3: Wallet & Intents

**Duration:** 1.5 hours
**Format:** hands-on + short concept talk

## Lesson Goal

By the end of this lesson you will have **a funded NEAR wallet**, a **testnet account** for free experiments, and you'll have completed **one cross-chain swap via Intents** — plus you can explain Intents in one sentence.

## Prerequisites

1. ✅ Lesson 1 done (Zed + DeepSeek)
2. ✅ A browser
3. ✅ A few dollars of a token to deposit (or just use testnet for free)

---

## Part 1: What NEAR Is — in 5 Minutes

**Why you need this before touching money:** NEAR is a blockchain, but it's designed differently from Bitcoin/Ethereum. Two things matter for you:

1. **Human-readable accounts.** Your address is a name like `alice.near`, not `0x7f3a…`. This makes it usable by normal humans.
2. **Chain abstraction.** NEAR's goal is to make *other* chains usable from one place — you'll see this concretely with Intents (Part 5).

Use Zed's AI panel to get the fundamentals in plain language:

```
Explain NEAR blockchain basics in simple language for a complete beginner.
Use everyday analogies. Cover:
1. What is a blockchain, in one paragraph
2. NEAR accounts — why they're human-readable (alice.near) and how
   that differs from Bitcoin/Ethereum addresses
3. Testnet vs mainnet — why we develop on testnet
4. Gas — what it is, who pays it, why it's cheap on NEAR
5. Public key vs private key (seed phrase) — which one you can share
```

**The one rule to memorize now:** a **seed phrase** (12 words) is the only way to recover your account. Write it on paper. Anyone with it controls your account. Never type it into a chat.

---

## Part 2: Mainnet vs Testnet

**Why:** you'll do real things on **mainnet** (real money) and practice on **testnet** (free fake money). Knowing the difference prevents expensive mistakes.

| | Mainnet | Testnet |
|---|---|---|
| Money | real, has value | fake, worthless |
| Account name | `alice.near` | `alice.testnet` |
| Cost to make mistakes | real loss | nothing |
| Use for | real deposits, real swaps | learning, testing, experimenting |

---

## Part 3: Create a Mainnet Wallet and Deposit

1. Go to [near.com](https://near.com)
2. Create an account (pick a human-readable name, e.g. `yourname.near`)
3. **Write the seed phrase on paper** — do not photograph it, do not type it anywhere
4. Deposit a small amount of a token (any amount, just to have something to move)

> **Why deposit:** Intents (Part 5) move value between chains — you need a little balance to try it.

**Verify:** your balance shows in the wallet. Note your account name — you'll reuse it.

---

## Part 4: Create a Testnet Account (free practice)

**Why:** the rest of the course experiments on testnet, where mistakes cost nothing.

Ask Zed's AI panel:

```
How do I create a NEAR testnet account (yourname.testnet)?
Point me to the current official wallet and the exact steps to switch
to testnet mode. Also tell me how to get free testnet NEAR from a faucet.
```

Typically: use a wallet's testnet mode (e.g. `testnet.mynearwallet.com`), create `yourname.testnet`, then get free tokens from the [NEAR faucet](https://docs.near.org/getting-started/faucet).

**Verify:** your testnet account has a small (non-zero) balance.

---

## Part 5: What Are Intents — the Big Idea

**Why this is the heart of the course:** Intents are how NEAR makes *other* chains usable from one place.

**The problem Intents solve.** Normally, moving value between chains means bridging and wrapping tokens — slow, manual, error-prone.

**What Intents do instead:** you express **what you want** ("swap USDC for NEAR"), and **solvers** (automated actors) compete to fulfill it. No manual bridging, no wrapping.

| Normal swap | Intents |
|---|---|
| you bridge, wrap, then swap | you just say what you want |
| you pick the route | solvers compete to settle it |
| you hold wrapped tokens | the solver settles on the destination chain |

**Cross-chain by design** — assets from many chains settle through Intents.

---

## Part 6: Do a Swap via Intents

1. Open the NEAR Intents app (linked from [near.com](https://near.com), or [near-intents.org](https://near-intents.org))
2. Connect your wallet
3. Do a **small** cross-chain swap (e.g. swap a little USDC for NEAR)
4. Watch it settle — this usually takes under a minute

**Verify:** the swapped asset appears in your wallet. Look up the transaction on the explorer ([nearblocks.io](https://nearblocks.io)) by searching your account name.

> **Troubleshooting note:** Intents are solver-matched, so occasionally a swap takes a minute or two. If it feels slow, wait and check the explorer before retrying.

---

## Homework

1. Confirm your mainnet wallet has a small balance and your testnet account has faucet tokens
2. Complete one Intents swap and paste the explorer link into the group chat
3. Write 3 sentences: what's the difference between a normal swap and an Intent?
4. Ask Zed's AI: "What is chain abstraction? Give 2 real examples." — write the best one in the chat

---

## Troubleshooting

### Swap slow or stuck

```
My NEAR Intents swap seems stuck. Here's my account: [account].
How do I check its status on the explorer, and how long should I wait?
```

### Can't find testnet mode in my wallet

```
The NEAR wallet shows only mainnet. How do I switch to testnet in
[your wallet name]? Walk me through creating a .testnet account.
```

### Faucet is empty

Try the alternative faucets listed in the official docs ([near-faucet.io](https://near-faucet.io)), or swap tokens at [testnet.ref.finance](https://testnet.ref.finance). You only need a tiny amount.

### I lost my seed phrase

If you still have access to the account, export it from the wallet settings and write it down **now**. If you don't — for a mainnet account with real funds, contact wallet support immediately; for a testnet account, just create a new one.

---

## Related Materials

- [[near-lesson-02-deploy-agent-cloud]] — Previous lesson: your agent
- [[near-lesson-04-confidential-intents]] — Next lesson: private money
- [[link-near]] — NEAR ecosystem links

## Result

After this lesson you can:
- Explain what NEAR is and why accounts are human-readable
- Tell mainnet from testnet and know when to use each
- Create and fund a NEAR wallet (mainnet + testnet)
- Explain Intents in one sentence and do a cross-chain swap
