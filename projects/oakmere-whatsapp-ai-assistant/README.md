# Oakmere Living — WhatsApp AI Customer Support Assistant

An n8n-based portfolio project for multilingual, knowledge-grounded WhatsApp customer support for a fictional home and furniture retailer.

## Project overview

I built and tested the full workflow in my own configured environment. The assistant is designed to answer product, delivery, returns, and store-policy questions using a curated knowledge base, handle supported voice notes, look up inventory and verified order status, create support tickets, and hand uncertain or sensitive cases to a human operator.

**Testing status:** Full workflow tested by the project author in their configured environment. This describes my own test setup; it does not mean the public sanitized exports are deployed as a hosted service or will run in another environment without configuration.

## Architecture

WhatsApp Cloud API → n8n webhook and message normalization → duplicate-message guard → text/voice processing → intent and policy routing → Supabase retrieval or approved data lookup → primary LLM with configured fallback → output validation → WhatsApp response.

Telegram is used for operator alerts. The design includes safe failure responses, idempotency, order-verification gates, and human escalation.

## Components

- **n8n workflows:** customer assistant, knowledge-base ingestion/RAG, and Telegram error alert.
- **Knowledge base:** Oakmere Living catalogue and policy reference PDF.
- **Supabase:** vector retrieval and structured data lookups, with least-privilege access and row-level security.
- **LLMs:** primary Groq model and configurable OpenRouter fallback.
- **Verification SQL:** price consistency and product-option count checks.
- **Documentation:** architecture, setup, credential mapping, security/privacy, and conversation scenarios.

## Key safeguards

- Do not disclose order status unless the required customer verification checks pass.
- Ground policy answers in retrieved evidence; escalate when evidence is missing or conflicting.
- Persist WhatsApp message IDs with a unique constraint to prevent duplicate side effects.
- Keep tokens and provider credentials in n8n Credentials; never commit secrets.
- Bound retries and fallback attempts, validate generated output, and provide a safe terminal-failure path.
- Alert operators with sanitized diagnostics rather than access tokens or unnecessary customer data.
- Treat the store and customer scenarios as fictional demo data.

## Setup

1. Review the workflow and architecture documentation before importing.
2. Configure Meta WhatsApp Cloud API, n8n, Supabase, Groq/OpenRouter, Google Drive (if used for ingestion), and Telegram credentials.
3. Replace environment-specific IDs and placeholders with your own values.
4. Apply the database schema, indexes, access policies, and verification SQL in a test environment.
5. Ingest and deduplicate the knowledge base, then run known-answer retrieval checks.
6. Test duplicate webhooks, voice-note failures, unavailable LLM providers, unverified order requests, escalation, and terminal errors.
7. Export only sanitized inactive workflows when publishing updates.

## Existing portfolio documentation

- [Oakmere workflow design and production-readiness checklist](../../workflows/oakmere-whatsapp-ai-customer-support.md)
- [Portfolio workflow library](../../workflows/README.md)

## Validation and limitations

The full workflow has been tested by me in my configured environment. The public repository is documentation and sanitized workflow material, not a hosted deployment. Anyone importing it into another environment must configure their own credentials, IDs, permissions, database schema, node versions, and API settings. No production deployment or quantified business outcome is claimed here.

## License

MIT — see the repository root [LICENSE](../../LICENSE).
