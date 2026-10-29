# Onboarding a blank organization or new project

Goal: a first register the user recognizes as theirs, with a project that has context, 10–30 risks, and mitigations linked to the risks that matter most. The interview is the default. When the user has a plan, proposal, design review or schedule, import from it, then interview to fill the gaps.

## 1. Project

`find_projects`. If the work has no project yet, ask what the program, product or effort is called and create it with `manage_project` `action="create"`. Read `get_organization` first, because it shows how risk IDs are numbered. Then list categories with `find_taxonomy` `kind="category"`: every risk needs a `category_id`.

Send a **project context** with the create call (`project_context`), and check the company context. Both carry the dated objectives and the scale that every consequence is sized against → READ `context.md` before the first draft, and offer to write either string that is empty or thin.

Ask which writing style the organization uses: RiskThing, NASA RMH or DoD RIO (`writing.md` § Choose a style).

## 2. Interview from the user's chair

Ask about decisions before risks. A register built from decisions reads as the user's own; one built from research reads as paperwork.

Ask, one or two at a time:

1. What are you deciding or committing to in the next quarter? (first customer, first flight, the partner deal, what to promise before the hires land)
2. What has to go right for the next milestone, and by when?
3. What depends on someone outside the team: a vendor, a host, a customer, a regulator, an investor?
4. Where is the margin thinnest: schedule, budget, mass, power, people?
5. What has gone wrong on a similar effort before?
6. What keeps you up at night about this?

For each answer, name the failure: what goes wrong if that decision is made late or wrong. Draft each risk with `writing.md`. Show the user batches of 3–5 drafts with titles, scores and one-line rationales. Change them on feedback.

Stop when the user's list runs dry, not at a target count.

## 3. Document import

When the user points at a document:

1. Read it all. Pull out the objectives and dates first, then every threat to them that it states or implies: assumptions, dependencies, open issues, "TBD" items, margins.
2. Draft the rows with `writing.md`. Every fact keeps its date and its place in the document.
3. Show the full draft list. Cut and merge with the user before you write anything.
4. Send the confirmed rows with `bulk_create_risks` (up to 100 items, each with `project_id` and `category_id`). Rows the user was unsure about go in as submissions instead (`submit_submission`).
5. Read every item's result. Fix and resend only the failed items, with a new idempotency key.

## 4. Mitigations

For the highest-severity risks, ask what the team will do, or propose actions they could take. Create each one with `create_mitigation` (title, description, `strategy_type`, project), then link it to every risk it reduces with `link_mitigation`. Expect more mitigations than risks. One action that answers three risks is the most useful row in the register.

## 5. Close

Summarize: how many risks, the top three by severity, the risks with no mitigation (`find_risks` with `project_id` and `rank_by="mitigation_coverage_gap"`), and the date. Tell the user that a check-in diffs from this date, so nothing needs capturing.
