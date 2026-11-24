# Example prompts

Prompts a person can paste to start real work with the skill. Each one is keyed to a moment when a company must get something right by a date: a raise, a bid, a review, a test, a first order.

The examples use Meridian Aerospace, a fictional small-satellite propulsion company. Replace the names, amounts and dates with your own.

## For agents: offering these

After the skill is installed, or when the user asks what it can do:

1. Ask what they are working on and by when, if you do not know.
2. Offer two or three prompts from this file that fit that answer, rewritten with their company, document and date. Do not list them all.
3. If nothing fits, write one with the anatomy below.

## What a good prompt holds

| Part | Example | Why |
|---|---|---|
| The skill and the source | "Use the riskthing skill. Attached is our current pitch deck." | The agent loads the rules and reads the real document, not a summary of it. |
| The project and why now | "We restarted our $500K raise after an investor's terms fell through." | Sets the objective and the date that every consequence is sized against. |
| The real question | "Is this hard and taking more time, or are we solving the wrong problem?" | Says what decision the answer serves. |
| The reader's chair | "Read the deck as an investor would." | Sets whose objections count. |
| The ground to cover | "The business model, the use cases we lead with, and how we read to US buyers." | Stops the list from drifting to generic risks. |
| The output | "A table of risk, likelihood, consequence and mitigation. Then the three you would fix first." | A table the user can keep, and a forced choice. |

## Raising money

### A round that has not closed

```text
Use the riskthing skill. Attached is Meridian Aerospace's current pitch deck.

We restarted our $500K raise after an investor's terms fell through. Everybody says we are on the right track, and the round still has not closed. I want to know why: is this hard and taking more time, or are we solving the wrong problem?

Read the deck as an investor would. List the risks that would stop an investor from writing a check, and for each one a mitigation we can act on before the next meeting. Look at the business model, the use cases we lead with, and how a company outside the US reads to US customers and US investors.

Give me a table of risk, likelihood, consequence and mitigation. Then tell me which three you would fix first.
```

### Before a lead's counsel reads the data room

```text
Use the riskthing skill. Attached are the documents in Meridian Aerospace's Series A data room: the deck, the financial model and the customer contracts.

A lead investor's counsel starts diligence in three weeks. List what each kind of investor will ask that the room does not answer yet: a defense-focused fund, a generalist fund and a strategic investor. For each gap, give the risk to the close and one thing we can add to the room before diligence starts.

Table of risk, likelihood, consequence and mitigation, sorted by risk score.
```

### How we read before the first meeting

```text
Use the riskthing skill. Read meridian-aerospace.example, our LinkedIn page and the last three press releases as an investor who has never heard of us.

What would make them stop reading, or ask a question we have no public answer for? Stale team pages, claims without a source, a product page that disagrees with the deck. For each, the risk to a first meeting and the fix.
```

## Winning work

### A government proposal

```text
Use the riskthing skill. Attached are the solicitation and our draft technical volume for a Phase II SBIR. Proposals are due on December 8.

Read the draft as the evaluation panel would, against the solicitation's evaluation criteria. List the risks that an evaluator would score as a weakness or a deficiency, and for each a change we can make before submission. Then list the risks to performing the contract if we win: schedule, key people, facilities, export control.

Two tables: risks to the award, and risks to delivery.
```

### An accelerator application

```text
Use the riskthing skill. Attached are our draft application to an accelerator and the program's published selection criteria. Applications close in ten days.

Read our draft as the selection committee would. What would make them pass on us, and what would make us stand out? Then tell me what attending costs us: founder time away, travel, and what slips at home during the sessions.
```

### A first production order

```text
Use the riskthing skill. We are quoting our first production order: 40 thrusters to one customer, delivery in two lots over nine months. Attached are the quote and our build plan.

List the risks to delivering the order on time and at the quoted margin: parts, yield, test capacity, cash before the first payment, and the people who hold the process. For each, a mitigation we can start this month.
```

## Building and testing

### A test campaign

```text
Use the riskthing skill. Attached is the environmental test plan for our qualification unit: vibration, thermal vacuum and EMI at an outside test house. The flight unit ships to the launch integrator on March 15.

List the risks to finishing qualification in time for that date: test house slots, fixtures, a failure that needs a redesign, and the hand-off to the flight build. For each, the mitigation and the date by which we must decide.
```

### A design review

```text
Use the riskthing skill. Attached are our slides for the preliminary design review in three weeks.

Read them as the review board chair would. List the risks the board will raise, the open items behind each one, and what we can close before the review. Use NASA RMH style.
```

### After an anomaly

```text
Use the riskthing skill. Our demonstration spacecraft stopped responding on day 3. Attached are the anomaly timeline and the telemetry summary.

List each candidate cause as a risk to the next vehicle, with the evidence for and against it. For each, a mitigation we can build into the next vehicle or its test plan, so we do not need to know the cause for certain to stop it happening again.
```

## Running the company

### Key people

```text
Use the riskthing skill. Meridian Aerospace is 15 people, and two founders make most of the decisions. List what breaks if either of us is out for a month during the next six months: customer commitments, the raise, approvals, signatures, and knowledge that lives in one head. For each, a mitigation that does not need a new hire.
```

### Going to market

```text
Use the riskthing skill. Attached are our pricing sheet and the plan for our first trade show in February.

List the risks to turning that show into three paid orders by June: who we meet, what we promise, how we follow up, and whether we can deliver what we sell there. For each, a mitigation and its owner's role.
```

### Moving off a spreadsheet

```text
Use the riskthing skill. Attached is our risk spreadsheet. Rewrite every row as a risk with a likelihood, a consequence and a rationale, merge the duplicates, and tell me which rows are not risks at all (tasks, complaints, or facts that are already true).
```

## With RiskThing connected

These need the RiskThing MCP server (see the README).

### Set up the register from what we just did

```text
Use the riskthing skill. Put the risks and mitigations from this conversation into a new RiskThing project called "Series A". Link each mitigation to every risk it reduces. Show me the list before you write anything.
```

### The weekly leadership meeting

```text
Use the riskthing skill. Run a check-in on the Series A project: what changed since last Monday, the top five risks, and the high risks with no mitigation. Ask me about each one, then record what I confirm.
```

### The board update

```text
Use the riskthing skill. What changed in the Meridian register since the board met on September 30? Draft a one-page update: what went up, what went down, what we decided, and what we need from the board.
```
