# Case Study: Veltoro — Messenger AI Shopping Assistant

## Overview
A webhook-based Messenger assistant that uses an AI agent and Supabase vector retrieval to answer product-related questions.

## Workflow design
The export includes a webhook, webhook acknowledgement, IF routing, AI Agent, Groq chat model, HTTP Request node, Supabase vector store, and Google Gemini embeddings.

## Integrations
Webhook/API handling, Groq, Supabase vector retrieval, Google Gemini embeddings, and the configured Messenger/Graph API requests.

## Why this design
Retrieval can ground answers in the product catalogue, while webhook acknowledgement and conditional routing support the messaging integration flow.

## Configuration and boundaries
Configure the Meta app/webhook settings, access tokens, Supabase index, embedding model, and product-catalogue content. Test signature/verification handling and error responses in the target deployment; the export alone does not prove that a public Messenger endpoint is deployed.

## Testing and status
Live-tested by the author in their configured n8n environment. Product-answer quality depends on catalogue coverage and the retrieval configuration.
