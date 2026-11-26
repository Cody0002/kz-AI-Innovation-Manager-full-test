# AI & Innovation Manager | Your first 90 days

You lead a four-person team and report to management. The CEO wants AI to be part of everyday work across the company. Where would you start, and how would you know it was helping?

**Time:** We expect this to take about 3 to 4 hours, including roughly 20 minutes to read the brief and set up. Please submit within **five calendar days** of receiving it.

## What to submit

Complete all three modules. They are parts of the same case. Use free or local tools. You’re welcome to use documentation, translation tools and AI assistance.

| Module | What to submit | Points |
|---|---|---:|
| A. [Choose your priorities](#module-a-choose-your-priorities) | `FINDINGS.md`, your calculations in `analysis/`, and `PLAN.md` | 50 |
| B. [Write to management](#module-b-write-to-management) | `MEMO.md` with two appendices | 25 |
| C. [Build a safe ticket-routing sample](#module-c-build-a-safe-ticket-routing-sample) | Your code, tests, outputs, `README.md` and `AI_USAGE.md` | 25 |

## Your first Monday

It’s Monday, 12 October 2026. You’ve joined a company that runs a real-money wallet app. Your work covers Customer Support (CS), Ops Analysts, Payments & Risk, VIP and Marketing.

- **Customer Support** wants AI to help sort incoming tickets this month. The CS lead estimates it could save 45 hours a week.
- **The CEO** wants a vendor called TriageGenie live in two weeks. The vendor claims 94% accuracy. CS can spare one agent for a pilot. Security can review the use of customer tickets in week 3. In your plan, treat the supplied tickets as customer records. Before that review, external tests may use only invented examples created independently of those records.
- **Teams** have submitted eight automation requests. Your team has a total of 160 build hours through 10 January 2027.
- **Last month’s report** says 78% of staff use AI. The CEO wants all five teams to use AI safely and usefully every week by the end of the 90 days.

### Data, costs and tools

The [data guide](DATA_GUIDE.md) covers the ticket sample, AI seats, automation requests and vendor quote. Treat the fictional customer records as real when applying the policies below.

| For your estimates | What to use |
|---|---|
| Support tickets | 720 per week across English, Thai, Vietnamese and Chinese |
| Support coverage | 24/7, with 8 agents, USD 7.50 per hour each, 52 weeks a year |
| Your team | Four people at USD 25 per hour each |
| AI seats | WorkAI Team, the approved tool in the case, costs USD 30 per person per month. Assume one seat per staff member. It runs outside company systems and does not train on company data. |
| Model costs | If your proposed solution uses a large language model (LLM), assume USD 20 a month. |

Our teams use ChatGPT, Codex, Claude, GitHub Copilot and the OpenAI API. We use BigQuery, Sheets and Excel for data, Lark for messages, and monday.com for tasks. Automations use Apps Script, JavaScript, Python, APIs and webhooks. We host on AWS EC2 with Ubuntu/Linux and Docker. If your plan relies on an integration, say what you’re assuming.

### Two policies apply throughout

- **P1. Customer data.** Remove personal data before sending anything outside company systems, including to an AI tool.
- **P2. Spending-related requests.** If a customer asks to limit, pause or close their account because of their spending, a person must handle the request within 24 hours. Leave replies and account changes to the person handling the request.

## Module A. Choose your priorities

#### Check the claims (10 points)

In `FINDINGS.md` (up to **350 words**), answer three questions:

1. How much time could CS realistically save on sorting tickets?
2. What does the 78% figure tell you? How would you measure weekly staff use, and what can you learn from the available data?
3. What needs attention first? Name one question whose answer could change your decision.

Cite record IDs or counts. Put your calculations in `analysis/` as a spreadsheet with formulas, a script or SQL so we can follow your numbers.

#### Plan the first 90 days (40 points)

Use these four headings in `PLAN.md` (up to **800 words**, including tables).

**1. What would you try first?**

Propose two ideas beyond the eight requests, including one that helps multiple teams. For each, explain who would benefit, what problem you see, what evidence or assumption you’re using, the likely benefit and the main risk. What’s the smallest test you’d run, and what result would justify taking the idea further? Explain how you’d check these needs with staff and find others. Compare your ideas with the eight requests and say what you’d start or defer. You can refer to the estimates in Appendix B.

**2. How would you help people use AI?**

Use the data to show where each team is starting. How would you get staff involved, make AI useful in their daily work and respond if use dropped? Say whether you’d keep the CEO’s target and why.

**3. How would you lead the work?**

Use a three-row table for weeks 1–2, 3–6 and 7–12. Give each phase a milestone, owner, measurable target and a way to check progress. For your first initiative, name one dependency, an early sign of delay and what you’d do next.

Show how the four people share delivery and IT support, who owns the work after launch and one skill you’d coach. Identify any decisions you need from Data, Product or Security.

**4. How would you know it’s working?**

Week 12 is your final checkpoint. Explain how the targets in your table capture usage, usefulness and quality. What result would make you continue, adjust or stop your first initiative? Explain how you’d manage your two biggest risks, what data staff can use and when someone must review the output.

## Module B. Write to management

#### Your message (10 points)

Open `MEMO.md` with the message you’d send to management (up to **250 words**). What can you promise by week 2, given the CEO’s deadline, CS staffing and Security’s review date? Explain the tradeoff and how you’d get the CEO, CS and Security to a decision.

Give your vendor recommendation, the impact you expect and how confident you are. Include where adoption stands today and your week-12 goal. End with two specific requests: who needs to do what, and by when?

#### The two appendices (15 points)

**Appendix A. Is TriageGenie worth buying?**

Recommend buying, piloting or declining. Give your reasons and say what could change your mind (up to **150 words**, plus one table). Compare first-year costs and the value of staff time saved for the vendor and an in-house build. Show your formulas and allow for support and human review. A shared savings estimate is fine if it fits both options. Would spending actually fall? For a pilot, give a duration and measurable safety and quality targets.

**Appendix B. What fits in 160 hours?**

Use one row for each of the eight requests and your two ideas. Use these columns:

| Request or idea | Decision (90 days, later or decline) | AI’s role (none, assists or decides) | Weekly benefit | Build hours | Owner | Reason |
|---|---|---|---|---|---|---|

For each new idea, estimate the hours for its first experiment. Count those hours toward the 160 only if you select that experiment. If a benefit is unknown, say how you’d check it.

Total the build hours for the work you select, including experiments, testing and integration. Include any work you committed to in `PLAN.md`. List training and support time separately, explain any changes to scope or estimates, and count each benefit once.

## Module C. Build a safe ticket-routing sample

#### Route the tickets (20 points)

Use `data/tickets.csv` to show which tickets need a person and which could safely go to a model for labeling. Complete this sample whatever you recommend in your plan. A local script in any language is enough.

- Run it with one offline command, using the supplied files and simulated external systems. It must work without an API key.
- Account for every row, mark duplicates and convert timestamps to UTC.
- Route P2 tickets and any other cases you judge need human review to a person. Record why and exclude them from anything you would send to a model.
- For eligible tickets, remove personal data before preparing the model input. Show this on at least two tickets. Keep money amounts and transaction references readable.
- Keep customer instructions from changing the routing rules. A person must approve replies, account changes and money movements.
- Write at least three automated tests. Together they should cover two kinds of personal data, P2 requests in multiple languages and a ticket that tries to override your instructions.

Save the routing results, proposed model inputs and test output in `out/`. The [submission guide](SUBMISSION_GUIDE.md#module-c-output-formats) gives the exact filenames, columns and labels. The prototype only prepares inputs for a model. You can leave the predicted category blank.

#### Explain how to run it (5 points)

In your `README.md`, give the setup, run and test commands. Say what you simulated, what you checked and where the sample has limits. Include a short [handoff to the team](SUBMISSION_GUIDE.md#production-handoff). Fill in the [AI usage template](AI_USAGE_TEMPLATE.md) and save it as `AI_USAGE.md`, whether or not you used AI.

## When you’re ready

Send your recruiter the link to your own repository. Use the [submission checklist](SUBMISSION_GUIDE.md#before-sending) to check the files and access.

If you’re invited to interview, we’ll spend 60 minutes on your work. You’ll brief staff in English, explain one of your decisions, make a small code or test change and respond to a stakeholder when a project falls behind. You can use your usual tools, including AI.
