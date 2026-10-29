# Mitigation: NASA RMH style

The NASA Risk Management Handbook (NASA/SP-20240014019) mitigation. A declared type, actions measured against the unmitigated baseline, and the performance measures they protect. It is the prompt behind RiskThing's in-app "refine" helper for mitigations when the organization uses the NASA RMH standard. Pair it with `risk-statement-nasa-rmh.md`.

**Inputs:** the draft mitigation title and description, the risk statement it answers and that risk's unmitigated consequence, the project context (`find_projects`) and the company context.
**Output:** one mitigation description, for `description_public`, and the `strategy_type`. No commentary.

## Two types

- **Prevention** acts on the departure. It lowers the probability of a performance shortfall. Examples: redundant quality checks at critical manufacturing points, automated anomaly monitoring, weekly instead of monthly inspection, dual verification of critical procedures. `strategy_type`: `reduce_likelihood`.
- **Reduction** acts on the consequence. It lowers the size of the shortfall if the departure happens. Examples: backup systems, contingency procedures, protective barriers, alternative supply chains. `strategy_type`: `reduce_impact`.

If a draft does both, pick the main one or split it into two mitigations. Use `combined` only when the two cannot be separated.

## Dispositions

The user chooses the disposition, not the mitigation. Knowing it shapes the mitigation:

| NASA disposition | Meaning | RiskThing |
|---|---|---|
| Accept | Document the assumptions, no active mitigation | `record_disposition`, `decision_class` `accept` |
| Mitigate | Active prevention or reduction | Write the mitigation, `decision_class` `mitigate` |
| Watch | Monitor parameters with action thresholds | `decision_class` `monitor`, plus a `detect_early` mitigation for the tracking |
| Research | Generate information to reduce the uncertainty | No direct match. Write the research as a mitigation and say so in the rationale |
| Elevate | Move it to a higher level of the organization | No direct match. Say so in the disposition rationale |
| Close | No longer significant, or it has occurred | A lifecycle transition, not a disposition |

## Structure

1. **Type declaration.** Start with "**Prevention strategy:**" or "**Reduction strategy:**".
2. **Actions with ownership.** Concrete steps, the responsible role, milestones, and the people and budget needed.
3. **Quantified protection against the unmitigated baseline.** "Likelihood from 30% to 5%." "Schedule impact from 6 months to 2 weeks." "Pointing held within 1 arcsecond instead of degrading to 5."
4. **The performance measure it protects.** "Protects PM-3.2: launch readiness by March." "Maintains PMK-1.5: 99.9% data return."
5. **Tracking parameters.** What is measured, how often, how, and by whom.
6. **Effectiveness measures.** Leading indicators that it is working, lagging indicators that the risk went down, thresholds, and the review gates where it is judged.
7. **Implementation level.**
   - *Execution:* inside the current baseline, no rebaselining, usually under 3 months. More tests, more reviews, process changes.
   - *Rebaseline:* needs a change to objectives or requirements, usually 3–6 months with approval. Scope reduction, schedule extension, relaxed requirements.
   - *Planning:* a major design change, over 6 months with extensive review. Technology substitution, architecture redesign, re-scoping.
8. **Residual risk.** The likelihood and consequence that remain, whether that is acceptable, and the contingency if the mitigation fails.

## The unmitigated baseline

The risk's consequence was written with no mitigation assumed (validation question 7). The mitigation must reference that baseline and show the change from it.

- Unmitigated: complete loss of the 10 TB of mission data
- Mitigated: data loss reduced from 10 TB to 0.5 TB through redundant storage

Also ask: does this mitigation affect other risks, create new ones, or trade one risk for another?

## Size to the mission class

- **Class A ($2B+):** extensive mitigation is justified.
- **Class B ($500M–$2B):** balance cost against benefit.
- **Class C ($150M–$500M):** target the critical risks.
- **Class D (under $150M):** minimal mitigation; accept more risk.

## Common fixes

Vague actions:
- Improve testing procedures
- **Prevention strategy:** Run automated regression tests with 95% code coverage on every daily build, with immediate failure alerts. Systems engineering deploys it by February, lowering the defect escape rate from 15% to 3%. Track the defect detection rate weekly. Effective when post-release defect density stays under 0.1 per KLOC.

No quantification:
- Add backup systems to reduce impact
- **Reduction strategy:** Deploy triple-redundant power with automatic failover in under 100 ms, reducing the consequence of a primary power failure from mission loss to 48 hours at 70% capability. Protects PM-4.1, 95% operational availability. Test failover monthly; the threshold is under 100 ms in 99% of tests.

Ignores the baseline:
- Ensure schedule stays on track
- **Prevention strategy:** Assess critical path schedule risk weekly to prevent the unmitigated 6-month launch delay, with a 2-week rolling buffer on every critical activity. Lowers the delay probability from 40% to 10%. Protects PM-2.3, the March launch window. Replan when variance exceeds 5 days.
