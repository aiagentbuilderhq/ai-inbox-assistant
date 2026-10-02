# Case Study: AI Inbox Assistant with Confidence Gate

**Client Type:** E-commerce store founder answering same 10 support questions daily
**Timeline:** 1 day (1 hour build + testing)
**Tools:** Gmail, Gemini 1.5 Flash, Make.com, Telegram, Google Sheets
**Cost to Run:** $0/month (free tiers)

### Problem
Founder spent 2+ hours daily on support inbox. 80% of emails were same 10 questions: shipping time, return policy, sizing, tracking, refunds. Manual replies, no templates, slow response.

**Impact:** 2 hrs/day lost + slow replies = lower customer satisfaction.

### Solution
Built AI assistant with confidence gate — the key differentiator:

**Knowledge Base:** Google Sheet with 10 Q&As (shipping 3-5 days, returns 30 days free, sizing true to size, payment card/PayPal, tracking emailed within 24h, refunds 5-7 business days, exchange policy, discount codes, delivery areas, damaged items)

**Automation Flow:**
1. Gmail watches for new emails
2. Gemini reads email + knowledge base → generates ANSWER + CONFIDENCE %
3. Router:
   - ≥80% confidence → Creates Gmail Draft (founder reviews, then sends)
   - <80% or ESCALATE → Sends Telegram alert to founder: "🚨 Needs human"

**Why Confidence Gate Matters:**
- Prevents hallucinations
- Builds trust — AI escalates instead of guessing
- Client controls final send — nothing auto-sends

**Example:**
- Email: "How long is shipping?" → Confidence 95% → Draft: "Shipping is 3-5 days..."
- Email: "Do you sell lawnmowers?" (outside KB) → Confidence 20% → Telegram: "🚨 Support email needs human: Do you sell lawnmowers?"

### Results
- **Routine Emails Handled:** 80% auto-drafted in minutes
- **Human Time:** 2 hrs/day → 15 min review
- **Response Time:** Hours → Minutes
- **Customer Satisfaction:** Up (faster replies, consistent answers)
- **Trust:** Founder trusts it because it knows when to escalate

### What Client Gets
- Working scenario + blueprint (sanitized)
- Knowledge base sheet template (10 Q&As — client fills their own)
- 5-min Loom walkthrough: how it works, how to add new Q&As, how to adjust confidence threshold
- Documentation: how to change escalation channel, how to add more inboxes
- 7 days support

### Tools & Cost
- Gmail (Watch + Draft) — free
- Gemini 1.5 Flash via Google AI Studio — free tier (15 req/min, ~$0 for this volume)
- Make.com free tier
- Telegram free
- Running cost $0 — client pays for build, documentation, upkeep

### Retainer Angle
"The tools are free, yes — the upkeep isn't. Automations break silently: connections expire, knowledge base needs new Q&As as business changes, new products need adding. Monthly plan means I'm watching it, updating knowledge base as your business changes, fixing within 24h when something breaks."

---
Demo: [Add Link] | Portfolio: github.com/aiagentbuilderhq/automation-portfolio
