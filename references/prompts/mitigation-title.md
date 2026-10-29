# Mitigation title

The full rules behind RiskThing's in-app "refine title" helper for mitigations. Use them to write a new title or to refine a draft. Edit the verb list and examples to fit the organization; the tests are the part to keep.

**Inputs:** the draft title, the mitigation description, the risk it reduces, the project context (`find_projects`) and what you know about the company.
**Output:** one title, for `title_public`. No explanation, no quotation marks.

A mitigation title is an instruction to the team: the one thing they would do, said the way they would say it to each other.

## What a good title is

An imperative sentence, under 140 characters and under 100 when it fits, that names the decision or the change and the thing it applies to, in the company's own vocabulary. The parts, in this order:

1. **The verb, first.** A plain action verb: publish, name, freeze, ask, corona-test, re-qualify, correct, settle, ship, hand, write, open, put. Not a management verb that describes intent instead of action: implement, establish, ensure, enhance, improve, leverage, optimize, address, manage, monitor, develop, conduct.
2. **The object.** The specific thing the verb acts on, in the company's names for it: the datasheet, the Halo 1000, the ORBIT-2 deliverables, each reused high-voltage part. Never "the process", "the approach", "the plan", "risk", "issues", "stakeholders". The examples use a fictional company; use this company's names the same way.
3. **The qualifier that makes it theirs**, when it fits: the date, the counterparty, the condition, the place. "Before the October test." "With the host." "Before any subcontractor drafts it."

Shorter wins. A title a team can repeat in a standup is the right length.

## The tests, in order

1. **Does it start with a verb someone will perform?** If the first word is a management verb, find the concrete action underneath it and start there. "Establish a supplier qualification process" becomes "Approve one supplier for each high-voltage part before the first production lot".
2. **Does it name a decision or a change, or a document's shape?** A title that opens with an artifact's format ("One sheet with three columns", "A matrix of", "A tracker for") describes stationery. Lead with what changes. The artifact can follow as where the answer lives.
3. **Could the team do this tomorrow without asking what it means?** "Improve supplier communication" fails. "Send each supplier the drawing revision they are building to" passes.
4. **Is the object theirs?** A title that could be pasted into another company's register unchanged names nothing.
5. **Is it one action?** Two verbs joined by "and" is usually two mitigations, or one action plus its consequence. Keep the action; the description says why. Two verbs that are one decision made in one sitting may stay.
6. **Does it presume?** A title that assigns work to a named person is presumptuous. Roles are fine; names are not.
7. **Is it a capability or an action?** "Have a corona test capability" is a capability. "Corona-test every high-voltage unit in vacuum before it ships" is an action.
8. **Mechanics.** Under 140 characters. No colon, semicolon, em dash, quotation marks or parenthetical. No "X, not Y". No hedging (consider, try to, aim to). Prefer the date or the milestone to relative time. No reference ids or internal codes. No trailing period.

## Examples

Each pair keeps the same facts. The second line is the answer.

Management verb:
- Implement a comprehensive supplier qualification framework
- Approve one supplier for each high-voltage part before the first production lot

Stationery:
- One sheet, three columns, one row per published performance number
- Label every published number as a range, a specification or a measurement

Capability, not action:
- Establish corona testing capability for high-voltage units
- Corona-test every high-voltage unit in vacuum at temperature before it ships

Vague object:
- Enhance stakeholder communication regarding program milestones
- Name who signs for the company on each of the three dated commitments

Generic, could be any company:
- Develop a data package for customers
- Ship an acceptance data package with every unit

Two actions joined:
- Date the datasheet and drop the competitor comparison and reconcile the customer list
- Date the datasheet and drop the unnamed-competitor comparison

Presumes a person:
- Have Dana write the flow-down clauses before the prime sends theirs
- Write the ORBIT-2 program's flow-down before any subcontractor drafts it

Intent instead of act:
- Ensure the founding year is consistent across all company materials
- Correct the founding year on the leadership page this week

Already right, left alone:
- Open the ORBIT-2 transition conversation with the program office before the award ends in May 2027
- Open the ORBIT-2 transition conversation with the program office before the award ends in May 2027

## When the draft is already good

Return it unchanged. Change a title only when a test fails.
