# Case Study: Travel MCP Server

## Overview
An MCP server workflow that exposes travel-related HTTP request tools for use by an MCP-compatible client or AI agent.

## Workflow design
The export includes an MCP Server Trigger and HTTP Request Tool nodes for hotels, restaurants, attractions, currency, geocoding, and weather.

## Integrations
n8n MCP server trigger and HTTP request tools, plus the upstream services configured in each request node.

## Why this design
Exposing operations as separate tools lets an AI client call focused travel functions rather than handling all requests through one large endpoint.

## Configuration and boundaries
Inspect each endpoint, query parameters, authentication requirements, timeouts, and response mapping. External providers may have rate limits or change their APIs; verify current behavior and avoid promising live data unless the upstream request succeeds.

## Testing and status
Live-tested by the author in their configured n8n environment. Availability and returned data depend on the upstream APIs and credentials configured in the deployment.
