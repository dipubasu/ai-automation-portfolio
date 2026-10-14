# Case Study: Excel Data Cleaning Automation

## Overview
This workflow processes customer records from an Excel workbook and creates a cleaner, categorized output plus a run summary. It is designed for inconsistent headers, formatting differences, missing or invalid values, and duplicate records.

## Workflow design
The 26-node export includes manual trigger and configuration, Google Drive download, Excel parsing, schema checks, standardization, duplicate detection, record classification, separate valid/review/invalid/duplicate/empty-row paths, merge/report generation, Drive upload, Google Sheets summary logging, and upsert of valid customer rows. Stop-and-error nodes cover key download, parsing, upload, and Sheets failure paths.

## Data quality handling
The workflow maps supported header aliases, normalizes text, checks email and phone formats, parses supported date formats, derives name fields when possible, and separates questionable records for review rather than silently treating every row as valid.

## Integrations
n8n, JavaScript transformation logic, Google Drive, Google Sheets, and Excel/XLSX.

## Sample execution
The project README records one development sample with four input rows, four processed records, three unique records, and one duplicate. These are sample-run figures, not a general performance claim.

## Configuration and boundaries
Connect your own Drive and Sheets credentials, set source/destination IDs and worksheet names, and review date convention, phone country code, and email-repair options. Phone validation is conservative; ambiguous dates may need review.

## Testing and status
Live-tested by the author in their configured n8n environment. The repository export is sanitized and intentionally inactive for sharing; configure it before running in another instance.
