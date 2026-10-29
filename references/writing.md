# Writing risks and mitigations

This file is the short form of the guidance RiskThing's in-app writing helpers use. Write each row so the user would recognize it as their own. The full prompts, one per job, are in `prompts/`; read the one for the job when you refine a row or when the short form is not enough.

## Contents

- Choose a style
- Risk title
- Risk description
- Likelihood
- Consequence
- Mitigation title
- Mitigation description
- Failures to catch before sending

## Choose a style

Titles follow the same rules in every style. The style sets the shape of the risk description and the mitigation description. Ask the user which one fits, once per organization, and use it for every row in the register.

| Style | Shape | Use it when | Risk | Mitigation |
|---|---|---|---|---|
| **RiskThing** (default) | Plain language, flexible structure | No standard is required, or the reader is a founder, a board or a mixed team | `prompts/risk-statement-riskthing.md` | `prompts/mitigation-riskthing.md` |
| **NASA RMH** | "Given that [condition], there is a possibility of [departure] affecting [asset], which can result in [consequence], adversely affecting [objective]" | NASA work, NASA-reviewed programs, or a customer who reads NASA/SP-20240014019 | `prompts/risk-statement-nasa-rmh.md` | `prompts/mitigation-nasa-rmh.md` |
| **DoD RIO** | "If [event] due to [cause], then [consequence]", or one of two other fixed formats | Defense programs, primes that flow down DoD practice | `prompts/risk-statement-dod-rio.md` | `prompts/mitigation-dod-rio.md` |

If the user has no preference, use RiskThing style. If the register already has rows, match the style they are written in. Do not mix styles in one register.

Titles: `prompts/risk-title.md` and `prompts/mitigation-title.md`. Scores: `prompts/rank-risk.md`, against the scales in `scales.md`.

## Risk title

**The asset at stake, then what could happen to it.** The asset is something the company has or wants: revenue, a sale, a flight, a delivery date, a claim it makes, credibility with a buyer or an investor, a part. What could happen is lost, delayed, challenged, spent, derated or missed.

- Continued federal grant revenue after the ORBIT-2 Phase II ends in May 2027
- GEO sales lost to a worst-case radiation assumption, because the Halo 6000 control path names no part class
- Halo HV units can corona-fail during chamber pump-down and ascent

Rules:

- Under 140 characters, and under 100 when it fits. Use their product, award, host and date names. Avoid "the situation" and "the exposure".
- One risk per title. Two assets joined by "and" make two rows.
- No evidence opener ("No public document shows…"), no clause that argues why it matters, and no watcher ("…for a buyer to check").
- No verdict. "Failure to publish results" accuses. "The efficiency claim rests on two different published figures" observes.
- No colon, semicolon, em dash, quotation marks or parenthetical. No trailing period. No relative time ("now", "recently", "this year"): write the date. No hedging verb, except one "could" or "can" in a scenario.
- If the title already passes, leave it alone.

## Risk description

In RiskThing style, one paragraph in three parts. The NASA RMH and DoD RIO styles use their own templates (see *Choose a style*).

1. **The condition that is true now**, with dated facts.
2. **What could follow from it**, written as uncertain ("could", "may").
3. **What that would cost**, quantified where possible (time, money, performance) and tied to an objective.

Describe the risk as it stands before any mitigation. If the event has already happened, it is an issue, not a risk. Write the risk that it continues or recurs.

> Our hardware vendor may miss the March 15 delivery date given its 40% on-time rate, which would push installation to April and forfeit the $200K early-completion bonus.

## Likelihood

Score the mechanism, not the outcome. Ask how much of the chain of causes is already in force, and how much still has to happen.

Score against the likelihood scale in `scales.md`. A probability exactly on a band boundary takes the lower rating. Safety risks use far tighter probability bands than cost and schedule risks.

`likelihood_rationale` says which link is established and which is uncertain. That split is the most useful sentence in the row.

> The vendor's on-time rate is published at 40%, and the order is already placed. What is uncertain is only whether this order is one of the late ones.

## Consequence

Score each area that applies (safety, performance, cost, schedule and the others in `scales.md`) separately, and use the highest. `scales.md` holds the scale RiskThing's AI ranking uses, and says how to size it for a smaller company.

The score follows the bands. The rationale puts the number in the company's terms, so the user can argue with it. `consequence_rationale` names the objective it threatens, such as a delivery date, a raise or a milestone. It also gives the anchor: "a $2M–$5M planning error against the last disclosed $6M raise". A NASA lesson about a flagship overrun is not this company's anchor.

A register that is mostly 4s and 5s is alarm, not analysis. Healthy registers cluster at likelihood 3, with a tail of 4s, and consequence 3–4, with a few 5s.

## Mitigation title

**An imperative that starts with a verb someone will perform**, then the object in their own names, then the qualifier that makes it theirs (a date, a counterparty, a condition).

- Approve one supplier for each high-voltage part before the first production lot
- Corona-test every high-voltage unit in vacuum at temperature before it ships
- Open the ORBIT-2 transition conversation with the program office before the award ends in May 2027

Rules:

- No management verbs: implement, establish, ensure, enhance, improve, leverage, optimize, address, manage, monitor, develop, conduct. Find the concrete action underneath.
- Lead with what changes, not with a document's shape. "One sheet, three columns…" describes stationery. Write "Label every published number as a range, a specification or a measurement" instead.
- One action. Name roles, not people. Write an action, not a capability: "Have a corona test capability" is a capability.
- Same mechanics as risk titles: under 140 characters, no colon, semicolon, dash, quotation marks or parenthetical, no hedging ("consider", "try to"), and no trailing period.

## Mitigation description

In RiskThing style, say how the mitigation lowers likelihood or consequence, and by about how much. Then say who does what, by when, and how the team will know it is working. Do not repeat a sentence.

Pick the `strategy_type` from how it works:

| Value | Works by |
|---|---|
| `reduce_likelihood` | Stopping the event from happening |
| `reduce_impact` | Making the event cost less |
| `detect_early` | Seeing it coming in time to act |
| `improve_response` | Recovering faster once it happens |
| `transfer_risk` | Moving the cost to someone else (contract, insurance) |
| `combined` | More than one of the above |

One mitigation that answers several related risks is worth more than several generic ones. Link it to each risk it reduces.

## Failures to catch before sending

| Failure | Test | Fix |
|---|---|---|
| **Blind spot**: "we could not see X" written as the user's risk | Would any company publish X (runway, backlog, a Plan B)? If not, its absence is not a finding. | Cut the row. |
| **No-shit row**: generic wisdom told to someone who lives it | Can they act on this row without writing it themselves? | State the exposure, not the behavior. Then attach a specific mitigation they could not have written. Cut only if neither works. |
| **Stationery mitigation**: opens with "one sheet", "a matrix", "a tracker" | Does the first sentence name something that changes? | Lead with the decision or the change. |
| **Undated fact** | Will this still read correctly in six months? | Write the date. |
| **Hidden guess** | Does the row rest on an inference? | Make the hedge visible, and score likelihood no higher than the inference supports. |
