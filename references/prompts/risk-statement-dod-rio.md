# Risk statement: DoD RIO style

The Department of Defense Risk, Issue and Opportunity (RIO) risk statement. Event, cause and consequence kept distinct, in one of three formats. It is the prompt behind RiskThing's in-app "refine" helper when the organization uses the DoD RIO standard. Use it for defense programs, for primes that flow down DoD practice, or when the user asks for "If… then…" statements.

**Inputs:** the draft title and description, the project context (`find_projects`) and the company context.
**Output:** one statement in one of the three formats, for `description_public`. No commentary.

## Elements

1. **Event or condition** (required): the uncertain future event or condition that could affect program objectives.
2. **Consequence** (required): the specific effect on cost, schedule, performance or safety if it occurs.
3. **Cause** (strongly recommended): the root or proximate cause. It clarifies the threat and lets the mitigation target it.

Keep the three distinct. The event is what might go wrong. The cause is why. The consequence is the measurable effect on the program.

## Three formats

Pick the one that fits the risk, and follow it exactly.

**If-then:** "If [uncertain event or condition] due to [cause], then [consequences for cost, schedule or performance]." Use it when the event leads clearly to the consequence.

> If the new composite material fails stress testing due to an unvalidated bonding process, then the wing redesign will add $2.5M in development cost and delay first flight by 3 months.

**Condition-consequence:** "[Uncertain condition] due to [cause]; therefore, [consequences]." Use it when an existing uncertain condition may get worse or show itself.

> Supplier quality control is inconsistent due to unstandardized procedures; therefore, component rejection rates may exceed 15%, causing production delays of 2–4 weeks per batch.

**Because-event-consequence:** "Because [root cause], [uncertain event] may occur, resulting in [consequences]." Use it when the root cause is the main driver.

> Because the contractor has no experience fabricating titanium alloy, manufacturing defects may occur, resulting in structural components that fail the 7.0g load requirement and need $1.8M in rework.

## Quantify the consequence

Include at least one:

- **Cost:** dollars or a share of the budget ("$2.5M overrun", "15% of the development budget")
- **Schedule:** weeks or months against a named event ("3-month delay to CDR")
- **Performance:** the degradation ("payload reduced from 500 to 400 lb", "accuracy from ±1 m to ±3 m")
- **Safety:** the metric ("collision probability from 1 in 10,000 to 1 in 1,000")

## Risk or issue

A risk is uncertain and uses may, could or potential. An issue is a current problem that needs resolution now. Convert an issue to a risk by finding the future uncertainty in it.

## Common fixes

Too general:
- Technology challenges may impact the program
- If the adaptive control algorithm fails to converge within 100 ms due to computational complexity, then the autonomous navigation system will miss the 99.9% reliability threshold, risking loss of CAT III certification

Issue, not risk:
- The schedule has already slipped 2 months
- If more requirements changes occur due to evolving threat assessments, then the schedule may slip a further 3–4 months beyond the current baseline

No quantification:
- Supplier delays could affect production
- If the titanium supplier cannot meet the 30-day delivery timeline due to raw material shortages, then production will drop from 2 units to 1 a month, losing $8M in monthly revenue

Cause without the risk:
- Lack of skilled personnel
- Because there are too few skilled welders, critical welds may fail inspection, resulting in 2-week rework cycles and $150K in added cost per vehicle

Certainty stated as a risk:
- The system will require maintenance
- If maintenance intervals exceed 500 flight hours due to unexpected component wear, then operational availability may drop below the required 85%

## Checklist

- A clear uncertain event or condition
- Specific, quantified consequences
- Cause, event and consequence kept distinct
- Conditional language (if, may, could)
- Enough detail to plan a mitigation
- One of the three formats, followed exactly
