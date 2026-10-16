# EstateBot — Property Knowledge Base Ingestion

## Business problem
A real-estate assistant can only answer from a property knowledge base if the underlying documents have been loaded into a searchable store. Manually copying property details into a database is time-consuming and can leave the assistant using incomplete or outdated information.

## Solution
This workflow handles the ingestion step for EstateBot. It downloads a property knowledge-base PDF from Google Drive, extracts its text, splits the content into smaller chunks, creates embeddings with Google Gemini, and inserts the resulting documents into a Supabase vector store.

## Business value
- Creates a repeatable way to prepare property documents for AI search.
- Separates knowledge-base updates from the customer-facing Telegram conversation.
- Makes it easier to refresh indexed information when source documents change.

## How it works
1. An operator starts a manual run.
2. The workflow downloads the configured PDF from Google Drive.
3. Text is extracted and split into chunks with overlap.
4. Gemini embeddings are generated and the chunks are stored in Supabase for retrieval.

## Intended use
An internal content-preparation workflow for a real-estate team maintaining the information used by its AI assistant.

## Setup and limitations
Confirm that the source PDF is current, text extraction is complete, the Supabase table and matching function are configured, and the embedding model matches the retrieval setup. Re-ingestion can create repeated or stale chunks unless the data-refresh strategy handles old records; check how updates and deletions are managed before running repeatedly.

## How I would measure success
Check document coverage, extraction quality, retrieval relevance for a test set of property questions, and how quickly updated documents become searchable. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. It is a manually run ingestion job and may be left inactive between knowledge-base updates.

[Open workflow JSON](estatebot-lead-qualification-server.json)

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

- Credentials and API keys are not included in this export. Configure your own credentials for the services used by the workflow.
- Some integrations may require API access, subscriptions, permissions, or additional setup.
- The exported workflow may require environment-specific changes before it works correctly.
- Importing this JSON does not automatically activate the workflow or guarantee successful execution.
- Test the workflow in your own n8n environment before using it in production.


## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).
