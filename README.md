# Dipu Basu — AI Automation Developer Portfolio

n8n Automation Engineer | AI Agent & RAG Developer

**Contact:** dpbasu32@gmail.com | +880 1876-233071 | [LinkedIn](https://linkedin.com/in/dipubasu) | Bangladesh — Remote / Worldwide

## About
AI Automation Developer specializing in n8n workflows, RAG systems, AI agents, and API integrations. I build automated systems for lead management, customer support, knowledge retrieval, and business operations using n8n, OpenAI, Groq, Gemini, Supabase, and REST APIs — with a focus on reliable workflow design, error handling, and maintainable integrations.

> **Security note:** Workflow exports in this repository should use placeholders for secrets and private identifiers. Import into your own n8n instance and connect your own credentials before running. Never commit API keys, tokens, OAuth secrets, or real customer data.

## Core Skills

- **Automation:** n8n · Make.com · Workflow Automation · Webhooks · MCP
- **AI & LLM:** OpenAI · Gemini · Groq / Llama · RAG (Retrieval-Augmented Generation) · Embeddings · Prompt Engineering · AI Agents · Cloudflare AI (Flux)
- **Voice & Audio:** ElevenLabs Conversational AI · ElevenLabs TTS · Voice AI Receptionist · Telegram Voice Message Understanding
- **Integrations:** HubSpot · Facebook Graph API · Telegram API · Gmail OAuth2 · WhatsApp · REST APIs · Shotstack · YouTube API · Google Drive API
- **Data & Infrastructure:** Supabase Vector DB · Google Sheets · Google Drive · API Authentication · Error Handling · Secure Credential Management

## Workflow Library

The workflows in this portfolio have been live-tested by me in my n8n environment. The `workflows/` directory contains their importable JSON exports; these files are not hosted services, and a sanitized export may still need your own credentials, API access, IDs, and environment-specific configuration to run in another instance. Some workflows may be intentionally left inactive when they are not currently needed.

- **CRM and lead intake:** webhook-based lead validation and HubSpot synchronization.
- **AI agents and RAG:** real-estate lead qualification, product-catalogue Q&A, and knowledge-grounded support flows.
- **Customer support:** email drafting with human approval, clinic email support, and Telegram-to-human handoff.
- **Content automation:** multi-scene YouTube video generation and publishing pipeline.
- **Tool-enabled travel assistant:** MCP-based travel tools, including discovery and utility integrations.
- **Data quality:** Excel/XLSX cleaning, validation, duplicate classification, report export, and Google Sheets run summaries.

See each linked project entry for its scope, integrations, setup notes, and limitations. Live testing refers to my configured environment; review credentials, IDs, permissions, and destination settings when importing into a different environment. Never commit credentials or real customer data.

## Projects

### 1. [Automated Lead Management Pipeline](workflows/lead-intake-hubspot-crm-sync.md) — n8n + HubSpot CRM Automation
Captures leads via webhook, validates submitted data, creates or updates HubSpot CRM records, and conditionally routes high-value opportunities. Includes Google Sheets logging and Telegram alerts for high-value leads and failed HubSpot syncs.
**Tech:** n8n · HubSpot · Webhooks · Telegram · Google Sheets · REST APIs

### 2. [EstateBot — AI Real Estate Lead Qualification Agent](workflows/estatebot-ai-agent-memory-supabase-rag.md)
A Telegram AI agent that answers property questions through Supabase retrieval and a property-ID lookup, then collects buyer requirements step by step and logs confirmed lead details to Google Sheets.
**Tech:** n8n · Telegram API · Groq / Llama · Supabase Vector DB · RAG · Google Sheets
Related: [EstateBot AI Agent + Memory + Supabase RAG](workflows/estatebot-ai-agent-memory-supabase-rag.json)

### 3. [Veltoro Messenger Assistant — AI Shopping Support](workflows/veltoro-messenger-ai-chatbot.md)
A Facebook Messenger webhook assistant that retrieves product information from a Supabase vector store and generates catalogue-grounded answers to customer questions.
**Tech:** n8n · Facebook Graph API · Supabase · Google Gemini Embeddings · Groq / Llama · RAG
Related: [Veltoro RAG Knowledge Base Setup](workflows/veltoro-rag-knowledge-base-setup.json)

### 4. [Veltoro Email Support — RAG with Human Approval](workflows/rag-email-customer-support-agent.md)
Detects unread customer emails via Gmail, cleans quoted replies/signatures, and uses a RAG agent (Groq, Supabase Vector Store, Gemini Embeddings) to draft a policy-grounded reply. A human reviews the draft before it is sent; rejected messages are flagged for manual review.
**Tech:** n8n · Gmail API · Groq / Llama · Supabase Vector DB · Google Gemini Embeddings · RAG · Human-in-the-Loop Approval

### 5. [Automated Dental Clinic Support Agent](workflows/dental-clinic-email-support-agent.md)
An AI email assistant that reads incoming clinic emails, uses clinic information configured in its prompt to draft a reply, and sends the response through Gmail. The exported workflow does not include a human approval step.
**Tech:** n8n · Gmail API · Groq / Llama

### 6. [Telegram Chatbot + Human Bridge Support](workflows/telegram-chatbot-human-bridge-support.md)
Multilingual (Bangla, English, Banglish) Telegram support assistant with conversation memory, voice-message understanding, and seamless escalation/hand-off to a human agent when needed.
**Tech:** n8n · Groq / Llama · Google Gemini · Telegram API

### 7. [AI YouTube Video Automation — Multi-Scene Pipeline](workflows/youtube-automation-topic-to-video.md)
An end-to-end pipeline that turns a topic into video metadata, a script, four scene prompts, generated images and voiceover, then renders a vertical video through Shotstack and uploads it to YouTube. The exported workflow sets upload privacy to private for review.
**Tech:** n8n · OpenAI API · Cloudflare AI (Flux) · ElevenLabs TTS · Shotstack API · YouTube API

### 8. [AI Travel Assistant — MCP-Based Multi-Tool Agent](workflows/ai-travel-assistant-mcp.md)
An MCP-based conversational agent that coordinates multiple tools for hotel search, restaurant discovery, live weather information, and currency conversion.
**Tech:** n8n · MCP Server/Client · Groq / Llama · Geoapify · Open-Meteo
Related: [Travel MCP Server](workflows/travel-mcp-server.json)

### 9. [Excel Data Cleaning Automation](projects/excel-data-cleaning-automation/README.md)
A data-quality workflow that imports Excel customer records from Google Drive, maps inconsistent headers, standardizes names and contact fields, validates email/phone/date values, detects duplicate records, routes questionable rows for review, exports a cleaned workbook, and logs run metrics to Google Sheets.
**Tech:** n8n · JavaScript · Google Drive · Google Sheets · Excel/XLSX · Data Validation · Deduplication · Error Handling
**Highlights:** configurable rules, audit-friendly original values, explicit needs-review handling, and failure branches for key integration steps.

### 10. [SmileCare Dental Clinic — ElevenLabs Voice AI Receptionist](workflows/elevenlabs-voice-agent-post-call-logging.md)
I built and tested an English-language dental clinic voice receptionist in ElevenLabs, then connected it to an n8n post-call webhook. The workflow extracts call metadata and summaries, appends structured records to Google Sheets, and emails a call notification to the clinic team. The public JSON is a sanitized, inactive export; my live n8n setup is separate, and imported copies need their own credentials and destination settings.
**Tech:** ElevenLabs Conversational AI · n8n · Webhooks · Google Sheets · Gmail · GPT-4o mini

## Education

Diploma in Computer Science & Technology — Satkhira Polytechnic Institute | 2023
