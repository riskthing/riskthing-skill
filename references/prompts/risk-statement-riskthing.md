# Risk statement: RiskThing style

The default style. Plain language with a flexible structure, written to work equally well in a board meeting, a design review and a team standup. It is the prompt behind RiskThing's in-app "refine" helper when the organization uses the RiskThing standard. Edit the examples to fit the organization.

**Inputs:** the draft title and description, the project context (`find_projects`) and the company context.
**Output:** one risk statement, for `description_public`. No commentary.

## The three elements

1. **The context** (optional but helpful). What is true now that creates the uncertainty. Present tense, factual. "Our payment processor has had 3 outages this month."
2. **The risk event** (required). What might go wrong, in conditional language: may, might, could. "Integration with the new API could fail during deployment."
3. **The impact** (required). Why it matters, quantified where possible and tied to an objective. "Delaying launch by 2 weeks and missing the holiday sales window worth $500K."

## Formats

Pick the one that communicates this risk best. Clarity matters more than format.

- **Narrative:** "Because [context], [what might happen], resulting in [impact on objectives]."
- **If-then:** "If [uncertain event] due to [cause], then [specific consequences]."
- **Direct:** "[Risk event] may occur, causing [quantified impact]."

## Risk or issue

- A **risk** might happen: "The server may crash during peak load."
- An **issue** has happened: "The server is down." That is not a risk.

If the draft describes an issue, write the risk that it continues or recurs: "If the current server instability continues…"

## Quantify

Specific enough to decide on:

- Time: "2–3 week delay", not "schedule impact"
- Money: "$50K–$100K cost", not "budget overrun"
- Performance: "30% throughput reduction", not "slower"

Ranges are fine when the exact figure is unknown: "Q2 2027", "$1M–$2M", "3–6 months".

## Checks

- **Uncertainty:** it describes something that might happen, not something that has.
- **Impact:** it shows the consequence for objectives, timeline or budget.
- **Clarity:** someone outside the project would understand the concern.
- **Honesty:** it describes the risk with no mitigation in place.

## Common fixes

Too vague:
- Technical problems might cause issues
- Integration between our Node.js backend and the legacy Oracle database may fail due to version incompatibility, requiring 2–3 weeks of custom adapter work and delaying the Q1 feature release

Already an issue:
- The team lacks cloud experience
- The team's limited cloud experience may lead to misconfiguration during the AWS deployment, exposing customer data or costing $10K–$30K in the first month

Missing quantification:
- Vendor might deliver late affecting the project
- Our hardware vendor may miss the March 15 delivery date given its 40% on-time rate, pushing installation to April and forfeiting the $200K early-completion bonus

Assumes mitigation:
- Server might fail but we have backups so impact is minimal
- Primary server failure could cause 4–8 hours of downtime during peak trading, losing $500K in transactions and breaching regulatory obligations

## Examples by context

- **Startup:** Our single technical founder could burn out from 80-hour weeks and delay the MVP by 1–2 months, missing the April 1 investor demo and putting the $500K seed round at risk.
- **Enterprise:** The upcoming GDPR audit may find our data retention practices noncompliant, with fines of 2–4% of global revenue ($2M–$4M) and 6–12 months of mandatory remediation.
- **Engineering:** Memory leaks in the payment module, measured at 50MB a day in testing, could crash production servers after 30 days of uptime, forcing restarts during business hours and affecting up to 10,000 transactions worth $1M a day.
