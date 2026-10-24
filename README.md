*Intuz — Your automation partner, one workflow at a time.*

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

[Intuz](https://www.intuz.com) helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [AI Consulting](https://www.intuz.com/ai-transformation-services/) · [AI Workflow Automation](https://www.intuz.com/workflow-automation-services/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

# Triage legal conflict checks from Slack with GPT-4o-mini and Google Sheets

## Quick overview

This workflow listens for new Slack messages, runs an OpenAI-powered conflict-intake agent that queries a Google Sheets–backed MCP tools endpoint, replies in the original Slack thread with a preliminary conflict summary, and appends an audit record to a Google Sheets log.

## How it works

1. Triggers when a new message is posted in the configured Slack channel.
2. Ignores bot or empty messages, then extracts the message text and key Slack metadata (user, channel, timestamp).
3. Builds a unique event key from the Slack channel and timestamp and checks a Google Sheets “ConflictAuditLog” tab to prevent processing the same message twice.
4. Sends the message text to an OpenAI agent, which extracts the prospective client and opposing party and calls a conflict-search MCP endpoint that queries Google Sheets records.
5. Parses the agent’s structured output to determine whether it indicates a potential conflict and routes the message accordingly.
6. Posts a “potential conflict” or “no potential conflict found in searched records” reply back to the original Slack thread.
7. Appends the request and key fields from the Slack reply to the Google Sheets ConflictAuditLog for auditing.

## Setup

1. Connect Slack credentials, add the Slack app/bot to your target channel, and select the channel in the Slack trigger and thread-reply steps.
2. Connect Google Sheets credentials and ensure the spreadsheet contains the required tabs (ConflictAuditLog, Clients, Matters, Parties, RelatedEntities) with the expected lookup columns (for example, event_key and name/entity_name).
3. Create or update the ConflictAuditLog sheet columns used for deduplication and logging (at minimum event_key, created_at, channel_id, message_ts, request_text, and status).
4. Connect an OpenAI credential and confirm the chat model selection used by the agent.
5. Activate the MCP server workflow (the MCP trigger path is /conflict-tools) and set the MCP Client endpoint URL to your own n8n MCP endpoint.

## FAQ

**What triggers this workflow?**  
The workflow triggers when a new message is posted in the configured Slack channel.

**How does the workflow prevent duplicate processing?**  
It builds a unique event key from the Slack channel and timestamp and checks the Google Sheets ConflictAuditLog tab to avoid processing the same message twice.

**What services does this workflow integrate with?**  
It integrates with Slack, OpenAI (GPT-4o-mini), and Google Sheets.

## Related n8n templates from Intuz

- [In-build Admin Panel and basic APIs for mobile app from Intuz](https://github.com/Intuz-production/Backend-API-NodeJs)
- [Simple Video player using Google ExoPlayer library](https://github.com/Intuz-production/VideoPlayer-android)
- [Instantly mirror new and updated QuickBooks invoices into a Google Sheet in real time, using a webhook — a live backup and reporting log outside QuickBooks.](https://github.com/Intuz-production/QuickBooks-Invoice-Sync)

[See all of Intuz's free n8n templates](https://www.intuz.com/n8n-workflow-automation-templates/)

## Connect with us

Intuz is a USA-based AI & workflow automation company with 16+ years of experience building custom AI-enabled workflow automations for SMBs and Enterprises, specializing in agentic AI, LLM integrations, and CRM/ERP sync across Healthcare, FinTech, eCommerce, Manufacturing, and Real Estate.

* **Website:** [https://www.intuz.com](https://www.intuz.com)
* **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
* **LinkedIn:** https://www.linkedin.com/company/intuz/
* **Get Started:** https://n8n.partnerlinks.io/intuz

## For Custom Workflow Automation

[Click here - Get Started](https://www.intuz.com/get-started/)
