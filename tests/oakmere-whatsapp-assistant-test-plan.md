# Oakmere WhatsApp AI Assistant — Test Plan

This checklist supports repeatable validation of the Oakmere Living portfolio workflow. I built and tested the workflow in my configured environment before publishing the portfolio entry. Results below are self-reported from my own testing in my configured environment; this repository update did not rerun the workflow.

## How to use this checklist

- Test in a non-production environment with fictional data and test credentials.
- Record the date, n8n version, workflow revision, environment, and result for each test run.
- Mark a case Pass or Fail only after observing the execution; otherwise leave it Not tested.
- Do not include access tokens, personal customer data, or private order details in screenshots or logs.
- When changing the workflow, rerun relevant cases before publishing the updated export.

## Test matrix

| ID | Scenario | Expected result | Result |
|---|---|---|---|
| T01 | Product questions (specs, care, warranty) | Answer matches the knowledge base | Pass |
| T02 | Shipping zones, rates and delivery time | Correct zone rates and times | Pass |
| T03 | Returns, refunds and cancellation policy | Answer matches the policy | Pass |
| T04 | Payments, promo code and loyalty | Answer matches the policy | Not tested |
| T05 | Stock lookup | Response matches live stock data | Pass |
| T06 | Order status with correct order number and email | Status and tracking shown | Pass |
| T07 | Order status with wrong email | Refused; no order details disclosed | Pass |
| T08 | Tracking lookup after verification | Tracking shown only after verification | Pass |
| T09 | Angry customer escalation to human | Support ticket created; human handover | Pass |
| T10 | Refund over USD 200 escalation | Support ticket created; human handover | Pass |
| T11 | Lost or damaged parcel ticket | Support ticket created | Pass |
| T12 | Out-of-scope request (custom order, press) | Honest answer or human handover | Pass |
| T13 | Prompt-injection attempt | Refused | Pass |
| T14 | Duplicate message / duplicate webhook | Handled once, no duplicate reply | Pass |
| T15 | Voice note transcription | Transcribed and answered | Pass |
| T16 | Voice note failure handling | Safe fallback response | Pass |
| T17 | Bangla-language query | Reply in Bangla | Pass |
| T18 | Provider outage / LLM fallback | Fallback model answers | Pass |
| T19 | Terminal error alert to Telegram | Owner alert sent | Pass |

18 of 19 listed scenarios passed in my own testing; 1 (payments, promo code and loyalty) was not tested. Results are self-reported from my configured environment.

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
