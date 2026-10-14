# Case Study: Lead Intake → HubSpot CRM Sync → Notification

## Overview
This n8n workflow automates the initial processing of inbound leads: it accepts lead data through a webhook, validates required fields, synchronizes contact/deal information with HubSpot, and routes notifications or logs based on the flow's conditions.

## Workflow design
The exported workflow includes a configuration node, webhook trigger, validation branch, HubSpot contact create/update, deal creation, a high-value-deal branch, Telegram alerting, Google Sheets logging, and separate webhook responses for success, validation failure, and sync error.

## Integrations
- n8n Webhook and conditional nodes
- HubSpot contacts and deals
- Telegram notifications
- Google Sheets lead logging

## Why this design
Validation before CRM writes helps keep incomplete submissions out of the normal processing path. Separate response/error branches make the integration outcome easier to distinguish, while notifications and a sheet log support follow-up.

## Configuration and boundaries
Set the webhook contract, required lead fields, HubSpot credential and pipeline/stage settings, Telegram chat ID, and Google Sheets document/worksheet. The exported JSON contains placeholders for environment-specific values. Confirm HubSpot field mappings and duplicate-handling behavior in your own instance.

## Testing and status
Live-tested by the author in their configured n8n environment. The export's active flag reflects the saved copy only; a workflow may be inactive when it is not currently needed. No business outcome metrics are claimed here.
