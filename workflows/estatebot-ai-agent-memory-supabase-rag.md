# Case Study: EstateBot — AI Agent, Memory and Supabase RAG

## Overview
A Telegram-facing real-estate assistant that combines conversation memory with retrieval from a Supabase vector store and records completed lead details.

## Workflow design
The export includes Telegram trigger and response nodes, field preparation, an AI agent, lead-completion branching, lead-data extraction, Google Sheets logging, OpenRouter/Groq model nodes, a vector-store question-answer tool, Supabase vector storage, Google Gemini embeddings, short-term chat memory, and a property-ID lookup tool.

## Integrations
Telegram, n8n AI Agent, OpenRouter and Groq model nodes, Supabase vector store, Google Gemini embeddings, Google Sheets, and a PostgreSQL lookup tool.

## Why this design
RAG can ground property-related responses in indexed source material, while memory supports multi-turn conversations. A completion branch provides a point to capture structured buyer requirements.

## Configuration and boundaries
Configure Telegram, model, Supabase, Google Sheets, and database credentials. Keep the indexed property data current and verify that the lookup tool's schema and permissions match the database.

## Testing and status
Live-tested by the author in their configured n8n environment. No lead-conversion or response-accuracy metrics are claimed in this case study.


## Workflow export

[**Open the n8n workflow JSON**](estatebot-ai-agent-memory-supabase-rag.json)
