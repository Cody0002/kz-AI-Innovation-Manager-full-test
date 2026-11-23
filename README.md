# AI & Innovation Manager: Your First 90 Days

We want a leader who identifies opportunities and helps the whole company use AI productively. Recommend a direction, explain its value and show how you would deliver it.

All company information and data in this exercise are fictional.

## 1. Start here

1. Read the scenario and company policies below.
2. Inspect the four supplied files using [DATA_GUIDE.md](DATA_GUIDE.md).
3. Complete the six tasks. Use [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md) for file formats and the final checklist.
4. Make your own recommendations. The requests are stakeholder suggestions, not an approved roadmap.

| Task | Deliverable | Flexible time guide | Points |
|---|---|---|---|
| 1. Establish the facts | FINDINGS.md and analysis/ | 25 min | 10 |
| 2. Demonstrate hands-on judgment | src/, tests/, out/ | 50 min | 20 |
| 3. Propose your company AI plan | PLAN.md | 65 min | 40 |
| 4. Make investment decisions | Appendices A and B in MEMO.md | 40 min | 15 |
| 5. Recommend a direction to management | Opening of MEMO.md | 20 min | 10 |
| 6. Explain and verify your work | Your README.md and AI_USAGE.md | 20 min | 5 |

Allow 20 minutes for reading and setup. Expected effort is 3-4 hours; stop at four hours and disclose unfinished work. Adjust the allocations as needed. Submit within five calendar days of receiving the assignment.

Use free or local tools. No paid AI key, Lark account, cloud deployment or UI is required. The run command must work offline; documentation, AI and translation tools may be used during preparation. Mock external systems. AI use is optional and does not affect your score.

## 2. Your situation

It is Monday 2026-10-12, your first week. Use that date for your plans. You report to the Head of Operations Analysts and lead a four-person team across automation, AI enablement and IT operations.

The company runs a real-money wallet app. Its five teams are Customer Support (CS, operating 24/7), Ops Analysts, Payments & Risk, VIP and Marketing.

You receive these messages:

- The CS lead wants AI ticket triage this month and claims it will save 45 hours each week.
- The CEO wants to sign with TriageGenie: 94% accuracy and delivery in two weeks.
- Teams have submitted eight automation requests. You have 160 build hours for the next 90 days, ending 2027-01-10.
- Last month's report says 78% of staff use AI. The CEO wants all five teams using AI safely and usefully every week within 90 days.

Propose what else deserves attention. Evidence is incomplete: distinguish facts, assumptions and unanswered questions.

## 3. Policies and operating facts

### Company policies

- **P1:** Customer personal data must be redacted before leaving company systems, including through AI tools.
- **P2:** When a customer asks to limit, pause or close their account because of their spending, a human must handle it within 24 hours. No automatic reply or account change.

### Facts you may use

- Tickets: 720 per week in English, Thai, Vietnamese and Chinese.
- Ticket queue: 8 agents, USD 7.50 per hour each, 52 weeks a year.
- Your team: four people, USD 25 per hour each. You allocate their work.
- Approved AI tool: WorkAI Team, USD 30 per seat per month, one seat per staff member. It is external cloud software, so P1 applies. It does not train on company data.
- If your own build uses an LLM (an AI text model), assume USD 20 a month.
- app_chat timestamps are UTC. web_form timestamps use GMT+7, dd/mm/yyyy HH:MM.
- Transaction references are TX followed by ten digits.

The data/ folder contains tickets.csv, ai_seats.csv, requests.csv and vendor_quote.md. Keep all four files unchanged and document any cleaning in your analysis.

## 4. Tasks

### Task 1. Establish the facts

Deliver FINDINGS.md (max 350 words) and a reproducible script or SQL in analysis/.

Assess the management claims with calculations and record IDs/counts. Explain the most urgent issue, its significance and your first business question. Define current AI adoption and the measure's limitations.

### Task 2. Demonstrate hands-on judgment

Build a small safe triage step using data/tickets.csv. This is a common skills sample; it does not require you to prioritize triage in your 90-day roadmap.

Your solution must:

- run with one offline command and no API key;
- account for every input row, identify duplicates and convert timestamps to UTC;
- redact personal data before forming any LLM payload, preserving money amounts and transaction references;
- identify human-only cases under P2 or your own justified safety rules and exclude them from payloads;
- treat instructions inside customer messages as untrusted input; model output must not send replies, change accounts or approve money;
- demonstrate redaction on at least two eligible tickets; and
- include at least three automated tests covering two kinds of personal data, multilingual P2 requests and instructions inside tickets.

Commit out/triage.csv, out/llm_payloads.jsonl and out/test_output.txt using the [output formats](SUBMISSION_GUIDE.md#task-2-output-formats). Generate proposed payloads even without a model call. The prompt must request one label: deposit, withdrawal, account_access, bonus or other. Include the category column, but its values may be blank and are not scored.

Add a short production handoff in your README.md: where it would run, key storage if applicable, failure behavior, human-queue ownership and overdue P2 detection. Explain one important limitation. This is a proposal, not an integration to build.

### Task 3. Propose your company AI plan

Deliver PLAN.md (max 800 words, including tables) with these four sections. Choose your approach; we have not prescribed an adoption program or a tool rollout.

**A. Opportunities and choices**

Propose two opportunities beyond the eight supplied requests. They must address a different problem or a materially different way of working, not just rename a request or swap its tool. At least one should help more than one team or improve a shared company capability. For each, state the problem and intended users, supporting evidence or assumption, expected value, main risk and the smallest experiment that would test it. Explain how you would discover and validate further needs with staff.

Prioritize across your ideas and existing requests; explain deferrals. New ideas need not come first. Both are proposals; only Task 2 requires implementation.

**B. Adoption and useful work**

Address safe, productive AI use across all five teams: how you would earn participation and respond if use declined. You may challenge or sequence the CEO's weekly-use ambition where evidence supports a better outcome; explain your alternative and measures. Ground your starting point in the data. Define success beyond activity counts. Your two proposed opportunities may also appear here; no separate ideas per team are required.

**C. Execution and leadership**

Set out the first two weeks, the next month and the remaining 90-day period. Include owners, dependencies on Data, Product and Security, your four-person team's responsibilities, one development or coaching action, and a pilot decision rule for continuing, changing or stopping. Show how you protect ongoing IT support while delivering the plan.

**D. Measures and safeguards**

Set measurable week-2, week-6 and week-12 targets, define how you will measure them, and address your top two risks. State the data boundaries and human review your plan requires.

### Task 4. Make investment decisions

In MEMO.md, include:

**Appendix A: Vendor decision** (max 150 words plus one table). Recommend buy, pilot or do not buy, with the evidence and conditions that would change your mind. Use a three-row, 12-month cost table: vendor, own triage build and value of triage time saved. Show formulas and assumptions, including support and human review. Separate released capacity from cash savings. If proposing a pilot, state its duration and numerical safety and quality pass criteria.

**Appendix B: Portfolio** (one compact table). For each of the eight requests and your two new ideas, show decision (90 days, later or no), AI role (none, assists or decides), estimated weekly benefit, build hours, owner and reason. Unknown benefits may be stated as unknown with a validation method.

Show the selected build-hour total, including testing, integration and any extra builds in PLAN.md: max 160. Explain revised estimates/scope, list training/support effort separately and avoid double-counted benefits.

### Task 5. Recommend a direction to management

At the top of MEMO.md, write a memo of max 250 words to your manager and the CEO. Lead with your recommendation and first delivery. Summarize the expected impact and its uncertainty, adoption baseline and week-12 goal, vendor decision, top risks and two requests for support with owners and dates. Keep definitions and numbers consistent with the supporting work.

### Task 6. Explain and verify your work

Write your own README.md using the submission guide, and complete AI_USAGE_TEMPLATE.md as AI_USAGE.md. Disclose actual time, assumptions, checks and unfinished work.

## 5. How we evaluate

The task weights above total 100. PLAN.md's 40 points cover independent opportunity discovery and experiments (15), useful adoption across teams (10), people leadership (5), execution (5), and safeguards (5).

A strong technical exercise alone is insufficient. To progress, candidates need at least 65/100 overall, 24/40 on the company plan, 8/15 on independent opportunity discovery and 6/10 on adoption, with no serious safety breach. Without a qualifying new opportunity, initiative scores below eight. We assess reasoning, not whether you chose our preferred ideas. We use the interview to verify ownership and explore uncertainty.

Unsafe disclosure, P2 automation, unreviewed model actions or committed secrets can disqualify a submission. Extra features, paid tools, slides and polished UI earn no extra credit. Honest limits are preferable to unsupported claims.

## 6. Submit and discuss

Follow [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md) for repository access and the final checklist. Send your own repository link to the recruiter. Do not submit a solution as a pull request to this test repository.

The 60-minute follow-up includes a short staff presentation, questions about your decisions and code, one small code change and a discussion of how you would adapt when circumstances change. Normal development tools, including AI, may be used. No slide deck or recording is required.
