# 🤖 Telegram AI Chatbot — n8n Workflow

An automated Telegram bot powered by **Groq's LLaMA 3.3 70B** model, built with n8n. Send any message to the bot and get instant AI-generated replies — with memory of past messages!

---

## 🔁 Workflow Overview

```
Telegram Trigger → AI Agent → Send a text message
                      ↑
              Groq Chat Model (LLaMA 3.3 70B)
              Simple Memory (last 20 messages)
```

---

## ✨ Features

- 💬 **Responds to Telegram messages** automatically
- 🧠 **Remembers context** — retains last 20 messages per session
- ⚡ **Powered by Groq + LLaMA 3.3 70B** — fast and free
- 🔄 **Always-on** — no manual execution needed once activated

---

## 🧩 Nodes Used

| Node | Purpose |
|------|---------|
| `Telegram Trigger` | Listens for incoming Telegram messages |
| `AI Agent` | Processes user message and generates a reply |
| `Groq Chat Model` | LLaMA 3.3 70B via Groq API as the LLM |
| `Simple Memory` | Stores last 20 messages for conversation context |
| `Send a text message` | Sends AI response back to the Telegram chat |

---

## 🚀 How to Use

### 1. Import the Workflow
- In n8n, go to **Workflows → Import**
- Upload `telegram-ai-bot-workflow.json`

### 2. Set Up Credentials
You'll need to configure:
- **Telegram API** — Create a bot via [@BotFather](https://t.me/BotFather) and get the token
- **Groq API** — Get a free API key at [console.groq.com](https://console.groq.com)

### 3. Activate
- Click the **Active toggle** (top-right) to turn the workflow ON
- Your bot is now live! 🎉

---

## ⚙️ Configuration

### AI System Prompt
The bot is configured to be a helpful and friendly assistant. You can customize the prompt in the **AI Agent** node:

```
You are a helpful and friendly AI assistant on Telegram.
Answer the user's questions clearly and concisely.
If you don't know something, say so instead of making up information.
Keep responses conversational and easy to understand.
```

### Memory
The `Simple Memory` node uses a fixed `sessionKey: "1234"` — for multi-user support, change this to a dynamic value like `{{ $json.message.chat.id }}`.

---

## 📋 Requirements

- n8n (cloud or self-hosted)
- Telegram Bot Token
- Groq API Key (free tier available)

---

## 📄 License

MIT — free to use and modify.
