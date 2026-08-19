# How to get IronClaw in your Telegram in less than 30 seconds

It will be really fast — all you need is to prepare a few small things. The whole flow: create a Telegram bot → deploy IronClaw on NEAR AI Cloud → connect them.

---

## 1. Create a Telegram bot for your IronClaw

1. Go to [@BotFather](https://t.me/BotFather).

![BotFather chat](assets/79637ae60b04ec4a68a47dff406d2655_MD5.jpeg)

2. Open the app and create a bot.

![Create a bot](assets/32d0dccc2c55f4298c37e35a9e5b7732_MD5.jpeg)

3. Add information about your bot:
   - Create a bot **Name** (it can be anything).
   - Create a bot **Username** (it must end with `bot`).
   - Click **Create Bot**.

![Bot name, username, create](assets/bedaf4c23a80ca975be9308c8a06dc80_MD5.jpeg)

4. Copy your Telegram bot **API token** — never share it with anyone. You can always get it again (or revoke it) in BotFather.

![Bot API token](assets/abcdb9d05e7cf1a218bdbeb68dad11d8_MD5.jpeg)

---

## 2. Deploy your IronClaw

1. Go to https://agent.near.ai and sign in the way you prefer.

![agent.near.ai](assets/9e14d47a07ce0a08fb6b6cbcb584b000_MD5.jpg)

2. Choose **Starter** and complete the transaction. You will need to attach a card, but the Starter plan is free.

![Starter plan](assets/1e826c1e818a91d2fe9552fa0c1436d2_MD5.jpg)

3. After the card is attached, click **Generate and Download Access Key**.

![Generate access key](assets/bd019caef2f71ee174d4a7793dd78a88_MD5.jpg)

4. You will get your **Public SSH key** — you can share it. After downloading your **Private SSH key** — never share it with anyone, keep it secret. Accept that you downloaded the private keys, then click **Activate Agent**.

![SSH keys](assets/92a12b2177d6396478e2e29be8060ab5_MD5.jpg)

Your IronClaw agent will be ready in less than 30 seconds.

---

## 3. Connect your IronClaw to Telegram

1. Click **Open IronClaw**.

![Open IronClaw](assets/43cf26dba887a3cc4507e4080e475d12_MD5.jpg)

2. In the left sidebar go to **Admin → Configuration**.

![Admin → Configuration](assets/03801f6033ba6e8f984bf3e9e78dfad6_MD5.jpg)

3. In **Telegram deployment configuration**, fill in the required fields.

![Telegram deployment configuration](assets/2a9165b3be0fb64587d8696344660fd9_MD5.jpg)

### Bot Token and Bot Username

You can get both in @BotFather (we created them in the first step). Click **Copy** and paste the token into the **Bot token** field. Add the **Bot username without the leading `@`**.

![Bot API token](assets/abcdb9d05e7cf1a218bdbeb68dad11d8_MD5.jpeg)

### Webhook secret token

You need a random string of digits and letters — 32 characters long. Go to https://generate-random.org/webhook-secrets and choose:

- Count = `1`
- Length = `32`
- Algorithm = `HMAC-SHA256`
- Format = `Hexadecimal`
- All extra options = off

Click **EXECUTE GENERATION**, copy the 32-character string and paste it into the **Webhook secret token** field.

![Webhook secret generator](assets/e2c3e668bf58339da3acb558868a7662_MD5.jpg)

### Public webhook URL

Check the URL of your agent. In the example it's `https://vast-fox-komoj.agents.near.ai/` — you will have a different one. Add `webhooks/extensions/telegram/updates` after your agent's URL:

```
https://<your-agent>.agents.near.ai/webhooks/extensions/telegram/updates
```

![Telegram deployment configuration](assets/2a9165b3be0fb64587d8696344660fd9_MD5.jpg)

After all 4 fields are filled, click **Save configuration**.

---

## 4. Install the Telegram extension and pair

1. In the left sidebar go to **Extensions**, search for **Telegram** and click **Install**.

![Extensions → Telegram](assets/2d9cf5ed03bf0ca10f3d284ed76d9e89_MD5.jpg)

2. A new window opens. Copy the **code** (8 digits and letters). Then either scan the QR code with your phone, or click **Open in Telegram**.

![Pairing code](assets/8ba7844a412ae9480e17d778879e8911_MD5.jpg)

3. You will be redirected to your Telegram bot. Click **START**, then send the copied code to the bot.

![START + send code](assets/a7bfa59d850e5feaef794cd3a0ecac18_MD5.jpg)

Done — your IronClaw is now in your Telegram.

---

## Troubleshooting

If your IronClaw doesn't connect after all this, go back to **Telegram deployment configuration**, paste the **Bot Token** and **Webhook Secret Token** again, click **Save Configuration**, and the bot will be paired.

---

## See also

- [ironclaw-telegram-cheatsheet.md](ironclaw-telegram-cheatsheet.md) — quick reference (NEAR AI Cloud vs self-hosted, save-failure pitfalls)
