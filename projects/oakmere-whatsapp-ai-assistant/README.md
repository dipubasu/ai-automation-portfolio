# Oakmere Living — WhatsApp AI Customer Support Assistant

An n8n-based portfolio project for multilingual, knowledge-grounded WhatsApp support for a fictional home and furniture retailer.

## Overview

I built and tested this workflow in my configured environment before publishing this portfolio entry. It is designed to answer product, delivery, returns, and store-policy questions from a curated knowledge base; process supported voice notes; look up inventory and verified order status; create support tickets; and escalate uncertain or sensitive cases to a human operator.

**Testing status:** I built and tested this workflow myself in my configured environment. The evaluation summary and per-category result fields are provided in the **Evaluation results** section below. I have not filled in counts that are not available in this README; add the actual counts from my test run rather than treating placeholders as results. The public repository includes sanitized, inactive n8n workflow JSON exports for the assistant, knowledge-base ingestion, and Telegram error alerts. These are publication-safe starting points, not a hosted deployment; configure your own credentials and IDs before importing or running them.

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

## What the assistant handles vs. escalates

| Group | What it handles |
|---|---|
| **Answered from the knowledge base** | Questions about the curated knowledge base: 24 products, shipping zones and rates, returns, refunds, warranty, payment methods, promotions, FAQs, and assistant guidelines. |
| **Answered from live database lookup** | Current product stock, order status, and tracking information. Order details are shared only when both the order number and the email address match the database. |
| **Escalated to a human with a support ticket** | A customer asks for a person, is angry or complains; a refund or compensation exceeds USD 200 or a refund is disputed; a parcel is lost, damaged, or stuck in customs; there is a payment problem or suspected fraud; legal, chargeback, or media issues are mentioned; a request is outside the knowledge base (such as custom orders, press, or partnerships); or the same issue remains unresolved after two attempts. |

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

See the [Oakmere WhatsApp assistant test plan](../../tests/oakmere-whatsapp-assistant-test-plan.md). I tested the workflow myself in my configured environment. The checklist describes the scenarios intended for evaluation; actual test counts and outcomes are summarized in the **Evaluation results** section below.

## Evaluation results

I tested the workflow in my configured environment. The test set covers categories such as product questions, shipping, returns policy, stock checks, order-status requests with correct verification, order-status requests with the wrong email, angry customers, out-of-scope requests, prompt-injection attempts, duplicate messages, voice notes, and Bangla-language queries.

Replace the placeholders below with the actual counts from my test run. Do not treat placeholders as measured results.

| Category | Questions tested | Resolved without handover | Correctly escalated | Incorrect or failed |
|---|---:|---:|---:|---:|
| Product questions | [count] | [count] | [count] | [count] |
| Shipping | [count] | [count] | [count] | [count] |
| Returns policy | [count] | [count] | [count] | [count] |
| Stock check | [count] | [count] | [count] | [count] |
| Order status — correct verification | [count] | [count] | [count] | [count] |
| Order status — wrong email | [count] | [count] | [count] | [count] |
| Angry customer / complaint | [count] | [count] | [count] | [count] |
| Out-of-scope request | [count] | [count] | [count] | [count] |
| Prompt injection attempt | [count] | [count] | [count] | [count] |
| Duplicate message | [count] | [count] | [count] | [count] |
| Voice note | [count] | [count] | [count] | [count] |
| Bangla-language query | [count] | [count] | [count] | [count] |
| **Total** | **[N]** | **[count]** | **[count]** | **[count]** |

- **Resolved without human handover:** [X]% of [N]
- **Correct escalation rate on cases that should escalate:** [Y]%

**Results to be added after running the test set** with the final counts, including the total number of questions tested and the correct outcomes for each category. No per-category counts or success rates are claimed until those values are filled in.

## Limitations

This is a portfolio demonstration for a fictional store using demo data, not a hosted service or production deployment. Evaluation results are based on my own test set, and the impact figures below are assumptions rather than measured outcomes. The exported workflows are inactive and require your own credentials and environment-specific configuration before use.

## Estimated impact (assumption-based)

For a hypothetical high-volume store, my assumption is that around 80% of support work may be routine and that automating some of this work could save approximately 15–20 hours of manual work per week. This is an estimate for a fictional store—not a measured result or a production outcome.

**Transparent calculation:**

Hours saved per week ≈ (messages per day × 7 × share of routine queries × average minutes per query) ÷ 60.

To calculate an estimate, supply these assumptions:
- **Messages per day:** [messages per day]
- **Share of routine queries:** [share of routine queries]
- **Average minutes per query:** [average minutes per query]

The 80% routine-work share and 15–20 hours per week are my current assumptions, not measured results. The estimate will remain assumption-based until the inputs are supplied and the calculation is completed.

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
