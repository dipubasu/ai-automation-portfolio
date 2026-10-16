# VELTORO — Product Catalogue Knowledge Base Ingestion

## Business problem
A shopping assistant cannot reliably answer catalogue questions unless product information is extracted and made searchable. If the source catalogue changes but the search index is not refreshed, customers may receive incomplete or outdated answers.

## Solution
I built a manual ingestion workflow that downloads VELTORO's product-catalogue PDF from Google Drive, extracts its text, prepares the content, creates Google Gemini embeddings, and inserts the documents into a Supabase vector store used by the Messenger assistant.

## Business value
- Turns a catalogue document into content that an AI assistant can search.
- Separates catalogue maintenance from live customer conversations.
- Gives the team a repeatable process for refreshing the assistant's knowledge when catalogue information changes.

## How it works
1. An operator starts the ingestion workflow.
2. The PDF is downloaded from Google Drive and its text is extracted.
3. Extracted content is prepared for document loading.
4. Gemini embeddings are created and the content is inserted into Supabase.

## Intended use
An internal setup/update workflow paired with the VELTORO Messenger AI Shopping Assistant.

## Setup and limitations
Configure the correct PDF, Google Drive credentials, Supabase credentials/table, and embedding model. Check that the text extraction includes relevant product details and that the retrieval workflow uses compatible embedding settings. Repeated inserts may leave duplicate or stale content unless the index refresh process handles old records.

## How I would measure success
Check product coverage, extraction accuracy, retrieval relevance for a set of sample customer questions, and how quickly catalogue updates become searchable. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. It is a manually run maintenance process and may be inactive when no catalogue update is required.

[Open workflow JSON](veltoro-rag-knowledge-base-setup.json)

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
