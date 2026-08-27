# AI-Powered Client Intake, Qualification and Onboarding with OpenAI, Supabase and Gmail

![AI-powered client intake, qualification and onboarding workflow](./upload/AI-Powered%20Client%20Intake,%20Qualification%20&%20Automated%20Onboarding%20System%20for%20Service%20Agencies(1).png)

> **Built by Muhammad Bilal — AI Automation Specialist**

## Overview

Turn every new client inquiry into a structured, scored, and actionable lead—without manually reviewing forms, writing repetitive emails, or updating lead records.

This workflow captures project information through an n8n Form, validates the submission, stores valid leads in Supabase, and uses OpenAI to create a structured requirements analysis. A transparent rule-based scoring system then classifies each opportunity as **HOT**, **WARM**, or **LOW-FIT**.

Each branch sends the appropriate client response, prepares an internal summary for the team, sends a Gmail notification, and updates the lead's final status in Supabase.

## Workflow integrations

| Integration | Purpose |
| --- | --- |
| 🧩 **n8n Form** | Captures client and project information |
| 🟢 **Supabase** | Stores lead data, analysis, scores, and statuses |
| 🤖 **OpenAI** | Produces a structured project summary and risk analysis |
| ✉️ **Gmail** | Sends client responses and internal team alerts |

## What this workflow does

1. Captures the client's name, email, company, industry, required service, project brief, budget, timeline, and phone number.
2. Normalizes all submitted fields into a consistent structure.
3. Validates required information, email format, and project-brief quality.
4. Sends a clarification email when important information is missing or invalid.
5. Creates a new lead record in Supabase when validation succeeds.
6. Uses OpenAI structured output to identify the service category, complexity, priority, missing information, risks, and recommended next step.
7. Calculates a deterministic qualification score using defined business rules.
8. Routes the lead into the correct follow-up path.
9. Sends a personalized client email and an internal Gmail notification.
10. Updates the final lead status in Supabase for future tracking and reporting.

## Lead routing logic

| Qualification | Score | Automated outcome |
| --- | ---: | --- |
| 🔥 **HOT** | 75–100 | Sends onboarding email, alerts the team, and marks `hot_onboarding_sent` |
| 🟡 **WARM** | 50–74 | Sends a follow-up email, alerts the team, and marks `warm_followup_sent` |
| ⚪ **LOW-FIT** | Below 50 | Sends a polite response, creates an internal log, and marks `low_fit_response_sent` |

The score considers budget, urgency, project-brief quality, service clarity, available business information, missing details, and risk flags. OpenAI analyzes the request, but the final qualification is controlled by deterministic rules for more predictable routing.

## Who this template is for

- AI automation agencies
- Marketing and creative agencies
- Software and web-development teams
- Consultants and professional service providers
- Freelancers managing a growing number of project inquiries
- Sales teams that need consistent lead qualification and follow-up

## Requirements

- An n8n instance
- A Supabase project with a `leads` table
- An OpenAI API credential
- A Gmail OAuth2 credential

## Setup

1. Import the workflow into n8n.
2. Create or select your Supabase `leads` table.
3. Connect your own Supabase credential to all Supabase nodes.
4. Connect your own OpenAI credential to **AI Requirement Analyzer**.
5. Connect your own Gmail OAuth2 credential to all Gmail nodes.
6. Replace `your-team-email@example.com` in the three internal notification nodes.
7. Replace **Your Agency Name** and **Automation Team** inside the client email templates.
8. Customize the form title, fields, budget ranges, scoring thresholds, and email wording for your business.
9. Test one incomplete, one HOT, one WARM, and one LOW-FIT submission.
10. Activate the workflow only after confirming all database updates and email recipients.

## Suggested Supabase fields

`id`, `full_name`, `email`, `company_name`, `industry`, `required_service`, `project_brief`, `budget_range`, `expected_timeline`, `phone_number`, `client_summary`, `service_category`, `complexity`, `priority`, `missing_information`, `risk_flags`, `recommended_next_step`, `qualification_score`, `qualification`, `lead_status`, `created_at`, `updated_at`

## Customization ideas

- Replace Gmail notifications with Slack, Microsoft Teams, or Discord.
- Create a CRM record in HubSpot, Pipedrive, or Airtable.
- Add calendar scheduling for HOT leads.
- Adjust qualification rules for your pricing and ideal client profile.
- Add error handling, retries, and an execution-error alert for your production environment.
- Send analytics to a dashboard for lead-source and conversion reporting.

## Security note

Connect your own credentials after importing. Before sharing an edited version, remove credential references, personal email addresses, test data, webhook identifiers, and pinned execution data from the exported workflow JSON.

---

**Created by Muhammad Bilal**  
**AI Automation Specialist**
