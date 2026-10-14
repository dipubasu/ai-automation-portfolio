# Case Study: Automated Dental Clinic Email Support Agent

## Overview
An email support workflow that uses an AI agent to prepare replies to incoming clinic messages and sends a reply through Gmail.

## Workflow design
The export includes a Gmail trigger, AI Agent, Groq chat model, and Gmail reply node.

## Integrations
Gmail trigger/reply and a Groq-hosted language model.

## Why this design
An email-triggered flow can reduce repetitive response drafting. Clinic-specific prompts and trusted information sources should be checked carefully so the agent does not invent service, fee, booking, or clinical details.

## Configuration and boundaries
Connect the correct Gmail account, review the prompt and response policy, and test with synthetic messages. This exported node structure does not itself establish that a separate clinic knowledge base or a human approval gate is present.

## Testing and status
Live-tested by me in my own n8n environment. Inactive status may be intentional when the workflow is not currently needed.


## Workflow export

[**Open the n8n workflow JSON**](dental-clinic-email-support-agent.json)
