# Oakmere Living — WhatsApp AI Customer Support Assistant

An n8n-based portfolio project for multilingual, knowledge-grounded WhatsApp support for a fictional home and furniture retailer.

## Overview

I built and tested this workflow in my configured environment before publishing this portfolio entry. It is designed to answer product, delivery, returns, and store-policy questions from a curated knowledge base; process supported voice notes; look up inventory and verified order status; create support tickets; and escalate uncertain or sensitive cases to a human operator.

**Testing status:** The workflow was tested by me in my configured environment before publication. This documentation update did not rerun the workflow. The public repository includes sanitized, inactive n8n workflow JSON exports for the assistant, knowledge-base ingestion, and Telegram error alerts. These are publication-safe starting points, not a hosted deployment; configure your own credentials and IDs before importing or running them.

## Architecture

WhatsApp Cloud API → n8n webhook and message normalization → duplicate-message guard → text/voice processing → intent and policy routing → Supabase retrieval or approved data lookup → primary LLM with configured fallback → output validation → WhatsApp response.

Telegram is used for operator alerts.

## Components

- **Orchestration:** n8n customer assistant, knowledge-base ingestion/RAG, and Telegram error alert workflows.
- **Messaging:** WhatsApp Cloud API; Telegram for operator notifications.
- **Knowledge retrieval:** Supabase vector store and a curated catalogue/policy reference.
- **Language models:** Groq primary model and configurable OpenRouter fallback.
- **Structured data:** inventory/order lookups and SQL verification checks.
- **Safety controls:** order-verification gates, duplicate-message protection, bounded retries, output validation, and human escalation.

## Key safeguards

- Do not disclose order status unless required customer verification checks pass.
- Ground policy answers in retrieved evidence; escalate when evidence is missing or conflicting.
- Persist WhatsApp message IDs with a unique constraint to reduce duplicate side effects.
- Store provider credentials in n8n Credentials; never commit secrets.
- Bound retries and fallback attempts and provide a safe terminal-failure path.
- Send operators sanitized diagnostics rather than tokens or unnecessary customer data.
- Use fictional demo data only.

## Setup overview

1. Review the [workflow design and production-readiness checklist](../../workflows/oakmere-whatsapp-ai-customer-support.md).
2. Configure your own Meta WhatsApp Cloud API, n8n, Supabase, Groq/OpenRouter, and Telegram credentials.
3. Replace environment-specific IDs and placeholders.
4. Apply and review the database schema, indexes, access policies, and verification SQL in a test environment.
5. Ingest the knowledge base and check retrieval with known-answer questions.
6. Test duplicate webhooks, voice-note failures, provider outages, unverified order requests, escalation, and terminal errors.
7. Sanitize and review exports before publishing them.

## Sanitized workflow exports

The following JSON exports are included in [`workflows/`](workflows/):

- [WhatsApp AI Customer Assistant](workflows/whatsapp-ai-customer-assistant.json)
- [Knowledge Base Ingestion (RAG)](workflows/knowledge-base-ingestion-rag.json)
- [Telegram Error Alert](workflows/error-alert-telegram.json)

The published exports have been parsed as JSON, set inactive, and scanned for embedded credential objects, obvious token patterns, and numeric chat IDs. Credential references and instance/workflow metadata were removed, and Telegram chat destinations use placeholders. This is a static sanitization review, not a guarantee of security or successful import in every n8n version. Configure your own n8n credentials and IDs; inspect every node and expression before activation. Do not commit real credentials or execution data.

## Test checklist

See the [Oakmere WhatsApp assistant test plan](../../tests/oakmere-whatsapp-assistant-test-plan.md). It is a reusable checklist, not evidence that every listed scenario has a recorded pass result. Record observed outcomes before claiming specific test coverage.

## Limitations

This is a fictional portfolio demonstration, not a hosted service or a claim of production deployment. The repository publishes sanitized workflow JSON exports, but they have not been imported and re-executed as part of this documentation update. Any future export or import into another environment will require its own credentials, IDs, permissions, database setup, node versions, and API configuration. No quantified business outcome is claimed.

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product. Obtain written permission from the copyright holder before reuse. See the repository root [LICENSE](../../LICENSE).

## Setup, Credentials & Testing

This workflow is provided as an exported n8n JSON template. It may require configuration before it runs successfully after import.

### Before running the workflow

1. Import the JSON file into your n8n instance.
2. Configure the required credentials, API keys, and service connections.
3. Replace placeholder values with your own IDs, URLs, and configuration settings.
4. Review the nodes and adjust settings for your environment.
5. Test the workflow with sample data before using it in production.

### Important notes

- Credentials and API keys are not included in this export. Configure your own credentials for the services used by the workflow.
- Some integrations may require API access, subscriptions, permissions, or additional setup.
- The exported workflow may require environment-specific changes before it works correctly.
- Importing this JSON does not automatically activate the workflow or guarantee successful execution.
- Test the workflow in your own n8n environment before using it in production.

The original workflow was built and tested in the author's configured environment. Your results may vary depending on your credentials, service configuration, and n8n setup.
