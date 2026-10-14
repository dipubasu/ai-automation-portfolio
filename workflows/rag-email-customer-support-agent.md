# Veltoro — RAG Email Customer Support with Human Approval

## Business problem
An online fashion retailer may receive repetitive questions about shipping, returns, payments, sizing, warranty, account help, and escalation. Replying manually to every email can slow the queue; allowing an AI to send policy answers without review risks incorrect or off-brand commitments.

## Solution
I built an email support flow that cleans the incoming email, searches Veltoro's policy knowledge base, and drafts a response grounded in the retrieved content. Instead of sending immediately, it requests human approval. Approved replies are sent through Gmail; rejected or unapproved cases are flagged for manual review.

## Business value
- Reduces the time support staff spend drafting routine responses.
- Keeps policy answers tied to the configured knowledge base.
- Preserves a human checkpoint before a customer receives the AI-written reply.
- Provides a route for messages that need individual judgement.

## How it works
1. Gmail detects a new customer email.
2. The workflow extracts and cleans the email content.
3. The AI agent searches the Supabase policy knowledge base and drafts a ready-to-review response.
4. A human receives an approval request.
5. Approved messages are sent; rejected messages are flagged for manual review.

## Intended use
Customer support teams that want AI assistance with email drafting but require a person to approve outbound replies.

## Setup and limitations
Configure Gmail, Groq, Gemini embeddings, and Supabase. Populate the knowledge base with current company policies and test both approval and rejection paths. Retrieval quality depends on the indexed content; the human reviewer remains responsible for checking accuracy, tone, and exceptions.

## How I would measure success
Measure draft preparation time, approval rate, common edits, policy accuracy, and time to resolution. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. Credentials and the knowledge-base index must be configured for the destination environment.

[Open workflow JSON](rag-email-customer-support-agent.json)
