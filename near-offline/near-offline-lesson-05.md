---
title: "NEAR Off-line Lesson 5: NEAR MCP, Skills & the Blockchain"
type: lesson
difficulty: intermediate
tags: [near, offline, mcp, near-mcp, blockchain, testnet, faucet, skills, skill-md, ironclaw]
created: 2026-08-19
updated: 2026-08-19
lesson_number: 5
---

# NEAR Off-line Lesson 5: NEAR MCP, Skills & the Blockchain

**Format:** Instructor-led classroom — screen sharing + hands-on practice

## How This Lesson Works

Same flow: instructor explains → demonstrates → drops prompt in chat → students copy-paste and repeat → wait for all → questions → next section.

---

## Prerequisites

From Lessons 1-4, every student must have:
1. ✅ Zed with DeepSeek connected
2. ✅ NEAR testnet account (`yourname.testnet`) — from Lesson 1
3. ✅ Own Telegram bot from Lesson 4 (running locally is fine)
4. ✅ IronClaw agent from Lesson 3
5. ✅ Project on GitHub

---

## Part 1: What Is MCP — in Plain Language

**MCP** stands for **Model Context Protocol**. It's a standard "plug" that connects AI to outside tools — the same way USB connects devices to your computer.

| Without MCP | With MCP |
|-------------|----------|
| AI can only chat — it knows things but can't DO anything | AI can call tools: read files, check balances, send transactions |
| You copy-paste data into the chat | AI fetches live data itself |
| You do the action, AI describes it | AI does the action (with your permission) |

**NEAR MCP** ([github.com/nearai/near-mcp](https://github.com/nearai/near-mcp), package `@nearai/near-mcp`) is the official MCP server for the NEAR blockchain. Once it's connected to Zed, your AI can:

- Create NEAR accounts and access keys
- Check account balances
- Sign and send transactions
- Inspect and execute smart contracts
- Import accounts from private keys (keys stay in a local keystore)

**What this means for you:** from now on, you control the blockchain with plain-language prompts. "Check my balance" → AI does it. "Send 0.5 testnet NEAR to my classmate" → AI does it. No memorizing commands.

---

## Part 2: Install NEAR MCP into Zed

The MCP server is a Node.js program. First, check Node is installed — in Zed's AI panel:

```
Check if Node.js is installed on my computer (node --version, npm --version).
If not — install it (use Homebrew on macOS: brew install node).
Then install the NEAR MCP server:
npm install -g @nearai/near-mcp@latest
Verify: the command "npx @nearai/near-mcp@latest --help" should print usage.
```

Now connect it to Zed. Zed has an MCP "context servers" setting. Ask AI:

```
Add the NEAR MCP server to Zed's MCP context servers
(~/.zed/settings.json, key "context_servers").

The server runs with: npx @nearai/near-mcp@latest run
Configure it and tell me how to verify it's connected in Zed.
Explain what you changed.
```

After restarting Zed (or the MCP connection), the NEAR tools should appear as available tools for the AI.

**Chat drop:**
- Paste the Node install prompt → wait for verification
- Paste the Zed MCP config prompt → restart Zed → ask AI: `List the tools you now have from NEAR MCP.`

---

## Part 3: Manage Accounts via Prompts — Create & Import

Two options — you already have `yourname.testnet` from Lesson 1. We'll do both:

**A. Import your existing account.** Export the private key from your wallet (wallet → account → security/export private key), then in Zed:

```
Using NEAR MCP, import my testnet account:
account: yourname.testnet
private key: PASTE_YOUR_PRIVATE_KEY

The MCP tool is import_account. After importing, verify it worked
by listing the accounts NEAR MCP knows about.
```

**B. Create a brand-new account for experiments.** In Zed:

```
Using NEAR MCP, create a new testnet account for me.
Suggest an account name based on my project name + "-bot" suffix.
After creation, show me the account ID and confirm it's recorded
in the MCP keystore. Warn me if the key is stored unencrypted.
```

> **Security note:** MCP keeps keys in a local keystore on your computer. Anyone with access to your laptop could use them. That's acceptable for worthless testnet tokens — and a good reason to never import a mainnet account on a shared machine.

**Chat drop:**
- (Optional) Export private key from your wallet → paste the import prompt
- Everyone: paste the create-account prompt

---

## Part 4: Get Testnet NEAR & Check Your Balance

New accounts start with 0 balance. Get free testnet NEAR from the official faucet:

1. Open the [NEAR docs faucet](https://docs.near.org/getting-started/faucet)
2. Enter your account ID (`yourname.testnet`)
3. Click **Request Tokens**

> Fallbacks if the faucet is empty: the external faucet at [near-faucet.io](https://near-faucet.io), or swap tokens at [testnet.ref.finance](https://testnet.ref.finance). (Fun fact: the NEAR CLI can even do this in one command: `near create-account <name>.testnet --useFaucet`.)

Now let AI check the balance — in Zed:

```
Using NEAR MCP, check the balance of:
1. yourname.testnet (my account)
2. The new account you created for me

Show both balances in NEAR.
```

**Chat drop:**
- Faucet: https://docs.near.org/getting-started/faucet → your account → Request Tokens
- Paste the balance-check prompt → read both balances aloud to your neighbor

---

## Part 5: Send Your First Transaction

The big moment — money moving on a blockchain, commanded by a sentence.

Exchange account names with a neighbor. In Zed:

```
Using NEAR MCP, send 0.1 testnet NEAR from my account
[YOUR_ACCOUNT] to my classmate's account [NEIGHBOR_ACCOUNT].

Before sending, show me exactly what you're about to do and ask
for my confirmation.
After sending, show the transaction hash and check both balances.
```

**You have now sent a blockchain transaction via natural language.** The transaction hash can be looked up on the [testnet explorer](https://testnet.nearblocks.io) — search your account to see the transfer in history.

**Chat drop:** Paste the send prompt (with your neighbor's account) → confirm → look up your account on https://testnet.nearblocks.io → show the transaction to the group.

---

## Part 6: Call a Smart Contract

Smart contracts are programs living on the blockchain. Reading from them is free — let's try.

In Zed:

```
Using NEAR MCP, call a smart contract on NEAR testnet.

1. Call the view method "ft_metadata" on the contract "wrap.testnet"
   (wrapped NEAR token on testnet). Show me what it returns.
2. Explain in simple language what that data means.
3. Then call a view method on any other well-known testnet contract
   of your choice and show the result.
```

No money spent — reading is free. You just queried a live blockchain program.

**Chat drop:** Paste the contract-call prompt → explain to your neighbor what `ft_metadata` returned.

---

## Part 7: Skills — Teach Your Agent New Abilities

**What is a skill?** A `SKILL.md` file — plain-text instructions + metadata that teaches an agent a reusable ability. You saw skills in Lesson 1 (context optimization). Now we write our own.

**IronHub** ([github.com/nearai/ironhub](https://github.com/nearai/ironhub), hub.ironclaw.com) is the library of "WASM tools and SKILL.md skills for the IronClaw agent runtime" — the skill marketplace for your Lesson 3 agent.

### Write your own SKILL.md

In your project folder, ask AI:

```
Create a SKILL.md file for my NEAR assistant. It teaches the agent
a new ability: "NEAR Expert Mode".

Content:
1. Frontmatter with name: near-expert, description: one sentence
2. When to use: when the user asks about NEAR (blockchain, accounts,
   testnet, gas, IronClaw, NEAR AI Cloud)
3. How to answer:
   - Always explain in simple language, no jargon without explanation
   - Mention which network the user is on (testnet = free, mainnet = real money)
   - Never ask for seed phrases or private keys
   - If asked to send real NEAR on mainnet — refuse and explain why
     (safety first)
4. Include 3 example Q&A pairs

Save it in my project as SKILL.md.
```

### Add it to your IronClaw agent

IronClaw supports skills and WASM tools. The exact place depends on the current admin UI — let AI guide you:

```
My IronClaw agent runs at https://<my-agent>.agents.near.ai.
I have a SKILL.md file in my project.

Guide me through adding this skill to IronClaw:
1. Where in the admin UI do skills/tools live?
2. Do I paste the SKILL.md content, or install from IronHub?
3. If the UI has an IronHub section — search it for useful NEAR skills
   and suggest one to install.

Also: IronClaw can connect MCP servers. Explain how I would connect
the NEAR MCP server (@nearai/near-mcp) to IronClaw so my agent
can also manage NEAR accounts. Point me to the right admin section.
```

**Chat drop:** Paste the SKILL.md prompt → review the file → paste the IronClaw guide prompt → follow AI's steps.

---

## Homework

1. Ask AI (via NEAR MCP) to show the last 5 transactions of your account
2. Write a second SKILL.md for your agent: "Crypto Safety Coach" (how to spot scams, never share keys, verify URLs)
3. Send 0.2 testnet NEAR back to your neighbor (square up!)
4. Commit SKILL.md files and push to GitHub
5. Think about the final project: your bot will check balances and send tokens. What commands should it have?

---

## Troubleshooting

### `npx` / `npm` Not Found

```
"npx" or "npm" is not recognized. Node.js isn't installed properly.
Install Node.js for my OS: [Windows / Mac / Linux]. On macOS use
Homebrew. Then verify: node --version && npm --version
```

### NEAR MCP Doesn't Appear in Zed

```
I configured NEAR MCP in Zed's settings but the tools don't appear.
Check ~/.zed/settings.json for errors, show me the correct
context_servers entry for a command-based MCP server, and tell me
how to restart the MCP connection in Zed.
```

### Faucet Says "Account Already Funded" / Out of Tokens

Try the other faucet ([near-faucet.io](https://near-faucet.io)), wait a bit, or swap via [testnet.ref.finance](https://testnet.ref.finance). You only need a tiny amount.

### Transaction Fails / Not Enough Balance

```
The transaction failed with: [paste error]. Diagnose it. If it's
a balance problem, tell me how much I need and check the faucet again.
```

### MCP Wants a Key I Don't Have

You can create a fresh account via MCP instead (Part 3, option B) — no key export needed. Only import the wallet account if you're comfortable exporting its private key.

### IronClaw Skills UI Looks Different

Interfaces change. Ask AI: `The IronClaw admin UI has no "Skills" section. Where do I add skills or MCP servers in the current version? Check docs.ironclaw.com.`

---

## Related Materials

- [[near-offline-lesson-04]] — Previous lesson: NEAR AI Cloud + own bot
- [[near-offline-lesson-06]] — Next lesson: final project & presentation
- [[ironclaw-telegram-cheatsheet]] — IronClaw reference (skills & MCP section)
- [[near-lesson-05-build-present]] — Online variant: extend with MCP + skills
- [[off-line-lesson-01]] — Original lesson 1 (first skill install, for comparison)

## Result

After this lesson, each student has:
- Node.js installed (if missing)
- NEAR MCP installed and connected to Zed — AI can now manage NEAR accounts
- A new testnet account created purely via prompts (+ optionally their Lesson 1 account imported)
- Free testnet NEAR from the official faucet
- Their first blockchain transaction sent by natural language, visible on the explorer
- A smart contract queried successfully (wrap.testnet)
- A hand-written SKILL.md teaching the agent "NEAR Expert Mode"
- IronClaw extended: skill added, NEAR MCP connection explored
- The full toolkit for the final project: prompts → blockchain, skills → agent
