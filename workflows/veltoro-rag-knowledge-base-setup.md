# Case Study: Veltoro — RAG Knowledge Base Setup

## Overview
A manual ingestion workflow that extracts text from a PDF and indexes it in Supabase for retrieval by a separate assistant workflow.

## Workflow design
The export includes a manual trigger, Google Drive download, Extract From File, document loader, Google Gemini embeddings, field preparation, and Supabase vector store nodes.

## Integrations
Google Drive, n8n document processing, Google Gemini embeddings, and Supabase vector storage.

## Why this design
Keeping document ingestion separate from customer-facing chat lets the knowledge base be updated and checked independently of conversations.

## Configuration and boundaries
Choose the correct source PDF, ensure extraction produces usable text, configure embedding dimensions/model consistently with the retrieval workflow, and verify the Supabase table/index settings. Re-run ingestion when source documents change and manage stale chunks appropriately.

## Testing and status
Live-tested by the author in their configured n8n environment. The export is inactive, which can be appropriate for an ingestion job that runs only when the knowledge base is updated.
