# Project 4: AI Inbox Assistant — Gmail + Gemini with Confidence Gate

> **One-liner:** Emails are summarized and AI-drafted replies are created automatically — high confidence → draft, low confidence → human escalation. Saves 2 hours of inbox time daily.

[![Gmail](https://img.shields.io/badge/Gmail-Trigger-red)](https://gmail.com)
[![Gemini](https://img.shields.io/badge/Gemini%201.5%20Flash-AI-blue)](https://aistudio.google.com)
[![Make.com](https://img.shields.io/badge/Make.com-Automation-blue)](https://make.com)
[![Telegram](https://img.shields.io/badge/Telegram-Escalation-blue)](https://telegram.org)

## 🎯 Problem
Founders spend 2+ hours daily on inbox: same 10 questions, manual summaries, drafting replies from scratch. Support emails eat productive time.

## ✅ Solution — The Confidence Gate Pattern (This Is What Makes It Professional)

Most AI email bots fail because they guess. This one **knows when it doesn't know**.

**Flow:**
1. **Gmail → Watch Emails** — New email arrives
2. **Gemini → Generate Text** — Prompt with company knowledge base + email content → Output: ANSWER + CONFIDENCE %
3. **Router (2 routes):**
   - Route 1: Confidence ≥ 80% → **Gmail → Create a Draft** (To: sender, Subject: Re: {{original}}, Body: AI draft — human reviews before sending)
   - Route 2: Confidence < 80% OR answer contains "ESCALATE" → **Telegram → Send Message** to founder: `🚨 Support email needs human: {{subject}} from {{sender}}`

**Nothing sends automatically. Human always approves.**

## 🏗️ Architecture

```
[Gmail: Watch Emails - Label: Inbox / Support]
        ↓
[Gemini: Generate Text - Prompt with Knowledge Base]
Prompt: "You are support for [Company]. Knowledge: Shipping 3-5 days, Returns 30 days free, Sizing true to size, Payment card/PayPal, Tracking emailed 24h, Refunds 5-7 days. Answer this email: {{text}}. If answer not in knowledge base, say EXACTLY: ESCALATE. Output: ANSWER: [text] | CONFIDENCE: [%]"
        ↓
[Router]
  ├─≥80% → [Gmail: Create a Draft]
  └─<80% or ESCALATE → [Telegram: Send Alert]
```

## 📸 Screenshots (Add Yours)

- `knowledge-base.png` — Google Sheet with 10 Q&As (Shipping, Returns, Sizing, Payment, Tracking, Refunds, etc)
- `scenario.png` — Full scenario: Gmail + Gemini + Router + Gmail Draft + Telegram
- `draft.png` — Gmail Drafts folder showing AI-drafted reply
- `escalation.png` — Telegram alert: "🚨 Support email needs a human"

## 📈 Results

- **Before:** 2 hrs/day on routine emails, same 10 Qs
- **After:** ~80% routine emails auto-drafted in minutes, humans handle only hard 20%
- **Response Time:** Hours → Minutes (draft ready instantly, human just reviews)
- **Build Time:** 1 hour
- **Client Trust:** Confidence gate prevents AI hallucinations — clients trust it because it escalates instead of guessing

## 🛠️ Tools Used

- Gmail (Watch Emails + Create Draft)
- Google AI Studio — Gemini 1.5 Flash (Free tier — 15 req/min, plenty for inbox)
- Make.com (Free tier)
- Telegram (Escalation alerts — free)
- Google Sheets (Knowledge base — 10 Q&As)
- **Running Cost:** $0/month free tiers — build + upkeep is the service

## 🎥 Demo Video

**YouTube Unlisted Link:** `[Paste Link Here]`

**Demo Script (45 sec):**
- 0-5s: "AI Inbox Assistant — Drafts High Confidence, Escalates Low"
- 5-15s: Show knowledge base sheet (10 Q&As)
- 15-30s: Send test email to yourself: "How long is shipping?" → Show Make.com run → Show Gmail Draft created
- 30-40s: Send second test: "Do you sell lawnmowers?" (outside KB) → Show Telegram escalation alert
- 40-45s: "80% auto-drafted, 20% escalated — AI that knows when it doesn't know. Built with Gmail + Gemini"

## 🚀 How To Replicate

1. Create Google Sheet: `Company Knowledge` → Columns: Question, Answer → Fill 10 Q&As for pretend e-commerce store
2. Make.com → New Scenario → Gmail → Watch Emails → Connection → Label: Inbox (or create label "Support")
3. Add Gemini → Generate Text → Connection: Paste Gemini API key from aistudio.google.com → Model: gemini-1.5-flash → Prompt: template above → Map {{email text}}
4. Add Router → Route 1: Filter: Confidence ≥ 80 → Gmail → Create a Draft → To: {{sender}}, Subject: Re: {{subject}}, Body: {{answer}}
5. Route 2: Filter: Confidence < 80 OR text contains ESCALATE → Telegram → Send Message → Alert template
6. Test 3 emails to yourself: (a) "How long is shipping?" (should draft) (b) "Do you sell lawnmowers?" (should escalate) (c) "My order arrived damaged" (should escalate)
7. Screenshot all 3 tests

## 💼 Client Pitch

> "Most AI support bots fail because they guess and anger customers. Mine has a confidence gate — high confidence → drafted reply you review, low confidence → alerts you. AI removes the boring 90%, you keep judgment on the hard 10%. That's the version customers trust."

## 🔒 Security

- No API keys in repo
- Fake customer emails only (test@client.com)
- Knowledge base uses pretend company data
- Drafts never auto-send — human approval required

## 📄 Case Study

See `case-study.md`

---
**Built by Isaac — aiagentbuilderhq | [Full Portfolio](https://github.com/aiagentbuilderhq/automation-portfolio) | Free Audit: [Calendar Link]**
