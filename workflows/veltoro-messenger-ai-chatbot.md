# VELTORO — Messenger AI Shopping Assistant

## Business problem
Customers shopping online often ask the same questions about product prices, SKU, materials, sizes, colors, fit, care instructions, and availability. If those questions wait for a human reply, customers may abandon the conversation; if a chatbot guesses, it can misrepresent the catalogue.

## Solution
I built a Facebook Messenger webhook flow for VELTORO that routes webhook verification and incoming messages, uses an AI agent to answer customer questions, and retrieves product details from a Supabase vector store. The agent is instructed to use catalogue information for product-specific answers and to say when the catalogue does not contain an answer.

## Business value
- Offers a conversational entry point for product questions on Messenger.
- Can reduce repetitive pre-purchase support questions.
- Keeps catalogue-specific answers grounded in indexed product information.
- Avoids intentionally inventing details when the retrieved catalogue has no answer.

## How it works
1. Meta sends webhook verification or message events to the n8n webhook.
2. The verification branch returns the expected challenge; message events are acknowledged.
3. The AI agent searches the product catalogue through Supabase retrieval.
4. The generated reply is sent back through the configured Facebook Graph API request.

## Intended use
An online retailer that wants to answer common product questions on its Facebook Page.

## Setup and limitations
Configure Meta webhook settings, page access token, verify token, app permissions, Supabase table/index, and embedding model. Test webhook verification and real message delivery using Meta's test tools before production. Answers are limited by catalogue completeness and retrieval quality; the workflow does not prove stock availability unless that information is present and current in the indexed data.

## How I would measure success
Track first-response time, questions resolved without staff help, unanswered catalogue queries, correction rate, and conversion from product enquiry to purchase. These are suggested measures, not claimed outcomes.

## Testing and export
I live-tested this workflow in my own n8n environment. Replace the placeholder Meta values and configure the catalogue connection when importing elsewhere.

[Open workflow JSON](veltoro-messenger-ai-chatbot.json)
