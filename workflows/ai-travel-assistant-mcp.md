# AI Travel Assistant — MCP-Based Multi-Tool Agent

## Business problem
Trip planning often means switching between weather sites, hotel and restaurant searches, attraction listings, currency tools, and notes about personal preferences. A generic chatbot may also give stale or invented answers when it relies only on model memory.

## Solution
I built a chat-based travel assistant that routes factual travel questions to tools exposed through an MCP server. It is instructed to geocode a destination before using location-based tools, retrieve current weather or place information from the relevant tool, and check or save preferences such as budget, hotel style, transport, diet, and activities.

## Business value
- Brings several travel lookups into one conversational entry point.
- Can reuse saved preferences instead of asking the traveller to repeat them every time.
- Encourages tool-grounded answers rather than relying on model memory for current travel facts.
- Can combine results into a more practical recommendation.

## How it works
1. The traveller asks a question in the chat interface.
2. The agent checks saved preferences for that chat session.
3. It calls the relevant MCP tools, using geocoding first for location-dependent searches.
4. It combines returned information and explains when a tool returns no data.
5. New preferences can be saved for future turns.

## Intended use
A travel-planning assistant prototype for travellers who want one place to ask about destination logistics and preferences.

## Setup and limitations
Configure the Gemini model, MCP client endpoint, exposed travel tools, and n8n data table. Availability and freshness depend on the external APIs behind the MCP server; a tool call is not a guarantee of booking availability or a confirmed reservation. Verify prices, opening hours, and bookings with the provider before making decisions.

## How I would measure success
Evaluate whether tool calls succeed, how often recommendations contain source-backed details, whether users repeat preferences, and how many answers require correction. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. Replace environment-specific MCP endpoints, credentials, and table references when importing elsewhere.

[Open workflow JSON](ai-travel-assistant-mcp.json)

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code, workflow, or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).

## Setup, Credentials & Testing

This workflow is provided as an exported n8n JSON template. It is not guaranteed to run immediately after import.

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


## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).
