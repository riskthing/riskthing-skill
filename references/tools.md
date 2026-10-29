# Tool map

The live schema is authoritative. Each grouped tool's selector enum lists its operations. This map gives the common moves.

## Contents

- Read
- Write
- Grouped tools and their selectors
- Lifecycle and dispositions
- Errors and retries

## Read

| Need | Call |
|---|---|
| Organization numbering and prefixes | `get_organization` |
| Projects | `find_projects` (add `project_id` for one) |
| Risks: list, search, rank | `find_risks`: filters list; `query` searches; `rank_by="severity"` or `"mitigation_coverage_gap"` with `project_id` ranks. A list filters by `project`; a search filters by `filters.project_id`. |
| One risk or mitigation | `get_risk`, `get_mitigation`. Each lists `next_valid_transitions`. |
| Mitigations | `find_mitigations` (`query` searches; with `query`, `exclude_attached_to_risk_id` leaves out the ones already linked) |
| Categories, tags | `find_taxonomy` `kind="category"` or `"tag"` |
| Dispositions | `find_dispositions` `subject="risk"` or `"mitigation"`; `subject="policy"` lists the policies a risk disposition can use |
| Inbox | `list_submissions`, `get_submission` |
| What changed | `diff_snapshots` `format="content"`, `from=<ISO time or snapshot id>` |
| The register at a past moment | `snapshots` `action="get"`, `snapshot_id="render"`, `as_of=<ISO time>` |
| Severity over time | `snapshot_trend` with a `series_id` from captured snapshots (`snapshots` `action="list"`) |
| One item's edit history | `change_history` |

## Write

| Need | Call |
|---|---|
| A confirmed risk | `create_risk` |
| Many confirmed risks | `bulk_create_risks` (1–100 items, partial success). Give each item a `category_id`. |
| An unconfirmed concern | `submit_submission` `kind="risk"` or `"mitigation"` |
| A mitigation | `create_mitigation`, then `link_mitigation` `action="link"` with `risk_id`, `mitigation_id`, and the risk's version as `expected_risk_version` |
| Change a risk or mitigation | `update_risk`, `update_mitigation` with `expected_version`. Reads return `title` and `description`; writes take `title_public` and `description_public`. |
| Rate a link | `link_mitigation` `action="update_effectiveness"`, `link_id`, `expected_version`, `effectiveness` (`high`, `medium`, `low`, `informational`, `unknown`) |
| Project | `manage_project` `action="create"`, `"update"` or `"transition"` |
| Category or tag | `manage_taxonomy` `action="create_category"`, `"attach_tag"`, and so on |

## Grouped tools and their selectors

| Tool | Selector |
|---|---|
| `manage_project` | `action`: create, update, transition |
| `manage_taxonomy` | `action`: create/update/soft_delete/restore for category or tag, plus attach_tag and detach_tag |
| `transition_risk`, `transition_mitigation` | `target_state`: transition, trash, restore, permanently_delete |
| `link_mitigation` | `action`: link, unlink, update_effectiveness |
| `record_disposition` | `action`: create_risk, update_risk, transition_risk, create_mitigation, update_mitigation, transition_mitigation, personal_set_risk |
| `snapshots` | `action`: get, list; `format="package"` exports |
| `diff_snapshots` | `format`: content, package |
| `briefings` | `action`: list, get, draft |
| `find_taxonomy` | `kind`: category, tag |
| `find_dispositions` | `subject`: risk, mitigation, policy |
| `find_risks`, `find_mitigations`, `find_projects` | Picked by which argument is present (`query`, `rank_by`, or an id) |

## Lifecycle and dispositions

- **Lifecycle** is where an item stands in its workflow. `get_risk` and `get_mitigation` list the valid next states in `next_valid_transitions`; pick `to_state` from that list. Send `target_state="transition"`, `to_state` and `expected_version`. A new risk starts in `private_draft` and shows on the published register only in `approved`, `active_monitoring` or `risk_mitigated`. Approval is the user's call, so ask before you approve. `trash`, `restore` and `permanently_delete` apply only to your own items. `permanently_delete` cannot be undone, so always confirm it with the user first. Everything else can be undone. To roll an item back, read it as of an earlier time (`snapshots` `action="get"`, `snapshot_id="render"`, `as_of`) and write those values back with an update.
- **Disposition** is the decision on how a risk is handled. Each risk has at most one. Its `decision_class` is one of `accept`, `mitigate`, `transfer`, `avoid`, `monitor` or `defer`, and `find_dispositions` filters by it. Create it with `record_disposition` `action="create_risk"`, sending `risk_id`, `disposition_policy_id` and `rationale`. Get the policy id from `find_dispositions` `subject="policy"`, choosing by its `decision_class`. On a Personal plan, use `action="personal_set_risk"` with `risk_id`, `decision_class` and `expected_version`; on a team plan it returns `authority_denied`. A `tier_upgrade_required` error means the plan does not include that move.

## Errors and retries

| Result | Meaning | Do |
|---|---|---|
| Payload `error.type="version_conflict"` with `current_version` | Someone changed the item after your read | Re-read it, check whether the change still makes sense, and resend with the new version. The suggested retry action already carries it. |
| Payload `error.type="not_found"` or `"authority_denied"` | The item does not exist, is not visible to the user, or the user cannot do this to it | Check the id; do not retry |
| JSON-RPC `-32602` with `data.allowed` | Wrong or missing selector value | Pick from `allowed` |
| JSON-RPC `-32602` with `data.conflicting_fields` | Two selectors at once, such as `query` with `rank_by` | Send only one |
| Payload `error.type="validation_failed"` with `error.fields.<name>[].code` | A field problem: `missing_required`, `invalid_format`, `invalid_enum`, or `corpus_not_implemented` | Fix the named field. For `corpus_not_implemented`, use `find_risks` or `find_mitigations` with `query`. |
| A timeout or dropped connection on a write | Unknown whether it landed | Resend with the same `_meta["riskthing/idempotency_key"]`. Never resend without the key. |

Send each new write with a fresh idempotency key, such as a UUID. Reuse a key only to retry that same write.
