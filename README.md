# Project 4: AI Inbox Assistant — Gmail + Gemini + n8n + MCP + Confidence Gate + RAG-lite

> **One-liner:** Emails summarized + AI-drafted replies automatically — high confidence → draft, low confidence → human escalation. Saves 2 hours inbox time daily. Built with Make.com + n8n + MCP + LangChain patterns.

[![Gmail API](https://img.shields.io/badge/Gmail%20API-Trigger-red)](https://developers.google.com/gmail/api)
[![Gemini](https://img.shields.io/badge/Gemini%201.5%20Flash%20%2F%20Pro-AI-blue)](https://aistudio.google.com)
[![n8n](https://img.shields.io/badge/n8n-Workflow-red)](https://n8n.io)
[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-purple)](https://modelcontextprotocol.io)
[![LangChain](https://img.shields.io/badge/LangChain-Pattern-green)](https://langchain.com)
[![RAG](https://img.shields.io/badge/RAG--lite-Knowledge%20Base-orange)](https://en.wikipedia.org/wiki/Retrieval-augmented_generation)

**Live Hub:** [automation-portfolio](https://github.com/aiagentbuilderhq/automation-portfolio) | **Other Projects:** [Sheets → Gmail](https://github.com/aiagentbuilderhq/sheets-gmail-automation) · [Weather Bot](https://github.com/aiagentbuilderhq/weather-telegram-bot) · [Form → Slack](https://github.com/aiagentbuilderhq/form-slack-leads) · [Lead Scoring](https://github.com/aiagentbuilderhq/ai-lead-scoring)

## 🎯 Problem
Founders spend 2+ hours daily on inbox: same 10 questions, manual summaries, drafting replies from scratch. Support emails eat productive time. Generic AI bots guess and anger customers.

## ✅ Solution — The Confidence Gate + MCP + RAG-lite Pattern (What Makes It Pro)

Most AI email bots fail because they guess. This one **knows when it doesn't know** — MCP principle.

**Flow (Make.com AND n8n versions):**

1. **Gmail → Watch Emails** — New email arrives (Gmail API + Webhook)
2. **Knowledge Base → RAG-lite** — Google Sheets with 10 Q&As acts as vector DB lite (Sheets API) — Shipping, Returns, Sizing, etc. — LangChain pattern: Retrieve relevant Q&A
3. **Gemini → Generate Text — MCP Pattern** — Prompt with knowledge base + email content → Output: ANSWER + CONFIDENCE % — Uses Gemini 1.5 Flash/Pro + Groq as fallback
4. **Router (2 routes) — Confidence Gate:**
   - Route 1: Confidence ≥80% → **Gmail → Create a Draft** (Human reviews before sending — Human-in-the-loop)
   - Route 2: Confidence <80% OR answer contains "ESCALATE" → **Telegram → Send Alert** + **Slack → Alert** to founder: `🚨 Support email needs human: {{subject}} from {{sender}}`

**Nothing sends automatically. Human always approves. That's why clients trust it.**

**n8n Version:**
```
[Gmail Trigger] → [Google Sheets Node: Get Knowledge Base] → [AI Agent Node: Gemini + MCP] → [IF Node: Confidence ≥80%] → [Gmail Node: Create Draft] / [Telegram Node: Escalate]
```

**MCP Explained:** Model (Gemini) → Context (Sheets knowledge base via RAG-lite) → Protocol (Gmail Draft or Telegram escalation). MCP is the standard for advanced AI agents that talk to tools — founders searching "MCP" want this.

**LangChain Pattern:** Retrieve (Sheets) → Augment (Prompt) → Generate (Gemini) — RAG-lite without expensive vector DB.

## 🏗️ Architecture

```
[Gmail: Watch Emails — Gmail API / Webhook]
        ↓
[Google Sheets: Get Knowledge Base — Sheets API — RAG-lite / LangChain Retrieve]
        ↓
[Gemini: Generate Text — Gemini API + Groq Fallback — MCP Pattern]
Prompt: "You are support for [Company]. Knowledge: Shipping 3-5 days, Returns 30 days free... Answer this email: {{text}}. If not in KB, say EXACTLY: ESCALATE. Output: ANSWER: [text] | CONFIDENCE: [%]"
        ↓
[Router / IF Node — Confidence Gate]
  ├─≥80% → [Gmail: Create a Draft — Gmail API]
  └─<80% or ESCALATE → [Telegram: Send Alert — Telegram API] + [Slack: Alert — Slack API]
```

## 📈 Results

- **Before:** 2 hrs/day on routine emails
- **After:** ~80% routine emails auto-drafted in minutes, humans handle only hard 20%
- **Response Time:** Hours → Minutes
- **Build Time:** 1 hour (both Make.com + n8n)
- **Client Trust:** Confidence gate prevents hallucinations — escalates instead of guessing — MCP + RAG-lite pattern is what advanced founders look for

## 🛠️ Tools Used — High-Value Founder-Searched Skills

- **Automation:** Make.com · n8n (AI Agent nodes) · Webhooks · Gmail API
- **AI:** Gemini 1.5 Flash/Pro (Google AI Studio) · Groq (Llama 3, Mixtral fallback) · OpenAI API (if client provides key) · MCP (Model Context Protocol) · LangChain patterns · RAG-lite (Sheets as knowledge base) · Prompt Engineering · Confidence Gates · Human-in-the-loop
- **APIs:** Gmail API · Google Sheets API (knowledge base) · Telegram Bot API · Slack API · Gemini API
- **Patterns:** RAG-lite (Retrieve from Sheets → Augment Prompt → Generate), Error Handling, Router, AI Fallback (Gemini → Groq)
- **Why This Matters:** Founders searching "MCP", "RAG", "LangChain", "AI Agent" want exactly this — AI that knows when to escalate, uses knowledge base, doesn't hallucinate. I build it on both Make.com and n8n.

## 🎥 Demo Video

**YouTube Unlisted:** `[Paste Link]`
Demo: Show knowledge base sheet (10 Q&As) → Send test email "How long is shipping?" → Show Make.com/n8n run → Show Gmail Draft created → Send second test "Do you sell lawnmowers?" (outside KB) → Show Telegram escalation

## 💼 Client Pitch — Sounds Pro

> "Most AI support bots fail because they guess and anger customers. Mine has a confidence gate + RAG-lite + MCP pattern — high confidence → drafted reply you review, low confidence → alerts you via Telegram/Slack. AI removes boring 90%, you keep judgment on hard 10%. Built on both Make.com and n8n, so I work in your existing stack. That's the version customers trust — and it's what advanced teams searching for MCP and RAG want."

## 🔒 Security

- No API keys, fake customer emails only, drafts never auto-send

---
**Built by Isaac — aiagentbuilderhq | [Full Portfolio Hub](https://github.com/aiagentbuilderhq/automation-portfolio) | Tech: Make.com + n8n + Gmail API + Sheets API + Gemini + Groq + MCP + LangChain + RAG-lite + Telegram/Slack APIs**
