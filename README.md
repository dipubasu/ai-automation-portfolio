# Dipu Basu — AI Automation Developer Portfolio

n8n Automation Engineer | AI Agent & RAG Developer

**Contact:** dpbasu32@gmail.com | +880 1876-233071 | [LinkedIn](https://linkedin.com/in/dipubasu) | Bangladesh — Remote / Worldwide

## About

AI Automation Developer specializing in n8n workflows, RAG systems, AI agents, and API integrations. I build automated systems for lead management, customer support, knowledge retrieval, and business operations using n8n, OpenAI, Groq, Gemini, Supabase, and REST APIs — with a focus on reliable workflow design, error handling, and maintainable integrations.

> **Note:** All workflow exports in this repository have had API keys, tokens, and personal identifiers replaced with placeholders (e.g. `YOUR_API_KEY`). Import these into your own n8n instance and connect your own credentials before running.

## Core Skills

- **Automation:** n8n · Make.com · Workflow Automation · Webhooks · MCP
- **AI & LLM:** OpenAI · Gemini · Groq / Llama · RAG (Retrieval-Augmented Generation) · Embeddings · Prompt Engineering · AI Agents · Cloudflare AI (Flux) · ElevenLabs TTS
- **Integrations:** HubSpot · Facebook Graph API · Telegram API · Gmail OAuth2 · WhatsApp · REST APIs · Shotstack · YouTube API · Google Drive API
- **Data & Infrastructure:** Supabase Vector DB · Google Sheets · Google Drive · API Authentication · Error Handling · Secure Credential Management

## Projects

### 1. [Automated Lead Management Pipeline](workflows/lead-intake-hubspot-crm-sync.json) — n8n + HubSpot CRM Automation
Captures leads via webhook, validates submitted data, creates or updates HubSpot CRM records, and conditionally routes high-value opportunities. Includes Google Sheets logging and Telegram alerts for high-value leads and failed HubSpot syncs.
**Tech:** n8n · HubSpot · Webhooks · Telegram · Google Sheets · REST APIs

### 2. [EstateBot — AI Real Estate Lead Qualification Agent](workflows/estatebot-lead-qualification-server.json)
A Telegram AI agent that qualifies property buyers through structured one-at-a-time questioning, maintains conversation context, and uses RAG to search a Supabase-based property knowledge base. Logs completed buyer requirements to Google Sheets and notifies agents in real time.
**Tech:** n8n · Telegram API · Groq / Llama · Supabase Vector DB · RAG · Google Sheets
Related: [EstateBot AI Agent + Memory + Supabase RAG](workflows/estatebot-ai-agent-memory-supabase-rag.json)

### 3. [Veltoro — AI Shopping Assistant (Messenger RAG Chatbot)](workflows/veltoro-messenger-ai-chatbot.json)
A Messenger-based RAG assistant that retrieves product information from a vectorized catalogue and generates context-aware answers to customer product questions.
**Tech:** n8n · Supabase · OpenAI Embeddings · Groq / Llama · Facebook Graph API
Related: [Veltoro RAG Knowledge Base Setup](workflows/veltoro-rag-knowledge-base-setup.json)

### 4. [Veltoro — AI Email Support with Human-in-the-Loop Approval](workflows/rag-email-customer-support-agent.json)
Detects unread customer emails every minute via Gmail, strips quoted replies/signatures, and uses a RAG agent (Groq, Supabase Vector Store, Gemini Embeddings) to search a policy knowledge base and draft a reply. Drafts go through human approval (Approve/Reject) before sending; rejected ones are flagged for manual review.
**Tech:** n8n · Gmail API · Groq / Llama · Supabase Vector DB · Google Gemini Embeddings · RAG · Human-in-the-Loop Approval

### 5. [Automated Dental Clinic Support Agent](workflows/dental-clinic-email-support-agent.json)
An AI email assistant that reads incoming patient emails every minute and drafts professional, on-brand replies strictly grounded in the clinic's own knowledge base (hours, fees, services, booking), escalating anything outside that scope instead of guessing.
**Tech:** n8n · Gmail API · Groq / Llama

### 6. [Telegram Chatbot + Human Bridge Support](workflows/telegram-chatbot-human-bridge-support.json)
Multilingual (Bangla, English, Banglish) Telegram support assistant with conversation memory, voice-message understanding, and seamless escalation/hand-off to a human agent when needed.
**Tech:** n8n · Groq / Llama · Google Gemini · Telegram API

### 7. [AI YouTube Video Automation — Multi-Scene Pipeline](workflows/youtube-automation-topic-to-video.json)
An end-to-end pipeline that turns a topic into a finished, published YouTube Short: OpenAI (GPT-4o-mini) generates the title, description, script, and 4 scene-by-scene image prompts; Cloudflare AI (Flux) generates a distinct photorealistic visual for each scene; ElevenLabs generates the voiceover; Shotstack composites the scenes with transitions and effects into one video; and the result is auto-uploaded to YouTube as a Short.
**Tech:** n8n · OpenAI API · Cloudflare AI (Flux) · ElevenLabs · Shotstack API · YouTube API

### 8. [AI Travel Assistant — MCP-Based Multi-Tool Agent](workflows/ai-travel-assistant-mcp.json)
An MCP-based conversational agent that coordinates multiple tools for hotel search, restaurant discovery, live weather information, and currency conversion.
**Tech:** n8n · MCP Server/Client · Groq / Llama · Geoapify · Open-Meteo
Related: [Travel MCP Server](workflows/travel-mcp-server.json)

## Education

Diploma in Computer Science & Technology — Satkhira Polytechnic Institute | 2023
