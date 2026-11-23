# Data Guide

All records are synthetic. Keep the four supplied files unchanged. Document any cleaning, exclusions and assumptions in your analysis and FINDINGS.md.

## data/tickets.csv

This is a sample of the previous week's support tickets.

| Field | Meaning |
|---|---|
| ticket_id | Ticket identifier from the source |
| created_at | Source timestamp; interpret it using channel as described below |
| channel | app_chat or web_form |
| language | en = English, th = Thai, vi = Vietnamese, zh = Chinese |
| customer_id | Synthetic customer identifier |
| vip_tier | Customer tier recorded by the source |
| subject, body | Customer message text |
| triage_minutes | Time to read and sort the ticket |
| handle_minutes | Total handling time, including triage; do not add the two durations together |

app_chat timestamps are UTC. web_form timestamps use GMT+7 and dd/mm/yyyy HH:MM. Transaction references have TX followed by ten digits. Keep references and money amounts readable when redacting personal data.

## data/ai_seats.csv

Each row represents a paid WorkAI seat. Decide and explain how you use the rows to measure staff adoption.

| Field | Meaning |
|---|---|
| user_id | Seat account identifier |
| team | Team recorded for the account |
| status | Account's recorded staff status |
| left_date | Recorded departure date, if present |
| tool | AI product assigned to the seat |
| monthly_cost_usd | Monthly seat price in USD |
| prompts_wk_MMDD | Prompt count in the week starting Monday 2026-MM-DD |
| other_ai_seen | AI websites or browser extensions observed by IT in the same four weeks |

An observed website or extension does not establish which data was entered into it. Distinguish evidence, risk and assumptions in your conclusions.

## data/requests.csv

| Field | Meaning |
|---|---|
| req_id, team | Request identifier and requesting team |
| title, description | Proposed behavior |
| volume_per_week | Stated weekly work volume |
| minutes_per_item | Stated time per work item |
| claimed_hours_per_week | Requester's claimed weekly saving |
| build_hours_est | Initial estimate of implementation hours |
| money_movement | Y/N flag supplied with the request |
| customer_facing | Y/N flag indicating whether the proposal faces customers |

Treat these as inputs to assess, rather than verified benefits or final estimates. Explain changes to scope or estimates and avoid counting the same saving twice.

## data/vendor_quote.md

The fictional vendor's offer contains product claims, supported languages, commercial terms and pricing. Use the scenario's date when assessing it. Separate vendor claims from facts supported by the supplied evidence.
