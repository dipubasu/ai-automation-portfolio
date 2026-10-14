# Automated Dental Clinic Email Support Agent

## Business problem
A clinic inbox can receive repeated questions about opening hours, consultation fees, available services, emergency hours, and appointment booking. Responding to each message manually takes staff time, while an incorrect answer about clinic policy can confuse patients.

## Solution
I built an email workflow that watches Gmail for incoming messages, asks an AI agent to draft a polite response using the clinic information embedded in its prompt, and replies through Gmail. The prompt explicitly tells the agent not to invent information and gives a standard response when the request is outside the listed information.

## Business value
- Helps handle repetitive administrative email questions.
- Keeps routine answers consistent with the configured clinic information.
- Provides a clear response path for questions that the configured information cannot answer.

## How it works
1. Gmail checks for incoming messages on the configured polling schedule.
2. The AI agent interprets the email snippet and drafts a response.
3. The reply is sent to the original email thread through Gmail.

## Intended use
A small clinic or service desk handling predictable, non-clinical administrative questions.

## Important boundaries
The current workflow sends the generated reply automatically; the exported JSON does not include a human approval step. It is not a diagnostic or medical-advice system. Before use, replace the example clinic details and phone number, review every policy in the prompt, and consider adding human approval for sensitive or ambiguous messages. The prompt's instruction not to invent information helps, but cannot guarantee every model response is correct.

## How I would measure success
Measure response time, proportion of routine questions handled correctly, staff corrections, and messages that should have been escalated. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. Configure Gmail credentials and verify the clinic-specific prompt before adapting it.

[Open workflow JSON](dental-clinic-email-support-agent.json)
