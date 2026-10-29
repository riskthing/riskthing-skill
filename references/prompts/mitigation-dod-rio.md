# Mitigation: DoD RIO style

The Department of Defense Risk, Issue and Opportunity (RIO) mitigation. A named response strategy, resourced actions, quantified reduction aimed at the risk's own consequence, and the residual risk. It is the prompt behind RiskThing's in-app "refine" helper for mitigations when the organization uses the DoD RIO standard. Pair it with `risk-statement-dod-rio.md`.

**Inputs:** the draft mitigation title and description, the risk it answers (statement and consequences), the project context (`find_projects`) and the company context.
**Output:** one mitigation description, for `description_public`, and the `strategy_type`. No commentary.

## Four response strategies

| Strategy | Purpose | When | RiskThing |
|---|---|---|---|
| **Avoid** | Remove the risk by changing the plan, requirement or approach | The consequence is unacceptable and an alternative exists | `decision_class` `avoid`. Write the change as a `reduce_likelihood` mitigation |
| **Transfer** | Move the responsibility or the cost to another party | Another party can manage it better | `decision_class` `transfer`, `strategy_type` `transfer_risk` |
| **Accept** | Acknowledge it and prepare for the consequence | Mitigation costs more than the impact, or it cannot be avoided | `decision_class` `accept`. A reserve held against it is a `reduce_impact` mitigation |
| **Mitigate (control)** | Lower the probability or the impact | The usual case | `decision_class` `mitigate`, `strategy_type` from how it works |

Examples:

- **Avoid:** Redesign the component with bolted aluminum joints, removing the titanium welding and the specialist skill it needs while still meeting the structural requirements.
- **Transfer:** Use a fixed-price contract with $50K a day in liquidated damages for delays, giving the supplier the incentive to hold 99.5% quality.
- **Accept:** Accept the 10% probability of a 2-week weather delay. Hold a $500K schedule reserve and name the parallel work that can continue during a delay.
- **Mitigate:** Run incremental integration tests every 2 weeks, lowering the probability of a critical failure from 30% to 5% and the possible rework from 6 months to 2 weeks.

## Five parts of the statement

1. **Specific actions:** concrete steps with an owner and a timeline.
2. **Measurable outcome:** the quantified reduction in probability or consequence.
3. **Resources:** the cost, people and schedule it needs.
4. **Success criteria:** observable signs that it is working.
5. **Residual risk:** what remains after it.

## Aim at the risk's own consequence

| The risk's consequence | The mitigation shows | Example |
|---|---|---|
| Cost | Cost reduction or control, in dollars | Dual-source the material, cutting the overrun exposure from $2M to at most $500K |
| Schedule | Schedule protection or recovery, in time | Run parallel development paths, cutting the possible critical path delay from 3 months to 3 weeks |
| Performance | The metric held or improved | Add redundant sensors to hold 99.9% accuracy through a single sensor failure |
| Safety | The safety metric or standard | Add automated collision avoidance, lowering incident probability from 1 in 1,000 to 1 in 100,000 |

A quality fix for a schedule risk is misaligned. Answer the consequence the risk names.

## Effective means

- **Actionable:** tasks, not intentions, with an owner and start and finish dates. "Improve quality control" fails. "Start 100% inspection with digital tracking by March 1, with 2 QA engineers auditing daily" passes.
- **Measurable:** a reduction target and progress indicators. "Lower the delay probability from 40% to 10% with weekly progress reviews and an early warning at 85% task completion."
- **Resourced:** funding, people and schedule effect named. "$200K and 3 test engineers for a 4-week test campaign on every critical interface."
- **Validated:** evidence it works, and a fallback. "Use the fault detection system proven on a prior program at 95%, with manual procedures if it fails."

## Common fixes

- **Vague:** "Monitor the situation closely" → "Audit the supplier weekly, with 24-hour corrective action for any defect rate above 2%."
- **Unrealistic:** "Eliminate all technical risk" → "Lower the technical risk probability from 60% to 20% through prototype testing and design iteration."
- **No success criteria:** "Implement training program" → "Certify 10 technicians through 40 hours of training by January 15, for a 95% first-pass qualification rate."
- **Ignores residual risk:** "Completely eliminates the risk" → "After the backup supplier is in place, a 5% probability remains of a 1-week delay if the primary supplier fails."

## Checklist

- The strategy is named: avoid, transfer, accept or mitigate
- Actions have owners and dates
- The reduction is quantified
- Resources are named
- Success criteria are defined
- It answers the risk's own consequence
- The residual risk is stated
- A fallback is named if the mitigation fails
