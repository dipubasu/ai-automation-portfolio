# Lead Intake → HubSpot CRM Sync → Notification

## Business problem
When leads arrive through different forms or landing pages, sales teams can lose time copying details into a CRM, miss incomplete submissions, or notice valuable opportunities too late. Manual handoffs also make it harder to see why a lead failed to enter the pipeline.

## Solution
I built this n8n workflow to accept a new lead through a webhook, validate the submitted data, create or update the contact in HubSpot, create a deal, and route follow-up based on deal value. High-value opportunities trigger a Telegram alert; the standard path is logged to Google Sheets. The webhook returns different responses for validation failure, successful processing, and sync errors.

## Business value
- Reduces repetitive lead entry between a website/form and CRM.
- Gives sales a faster signal when a lead meets the configured high-value condition.
- Creates a lightweight log for standard leads.
- Makes failed CRM syncs visible so a lead can be followed up manually rather than silently disappearing.

## How the workflow operates
1. Receives the lead payload by webhook.
2. Checks whether the required lead fields are present.
3. Creates or updates the HubSpot contact, then creates a deal.
4. Checks the deal amount against the configured high-value condition.
5. Sends a Telegram alert for high-value deals or logs standard leads in Google Sheets.
6. Returns a success, validation-error, or sync-error response.

## Intended use
Small sales teams or businesses that collect leads online and use HubSpot as their CRM.

## Setup and limitations
Configure the incoming payload contract, required fields, HubSpot credentials and deal pipeline/stage, high-value threshold, Telegram chat ID, and Google Sheets destination. Verify duplicate handling and HubSpot field mappings in your account. The workflow's value depends on valid incoming data and correct CRM configuration; it does not guarantee lead conversion.

## How I would measure success
Track valid leads processed, CRM sync failures, time from submission to CRM entry, high-value alert latency, and leads requiring manual follow-up. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. The exported JSON uses placeholders for environment-specific values and may need configuration before import.

[Open workflow JSON](lead-intake-hubspot-crm-sync.json)

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).

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
