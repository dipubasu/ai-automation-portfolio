# Oakmere WhatsApp AI Assistant — Test Plan

This checklist supports repeatable validation of the Oakmere Living portfolio workflow. I built and tested the workflow in my configured environment before publishing the portfolio entry. This file does not claim that this repository update reran the workflow or that the cases below have recorded pass/fail evidence.

## How to use this checklist

- Test in a non-production environment with fictional data and test credentials.
- Record the date, n8n version, workflow revision, environment, and result for each test run.
- Mark a case Pass or Fail only after observing the execution; otherwise leave it Not run.
- Do not include access tokens, personal customer data, or private order details in screenshots or logs.
- When changing the workflow, rerun relevant cases before publishing the updated export.

## Test matrix

| ID | Scenario | Expected result | Result |
|---|---|---|---|
| T01 | Product question with matching knowledge-base evidence | Reply reflects retrieved catalogue information and avoids unsupported details | Not run |
| T02 | Shipping, returns, or store-policy question | Reply stays within configured policy content | Not run |
| T03 | Missing or conflicting policy evidence | Assistant escalates or asks for clarification rather than guessing | Not run |
| T04 | Supported WhatsApp voice note | Audio is transcribed and follows normal routing | Not run |
| T05 | Voice-note processing failure | Safe fallback or human handoff; no unhandled failure | Not run |
| T06 | Duplicate delivery of the same WhatsApp message ID | No duplicate replies, tickets, or notifications | Not run |
| T07 | Stock lookup for a known fictional SKU | Response matches configured inventory data | Not run |
| T08 | Order request without required verification | No order details are disclosed | Not run |
| T09 | Order request after successful verification | Only permitted status fields are returned | Not run |
| T10 | Support-ticket creation and retry | Unique ticket ID; retry does not create an unintended duplicate | Not run |
| T11 | Primary LLM timeout or retryable error | Bounded fallback runs; only one customer reply is sent | Not run |
| T12 | Primary and fallback LLM unavailable | Safe customer response and sanitized operator alert | Not run |
| T13 | Telegram operator notification | Correct destination receives alert without secrets or unnecessary customer data | Not run |
| T14 | Malformed webhook or invalid payload | Request is handled safely without unintended side effects | Not run |
| T15 | Unsupported formatting or excessive output length | Final WhatsApp message is validated and within configured limits | Not run |
| T16 | Database/API permission failure | Safe failure handling; private data is not exposed and retries are bounded | Not run |

## Run record

Copy this section for each actual test session.

- **Date/time:**
- **Workflow revision:**
- **n8n version:**
- **Environment:**
- **Tester:**
- **Cases run:**
- **Failures and execution references (redacted):**
- **Follow-up fixes:**

## Publishing checklist

- [ ] Export the workflow from the tested environment.
- [ ] Remove credential objects, tokens, private identifiers, customer data, and execution payloads.
- [ ] Replace environment-specific IDs with clear placeholders.
- [ ] Confirm the exported workflow is inactive by default.
- [ ] Import the sanitized export into a clean test instance and validate setup instructions.
- [ ] Record actual test outcomes; do not present unrun cases as passed.
- [ ] Verify README and case-study links before publishing.
