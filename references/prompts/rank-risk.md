# Rank a risk

The procedure behind RiskThing's in-app "AI ranking" of a risk's likelihood and consequence, written for an agent. The scales live in `../scales.md`; edit them there, not here.

**Inputs:** the risk title and description, the project context (`find_projects`) and the company context.
**Output:** `likelihood` and `consequence` (1–5), each with a 2–4 sentence rationale, for `likelihood_rationale` and `consequence_rationale`. Send all four together.

## Likelihood

1. Decide the risk's main impact: human safety, or cost, schedule and performance. The two use different probability columns.
2. If there is a probability estimate, use the column for that impact. If there is none, use the meaning column.
3. A probability exactly on a boundary takes the lower rating.
4. Score the mechanism, not the outcome. Ask how much of the chain of causes is already in force, and how much still has to happen. The rationale says which link is established and which is uncertain.

Example: a 5% probability on a schedule risk is a 2, because 5% falls in the more-than-1%-up-to-10% band. The same 5% on a safety risk is a 4.

## Consequence

1. Score each area that applies: safety of people, facilities and equipment, environment, performance, cost and schedule. An area that does not apply scores 0.
2. The highest of those scores is the consequence.
3. Rate the realistic outcome of this risk on this project, not the worst case imaginable.

Example: safety 2, performance 3, schedule 4 and cost 3 make a consequence of 4, from schedule.

The rationale names the area that set the score and the objective it threatens (a delivery date, a raise, a milestone), and gives the anchor in the company's own terms: "a $2M–$5M planning error against the last disclosed $6M raise".

## Calibration

A register that is mostly 4s and 5s is alarm, not analysis. Healthy registers cluster at likelihood 3 with a tail of 4s, and consequence 3–4 with a few 5s. Before you send a 5, check that the evidence supports it.
