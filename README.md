# Lead Capture — Forms + Sheets + Gmail + Slack + Contacts
 An end-to-end n8n automation that turns a web contact form submission into a fully processed lead — logged, welcomed, saved as a contact, and flagged to the team — with zero manual steps.
 # What it does :
 1 . Captures leads — An n8n Form trigger collects Full Name, Phone Number, and Email.
 2 . Logs to Google Sheets — Every submission is appended as a new row for record-keeping.
 3 . Sends a welcome email — Gmail automatically emails the lead a welcome message.
 4 . Creates a Google Contact — The lead's name, email, and phone are saved to Google Contacts.
 5 . Notifies the team on Slack — A message is posted to a Slack channel with the lead's details so the team can follow up immediately.

 ## Stack

- n8n (Form Trigger)
- Google Sheets
- Gmail
- Google Contacts
- Slack

## Setup

1. Import `lead-capture-workflow.json` into your n8n instance (**Workflows → Import from File**).
2. Reconnect the following credentials in each node:
   - Google Sheets (OAuth2)
   - Gmail (OAuth2)
   - Google Contacts (OAuth2)
   - Slack (OAuth2)
3. Update these node fields with your own values:
   - **Append row in sheet** → `documentId` (your Google Sheet)
   - **Send a message1** (Slack) → `channelId` (your target channel)
4. Activate the workflow and grab the form's public URL from the **On form submission** trigger node.

## Notes

- Phone numbers are explicitly cast to string (`.toString()`) before being sent to Google Contacts, since the API rejects numeric types.
- Before publishing this repo, consider replacing the Sheet ID/URL and Slack channel ID with placeholders if you don't want those internal identifiers exposed publicly.
