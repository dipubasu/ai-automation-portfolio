# Oakmere Living — WhatsApp AI Customer Support Assistant

> **Author testing status:** I built and tested this workflow in my configured environment before publishing this portfolio entry. This documentation update did not rerun the live workflow. The public repository now includes sanitized, inactive JSON exports for the assistant, RAG ingestion, and Telegram error alert under [`projects/oakmere-whatsapp-ai-assistant/workflows/`](../projects/oakmere-whatsapp-ai-assistant/workflows/). They were statically reviewed and parsed as JSON, but were not imported or re-executed during this documentation update.

## Overview

Oakmere Living is a fictional online-store demo exploring WhatsApp customer support automation with n8n. The workflow combines policy-grounded answers, voice-note transcription, stock and order lookups, support-ticket creation, and human escalation.

## Intended capabilities

- Answer shipping, returns, product, and store-policy questions from a Supabase-backed knowledge base.
- Transcribe supported WhatsApp voice notes before processing the request.
- Check stock through the configured data source.
- Retrieve order status only after required customer verification checks pass.
- Escalate uncertain or sensitive requests to a human and notify the operator through Telegram.
- Provide a customer-safe response when the AI or a downstream integration fails.

## Architecture

WhatsApp Cloud API → n8n webhook and message normalization → duplicate-message guard → text/voice processing → intent and policy routing → Supabase retrieval or approved data lookup → primary LLM (Groq) → configured fallback LLM (OpenRouter) → output validation/formatting → WhatsApp response.

Failure paths should record a safe diagnostic event, alert the operator without exposing secrets or unnecessary customer data, and send a customer-facing fallback only when the incoming message is a genuine customer message and a reply can safely be sent.

## Production-readiness requirements

1. **LLM resilience:** configure a tested OpenRouter fallback with an explicit model ID, timeout, bounded retries, and provider-specific error handling. Do not retry indefinitely. Confirm both providers use compatible prompt/output expectations.
2. **Customer failure response:** route terminal failures to a short, localized WhatsApp message with a support/human-contact option. Prevent the error path from recursively triggering itself.
3. **Idempotency:** persist the incoming WhatsApp `wamid` with a unique constraint before side effects. Repeated deliveries must not create duplicate replies, tickets, or notifications.
4. **Grounded answers:** require retrieved policy evidence for policy claims; if evidence is missing or conflicting, escalate instead of guessing.
5. **Order privacy:** do not reveal order data unless verification succeeds. Never treat a customer-supplied order number alone as identity verification.
6. **Output sanitation:** enforce a length limit, remove unsupported Markdown, and validate the final message before sending.
7. **Ticket integrity:** use a database-generated ID/sequence or UUID, not a second-precision timestamp. Avoid blind retries for non-idempotent ticket creation.
8. **Least privilege:** use separate, restricted credentials where practical; enable RLS and restrict database functions/views to the minimum required operations.
9. **Webhook security:** verify Meta's webhook signature using the official verification method supported by the deployment. Do not assume a public webhook URL alone authenticates requests.
10. **Knowledge-base hygiene:** deduplicate/re-ingest the corpus in a controlled way and verify retrieval quality with known-answer tests.
11. **Observability:** log correlation/message IDs, route, latency, provider, and sanitized error codes; do not log access tokens, full customer messages, or private order details unnecessarily.
12. **Safe publishing:** export an inactive sanitized workflow; replace credential references and instance-specific IDs with placeholders; scan JSON, screenshots, logs, and sample data for secrets and personal information. The public exports are starting points only; review node expressions and configure credentials before use.

## OpenRouter fallback configuration notes

- Use the official OpenRouter API endpoint and an API key stored in n8n Credentials, never inline in a node or committed JSON.
- Select a specific model ID and verify its availability, context window, output format, and rate limits before testing.
- Keep the same system policy, language behavior, retrieval context, and output constraints as the primary model.
- Prefer a bounded fallback path: invoke OpenRouter only for retryable primary-provider failures such as rate limiting, temporary server errors, or provider timeouts. Do not automatically fallback for malformed input, verification failures, policy denials, or database authorization errors.
- If using a LangChain fallback-model feature, confirm it is supported by the exact n8n node/version and test that it actually switches providers. Otherwise, use an explicit error/fallback branch.
- Test a forced primary-provider failure and verify that only one customer reply is sent.
- Treat provider fallback as best-effort, not a guarantee of availability. If both providers fail, use the customer-safe failure path and operator alert.

## Testing and validation

The workflow was tested in my configured environment before publication. This repository update did not rerun it, and this repository does not currently include recorded pass/fail evidence from that earlier testing. Use the [Oakmere WhatsApp assistant test plan](../tests/oakmere-whatsapp-assistant-test-plan.md) to record results when revalidating a changed workflow or an import in another environment.

## Published workflow exports

- [WhatsApp AI Customer Assistant JSON](../projects/oakmere-whatsapp-ai-assistant/workflows/whatsapp-ai-customer-assistant.json)
- [Knowledge Base Ingestion (RAG) JSON](../projects/oakmere-whatsapp-ai-assistant/workflows/knowledge-base-ingestion-rag.json)
- [Telegram Error Alert JSON](../projects/oakmere-whatsapp-ai-assistant/workflows/error-alert-telegram.json)

These exports are inactive and have placeholders for environment-specific chat/phone IDs. They are not a substitute for importing into a clean test instance and validating each credential, node version, and expression.

## Suggested repository assets

- Sanitized, inactive n8n workflow export(s), if/when further versions are published
- SQL schema and indexes, including unique idempotency key
- Fictional sample catalogue and policy data
- Test matrix with actual pass/fail evidence
- Architecture diagram and redacted execution screenshots
- Setup guide and environment-variable/credential checklist

## Demo disclaimer

Oakmere Living is a fictional portfolio demonstration, not a claim of production deployment. Do not claim measured business outcomes unless independently verified.

## Setup, Credentials & Testing

This workflow is provided as an exported n8n JSON template. It is not guaranteed to run immediately after import.

### Before running the workflow

1. Import the JSON file into your n8n instance.
2. Configure the required credentials, API keys, and service connections.
3. Replace placeholder values with your own IDs, URLs, and configuration settings.
4. Review the nodes and adjust settings for your environment.
5. Test the workflow with sample data before using it in production.

### Important notes

- Credentials and API keys are not included in this export. You must configure your own credentials for the services used by the workflow.
- Some integrations may require API access, subscriptions, permissions, or additional setup.
- The exported workflow may require environment-specific changes before it works correctly.
- Importing this JSON does not automatically activate the workflow or guarantee successful execution.
- Test the workflow in your own n8n environment before using it in production.

The original workflow was built and tested in the author's configured environment. Your results may vary depending on your credentials, service configuration, and n8n setup.

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).
