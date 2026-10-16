# EstateBot — Real Estate Assistant, Property Search and Lead Qualification

## Business problem
Property enquiries often arrive as unstructured conversations. Agents need to answer property questions accurately, understand a buyer's requirements, and collect enough details for follow-up. Asking every question at once can create friction, and answering property questions from memory risks inaccurate claims.

## Solution
I built a Telegram-based real-estate assistant that searches a property knowledge base for property-related questions and qualifies interested buyers through a step-by-step conversation. It collects name, phone, budget, location, property type, and buying timeline, then asks the user to confirm the summary before marking the lead complete. Completed details are logged to Google Sheets. The current node structure does not show a separate real-time agent notification step.

## Business value
- Gives prospective buyers a conversational first point of contact.
- Grounds property answers in the configured property database rather than model memory.
- Collects a more structured lead record for a human sales agent.
- Keeps conversational context for multi-turn enquiries.
- Supports exact property-ID lookup as well as broader semantic property searches.

## How it works
1. A user messages the Telegram bot.
2. The agent answers property questions using the Supabase retrieval tool or exact-ID lookup.
3. For qualification, it asks for one requirement at a time and gathers the buyer's details.
4. After the buyer confirms the summary, the workflow extracts the structured lead.
5. The lead is appended to Google Sheets and the user receives a confirmation message.

## Intended use
Real-estate agencies that want to handle first-line property questions and collect structured buyer enquiries before a human follow-up.

## Setup and limitations
Configure Telegram, model, Supabase, PostgreSQL lookup, and Google Sheets credentials; populate the property database and confirm the expected data format. The workflow collects personal contact information, so access to logs and sheets should be restricted. The confirmation message says an agent will contact the buyer within 24 hours; only use that promise if the business can actually meet it.

## How I would measure success
Track completed lead profiles, drop-off during qualification, property questions answered from retrieved records, human follow-up time, and invalid or incomplete lead records. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. Replace placeholder sheet IDs and environment-specific credentials before importing elsewhere.

[Open workflow JSON](estatebot-ai-agent-memory-supabase-rag.json)

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

