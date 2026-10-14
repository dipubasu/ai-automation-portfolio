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
