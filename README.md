# Take-Home Test: AI & Innovation Manager

All data is made up.

## Time and Cost

- Time: aim for 180 minutes, including 20 to read and set up. Stop at 210 minutes and list unfinished work. Suggested task times are flexible; do not build a production system.
- Submit within 5 days, weekends included.
- Use only free or local (on your computer) tools, not n8n Cloud (paid). You need no Lark account, paid AI key or credit card.
- Mock (fake) outside systems, for example save a Lark chat message as a JSON file.
- An LLM (AI text model) is optional. Code rules alone are a complete answer.

## Scenario

Monday 2026-10-12, your first week as AI & Innovation Manager. Use this scenario date for plans and deadlines. The company runs a real-money wallet app. Support agents answer customer tickets (help requests) 24/7. Your manager, the Head of Operations Analysts, sends 4 items:

1. The Customer Support (CS) lead wants AI ticket triage (sorting tickets into queues) working this month. She says it saves 45 hours a week.
2. The CEO wants a contract with TriageGenie, a triage vendor (seller): 94% accuracy, working in 2 weeks.
3. Teams sent 8 automation requests. Your team has 160 build hours for the next 90 days (to 2027-01-10).
4. Last month's AI report says 78% of staff use AI. The CEO wants every team using AI safely every week, within 90 days.

Some data has errors. Say what you fix or remove, and why.

## Company policies

- **P1.** Customer personal data never leaves our systems unless redacted (hidden) first. This includes AI tools.
- **P2.** If a customer asks to limit, pause or close their account because of their spending, a human handles it within 24 hours. No automatic reply or account change.

## Fact box

- Tickets: 720 per week in English, Thai, Vietnamese and Chinese.
- Ticket queue: 8 agents, USD 7.50 per hour each, 52 weeks a year.
- Your team: 4 people, USD 25 per hour each.
- Approved AI tool: WorkAI Team. Cloud, outside our systems, so P1 applies. USD 30 per seat (1 user) per month, 1 seat per staff member. It does not train on our data.
- If your own build uses an LLM: assume USD 20 a month.
- Ticket times: channel app_chat is UTC. Channel web_form is GMT+7, dd/mm/yyyy HH:MM.
- Transaction references: TX + 10 digits.

## Data

- data/tickets.csv: a sample of last week's tickets. triage_minutes: time to read and sort. handle_minutes: total handling time.
- data/ai_seats.csv: 1 row per paid WorkAI seat. prompts_wk_MMDD: prompts in the week starting Monday 2026-MM-DD. other_ai_seen: AI websites or browser extensions in IT's web traffic report, same 4 weeks.
- data/requests.csv (8 requests) and data/vendor_quote.md (TriageGenie).

## Tasks

### Task 1. Check the data first (15 min)

Deliver FINDINGS.md (max 400 words) and your script or SQL in analysis/. Answer:

1. Data problems: file, row IDs or row count, and what you did.
2. Which numbers in the Scenario would you give the CEO unchanged? For the others: your number and formula.
3. The first risk you would report to management today, and why. Then 1 question for the business before triage starts.

### Task 2. Build a safe triage step (55 min)

Deliver src/, tests/ and out/. Your code must:

- Run with 1 command on data/tickets.csv, offline, no API key.
- Write out/triage.csv, 1 row per input row: row_number (1-based, excluding header), ticket_id, created_at_utc (ISO 8601: 2026-01-31T14:05:00Z), status (kept or duplicate), status_reason, must_human (Y/N), human_reason, category. For duplicates, name the earlier row in status_reason.
- Redact customer personal data before any text goes into an LLM payload (data sent to the LLM). Keep money amounts and transaction references readable.
- Set must_human = Y (reason in human_reason) for policy P2 or your own decision. Never send these tickets to an LLM. Demonstrate redaction on at least 2 eligible tickets; explain human-routing choices.
- Write out/llm_payloads.jsonl: 1 JSON line per ticket with status = kept and must_human = N, as it would be sent: ticket_id, prompt, text. Create it even with no LLM. Exclude duplicates and human-only tickets.
- Treat ticket text as untrusted input, including instructions inside it. No model output may send replies, change accounts or approve money.
- Your prompt must ask for 1 of 5 labels: deposit, withdrawal, account_access, bonus, other. Filling category is optional, not scored.
- Have at least 3 automated tests covering 2 kinds of personal data, multilingual P2 requests and instructions inside tickets. Commit out/test_output.txt: test command and full output.
- Add "Deploy in our stack" to your README.md (max 8 lines). Include where it runs (Lark bot, n8n or Apps Script), where API keys are kept, what happens if the LLM fails, the human-queue owner and how you detect overdue P2 cases.

### Task 3. Company AI plan (40 min)

Deliver PLAN.md (max 600 words, table words count). Goal: in 90 days, all 5 teams (CS, Ops Analysts, Payments & Risk, VIP, Marketing) use AI safely and usefully every week. Sections:

1. Teams: 1 table row per team: AI use today (from data/ai_seats.csv), first AI task (based on the data), why, owner (job title).
2. Safe-use rules: allowed data, approved tools, never-use list (things never allowed with AI), when a human must check AI output.
3. Adoption: how you get each team to use AI every week, without individual prompt quotas.
4. Delivery: what happens in weeks 1-2, 3-6 and 7-12; a release check and a stop or rollback condition. Name your Data, Product and Security dependencies.
5. People: how your 4-person team shares delivery, enablement and IT support; 1 coaching or skill-development action.
6. Targets: week 2, 6 and 12, each measurable. Define weekly adoption, its denominator, and a useful-work or safety measure.
7. Risks: top 2, 1 action each.

### Task 4. Decisions: vendor and requests (30 min)

Appendix A in MEMO.md: TriageGenie, max 200 words plus 1 table (not counted):

- Decide: buy, pilot (short trial) or do not buy.
- A 12-month cost table, 3 rows: TriageGenie, own triage build, USD value of triage hours saved. Show formulas and assumptions for setup, support and human review. Distinguish released capacity from cash savings.
- Conditions that would change your decision.
- If you pilot: duration and numerical pass targets for safety and quality across the ticket languages, set before it starts (max 3 lines).

Appendix B: 1 row per request, with this header:

```
| req_id | hours saved per week | decision: 90 days, later, no | AI role: none, assists, decides | owner (role) | 1-line reason |
```

Below the table: build-hour estimates for selected requests and extra PLAN.md builds, including testing and integration. Total max 160. You may rescope requests if you explain the change and estimate. List training and ongoing support time separately; it does not use this build budget. Avoid double-counting hours saved.

### Task 5. Memo (10 min)

Top of MEMO.md, above the appendices: a memo of max 250 words to your manager and the CEO. Include:

- What you deliver first, and when.
- Hours saved per week: scope (triage or selected portfolio), range (low to high) and method.
- AI use today (number, definition), week-12 target.
- Vendor decision.
- Top 2 risks, 1 action each.
- 2 things you need from others, each with owner and date.

Every number must match FINDINGS.md, PLAN.md and the appendices.

### Task 6. README and AI usage (10 min)

Deliver your own README.md (it replaces this file) and AI_USAGE.md:

- README.md: run and test commands, tools used (1 line), what is real or mocked, what you left out, real minutes per task.
- AI_USAGE.md: fill in AI_USAGE_TEMPLATE.md.

## Rules

- AI tools are allowed and encouraged. You may paste this data into them. Do not add real data or commit secrets (API keys, passwords).
- Honest unfinished work is better than work that hides missing parts.
- Unsafe data disclosure, P2 automation, unreviewed model actions or committed secrets can disqualify a submission. We assess reasoning and working evidence; extra features and paid tools earn no extra points.

## Evaluation

| Task | Points |
|---|---|
| 1. Data findings | 15 |
| 2. Safe build | 25 |
| 3. Company AI plan | 25 |
| 4. Decisions | 20 |
| 5. Memo | 10 |
| 6. README and AI usage | 5 |
| **Total** | **100** |

## Submission

Create your own repository and send its link to your recruiter. Prefer a private repository with read access for the GitHub user they name; a public repository is accepted. Do not open a pull request with your solution in this test repository. If you cannot use GitHub, email them a git bundle.

Your repo must have: README.md, FINDINGS.md, PLAN.md, MEMO.md, AI_USAGE.md, src/, tests/, out/ (committed), analysis/ and data/ (our 4 files, unchanged).

## Live follow-up

Interview: 60 minutes on video. Present PLAN.md as if to all staff (10 minutes), explain your repo, and make 1 small code change.

## FAQ

**I do not read Thai, Vietnamese or Chinese.** Use any free translation tool.

**Something is unclear.** Write your assumption in your README.md and continue. Reasoned alternatives are accepted.
