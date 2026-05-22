# HireFlow Shareable Package

This folder contains sanitized copies of the HireFlow demo files. The original local files were not modified.

## What Is Included

- `HireFlow Dashboard - SHAREABLE.html`
  A browser-based recruitment dashboard for HR users. It reads jobs, candidates, and CV analysis records from Airtable, shows candidate status, opens candidate profiles, displays AI CV analysis, and sends HR actions to n8n.

- `HireFlow - AI Job Intake & Publishing Engine - SHAREABLE.json`
  An n8n workflow that receives HR messages through Telegram, helps define a job, creates a Google Form through Google Apps Script, saves the job in Airtable, and sends the final job post/form link back to Telegram.

- `CV Intake & Scoring - SHAREABLE.json`
  An n8n workflow that receives Google Form submissions, downloads/extracts CV text, scores the candidate with AI, saves candidate and analysis records in Airtable, and routes candidates by recommendation.

- `HireFlow - HR Action Webhook - SHAREABLE.json`
  An n8n workflow for HR and candidate actions such as interview scheduling, confirmation, rescheduling, candidate portal actions, calendar slot handling, and emails.

## Dashboard Overview

The dashboard is a single HTML file. It is intended for a private/internal HR user.

Main capabilities:

- View open jobs from Airtable.
- View candidates per job.
- See candidate status, score, and AI analysis.
- Open candidate details and CV analysis.
- Schedule, confirm, reject, cancel, or reschedule interviews through n8n actions.
- Candidate portal flows can confirm attendance, request reschedule, select slots, or suggest a new time.

Important security note:

The dashboard currently calls Airtable directly from browser JavaScript using an Airtable PAT. This is acceptable only for local/private demos. For production, put Airtable access behind a backend or n8n webhook so the Airtable token is never exposed in the browser.

## Placeholders To Replace

Replace these placeholders with your own values before running:

- `YOUR_AIRTABLE_PAT`
- `AIRTABLE_BASE_ID`
- `AIRTABLE_JOBS_TABLE_ID`
- `AIRTABLE_CANDIDATES_TABLE_ID`
- `AIRTABLE_CV_ANALYSIS_TABLE_ID`
- `YOUR_N8N_PUBLIC_URL`
- `YOUR_N8N_PUBLIC_HOST`
- `YOUR_GOOGLE_APPS_SCRIPT_DEPLOYMENT_ID`
- `YOUR_TEMPLATE_FORM_ID`
- `YOUR_GOOGLE_CALENDAR_ID@group.calendar.google.com`
- `YOUR_EMAIL@gmail.com`
- `EXAMPLE_DRIVE_FILE_ID` if present in sample/test expressions

## Credentials To Reconnect In n8n

After importing the n8n workflows, reconnect credentials manually:

- Telegram
- OpenRouter
- Airtable
- Gmail
- Google Calendar
- HTTP Header Auth or Google Apps Script auth, if used

## Setup Order

1. Import the n8n workflows.
2. Reconnect all credentials.
3. Replace Airtable base/table placeholders.
4. Replace `YOUR_N8N_PUBLIC_URL` with your production n8n URL.
5. Deploy the Google Apps Script form creator and replace `YOUR_GOOGLE_APPS_SCRIPT_DEPLOYMENT_ID`.
6. Replace `YOUR_TEMPLATE_FORM_ID` with your Google Form template ID.
7. Replace Google Calendar and email placeholders in the HR action workflow.
8. Update `HireFlow Dashboard - SHAREABLE.html` config:

```js
const CFG = {
  AIRTABLE_KEY: 'YOUR_AIRTABLE_PAT',
  AIRTABLE_BASE: 'AIRTABLE_BASE_ID',
  N8N_URL: 'https://YOUR_N8N_PUBLIC_URL/webhook/hr-action',
};
```

9. Open the dashboard HTML locally or host it privately.

## Sanitization Notes

The shareable copies were checked for:

- Real Airtable PATs.
- Real Airtable base/table IDs.
- Real n8n/ngrok URLs.
- Real Google Apps Script deployment IDs.
- Real Google Form template IDs.
- Real email addresses.
- Real Google Calendar IDs.
- n8n credential objects.
- n8n webhook IDs.
- n8n workflow IDs, version IDs, instance metadata, and pinned execution data.

Only placeholders and public service URLs remain.

