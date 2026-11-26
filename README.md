# AI & Innovation Manager: Your First 90 Days

What should the company do with AI in the next 90 days? Make a recommendation to management, show how your team would deliver it and demonstrate one safety decision in a small working prototype.

The scenario and data are fictional. Treat the records as customer data when applying the case policies.

## 1. Start here

Complete all three modules for one case. Use the [data guide](DATA_GUIDE.md) for the four source files and the [submission guide](SUBMISSION_GUIDE.md) for file formats and access.

| Module | Submit | Points |
|---|---|---:|
| A. [Diagnose and propose a 90-day plan](#module-a-diagnose-and-propose-a-90-day-plan) | FINDINGS.md, analysis/, PLAN.md | 50 |
| B. [Make the investment decisions](#module-b-make-the-investment-decisions) | MEMO.md, including both appendices | 25 |
| C. [Demonstrate hands-on judgment](#module-c-demonstrate-hands-on-judgment) | src/, tests/, out/, README.md, AI_USAGE.md | 25 |

**Estimated effort is 3 to 4 hours**, including about 20 minutes for reading and setup. Submit within **five calendar days** of receiving the assignment.

Use free or local tools. Documentation, translation tools and AI assistance are welcome.

## 2. Your situation

You lead a four-person team and report to management. Your first week starts on Monday, 12 October 2026. Use that date as the starting point for your plan.

The company runs a real-money wallet app. Your adoption plan covers Customer Support (CS, operating 24/7), Ops Analysts, Payments & Risk, VIP and Marketing.

- The CS lead wants AI to help sort incoming support tickets this month and claims it will save 45 hours each week.
- The CEO wants TriageGenie live in two weeks, citing its claim of 94% accuracy. The CS lead can spare one agent for a pilot. Security can review the proposed use of customer tickets in week 3. Until then, external testing is limited to synthetic tickets.
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
- WorkAI Team is the fictional approved AI tool used in the case and seat data. Assume USD 30 per seat per month and one seat per staff member. It runs outside company systems, so P1 applies. It does not train on company data.
- If your proposed solution uses an LLM (an AI text model), assume USD 20 a month for the case.

### Company tools

| Area | Tools we use |
|---|---|
| AI and development | ChatGPT, Codex, Claude, GitHub Copilot and the OpenAI API, which we access with API keys |
| Data and reporting | BigQuery, Google Sheets and Excel |
| Automation and integrations | Google Apps Script, JavaScript, Python, APIs and webhooks |
| Team workflows | Lark for communication and alerts, monday.com for tracking tasks |
| Hosting | AWS EC2, Ubuntu/Linux and Docker |

Use these tools as context for your plan. State integration assumptions. For the offline prototype, choose your language and mock external systems. Keep the supplied data unchanged.

## 4. The three modules

### Module A. Diagnose and propose a 90-day plan

#### Findings (10 points)

Write FINDINGS.md (max 350 words). Put your calculations in analysis/ as a spreadsheet with formulas, a script or SQL so someone else can check them.

Check the triage savings and AI usage claims. Show your calculations and cite supporting record IDs or counts. Explain how you measured adoption and what the data can tell you. Name the most urgent issue and one question whose answer would change your decision.

#### Company AI plan (40 points)

Write PLAN.md in four sections (max 800 words, including tables).

**1. Opportunities and choices**

Propose two distinct opportunities beyond the eight requests. At least one should help multiple teams. For each, give the problem, users, evidence or assumption, expected value, main risk and smallest useful experiment. Explain how you would discover and validate further needs with staff.

Compare your ideas with the existing requests. Recommend what to start first and explain what you would defer.

**2. Adoption and useful work**

Use the data to describe where the five teams are starting. Explain how you would earn participation, help teams use AI in their daily work and respond if use fell. Assess whether the CEO's target makes sense and justify any change to the pace or target.

**3. Execution and leadership**

Use a three-row table for weeks 1 to 2, 3 to 6 and 7 to 12. For each phase, give a milestone, an accountable owner and the evidence you would check with them. For your first initiative, identify one dependency that could delay it, the first sign of a slip and the decision you would make if it slipped.

Show how your four-person team shares delivery and ongoing IT support, who owns the work after launch and one skill you would coach. Name the decisions you need from Data, Product or Security where relevant.

**4. Measures and safeguards**

Put measurable targets in the same table. Use week 12 as your final reporting checkpoint. Explain how you would measure usage, usefulness and quality, and what result would make you continue, change or stop the first initiative. Address your two biggest risks, including what data teams can use and when a person needs to review AI output.

### Module B. Make the investment decisions

#### Management memo (10 points)

Write the opening of MEMO.md as the message you would send to management (max 250 words). Given the CEO's two-week target, CS staffing and Security's review date, what can you commit to by week 2? Explain the tradeoff and how you would get the three stakeholders to a decision. Include your vendor recommendation, expected impact and uncertainty, adoption baseline and week-12 goal. Close with two specific requests, each with an owner and a date. Put the detailed calculations in the appendices.

#### Vendor and portfolio decisions (15 points)

**Appendix A. Vendor decision** (max 150 words plus one table). Recommend whether to buy, run a pilot or decline. Explain what evidence supports your choice and what could change it. Use one table to compare 12-month vendor and in-house costs with the value of staff time each option could save. One savings estimate is enough if it applies to both options. Show your formulas and assumptions, including support and human review. Explain whether spending would fall. For a pilot, give a duration and measurable safety and quality criteria.

**Appendix B. Portfolio** (one compact table). For each of the eight requests and your two new ideas, show decision (90 days, later or no), AI role (none, assists or decides), estimated weekly benefit, build hours, owner and reason. Unknown benefits may be stated as unknown with a validation method.

In Appendix B, total the build hours for selected work, including experiments, testing, integration and builds proposed in PLAN.md. Stay within 160 hours. Explain revised scope or estimates, list training and support effort separately, and count each benefit once.

### Module C. Demonstrate hands-on judgment

#### Safe triage sample (20 points)

Build one step using data/tickets.csv that decides which tickets need a person and which may safely go to a model for labeling. A local script is enough. Everyone uses this sample, whatever they recommend in their plan.

- Run with one offline command and no API key.
- Account for every input row, identify duplicates and convert timestamps to UTC.
- Redact personal data before forming any LLM payload. Preserve money amounts and transaction references. Demonstrate redaction on at least two eligible tickets.
- Flag P2 cases and any other cases that need human review. Record the reason and exclude them from model payloads.
- Treat customer instructions as untrusted input. Keep replies, account changes and money approvals under human control.
- Include at least three automated tests. Cover two kinds of personal data, P2 requests in multiple languages and a ticket that tries to override the triage instructions.

Commit out/triage.csv, out/llm_payloads.jsonl and out/test_output.txt using the [output formats](SUBMISSION_GUIDE.md#module-c-output-formats). Generate proposed payloads even without a model call. The prompt must request one label: deposit, withdrawal, account_access, bonus or other. Include the category column, but its values may be blank and are not scored.

In your README.md, include a short [production handoff](SUBMISSION_GUIDE.md#production-handoff) explaining how your prototype could be operated.

#### Reproducibility and AI disclosure (5 points)

Write your own README.md using the submission guide, and complete AI_USAGE_TEMPLATE.md as AI_USAGE.md. Document assumptions, checks and known limitations.

## 5. How we evaluate

We look for original ideas grounded in staff needs, sustained adoption, credible delivery commitments and sound investment decisions. In the prototype we check reproducibility, P1 and P2 compliance and human control of consequential actions. Use placeholders for credentials.

## 6. Submit and discuss

Send your recruiter your own repository link using the [submission checklist](SUBMISSION_GUIDE.md#before-sending).

If invited to a 60-minute interview, use your submission to brief staff in English, explain your decisions, make a small code or test change and respond to a stakeholder when a project goes off track. You may use your usual development tools, including AI.
