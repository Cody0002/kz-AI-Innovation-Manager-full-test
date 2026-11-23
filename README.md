# AI & Innovation Manager: Your First 90 Days

Show how you would find valuable opportunities, lead useful AI adoption across teams and turn your recommendations into a 90-day plan.

All company information and data in this exercise are fictional.

## 1. Start here

Read the scenario and policies, then review the four supplied files using [DATA_GUIDE.md](DATA_GUIDE.md). Complete all three modules for the same case. You choose which opportunities to pursue and how to deliver them.

| Module | Submit | Points |
|---|---|---:|
| A. Diagnose and propose a 90-day plan | FINDINGS.md, analysis/, PLAN.md | 50 |
| B. Make the investment decisions | MEMO.md, including both appendices | 25 |
| C. Demonstrate hands-on judgment | src/, tests/, out/, README.md, AI_USAGE.md | 25 |

**Estimated effort is 3 to 4 hours**, including about 20 minutes for reading and setup. Submit within **five calendar days** of receiving the assignment.

Use free or local tools. You may use documentation and translation tools while preparing your work. AI assistance is optional.

File formats and the final checklist are in [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md).

## 2. Your situation

It is Monday 2026-10-12, your first week. Use that date for your plans. You report to the Head of Operations Analysts and lead a four-person team across automation, AI enablement and IT operations.

The company runs a real-money wallet app. Its five teams are Customer Support (CS, operating 24/7), Ops Analysts, Payments & Risk, VIP and Marketing.

These are the requests and claims on your desk.

- The CS lead wants AI to help sort incoming support tickets this month and claims it will save 45 hours each week.
- The CEO wants to sign with TriageGenie: 94% accuracy and delivery in two weeks.
- Teams have submitted eight automation requests. You have 160 build hours for the next 90 days, ending 2027-01-10.
- Last month's report says 78% of staff use AI. The CEO wants all five teams using AI safely and usefully every week within 90 days.

Decide what deserves attention. Distinguish facts, assumptions and questions you would verify.

## 3. Policies and operating facts

### Company policies

- **P1:** Customer personal data must be redacted before leaving company systems, including through AI tools.
- **P2:** When a customer asks to limit, pause or close their account because of their spending, a human must handle it within 24 hours. No automatic reply or account change.

### Facts you may use

- Tickets: 720 per week in English, Thai, Vietnamese and Chinese.
- Ticket queue: 8 agents, USD 7.50 per hour each, 52 weeks a year.
- Your team: four people, USD 25 per hour each. You allocate their work.
- If your own build uses an LLM (an AI text model), assume USD 20 a month.
- app_chat timestamps are UTC. web_form timestamps use GMT+7, dd/mm/yyyy HH:MM.
- Transaction references are TX followed by ten digits.

### Tools in this scenario

- WorkAI Team is the approved AI tool. It costs USD 30 per seat per month, with one seat per staff member. The service runs outside company systems, so P1 applies. It does not train on company data.
- Ops uses BigQuery for reporting and Lark for team communications. IT supports staff access to Google, Lark, WorkAI and internal admin tools.

Use this context when proposing integrations or changes to staff workflows. State any assumptions about access or capabilities. Build locally in a language of your choice and mock external systems. Keep the four supplied data files unchanged.

## 4. The three modules

### Module A. Diagnose and propose a 90-day plan

#### Findings (10 points)

Write FINDINGS.md (max 350 words) and put a reproducible script or SQL in analysis/.

Check the triage savings and AI usage claims. Show your calculations and cite supporting record IDs or counts. Explain how you measured adoption and what the data can tell you. Name the most urgent issue and one question whose answer would change your decision.

#### Company AI plan (40 points)

Write PLAN.md (max 800 words, including tables) with the four sections below. Choose an adoption approach that fits your findings.

**1. Opportunities and choices**

Propose two opportunities beyond the eight supplied requests. Each should address a different problem or introduce a materially different way of working. At least one should help more than one team or improve a shared company capability. For each, state the problem and intended users, supporting evidence or assumption, expected value, main risk and the smallest experiment that would test it. Explain how you would discover and validate further needs with staff.

Compare your ideas with the existing requests. Recommend what to start first and explain what you would defer.

**2. Adoption and useful work**

Use the data to describe where the five teams are starting. Explain how you would earn participation, help teams use AI in their daily work and respond if use fell. Assess whether the CEO's target makes sense and justify any change to the pace or target.

**3. Execution and leadership**

Set out your plan for weeks 1 to 2, 3 to 6 and 7 to 12. Assign responsibilities across your four-person team, identify what you need from Data, Product and Security, and include one coaching or development action. Explain who will own the work after launch, how you will cover IT support and what evidence would make you continue, change or stop the first initiative.

**4. Measures and safeguards**

Set measurable targets for weeks 2, 6 and 12. Show how you would measure usage, usefulness and quality. Address your two biggest risks and explain what data teams can use and when a person needs to review AI output.

### Module B. Make the investment decisions

#### Management memo (10 points)

At the top of MEMO.md, write a memo of max 250 words to your manager and the CEO. Lead with your recommendation and first delivery. Summarize the expected impact and its uncertainty, adoption baseline and week-12 goal, vendor decision, top risks and two requests for support with owners and dates. Keep definitions and numbers consistent with the supporting work.

#### Vendor and portfolio decisions (15 points)

**Appendix A. Vendor decision** (max 150 words plus one table). Recommend whether to buy, run a pilot or decline. Explain what evidence supports your choice and what could change it. Show three figures over 12 months in one table: vendor cost, in-house triage cost and value of the staff time saved. State your formulas and assumptions, including support and human review. Explain how much time the team would free up and whether spending would fall. For a pilot, give a duration and measurable safety and quality criteria.

**Appendix B. Portfolio** (one compact table). For each of the eight requests and your two new ideas, show decision (90 days, later or no), AI role (none, assists or decides), estimated weekly benefit, build hours, owner and reason. Unknown benefits may be stated as unknown with a validation method.

In Appendix B, total the build hours for selected work, including experiments, testing, integration and builds proposed in PLAN.md. Stay within 160 hours. Explain revised scope or estimates, list training and support effort separately, and count each benefit once.

### Module C. Demonstrate hands-on judgment

#### Safe triage sample (20 points)

Build a small, safe triage step using data/tickets.csv. Everyone works from the same technical brief. You decide whether triage belongs in your 90-day plan.

The sample needs to meet these requirements.

- Run with one offline command and no API key.
- Account for every input row, identify duplicates and convert timestamps to UTC.
- Redact personal data before forming any LLM payload. Preserve money amounts and transaction references. Demonstrate redaction on at least two eligible tickets.
- Flag P2 cases and any other cases that need human review. Record the reason and exclude them from model payloads.
- Treat customer instructions as untrusted input. Keep replies, account changes and money approvals under human control.
- Include at least three automated tests. Cover two kinds of personal data, P2 requests in multiple languages and instructions inside tickets.

Commit out/triage.csv, out/llm_payloads.jsonl and out/test_output.txt using the [output formats](SUBMISSION_GUIDE.md#module-c-output-formats). Generate proposed payloads even without a model call. The prompt must request one label: deposit, withdrawal, account_access, bonus or other. Include the category column, but its values may be blank and are not scored.

In your README.md, include a short [production handoff](SUBMISSION_GUIDE.md#production-handoff) explaining how your prototype could be operated.

#### Reproducibility and AI disclosure (5 points)

Write your own README.md using the submission guide, and complete AI_USAGE_TEMPLATE.md as AI_USAGE.md. Document assumptions, checks and known limitations.

## 5. How we evaluate

We look for original opportunities tied to real work, a plan to sustain useful adoption, sound investment decisions and a small, reproducible prototype. Explain your assumptions, tradeoffs and safeguards so reviewers can follow your reasoning.

Use synthetic data and placeholders for any credentials. Reviewers will check compliance with P1 and P2 and look for human control of consequential actions.

## 6. Submit and discuss

Follow [SUBMISSION_GUIDE.md](SUBMISSION_GUIDE.md) for repository access and the final checklist. Send your own repository link to the recruiter. Do not submit a solution as a pull request to this test repository.

If invited to a 60-minute interview, use your submission to brief staff, explain your decisions, make a small code change and adapt your plan to new information. You may use your usual development tools, including AI.
