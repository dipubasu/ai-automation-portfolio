# n8n Workflow Library

The workflow projects documented in this portfolio were built and tested by me in my configured environment before I published their portfolio entries. This directory contains JSON exports for the workflows that currently have a published export; some projects are documentation-only. Some exports may be intentionally inactive because they are not currently needed; an inactive export does not by itself mean a workflow is untested. When importing into another n8n instance, credentials, IDs, permissions, and service settings may need to be configured for that environment.

## Workflow catalogue

### Lead intake and CRM

- **[Lead Intake → HubSpot CRM Sync → Notification](lead-intake-hubspot-crm-sync.json) · [Case study](lead-intake-hubspot-crm-sync.md)** — Receives new lead data through a webhook, checks required lead data, creates or updates a HubSpot contact, creates a deal, branches for high-value deals, logs standard leads to Google Sheets, and returns webhook responses for success, validation, and sync-error paths.
- **[Excel Data Cleaning Automation](excel-data-cleaning-automation.json) · [Case study](excel-data-cleaning-automation.md)** — Manual-run workflow that downloads and parses an Excel workbook, checks its schema, standardizes and validates records, detects duplicates, classifies rows, builds and uploads a report, upserts valid customer rows, logs run metrics, and includes explicit stop/error nodes for key integration failures. See the [project setup and limitations](../projects/excel-data-cleaning-automation/README.md).

### Real-estate AI and retrieval

- **[EstateBot Lead Qualification Server](estatebot-lead-qualification-server.json) · [Case study](estatebot-lead-qualification-server.md)** — Ingests a document from Google Drive, extracts its content, splits it into chunks, creates Google Gemini embeddings, and writes content to a Supabase vector store. This is a knowledge-base ingestion workflow, distinct from the Telegram-facing agent.
- **[EstateBot AI Agent + Memory + Supabase RAG](estatebot-ai-agent-memory-supabase-rag.json) · [Case study](estatebot-ai-agent-memory-supabase-rag.md)** — Telegram-triggered agent workflow with chat memory, a Supabase vector-store question-answer tool, lead-completion branching, Google Sheets logging, and Telegram responses. It also includes a property-ID lookup tool.

### Customer support and messaging

- **[Oakmere Living — WhatsApp AI Customer Support Assistant](oakmere-whatsapp-ai-customer-support.md)** — Case study and production-readiness notes for a workflow I built and tested in my configured environment before publication. Sanitized, inactive JSON exports for the assistant, RAG ingestion, and Telegram error alert are linked from the [Oakmere project README](../projects/oakmere-whatsapp-ai-assistant/README.md#sanitized-workflow-exports); see also the [test checklist](../tests/oakmere-whatsapp-assistant-test-plan.md).
- **[Dental Clinic Email Support Agent](dental-clinic-email-support-agent.json) · [Case study](dental-clinic-email-support-agent.md)** — Uses a Gmail trigger, an AI agent, and a Groq chat model to prepare a response to an incoming message, then replies through Gmail. Verify the prompt, knowledge sources, and clinic policies before using with real patient messages.
- **[Veltoro RAG Email Customer Support Agent](rag-email-customer-support-agent.json) · [Case study](rag-email-customer-support-agent.md)** — Detects incoming customer email, cleans message content, drafts a knowledge-base-grounded response using a Supabase vector store, requests human approval, sends approved replies, and flags unapproved cases for manual review.
- **[Telegram Chatbot + Human Bridge Support](telegram-chatbot-human-bridge-support.json) · [Case study](telegram-chatbot-human-bridge-support.md)** — Telegram support flow using an AI agent, short-term memory, routing branches, and message replies. It includes file retrieval and audio-analysis nodes for voice-message handling; review the branch conditions and handoff behavior in n8n before deployment.
- **[Veltoro Messenger AI Chatbot](veltoro-messenger-ai-chatbot.json) · [Case study](veltoro-messenger-ai-chatbot.md)** — Webhook-based Messenger chatbot flow with webhook acknowledgement, an AI agent, Groq chat model, and Supabase vector retrieval for catalogue-grounded responses.
- **[Veltoro RAG Knowledge Base Setup](veltoro-rag-knowledge-base-setup.json) · [Case study](veltoro-rag-knowledge-base-setup.md)** — Manual ingestion flow that downloads a PDF from Google Drive, extracts its text, prepares documents, generates Google Gemini embeddings, and stores them in Supabase for later retrieval.

### Travel tools and MCP

- **[AI Travel Assistant (MCP)](ai-travel-assistant-mcp.json) · [Case study](ai-travel-assistant-mcp.md)** — Chat-triggered AI travel assistant connected to a Travel MCP tools client, a Google Gemini chat model, and data-table tools for saving and retrieving preferences.
- **[Travel MCP Server](travel-mcp-server.json) · [Case study](travel-mcp-server.md)** — Exposes HTTP request tools through an MCP server trigger for hotel, restaurant, attraction, currency, geocoding, and weather-related operations. External API access and parameters must be configured and verified in the target environment.

### Video and content production

- **[YouTube Automation — Topic to Video](youtube-automation-topic-to-video.json) · [Case study](youtube-automation-topic-to-video.md)** — Manual-run pipeline that develops a topic into video details and scene prompts, generates image and voiceover assets, uploads assets for processing, assembles a Shotstack render payload, checks render status, downloads the result, and uploads it to YouTube. This flow depends on multiple external services and should be tested end-to-end with test credentials and non-public output first.

## Before importing

1. Check the workflow JSON and confirm node types are supported by your n8n version.
2. Add your own credentials through n8n's credential manager; do not paste secrets into workflow parameters or commit them to Git.
3. Replace placeholder IDs, URLs, model settings, and other environment-specific configuration.
4. Verify external API permissions, quotas, and request/response formats.
5. When moving a workflow to a different instance or changing its configuration, run a controlled test and inspect success and error paths before enabling it for production use.

The `active` flag records the state saved in each export; some workflows are intentionally inactive when not needed. I live-tested the published workflow exports in my configured environment before publishing them. The Oakmere WhatsApp project has sanitized JSON exports under its project directory; the case-study folder itself contains design notes. Behavior in another environment depends on its credentials, permissions, IDs, service availability, and configuration.

## Code reuse and permissions

This repository is public for viewing, review, testing, and portfolio evaluation. Permission is required before reusing, copying, modifying, redistributing, or incorporating workflow JSON, code, or other repository material into another project or product. Obtain written permission from the copyright holder before reuse. See the repository root [LICENSE](../LICENSE).

## Code reuse and permissions

This repository is public for viewing, review, testing, and portfolio evaluation. Permission is required before reusing, copying, modifying, redistributing, or incorporating workflow JSON, code, or other repository material into another project or product. Obtain written permission from the copyright holder before reuse. See the repository root [LICENSE](../LICENSE).
