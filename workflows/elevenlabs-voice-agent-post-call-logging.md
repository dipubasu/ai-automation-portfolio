# SmileCare Dental Clinic — ElevenLabs Voice AI Receptionist

## Overview
I built and tested an English-language voice receptionist for SmileCare Dental Clinic in ElevenLabs Conversational AI, then connected it to an n8n post-call workflow. The setup captures call metadata and summaries in Google Sheets and sends a Gmail notification to the clinic team.

## Voice agent configuration
- **Agent name:** Aria
- **Voice:** Adam
- **Language:** English
- **LLM:** GPT-4o mini
- **Default personality:** Off
- **Opening message:** “Hello! Thank you for calling SmileCare Dental Clinic. How can I help you today?”
- **Clinic hours:** Saturday–Thursday, 9:00 AM–7:00 PM; closed Friday
- **Location:** Gulshan, Dhaka
- **Services:** General checkups, teeth cleaning, teeth whitening, cavity fillings, and root canal
- **Booking behavior:** Ask for the preferred day and time, then explain that a team member will call back to finalize the appointment.
- **Unknown questions:** Offer a team callback rather than guessing.


## Voice agent prompt
I configured the agent with the following receptionist instructions:

> You are Aria, a professional voice receptionist for SmileCare Dental Clinic. Your job is to greet callers warmly and professionally, answer questions about clinic hours, services, and appointment booking, and keep responses short and conversational because this is a phone call, not a chat message.
>
> Clinic information: Saturday to Thursday, 9 AM to 7 PM; closed Fridays. Services include general checkups, teeth cleaning, teeth whitening, cavity fillings, and root canal. Location: Gulshan, Dhaka.
>
> If someone wants to book an appointment, ask for their preferred day and time and confirm that someone from the team will call them back to finalize. If you do not know an answer, say: “Let me connect you with our team for that — they'll call you back shortly.” Always be warm, brief, and professional.

**Opening message:** “Hello! Thank you for calling SmileCare Dental Clinic. How can I help you today?”

## n8n post-call workflow
1. Receives an ElevenLabs post-call webhook event.
2. Extracts the call timestamp, conversation ID, transcript summary, duration, and success classification.
3. Appends the structured record to Google Sheets.
4. Sends a Gmail notification with the conversation ID, duration, success status, and summary.

## Data captured
| Field | Purpose |
|---|---|
| Timestamp | Call start time in ISO format when supplied; otherwise the workflow execution time |
| Conversation ID | Reference to the ElevenLabs conversation |
| Summary | Post-call transcript summary |
| Duration (sec) | Call duration in seconds |
| Successful | ElevenLabs call-success classification |

## Setup
1. Import [the sanitized n8n workflow JSON](elevenlabs-voice-agent-post-call-logging.json) into your n8n instance.
2. Configure the Webhook node and copy its **production URL** into the ElevenLabs agent's post-call webhook settings. Select the relevant post-call event in ElevenLabs.
3. Connect your own Google Sheets OAuth2 and Gmail credentials in n8n.
4. Replace the placeholder spreadsheet ID and notification email in the nodes.
5. Ensure the Google Sheet has these exact headers: `Timestamp`, `Conversation ID`, `Summary`, `Duration (sec)`, `Successful`.
6. Send a test call and confirm the webhook payload paths match the event delivered by your ElevenLabs configuration before activating the workflow.

## Important notes and limitations
- The JSON export is **sanitized**: credentials, the original webhook path, spreadsheet ID, and notification address are replaced or removed. The workflow is inactive on import and requires your own configuration.
- The export logs call summaries and metadata; it does not itself create or confirm appointments in a clinic scheduling system.
- The callback promise is part of the voice prompt; an actual callback requires a separate staff process or scheduling/CRM integration.
- Treat call summaries and transcripts as potentially sensitive customer information. Limit sheet access and email recipients, and disclose call recording/transcription practices as required by applicable law and clinic policy.
- The exported workflow uses normalized Google Sheets column mappings. Ensure the destination sheet headers exactly match the five fields listed above.

## Testing and security
I tested the voice agent and post-call workflow in my n8n environment. The public JSON is a sanitized, inactive export, not a copy of my live credentials or deployment settings. After importing it elsewhere, configure the webhook path, Google Sheets destination, Gmail recipient, and credentials before running a test call.

The exported webhook does not include authentication or signature validation. Before exposing it to production traffic, add an appropriate authentication/verification mechanism and verify the ElevenLabs event source. Treat call summaries and transcripts as potentially sensitive customer data.

## Success measures
Suggested metrics: calls received, call-success rate, average call duration, percentage of calls with usable summaries, and callback requests requiring staff follow-up. These are evaluation suggestions, not measured outcomes.

## Tech stack
ElevenLabs Conversational AI · n8n · Webhooks · Google Sheets · Gmail · GPT-4o mini

## Export
[Download/view the sanitized n8n workflow JSON](elevenlabs-voice-agent-post-call-logging.json)

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

The original workflow was built and tested in the author's configured environment. Your results may vary depending on your credentials, service configuration, and n8n setup.


## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../../LICENSE).
