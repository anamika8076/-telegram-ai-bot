# 🤖 Telegram AI Chatbot — n8n Workflow

> A production-ready Telegram bot powered by **Groq's LLaMA 3.3 70B**, built with n8n. Supports per-user memory, error handling, and zero manual intervention.

---

## 📸 Workflow Preview

![Workflow Preview](workflow.png)

> 🎬 *Demo GIF coming soon*

---

## ✨ Features

| Feature | Details |
|--------|---------|
| 💬 Auto-reply | Responds to every Telegram message instantly |
| 🧠 Per-user Memory | Each user gets their own conversation context (last 20 messages) |
| ⚡ Groq LLaMA 3.3 70B | Fast, free, and powerful LLM |
| 🛡️ Error Handling | Sends a friendly error message if something goes wrong |
| 🔄 Always-on | Activate once, runs 24/7 — no manual execution needed |

---

## 🔁 Workflow Architecture

```
Telegram Trigger
      │
      ▼
  AI Agent ──────────────── [Error] ──→ Send Error Message
      │        ↑       ↑
      │   Groq Model  Simple Memory
      │             (per user chat.id)
      ▼
Send a text message
```

---

## 🧩 Nodes

| Node | Type | Purpose |
|------|------|---------|
| `Telegram Trigger` | Trigger | Listens for incoming messages |
| `AI Agent` | LangChain Agent | Orchestrates LLM + memory |
| `Groq Chat Model` | LLM | LLaMA 3.3 70B via Groq API |
| `Simple Memory` | Memory | Per-user context window (20 msgs) |
| `Send a text message` | Action | Sends AI reply to user |
| `Send Error Message` | Error Handler | Notifies user on failure |

---

## 🚀 Setup Guide

### 1. Import Workflow
- In n8n: **Workflows → Import from file**
- Upload `telegram-ai-chatbot-n8n.json`

### 2. Configure Credentials

#### Telegram Bot
1. Message [@BotFather](https://t.me/BotFather) on Telegram
2. Run `/newbot` and follow instructions
3. Copy the **API Token**
4. In n8n → Credentials → Add **Telegram API**

#### Groq API
1. Sign up at [console.groq.com](https://console.groq.com)
2. Generate an **API Key** (free tier available)
3. In n8n → Credentials → Add **Groq API**

### 3. Activate
- Toggle the **Active switch** (top-right in n8n editor) to ON
- Your bot is now live 🎉

---

## ⚙️ Customization

### Change the AI Personality
Edit the system prompt inside the **AI Agent** node:
```
You are a helpful and friendly AI assistant on Telegram.
Answer the user's questions clearly and concisely.
```

### Change the Model
In the **Groq Chat Model** node, swap `llama-3.3-70b-versatile` with any supported model:
- `llama-3.1-8b-instant` — faster, lightweight
- `mixtral-8x7b-32768` — great for longer context

### Memory Window
In **Simple Memory** node, adjust `contextWindowLength` (default: 20 messages).

---

## 📋 Requirements

- [n8n](https://n8n.io) (cloud or self-hosted)
- Telegram Bot Token (free via BotFather)
- Groq API Key (free tier available)

---

## 📄 License

MIT — free to use, modify, and share.
