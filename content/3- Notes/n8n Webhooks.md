---
tags:
  - AI
  - Automation
---
In order to achieve a Telegram-triggered workflow, you need to use **Webhooks**. 

n8n uses 2 Webhook endpoints: **webhook-test/** and **webhook/**. You should enable them in [[Cloudflare Setup]].

Then, you adjust Telegram bot's webhook url with the command:
```
https://api.telegram.org/bot<BOT-ID>/setWebhook?url=https://your-url.com/webhook/your-url
```