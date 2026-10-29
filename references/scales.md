# Rating scales

These are the likelihood and consequence scales RiskThing's in-app AI ranking uses. Score every risk against them unless the user has their own. They are a starting point: if the organization works at a different scale, edit the bands in this file and keep the five steps.

A value exactly on a boundary takes the lower rating, in every table here. A 33% probability is a 3, and a $1M cost is a 2.

## Likelihood

| Rating | Meaning | Probability: cost, schedule or performance | Probability: human safety |
|---|---|---|---|
| 5 - Very High | Almost certain. Known triggers are imminent or already occurring. | More than 50% | More than 10% |
| 4 - High | Likely. Triggers are likely to occur, so expect the risk at some point. | More than 33%, up to 50% | More than 1%, up to 10% |
| 3 - Medium | Possible. Some triggers can occur, and the risk can occur under specific conditions. | More than 10%, up to 33% | More than 0.1%, up to 1% |
| 2 - Low | Unlikely. Few triggers are known, and current conditions do not suggest one. | More than 1%, up to 10% | More than 0.0001%, up to 0.1% |
| 1 - Very Low | Rare. No known or foreseeable trigger. | 1% or less | 0.0001% or less |

Use the meaning when there is no probability estimate. When there is one, use the column for the risk's main impact. The same 5% is a 2 for a schedule risk and a 4 for a safety risk.

## Consequence

Rate each area that applies. The highest rating is the consequence. An area that does not apply scores 0.

| Rating | Cost | Schedule | Performance | Safety of people |
|---|---|---|---|---|
| 5 - Severe | More than $50M, or possible cancellation | More than 3 months on the critical path, or possible cancellation | Goals not achievable with current technology | Possible death or loss of crew |
| 4 - Major | More than $10M, up to $50M | More than 1 month, up to 3 months on the critical path | Major impact on requirements or goals | Possible permanent disabling injury |
| 3 - Moderate | More than $1M, up to $10M | Up to 1 month on the critical path | Moderate impact on requirements or goals | Possible severe injury or illness |
| 2 - Minor | More than $100K, up to $1M | Covered by schedule reserve | Minor impact on requirements or goals | Possible minor injury or illness |
| 1 - Negligible | $100K or less | Negligible | Negligible | First aid at most |

Two more areas use the same five steps:

| Rating | Facilities, equipment and hardware | Environment |
|---|---|---|
| 5 | Destruction of critical facilities, major systems or the vehicle | Serious or repeat violations that end the project |
| 4 | Destruction of noncritical facilities or assets | Major violation that stops work for a time |
| 3 | Major property damage | Moderate violation that needs immediate remediation |
| 2 | Minor property damage | Minor reportable violation |
| 1 | More than normal wear | Negligible, not reportable |

## Sizing to the company

The cost bands fit a large program. For a smaller company, either keep the bands and put the comparison in the rationale ("$400K against a $2M annual budget"), or rescale the cost column here to a fraction of the budget, for example:

| Rating | Cost as a share of the annual budget or the remaining runway |
|---|---|
| 5 | More than 50%, or the company cannot continue |
| 4 | More than 20%, up to 50% |
| 3 | More than 5%, up to 20% |
| 2 | More than 1%, up to 5% |
| 1 | 1% or less |

Whichever you use, use the same scale for every risk in a register. Two risks with the same score must mean the same thing.

## The score and the level

The risk score is likelihood times consequence, 1 to 25. RiskThing bands it as Critical (25), High (20–24), Medium-high (15–19), Medium (8–14), Low (4–7) and Minimal (1–3).

If the user changes these scales, the in-app AI ranking still uses the original ones. Say so when the user compares an agent score with an in-app one.
