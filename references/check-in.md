# Check-in: review, revise, monitor, add

Run a check-in when the user asks for one ("risk check-in", "review the register", "what changed") or at an agreed cadence. Goal: the register matches reality again, and the user knows what moved.

## 1. What changed

`diff_snapshots` with `format="content"`, `project`, and `from` set to the last check-in as an ISO-8601 time, such as `2026-10-01T00:00:00Z`. Omit `to` to diff against now. No captured snapshot is needed.

If nobody knows when the last check-in was, use the project's last activity or ask. Do not guess silently.

Report additions, removals and score changes in a few lines. Lead with anything whose severity went up.

## 2. Review what matters

1. `find_risks` with `project_id` and `rank_by="severity"`: the top of the register.
2. `find_risks` with `project_id` and `rank_by="mitigation_coverage_gap"`: high risks with nothing reducing them.
3. `find_risks` with `owner="me"`: the user's own items.
4. `list_submissions`: open hunches waiting for review.

For each risk you raise, ask one question: is it still true, did the score move, and is the mitigation happening?

## 3. Revise

For each change the user confirms:

- **Rescore or reword:** `get_risk`, then `update_risk` with `expected_version`. Send `likelihood` and `consequence` together with fresh rationales that say what changed and when.
- **Mitigation progress:** `get_mitigation`, then `update_mitigation`, or `link_mitigation` with `action="update_effectiveness"` (`link_id`, `expected_version`, `effectiveness`) for how well it is working on a given risk.
- **Retire or close:** call `transition_risk` with `target_state="transition"`, `to_state` and `expected_version`. Pick `to_state` from the `next_valid_transitions` that `get_risk` returns. To record a decision to accept, monitor, transfer, avoid or defer a risk, use `record_disposition` instead → `tools.md` § Lifecycle and dispositions.
- **Submissions:** `claim_submission` (with `target_project_id`, `target_category_id` and `expected_version`) turns a confirmed hunch into an official risk. `discard_submission` drops one and needs a `rationale`.

## 4. Add

Ask what is new since the last check-in: new commitments, new dependencies, surprises. Capture each one as in SKILL.md § Capture during work.

If a dated objective in the project context has passed, or a new commitment came up, offer to update the context → `context.md`.

## 5. Close

One short summary: what moved, what was added, what still has no mitigation, and today's date as the next check-in's `from`. If the user wants a written record and `snapshots` `action="list"` shows a captured snapshot, `briefings` with `action="draft"`, `snapshot_id` and `body_markdown` drafts one against it. Without a captured snapshot, write the summary in chat.
