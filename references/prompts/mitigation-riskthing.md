# Mitigation: RiskThing style

The default style. Specific actions, how they reduce the risk, and how the team will know they are working, in language both the team and an executive understand. It is the prompt behind RiskThing's in-app "refine" helper for mitigations when the organization uses the RiskThing standard. Edit the examples to fit the organization.

**Inputs:** the draft mitigation title and description, the risk it reduces (title, description and scores), the project context (`find_projects`) and the company context.
**Output:** one mitigation description, for `description_public`, and the `strategy_type`. No commentary.

## The three elements

1. **The actions** (required). The specific steps, who does them, and when. "Run automated database backups every 6 hours starting Monday."
2. **The risk reduction** (required). How it addresses the risk: does it stop the event, or make it cost less? "Cuts the worst-case data loss from 24 hours to 6."
3. **The success measure** (recommended). How the team will know it is working. "100% of backups complete, and monthly restore tests finish in under 30 minutes."

## Strategy types

| Approach | Works by | `strategy_type` | Example |
|---|---|---|---|
| Prevention | Lowering the likelihood | `reduce_likelihood` | Daily code review on payment code, cutting the defect rate from 15% to 3% |
| Impact reduction | Lowering the consequence | `reduce_impact` | Redundant servers that limit downtime to 15 minutes instead of 4 hours |
| Early detection | Seeing it in time to act | `detect_early` | A weekly supplier on-time dashboard that alerts below 90% |
| Response | Recovering faster once it happens | `improve_response` | Runbooks for the 5 likeliest failures, cutting resolution from days to hours |
| Transfer | Moving the cost to someone else | `transfer_risk` | Cyber insurance covering breach costs up to $1M |
| More than one | | `combined` | |

Acceptance is a decision, not a mitigation. Record it with `record_disposition` (`decision_class` `accept`). A reserve held against an accepted risk ("2 weeks of schedule buffer and $50K contingency") is a `reduce_impact` mitigation.

## Checks

- **Specific:** could someone start tomorrow?
- **Mechanism:** is it clear whether it lowers the likelihood or the consequence?
- **Measurable:** will the team know whether it is working?
- **Feasible:** is it realistic for the time, money and people available?

## Common fixes

Too vague:
- Improve testing
- Add automated integration tests for every payment workflow, run nightly on staging. QA owns it by March 1. Target: production bugs from 5 a month to fewer than 1.

No mechanism:
- Hire consultant to help
- Engage a cloud architecture consultant for a 2-week review to find and fix configuration weaknesses before they expose the 10K customer records.

No success measure:
- Monitor the situation closely
- Track supplier on-time delivery weekly on the dashboard, with an alert below 90%. Success is 95% or better through Q2.

Unrealistic scope:
- Completely redesign the system
- Refactor the authentication module, the highest-risk component, over 3 sprints, bringing its vulnerabilities from critical to low against OWASP.

## Examples

- **Prevention:** Require pair programming and senior review on every payment code change before merge. This lowers the likelihood of payment fraud from about 30% to 5%, based on our history. Success is zero critical vulnerabilities in payment code next quarter.
- **Impact reduction:** Deploy database read replicas in 3 availability zones with automatic failover. A primary failure switches over in under 30 seconds, cutting downtime from 4 hours to 5 minutes and revenue loss from $200K to $3K. Success is every monthly failover test finishing in under 30 seconds.
- **Transfer:** Negotiate a fixed-price contract with a 10% cap on change orders by February 15. The vendor carries costs above $550K, so our exposure is at most $50K.

## Quantify

- Likelihood: "from 40% to 10%"
- Consequence: "from $100K to $20K"
- Time: "detection from 24 hours to 1"
- Coverage: "protects 80% of the revenue at risk"

Estimates are fine: "about half", "2–3 times faster", "70–90% of cases". Say what risk remains after the mitigation.
