# Case Study: EstateBot Lead Qualification Server — Knowledge Ingestion

## Overview
Despite the filename, this exported workflow is the document-ingestion side of the EstateBot setup: it loads source content and prepares it for retrieval, rather than acting as the Telegram conversation flow.

## Workflow design
The export includes a manual trigger, Google Drive node, Extract From File, recursive text splitter, default data loader, Google Gemini embeddings, and Supabase vector store.

## Integrations
Google Drive, n8n document processing and text splitting, Google Gemini embeddings, and Supabase vector storage.

## Why this design
Separating ingestion from the chat agent lets source documents be indexed independently before the conversational agent retrieves relevant chunks.

## Configuration and boundaries
Configure the source document, Google Drive permissions, embedding model, Supabase credentials and collection/table settings. Re-index when source content changes, and verify the target schema before ingestion.

## Testing and status
Live-tested by the author in their configured n8n environment. The export is saved inactive; that may be intentional if ingestion is run only when the knowledge base needs updating.


## Workflow export

[**Open the n8n workflow JSON**](estatebot-lead-qualification-server.json)
