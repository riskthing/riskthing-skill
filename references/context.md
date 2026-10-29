# Company and project context

RiskThing keeps two short context strings, and every in-app AI helper reads them: the **company context** for the organization, and a **project context** for each project. They are also what you draft and score against. A model that knows nothing about the company decides what a realistic risk looks like, and how severe it is, from these strings alone. Good context gives risks and mitigations that name the company's own dates, dependencies and scale. Thin context gives generic rows.

## Where they live

| String | Limit | Read | Write |
|---|---|---|---|
| Project context | 1,000 characters | `find_projects` returns `project_context` | `manage_project` `action="update"` with `project_context` and `expected_version`, or the **Project Management** page in the admin portal |
| Company context | 1,000 characters | Not returned by the tools. Ask the user | An administrator, in the admin portal: **Configure AI Settings** → **AI Company Context** → **Save AI Preferences** |

For the company context, draft the string and tell the user to have their RiskThing administrator paste it at <https://app.riskthing.com/admin_portal/ai-preferences/>. Do not claim you saved it.

## When to nudge

- **Onboarding:** before the first draft, read the project context. If it is empty or has no dated objective, offer to write it. Ask whether the company context is filled in.
- **Check-in:** if an objective in the project context has a date that has passed, or a new commitment came up, offer to update it.
- **Generic drafts:** if your drafts could be pasted into another company's register unchanged, the context is the likely cause. Say so in one line and offer to fix it.

One offer per session. Do not block other work on it.

## Two channels

The strings have separate jobs. Content in the wrong one is a defect.

**Company context: how the company is run. Never the product.** Fundraising and capital, board and investors, hiring, finance and grant administration, legal and corporate structure, regulatory and export-control posture, IT and security compliance, sales, marketing and partnerships.

**Project context: the product or program.** Current goals, driving requirements, success measures and constraints: committed dates, outside suppliers it depends on, and the resources it shares with other work.

## What earns a place

Context supplies the facts risks are scored against. It does not supply the risks. Never write a list of concerns, worries or threats: the register generates those, and a list narrows every draft to the risks someone already imagined.

For each clause, name the output it changes. Keep it only if you can. In the order they claim the budget:

1. **Dated objectives.** What the company or project has said it will deliver, raise, fly, ship or close, and by when. Every consequence rationale names the objective a risk threatens. A string without one leaves nothing to anchor to.
2. **Dated capital and instruments.** Each raise, award and contract with its amount, date and end date, the largest above all. The consequence scales are sized for large programs. The largest instrument is what a cost is compared against.
3. **Size as a band.** "10–30 people", or a published hiring plan. Never a headcount.
4. **Quantified requirements, with units.** Capacity, accuracy, throughput, mass, dates.
5. **Named outside dependencies.** Suppliers, partners, launch or delivery providers, customers, regulators. Schedule and compliance risk start there.
6. **Where the company operates, and under what controls.**
7. **What is still undecided.** Requirements marked to be determined or not yet baselined. This lets a score justify its likelihood.
8. **Whether the work is crewed or safety-of-life.** That decides whether whole consequence areas apply.

Leave out adjectives without numbers, marketing language, mission statements, founding stories, awards, street addresses, and named people. Write the role and what changed: "CFO appointed August 3, 2026". Leave out anything secret, personal or export-controlled; the strings are sent to the AI provider. A string that ends when the facts end is right at 700 characters.

## Help the user write it

1. Ask what they will deliver, raise or commit to in the next year, with dates. Then the capital behind it, the outside dependencies, and what is still undecided.
2. If they point at a plan, a pitch deck, a proposal or the company website, read it and pull out the facts above. Each figure keeps its date.
3. Draft both strings. Show each with its character count.
4. Check the draft against the list below, and revise.
5. On the user's yes, write the project context with `manage_project`. Give the user the company context to paste into the portal.

## Check before you hand it over

| Check | Fails when |
|---|---|
| Dated objective | Nothing the company or project will deliver, with its date |
| Channel | Product detail in the company context, or fundraising, hiring or legal in the project context |
| Concerns | Any list of worries, threats or things that could go wrong |
| Invented figures | A number the user or a source did not give. Mark an estimate as one |
| Stale dates | A figure with no date, or a target date that has passed |
| Scale | No capital, no size band, or no word on whether people's safety is at stake |
| Dead weight | A clause that changes no draft or score |
| Headcount or address | Any employee count, or a street address |
| Mechanics | Over 1,000 characters, line breaks, markdown or curly braces |
| Their own read | Something the founder would see as wrong, out of date or presumptuous |
