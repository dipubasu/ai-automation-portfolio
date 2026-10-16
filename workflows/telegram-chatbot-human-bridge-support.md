# DPTECH — Telegram Support Assistant with Human Handoff

## Business problem
A digital-services business may receive support questions in Bangla, English, or mixed Banglish. A small team can struggle to respond consistently outside office hours, and questions about custom pricing or consultations often need a person rather than an automated answer.

## Solution
I built a Telegram support flow that routes incoming messages, uses an AI assistant grounded in configured DPTECH service information, and can mark conversations for human handoff. The workflow also includes a file-retrieval and audio-analysis path so voice messages can be interpreted before the assistant responds.

## Business value
- Gives customers a consistent first response in the language they use.
- Handles common service and package questions using configured business information.
- Signals when a question needs a human instead of inventing an answer.
- Supports text and voice-message interactions in the same channel.

## How it works
1. Telegram receives a customer message.
2. Routing logic selects the relevant message path.
3. Text is prepared for the AI agent, or an audio message is retrieved and analyzed first.
4. The agent generates a response and adds a handoff marker for cases configured to need a person.
5. The workflow sends the response and forwards a support request through the configured Telegram route.

## Intended use
A digital agency or service business that wants to automate common Telegram enquiries while keeping human support available for exceptions.

## Setup and limitations
Configure Telegram credentials, chat IDs, AI model credentials, and routing conditions. Review every Switch/IF branch and test both text and audio paths. The JSON includes a human-handoff marker and notification path; the real-world handoff still depends on the receiving team's process and availability.

## How I would measure success
Track first-response time, language-related corrections, handoff frequency, unresolved conversations, and staff workload. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. Configure credentials and destination IDs when importing elsewhere.

[Open workflow JSON](telegram-chatbot-human-bridge-support.json)

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

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).
