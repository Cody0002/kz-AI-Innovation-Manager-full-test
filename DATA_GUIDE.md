# Data Guide

This case has four files. Keep the originals in `data/` and record any cleaning, exclusions or assumptions in `analysis/` and `FINDINGS.md`.

## data/tickets.csv

The sample comes from the week before your first Monday in the case.

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

Each row is a paid WorkAI seat. In your findings, explain which rows you counted when measuring how often staff use AI.

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

IT can see which sites or extensions were used. The records don’t show what anyone entered.

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

These are the teams’ estimates. If you change an estimate or the scope of a request, explain why. Count each saving once.

## data/vendor_quote.md

Read the vendor’s offer as of 12 October 2026, your first day in the case. It lists the languages, terms and price on offer. Use the other files to check which claims the evidence supports.
