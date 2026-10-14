# Case Study: AI Travel Assistant (MCP)

## Overview
A chat-triggered travel assistant that uses an AI agent and an MCP tool client to access travel-related tools and manage saved user preferences.

## Workflow design
The exported workflow contains a chat trigger, AI agent, Travel MCP tools client, Google Gemini chat model, and data-table tools for retrieving and saving preferences.

## Integrations
n8n chat trigger and AI Agent, Google Gemini, an MCP server exposing travel tools, and n8n data tables.

## Why this design
Keeping travel actions behind tools separates conversational planning from the operations that retrieve travel information. Saving preferences can help maintain continuity between requests.

## Configuration and boundaries
Configure the MCP server URL and exposed tools, model credentials, and preference-table access. The exact availability and accuracy of travel results depend on the connected MCP server and its upstream services.

## Testing and status
Live-tested by me in my own n8n environment. The exported active flag is not a promise that the copy is active in every environment.


## Workflow export

[**Open the n8n workflow JSON**](ai-travel-assistant-mcp.json)
