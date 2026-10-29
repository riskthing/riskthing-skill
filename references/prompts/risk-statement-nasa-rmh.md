# Risk statement: NASA RMH style

The NASA Risk Management Handbook (NASA/SP-20240014019) risk statement. One fixed template, five components, and a seven-question validation. It is the prompt behind RiskThing's in-app "refine" helper when the organization uses the NASA RMH standard. Use it for NASA work, for programs reviewed by NASA, or when the user asks for "Given that…" statements.

**Inputs:** the draft title and description, the project context (`find_projects`) and the company context.
**Output:** one statement in the template below, for `description_public`. No commentary.

## Template

**Given that [Condition], there is a possibility of [Departure] affecting [Asset], which can result in [Consequence], adversely affecting the achievement of [Affected Objective(s)].**

## The five components

### 1. Condition: the current facts

Present tense, verifiable, measurable. Convert assumptions to evidence and make implicit conditions explicit.

- "Software is complex" → "the software complexity metric exceeds 150 (threshold: 100)"
- "Supplier issues" → "the supplier has missed 3 of its last 5 delivery milestones"
- "Old equipment" → "the ground support equipment is 15 years past its design life"

### 2. Departure: the uncertain event

Future tense with may, might or could. Specific timing and trigger. A credible possibility.

- "System will fail" → "the primary power system may fail in cascade during peak load"
- "Schedule problems" → "critical path activities could slip beyond the launch window"
- "Integration issues" → "the software-hardware interfaces might show incompatibilities during system test"

### 3. Asset: the affected element

A specific subsystem or component, in the program's own nomenclature, traceable to the work breakdown structure.

- "The spacecraft" → "the attitude control subsystem"
- "Ground stuff" → "the mission operations control center"
- "Communications" → "the Ka-band high-gain antenna assembly"

### 4. Consequence: the unmitigated impact

**Remove every mitigation assumption.** Strip out "unless" and "if we" clauses. Quantify the direct effect.

- "Delay unless we expedite" → "a 6-month launch delay"
- "Problems with backup systems helping" → "complete loss of navigation redundancy"
- "Cost overrun but we can descope" → "$45M cost growth"

### 5. Affected objectives: the measurable goals

Link to a specific requirement, performance measure or milestone.

- "Mission impact" → "the 10 TB primary science data requirement"
- "Budget problems" → "the $850M cost cap"
- "Performance issues" → "the 0.5 arcsecond pointing stability requirement"

## Process

1. **Parse the draft.** Mark which components are present, missing or weak.
2. **Fill the gaps from context.** A missing asset often follows from the consequence; a missing condition from the problem context. A missing quantity gets a range sized to the project.
3. **Apply the template.** Condition → departure → asset → consequence → objective.
4. **Validate** against the seven questions. All must pass.

## Seven-question validation

1. **Impact on objectives.** Does it affect a measurable objective?
2. **Clear communication.** Does condition → departure → consequence flow?
3. **Evidence base.** Is the condition fact, not speculation?
4. **Change from baseline.** Is this a departure from the plan?
5. **Factual condition.** Can the condition be verified?
6. **Credible departure.** Does the departure follow from the condition?
7. **Unmitigated consequence.** Is the consequence stated with no mitigation assumed?

## Common fixes

Vague:
- Software might have problems affecting the mission
- Given that flight software integration testing revealed 23 interface discrepancies, there is a possibility of undetected software faults appearing during critical mission phases affecting the command and data handling system, which can result in loss of vehicle control for up to 72 hours, adversely affecting the achievement of the requirement to keep continuous ground contact for 99% of the mission.

Risk mixed with mitigation:
- If power fails we'll switch to backup but that might not work causing issues
- Given that the primary power system shows 8% degradation after 6 months (design: under 2% per year), there is a possibility of complete primary power failure affecting the main bus power distribution, which can result in a 48-hour science data gap and thermal excursions below -40°C, adversely affecting the achievement of the 95% data completeness requirement.

Issue stated as a risk:
- The schedule is already slipped by 2 months
- Given that the program is 2 months behind the baseline schedule, there is a possibility of further technical discoveries during system integration affecting the critical path, which can result in missing the March launch window and a 26-month wait for the next opportunity, adversely affecting the achievement of the $400M life-cycle cost cap.

No quantification:
- Vendor might deliver late causing problems
- Given that the reaction wheel vendor has a 40% on-time delivery rate over the past 18 months, there is a possibility of reaction wheel delivery delays affecting the spacecraft integration and test schedule, which can result in a 3-month slip and $2.4M in added storage costs, adversely affecting the achievement of the Q4 launch readiness milestone.

Two risks conflated (split, and keep the larger):
- Thermal and vibration testing might fail causing redesign and delays
- Given that preliminary thermal analysis shows 5°C margin (requirement: 10°C minimum), there is a possibility of thermal qualification test failure affecting the optical bench assembly, which can result in a 4-month redesign and $3.5M in added engineering cost, adversely affecting the achievement of the Critical Design Review exit criteria.

## Sizing by mission class

Size the quantities to the program. The same draft reads differently at each scale:

- **Class A ($2B+ flagship):** integration of 4 instruments from different vendors could cut concurrent observation capability by 30%, against a $2.3B multi-spectral science investment.
- **Class B ($500M–$2B):** 3 of 5 single-source critical suppliers could delay propulsion delivery by 8 months and $24M, against a planetary launch window.
- **Class C ($150M–$500M):** a deployment mechanism that failed 2 of 8 cold tests could cut the data rate 100-fold, against a 500 GB science return.
- **Class D (under $150M):** COTS parts with no radiation testing could latch up and lose the spacecraft within 30 days, against a 6-month technology demonstration.

## Reminders

- **Condition:** present tense, factual, measurable.
- **Departure:** future tense with may, might or could.
- **Asset:** a specific subsystem or component, never "the system".
- **Consequence:** the raw impact, no mitigation assumed.
- **Objectives:** quantified goals or requirements.
