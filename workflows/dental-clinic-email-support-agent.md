# Automated Dental Clinic Email Support Agent

## Business problem
A clinic inbox can receive repeated questions about opening hours, consultation fees, available services, emergency hours, and appointment booking. Responding to each message manually takes staff time, while an incorrect answer about clinic policy can confuse patients.

## Solution
I built an email workflow that watches Gmail for incoming messages, asks an AI agent to draft a polite response using the clinic information embedded in its prompt, and replies through Gmail. The prompt explicitly tells the agent not to invent information and gives a standard response when the request is outside the listed information.

## Business value
- Helps handle repetitive administrative email questions.
- Keeps routine answers consistent with the configured clinic information.
- Can use a fallback response for questions outside the configured clinic information.

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

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).

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

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).

