# Excel Data Cleaning Automation

## Business problem
Customer spreadsheets often arrive with inconsistent column names, messy text, malformed contact details, mixed date formats, blank rows, and duplicate customers. Cleaning these manually is repetitive and makes it easy to remove the wrong row or overlook questionable data.

## Solution
I built an n8n workflow that reads an Excel workbook from Google Drive, maps supported header aliases, standardizes and validates records, detects duplicates, and separates rows into valid, needs-review, invalid, duplicate, and empty-row categories. It then creates a report, uploads the output to Drive, upserts valid customer records into Google Sheets, and records run-level metrics.

## Business value
- Reduces repetitive spreadsheet cleanup.
- Makes data-quality decisions more transparent by keeping separate categories instead of treating every row as clean.
- Gives teams a repeatable report and run summary to review.
- Helps keep a cleaned customer sheet updated without manually copying each valid record.

## How the workflow operates
1. Downloads and parses the source workbook.
2. Maps supported header names and checks required columns.
3. Normalizes text and validates email, phone, and date fields according to configuration.
4. Detects duplicates using configured keys such as email, phone, and customer ID.
5. Classifies rows and assembles an output workbook.
6. Uploads the report, logs summary metrics, and upserts valid records into Google Sheets.
7. Stops with explicit errors for key Drive, parsing, upload, or Sheets failures.

## Intended use
Operations, sales, and admin teams that regularly receive customer lists in Excel and need a repeatable first-pass data-quality process.

## Sample run
The project notes one development sample with four input rows, four processed records, three unique records, and one duplicate. This is an example from that sample only, not a benchmark or guarantee for other files.

## Setup and limitations
Connect your own Google Drive and Sheets credentials, set the source/destination IDs and worksheet names, and review required fields, date convention, email auto-fix, dedupe keys, and default phone country code. Phone checks are conservative; ambiguous dates or uncertain matches should be reviewed by a person.

## How I would measure success
Compare manual cleanup time, duplicate rate, number of rows sent to review, invalid-record rate, and the number of upload/sync failures before and after adoption. These are suggested measures, not claimed outcomes.

## Testing and export
I live-tested this workflow in my own n8n environment. The public JSON is a sanitized, intentionally inactive export; configure your own credentials and IDs before running it.

[Open workflow JSON](excel-data-cleaning-automation.json)

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).

## Setup, Credentials & Testing

This workflow is provided as an exported n8n JSON template. It is not guaranteed to run immediately after import.

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


## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).
