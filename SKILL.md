---
name: riskthing
description: Works a RiskThing risk register through the RiskThing MCP server — captures risks and mitigations as they surface during normal work, onboards a blank organization or new project by interview or document import, and runs check-ins that review, revise and add to an existing register. Also drafts and scores risk statements and mitigations in RiskThing, NASA RMH or DoD RIO style, with or without the server. Use when a risk, hunch, blocker, dependency slip, schedule threat or "what could go wrong" comes up while working; when the user asks to set up RiskThing, add or update risks or mitigations, score likelihood and consequence, write or refine a risk statement or mitigation, or do a risk check-in or review; or when a RiskThing tool returns version_conflict, a grouped-tool selector error, or partial bulk_create_risks results.
compatibility: Register work needs the RiskThing MCP server (tools such as find_risks, create_risk, diff_snapshots). The writing and scoring references work without it.
---

# RiskThing

RiskThing keeps a risk register: projects hold risks, and mitigations are linked to the risks they reduce. This skill covers what to do with it. The server's own `instructions` state the calling rules; the table below repeats them because not every client shows them.

## Calling rules

| Rule | Why |
|---|---|
| Read the item, then send its `version` as `expected_version` on any change | A stale version returns `version_conflict`; its suggested action carries the current version for one retry. Re-read if the content may have changed. |
| Grouped tools pick the operation by one selector: `action`, `target_state`, `kind`, `subject` or `format` (or the presence of `query` / `rank_by` on `find_risks`) | The selector enum lists the choices. A wrong selector is a JSON-RPC `-32602` naming the allowed values. |
| Titles and descriptions go in `title_public` and `description_public`. Submissions use `title` and `description` | There is no plain `title` field on risks or mitigations. |
| `likelihood` and `consequence` go together, each with its rationale | Sending one without the other is rejected. → READ `references/scales.md` for the scales. |
| Unconfirmed concern → `submit_submission`. Confirmed risk → `create_risk` | A submission lands in an inbox for review and creates no official risk. |
| `suggested_actions` are operations you are allowed to run next | They are not advice. Choose from the user's goal. |
| Retry a write with the same `params._meta["riskthing/idempotency_key"]` | A replay returns the stored result instead of writing twice. |
| `owner="me"` filters to the user's own items | Works on `find_risks` and `find_mitigations`. |

`bulk_create_risks` succeeds or fails per item. Read every item's result and report the failures. Do not report the batch as done.

`search_knowledgebase` searches only the risks and mitigations the user can see (`corpus="tenant_artifacts"`). Other knowledgebase corpora are not implemented yet. To ask for one, write to support@riskthing.com.

## Without RiskThing

If no RiskThing tools are connected and the user wants to connect, send them to <https://app.riskthing.com/account/tokens/> to create an API token, then add the MCP server `https://app.riskthing.com/mcp` with the header `Authorization: Bearer <token>`. If creating the token fails with "Your organization policy does not allow API token minting", tell the user to ask their RiskThing administrator to open API and MCP access at <https://app.riskthing.com/admin_portal/policy/>. The skill's README has the full steps.

The writing guidance applies either way. Draft and score rows with `references/context.md`, `references/writing.md`, `references/scales.md` and `references/prompts/`, and give them to the user as a table they can keep. Skip every tool call in this file.

## Start

1. `get_organization`, then `find_projects`. Then `find_risks` with the project to see whether the register is empty.
2. Route:

| State | Do |
|---|---|
| No project, or an empty project | Onboarding → READ `references/onboarding.md` |
| Register exists, and the user asked for a check-in, a review, or "what changed" | Check-in → READ `references/check-in.md` |
| A risk came up during other work | Capture, below |

## Capture during work

Fire when something in the session is a risk: a dependency that may slip, a test that shows a margin is thin, a vendor that missed a date, a design choice with a known failure mode, or the user saying "I'm worried that…".

1. Say it in one line and ask whether to record it. Do not write without the user's yes.
2. Search first: `find_risks` with `query` and `filters.project_id`. If it matches an existing risk, offer to update that one (read it, then `update_risk`) instead of creating a duplicate.
3. Hunch, or the user is unsure → `submit_submission` with `kind="risk"`, a title, a description and the target project.
4. Confirmed → `create_risk` with `project_id`, `category_id` (from `find_taxonomy` `kind="category"`), title, description, likelihood, consequence and both rationales. Draft them with `references/writing.md`. Show the draft before you send it.
5. If the user names what they will do about it, `create_mitigation`. Then `link_mitigation` with `action="link"`, `risk_id`, `mitigation_id`, and the risk's version as `expected_risk_version`.

Stay brief. Capture is a side task, so do not break the user's flow with a register review.

## Writing

Every title, description, score and rationale follows `references/writing.md`. Read it before you draft the first risk or mitigation of a session. The short version:

- **Risk title:** the asset at stake, then what could happen to it, in the company's own names. Under 140 characters.
- **Mitigation title:** an imperative that starts with a concrete verb and names its object.
- **Likelihood:** how much of the cause is already in force. **Consequence:** sized against this company's scale and tied to an objective.
- **Context:** the company and project context strings set what a realistic risk looks like and how severe it is. If drafts come out generic, the context is the likely cause → READ `references/context.md`.
- **Style:** RiskThing (default), NASA RMH or DoD RIO. Ask once which the organization uses, and match an existing register. `writing.md` § Choose a style lists the prompt for each.

## Tool map

Which tool and selector does what, error envelopes, and lifecycle and disposition moves → READ `references/tools.md`.
