# SmileCare Dental Clinic — ElevenLabs Voice AI Receptionist

## Overview
A voice receptionist prototype for SmileCare Dental Clinic, configured in ElevenLabs Conversational AI, with an n8n post-call workflow that records call metadata and summaries in Google Sheets and sends a Gmail notification to the clinic team.

## Voice agent configuration
- **Agent name:** Aria
- **Voice:** Adam
- **Language:** English
- **LLM:** GPT-4o mini (as configured by the project owner)
- **Default personality:** Off
- **Opening message:** “Hello! Thank you for calling SmileCare Dental Clinic. How can I help you today?”
- **Clinic hours:** Saturday–Thursday, 9:00 AM–7:00 PM; closed Friday
- **Location:** Gulshan, Dhaka
- **Services:** General checkups, teeth cleaning, teeth whitening, cavity fillings, and root canal
- **Booking behavior:** Ask for the preferred day and time, then explain that a team member will call back to finalize the appointment.
- **Unknown questions:** Offer a team callback rather than guessing.


## Voice agent prompt
The following prompt reflects the supplied configuration for the prototype:

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
- The source export's Google Sheets mapping used whitespace-padded column names for Summary and Successful. This sanitized version normalizes those names; confirm the destination sheet headers before testing.
- “GPT-4o mini” reflects the supplied project details; verify the exact model label in ElevenLabs before presenting it as a verified platform setting.

## Success measures
Suggested metrics: calls received, call-success rate, average call duration, percentage of calls with usable summaries, and callback requests requiring staff follow-up. These are evaluation suggestions, not measured outcomes.

## Tech stack
ElevenLabs Conversational AI · n8n · Webhooks · Google Sheets · Gmail · GPT-4o mini

## Export
[Download/view the sanitized n8n workflow JSON](elevenlabs-voice-agent-post-call-logging.json)
