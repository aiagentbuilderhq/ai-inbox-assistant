# Setup Guide — ai-inbox-assistant — Client Delivery Version

## What Client Gets

- Working scenario (Make.com blueprint + n8n workflow JSON — sanitized, no keys)
- 15-min Loom walkthrough video
- 1-page documentation (this file)
- 7 days support — if it breaks, fixed free within 24h
- Built on YOUR accounts — you keep everything, no vendor lock-in

## Prerequisites (Client Needs)

- Gmail account (for Gmail API)
- Google Sheets account (for Sheets API)
- Make.com free account OR n8n cloud/self-host free
- For this specific project: See README for API keys needed (all free tiers)

## Setup Steps (Copy-Paste for Client)

1. **Create Connections (5 min):**
   - Make.com/n8n → Create connection → Google Sheets API → Authorize with your Google account
   - Same for Gmail API, Slack API, Telegram Bot API (if needed) — all via OAuth, no keys to copy manually

2. **Import Blueprint (2 min):**
   - Make.com: Create new scenario → ... → Import Blueprint → Select `blueprint.json` from this repo
   - n8n: Import from File → Select workflow JSON
   - Replace placeholder `YOUR_API_KEY`, `YOUR_CONNECTION_ID` with your connections (dropdown select)

3. **Test with Fake Data (5 min):**
   - Add test row / submit test form / send test email to yourself
   - Click Run Once → Verify output (email received, Slack message, etc.)
   - Check screenshots folder in this repo for expected output

4. **Turn ON & Schedule (1 min):**
   - Make.com: Toggle ON → Schedule: Every 15 min (free) or Instant via Webhook
   - n8n: Activate workflow → Schedule Trigger: Every 15 min or Cron

5. **Documentation & Handover (10 min Loom):**
   - Watch Loom walkthrough link in README
   - This SETUP.md explains how to edit: add recipients, change Slack channel, adjust prompt, change threshold

## How to Edit (Common Changes)

- **Add more email recipients:** Gmail node → To field → Add more emails separated by comma
- **Change Slack channel:** Slack node → Channel → Select #sales instead of #leads
- **Adjust AI prompt:** Gemini node → Prompt → Edit ICP or knowledge base
- **Change score threshold:** Sheets Search Rows node → Filter → Change Score ≥8 to ≥7
- **Add new API:** Replace HTTP Request URL with new API endpoint (Shopify, Stripe, HubSpot, etc.) — same nodes, different URL

## Security — Never Do This

- Never commit API keys to GitHub — use .env file (already in .gitignore)
- Never use real client data in tests — fake data only: Test Person, test@email.com
- Never share blueprint with real keys — sanitize before sharing (replace keys with YOUR_API_KEY)

## Support

- 7 days free support: If it breaks, I fix free within 24h
- After 7 days: Monthly retainer optional — $150/month for 10 hrs monitoring + updates + fixes within 24h
- Retainer pitch: "The tools are free, yes — the upkeep isn't. Automations break silently: connections expire, quotas run out, business changes. Monthly plan means I'm watching it, updating as business changes, fixing within 24h."

## Cost to Run

- All free tiers: Make.com free (1,000 ops/month), n8n free self-host, Gmail API free, Sheets API free, Slack API free, Telegram API free, Gemini free tier (15 req/min), Apollo free, Hunter free (25 searches/month)
- Client pays for build + documentation + upkeep, not software subscriptions — runs on tools they already have

---

Built by Isaac — aiagentbuilderhq | Hub: https://github.com/aiagentbuilderhq/automation-portfolio
