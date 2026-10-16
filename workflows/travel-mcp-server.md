# Travel MCP Server — Travel Search Tools for AI Assistants

## Business problem
A travel assistant that needs to answer destination questions may otherwise rely on a language model's stored knowledge, which can be stale or inaccurate for current weather, nearby places, and currency rates. Maintaining separate custom integrations for every assistant can also duplicate work.

## Solution
I built an MCP server workflow that exposes separate HTTP request tools for geocoding, hotels, restaurants, attractions, currency conversion, and weather. An MCP-compatible AI client can call the relevant tool when a user asks a travel question.

## Business value
- Makes travel data lookups available through a consistent tool interface.
- Separates individual data sources into focused operations that are easier to inspect and maintain.
- Helps an AI assistant use live tool responses instead of guessing factual details.

## How it works
1. An MCP-compatible client connects to the n8n MCP server.
2. The client selects a tool based on the travel question.
3. Geocoding can translate a destination into coordinates for location-based searches.
4. The selected HTTP request calls its configured upstream service and returns the response to the client.

## Intended use
A reusable tool layer for an AI travel assistant or other MCP-compatible client.

## Setup and limitations
Configure each HTTP endpoint, query parameters, authentication, and upstream API access. Verify provider response formats and rate limits. Tool exposure does not itself guarantee that an upstream service is available or that returned hotel data represents confirmed booking availability.

## How I would measure success
Measure tool-call success rate, API latency, data freshness, and how often users need to verify or correct results. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. External API behavior depends on the services and credentials configured in the target environment.

[Open workflow JSON](travel-mcp-server.json)

## Setup, Credentials & Testing

This workflow is provided as an exported n8n JSON template. It may require configuration before it runs successfully after import.

### Before running the workflow

1. Import the JSON file into your n8n instance.
2. Configure the required credentials, API keys, and service connections.
3. Replace placeholder values with your own IDs, URLs, and configuration settings.
4. Review the nodes and adjust settings for your environment.
5. Test the workflow with sample data before using it in production.

### Important notes

- Credentials and API keys are not included in this export. Configure your own credentials for the services used by the workflow.
- Some integrations may require API access, subscriptions, permissions, or additional setup.
- The exported workflow may require environment-specific changes before it works correctly.
- Importing this JSON does not automatically activate the workflow or guarantee successful execution.
- Test the workflow in your own n8n environment before using it in production.

The original workflow was built and tested in the author's configured environment. Your results may vary depending on your credentials, service configuration, and n8n setup.

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).
