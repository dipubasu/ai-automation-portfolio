# Case Study: Veltoro — RAG Email Customer Support with Human Approval

## Overview
An email support flow that drafts knowledge-grounded replies and places a human approval step before sending them.

## Workflow design
The exported workflow includes a Gmail trigger, email-content cleaning, an AI agent, Supabase vector-store question answering, Groq chat model, Google Gemini embeddings, an approval request, an approval condition, Gmail send/reply action, manual-review flagging, and marking the message as read.

## Integrations
Gmail, Groq, Supabase vector store, Google Gemini embeddings, and n8n conditional routing.

## Why this design
Retrieval helps the agent reference the support knowledge base. Human approval adds a review checkpoint before an AI-drafted message is sent to a customer.

## Configuration and boundaries
Connect the Gmail and model/vector-store credentials, populate and maintain the knowledge base, and verify that approval notifications and branch conditions behave as intended. Do not send real customer replies until test cases cover both approval and rejection paths.

## Testing and status
Live-tested by the author in their configured n8n environment. No claim is made that every future reply will be correct; knowledge quality and review policy remain important.
