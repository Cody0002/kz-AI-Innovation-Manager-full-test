# Take-Home Test: AI & Innovation Manager

You are the incoming AI & Innovation Manager. Check competing business claims, build a small safe triage prototype, and recommend a practical company AI plan. We assess judgment, safety, delivery and leadership.

All data is made up.

## Start here

1. Read the scenario, policies and tasks below.
2. Review the four supplied files using [DATA_GUIDE.md](DATA_GUIDE.md).
3. Complete all six tasks. The table below maps each task to its deliverables.
4. Use [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md) for output formats and the final checklist.

| Task | Deliverables | Suggested time |
|---|---|---|
| 1. Check the data | FINDINGS.md and analysis/ | 15 min |
| 2. Safe triage prototype | src/, tests/ and three files in out/ | 55 min |
| 3. Company AI plan | PLAN.md | 40 min |
| 4. Vendor and request decisions | Appendices A and B in MEMO.md | 30 min |
| 5. Management memo | Opening section of MEMO.md | 10 min |
| 6. Explain your work | Your README.md and AI_USAGE.md | 10 min |

Allow another 20 minutes to read and set up. No UI, live integrations or cloud deployment are required.

## Time and Cost

- Time: aim for 180 minutes, including 20 to read and set up. Stop at 210 minutes and list unfinished work. Suggested task times are flexible; do not build a production system.
- Submit within 5 days, weekends included.
- Use only free or local (on your computer) tools, not n8n Cloud (paid). You need no Lark account, paid AI key or credit card.
- Mock (fake) outside systems, for example save a Lark chat message as a JSON file.
- An LLM (AI text model) is optional. Code rules alone are a complete answer. Even without an LLM, generate the safe example payloads required in Task 2.
- The submitted run command must work offline. You may use online documentation, AI or translation tools during preparation.

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

## Provided data

The data/ folder contains tickets.csv, ai_seats.csv, requests.csv and vendor_quote.md. See [DATA_GUIDE.md](DATA_GUIDE.md) for their contents and field meanings. Keep these four files unchanged; record cleaning decisions in your analysis.

## Tasks

### Task 1. Check the data first (15 min)

Deliver FINDINGS.md (max 400 words) and your script or SQL in analysis/. Answer:

1. Data problems: file, row IDs or row count, and what you did.
2. Which numbers in the Scenario would you give the CEO unchanged? For the others: your number and formula.
3. The first risk you would report to management today, and why. Then 1 question for the business before triage starts.

### Task 2. Build a safe triage step (55 min)

Deliver src/, tests/ and out/. Use any language that meets these requirements:

1. Run on data/tickets.csv with one offline command and no API key.
2. Keep a record of every input row, identify duplicates, and convert timestamps to UTC.
3. Hide customer personal data before creating any LLM payload. Keep money amounts and transaction references readable. Demonstrate redaction on at least two eligible tickets.
4. Mark P2 and other human-only tickets with a reason. Never include them in LLM payloads. Explain your human-routing choices.
5. Treat ticket text as untrusted input, including instructions inside it. No model output may send replies, change accounts or approve money.
6. Produce out/triage.csv and out/llm_payloads.jsonl using the [exact formats](SUBMISSION_GUIDE.md#task-2-output-formats).
7. Include at least three automated tests covering two kinds of personal data, multilingual P2 requests and instructions inside tickets. Save the command and full output in out/test_output.txt.

The payload prompt must ask for one label: deposit, withdrawal, account_access, bonus or other. Include the category column in triage.csv; its values may be blank and are not scored. No model call is required.

In your README.md, add **Deploy in our stack** (max eight lines): where it would run (Lark bot, n8n or Apps Script), where keys would be stored, the LLM failure fallback, the human-queue owner and how overdue P2 cases would be detected. This is a written proposal; implementation is not required.

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

Use consistent definitions and numbers across FINDINGS.md, PLAN.md and the appendices. Clearly label different scopes, such as triage savings versus total portfolio savings.

### Task 6. README and AI usage (10 min)

Deliver your own README.md using the submission checklist, and complete AI_USAGE_TEMPLATE.md as AI_USAGE.md.

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

Follow [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md) for the repository structure, document limits and final checklist. Write your own README.md in place of this brief; keep a separate copy of the instructions for reference.

Send your own repository link to the recruiter using the access instructions in the submission guide.

## Live follow-up

The 60-minute interview includes a ten-minute staff presentation, a repo explanation and one small code change. See the submission guide for details.

## Questions and assumptions

Free translation tools are allowed. If something is unclear, state your assumption and continue. Reasoned alternatives are accepted.
