# AI & Innovation Manager: Your First 90 Days

We want a leader who identifies opportunities and helps the whole company use AI productively. Recommend a direction, explain its value and show how you would deliver it.

All company information and data in this exercise are fictional.

## 1. Start here

Read the scenario and policies, then review the four supplied files using [DATA_GUIDE.md](DATA_GUIDE.md). Complete all three modules for the same case. You choose which opportunities to pursue and how to deliver them.

| Module | Submit | Points |
|---|---|---:|
| A. Diagnose and propose a 90-day plan | FINDINGS.md, analysis/, PLAN.md | 50 |
| B. Make the investment decisions | MEMO.md, including both appendices | 25 |
| C. Demonstrate hands-on judgment | src/, tests/, out/, README.md, AI_USAGE.md | 25 |

**Estimated effort is 3 to 4 hours**, including about 20 minutes for reading and setup. Submit within **five calendar days** of receiving the assignment.

Use free or local tools and mock external systems. The run command must work offline. You may use documentation, AI and translation tools during preparation. AI use is optional. A small local script is sufficient.

File formats and the final checklist are in [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md).

## 2. Your situation

It is Monday 2026-10-12, your first week. Use that date for your plans. You report to the Head of Operations Analysts and lead a four-person team across automation, AI enablement and IT operations.

The company runs a real-money wallet app. Its five teams are Customer Support (CS, operating 24/7), Ops Analysts, Payments & Risk, VIP and Marketing.

You receive these messages:

- The CS lead wants AI to help sort incoming support tickets this month and claims it will save 45 hours each week.
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

## 4. The three modules

### Module A. Diagnose and propose a 90-day plan

#### Findings (10 points)

Write FINDINGS.md (max 350 words) and put a reproducible script or SQL in analysis/.

Assess the management claims with calculations and record IDs/counts. Explain the most urgent issue, its significance and your first business question. Define current AI adoption and the measure's limitations.

#### Company AI plan (40 points)

Write PLAN.md (max 800 words, including tables) with the four sections below. Choose an adoption approach that fits your findings.

**1. Opportunities and choices**

Propose two opportunities beyond the eight supplied requests. Each should address a different problem or introduce a materially different way of working. At least one should help more than one team or improve a shared company capability. For each, state the problem and intended users, supporting evidence or assumption, expected value, main risk and the smallest experiment that would test it. Explain how you would discover and validate further needs with staff.

Choose what to start first across your ideas and the existing requests. Explain what you would defer. Submit your ideas as proposals in PLAN.md and Appendix B.

**2. Adoption and useful work**

Explain how you would help all five teams adopt useful, safe AI workflows, earn participation and respond if use declined. You may propose a different pace or target for the CEO's weekly-use ambition. Explain the evidence and how you would measure success. Ground your starting point in the data. Define success beyond activity counts. Your two opportunities may also support this part of the plan.

**3. Execution and leadership**

Set out your plan for weeks 1 to 2, 3 to 6 and 7 to 12. Include owners, dependencies on Data, Product and Security, your four-person team's responsibilities and one development or coaching action. Define what evidence would lead you to continue, change or stop your first initiative. Show how you protect ongoing IT support while delivering the plan.

**4. Measures and safeguards**

Set measurable week-2, week-6 and week-12 targets, define how you will measure them, and address your top two risks. State the data boundaries and human review your plan requires.

### Module B. Make the investment decisions

#### Management memo (10 points)

At the top of MEMO.md, write a memo of max 250 words to your manager and the CEO. Lead with your recommendation and first delivery. Summarize the expected impact and its uncertainty, adoption baseline and week-12 goal, vendor decision, top risks and two requests for support with owners and dates. Keep definitions and numbers consistent with the supporting work.

#### Vendor and portfolio decisions (15 points)

**Appendix A: Vendor decision** (max 150 words plus one table). Recommend buy, pilot or do not buy, with the evidence and conditions that would change your mind. Use a three-row, 12-month cost table: vendor, own triage build and value of triage time saved. Show formulas and assumptions, including support and human review. Separate released capacity from cash savings. If proposing a pilot, state its duration and numerical safety and quality pass criteria.

**Appendix B: Portfolio** (one compact table). For each of the eight requests and your two new ideas, show decision (90 days, later or no), AI role (none, assists or decides), estimated weekly benefit, build hours, owner and reason. Unknown benefits may be stated as unknown with a validation method.

In Appendix B, total the build hours for selected work, including experiments, testing, integration and builds proposed in PLAN.md. Stay within 160 hours. Explain revised scope or estimates, list training and support effort separately, and count each benefit once.

### Module C. Demonstrate hands-on judgment

#### Safe triage sample (20 points)

Build a small, safe triage step using data/tickets.csv. Everyone works from the same technical brief. You decide whether triage belongs in your 90-day plan.

Your solution must:

- run with one offline command and no API key;
- account for every input row, identify duplicates and convert timestamps to UTC;
- redact personal data before forming any LLM payload, preserving money amounts and transaction references;
- identify human-only cases under P2 or your own justified safety rules and exclude them from payloads;
- treat instructions inside customer messages as untrusted input; model output must not send replies, change accounts or approve money;
- demonstrate redaction on at least two eligible tickets; and
- include at least three automated tests covering two kinds of personal data, multilingual P2 requests and instructions inside tickets.

Commit out/triage.csv, out/llm_payloads.jsonl and out/test_output.txt using the [output formats](SUBMISSION_GUIDE.md#module-c-output-formats). Generate proposed payloads even without a model call. The prompt must request one label: deposit, withdrawal, account_access, bonus or other. Include the category column, but its values may be blank and are not scored.

In your README.md, propose where this would run, how you would store any keys, what happens on failure, who owns the human queue and how they would detect overdue P2 cases. Explain one important limitation.

#### Reproducibility and AI disclosure (5 points)

Write your own README.md using the submission guide, and complete AI_USAGE_TEMPLATE.md as AI_USAGE.md. Document assumptions, checks and known limitations.

## 5. How we evaluate

The assessment totals 100 points. PLAN.md's 40 points cover independent opportunity discovery and experiments (15), useful adoption across teams (10), people leadership (5), execution (5), and safeguards (5).

To progress, candidates need at least 65/100 overall, 24/40 on the company plan, 8/15 on independent opportunity discovery and 6/10 on adoption, with no serious safety breach. Advancing also requires at least one qualifying new opportunity. We assess the reasoning behind your choices. We use the interview to verify ownership and explore uncertainty.

Unsafe disclosure, P2 automation, unreviewed model actions or committed secrets can disqualify a submission. Extra features, paid tools, slides and polished UI earn no extra credit. Honest limits are preferable to unsupported claims.

## 6. Submit and discuss

Follow [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md) for repository access and the final checklist. Send your own repository link to the recruiter. Do not submit a solution as a pull request to this test repository.

The 60-minute follow-up includes a short staff presentation, questions about your decisions and code, one small code change and a discussion of how you would adapt when circumstances change. Normal development tools, including AI, may be used. No slide deck or recording is required.
