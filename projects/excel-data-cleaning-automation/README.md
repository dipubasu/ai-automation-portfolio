# Excel Data Cleaning Automation

An n8n workflow that turns messy Excel customer data into a standardized, validated, deduplicated dataset and a run summary for review.

## Project overview

**Problem:** Customer spreadsheets often contain inconsistent names, email formatting errors, mixed date formats, incomplete contact details, and duplicate records. These issues can lead to unreliable reporting and repeated customer records.

**Solution:** This workflow reads an Excel workbook from Google Drive, maps source headers to canonical fields, cleans and validates records, identifies duplicates, classifies records by quality, produces a cleaned Excel report, and logs run metrics to Google Sheets.

## Workflow stages

1. **Trigger & configuration** — start a manual run and load configurable rules.
2. **Download & parse** — retrieve the source workbook from Google Drive and extract its rows.
3. **Schema validation** — normalize supported header aliases and check required columns.
4. **Clean & standardize** — normalize text, validate email addresses and phone numbers, parse supported date formats, and derive `first_name` / `last_name` from `full_name` when needed.
5. **Duplicate detection** — identify definite duplicates and potential matches for review.
6. **Record classification** — route records into valid, needs-review, invalid, duplicate, and empty-row groups.
7. **Reporting & export** — build a cleaned Excel workbook, upload the result, upsert valid customer records, and append a run summary to Google Sheets.
8. **Failure handling** — stop with a clear error when key Drive, parsing, upload, or Sheets operations fail.

## Integrations

- **n8n** — workflow orchestration and transformation logic
- **Google Drive** — source workbook download and cleaned report upload
- **Google Sheets** — cleaned customer upserts and append-only run summary
- **Excel/XLSX** — input parsing and generated report

## Data quality controls

- Header alias mapping and required-column checks
- Email syntax validation with optional conservative typo repairs
- International phone normalization using a configured default country calling code
- Supported date parsing with explicit handling for ambiguous day/month values
- Duplicate detection and candidate-review routing
- Row-level classification and aggregate run metrics
- Original field values retained for audit where applicable

## Sample outcome

The test workbook shown during development included a repeated customer record. The workflow summary reported four input rows, four processed records, three unique records, and one duplicate. A record flagged for review should be checked rather than treated as automatically clean.

These counts describe the sample execution only; they are not a performance guarantee for other files.

## Download the workflow

[**Download the n8n workflow JSON**](../../workflows/excel-data-cleaning-automation.json)

The workflow has been live-tested in my configured n8n environment. The repository export is a sanitized, inactive copy for sharing; it contains no saved n8n credential objects and uses placeholders for source/destination IDs. After importing into your own instance, connect your Google Drive and Google Sheets credentials and configure the IDs and worksheet names in the `Config` node and Google Sheets nodes.

## Setup

1. Import the workflow JSON into your own n8n instance.
2. Create/connect your own Google Drive and Google Sheets credentials through n8n's credential manager.
3. Configure the source Excel file ID, destination report file ID (or adjust the upload node to create a new file), and destination spreadsheet ID.
4. Ensure the spreadsheet contains the expected worksheets, including `Cleaned_Customers` and `Run_Summary`, with headers matching the workflow's mapped fields.
5. Review the `Config` node settings, especially required columns, date convention, email auto-fix behavior, and default phone country calling code.
6. If you are adapting the workflow for another environment, run it against a copy of your input workbook first, then inspect the cleaned data, duplicates, and needs-review records before using it operationally.

## Security notes

- Do not commit OAuth tokens, API keys, client secrets, real customer spreadsheets, or execution data.
- Keep credentials in n8n's credential manager; never paste secrets into node parameters or this repository.
- Replace all file and spreadsheet IDs with your own values after importing.
- The repository export is intentionally inactive; activate it in your own n8n instance only after connecting credentials and configuring destination IDs.
- Review the exported JSON and its node parameters before each public release. Automated pattern scans reduce risk but cannot guarantee that every secret has been detected.

## Limitations

- Phone validation is intentionally conservative and is not a substitute for a dedicated phone-number metadata library.
- Date strings with ambiguous day/month ordering are marked for review unless a DMY or MDY convention is configured.
- Google Drive upload behavior depends on the destination node configuration and the permissions of the connected account.
- Validate the workflow in your own n8n version and test with representative files before production use.

## Tech stack

`n8n` · `JavaScript` · `Google Drive API` · `Google Sheets API` · `Excel/XLSX` · `Data Validation` · `Deduplication` · `Error Handling`


---

Built as a portfolio project by Dipu Basu.

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).

## Setup, Credentials & Testing

This workflow is provided as an exported n8n JSON template. It is not guaranteed to run immediately after import.

### Before running the workflow

1. Import the JSON file into your n8n instance.
2. Configure the required credentials, API keys, and service connections.
3. Replace placeholder values with your own IDs, URLs, and configuration settings.
4. Review the nodes and adjust settings for your environment.
5. Test the workflow with sample data before using it in production.

### Important notes

- Credentials and API keys are not included in this export. You must configure your own credentials for the services used by the workflow.
- Some integrations may require API access, subscriptions, permissions, or additional setup.
- The exported workflow may require environment-specific changes before it works correctly.
- Importing this JSON does not automatically activate the workflow or guarantee successful execution.
- Test the workflow in your own n8n environment before using it in production.

The original workflow was built and tested in the author's configured environment. Your results may vary depending on your credentials, service configuration, and n8n setup.

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).

