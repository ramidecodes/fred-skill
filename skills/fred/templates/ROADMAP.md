# {{PRODUCT_NAME}} — FRED roadmap

**Updated:** {{DATE}}. **Next unused FRED ID:** `{{NEXT_NNN}}`.
**Active / focus trackline(s):** {{TRACKLINE_OR_NONE}}.

[Entrypoint](../agent-guides/00-AGENT-ENTRYPOINT.md) owns project workflow.
FRED headers own detailed lifecycle state and evidence; this roadmap summarizes
work and scheduling. [OPERATIONS](./OPERATIONS.md) owns delivery-task status.

A **trackline** is a named parallel claim board with ordered FRED rows, a
claim/owner, exclusive write paths or serialization rules, and no silent
cross-trackline switch. Historical inventory boards may sit beside an **active**
claim board without duplicating authority — only the active board schedules
new claims unless a row is explicitly re-claimed.

## Tracks in priority order

{{TRACK_OUTCOMES_OWNERS_SHARED_CONTRACT_OWNERS_AND_INTEGRATION_POINTS}}

Keep slices ordered within each track. Group by bounded outcome and ownership;
identify shared contracts and shared-file/migration coordination. Filename IDs
are stable identity, not execution order. A diagram is optional.

| Track | FRED | State | Implementation prerequisites | Readiness / claim | Next action / owner |
| --- | --- | --- | --- | --- | --- |
| {{TRACK}} | [{{NNN}} — {{TITLE}}](./{{NNN}}-{{slug}}.md) | Draft | {{CONTRACT_OR_IMPLEMENTED_DEPENDENCY_OR_NONE}} | {{READY_CLAIMED_BLOCKED_AND_REASON}} | {{NEXT_ACTION_AND_OWNER}} |

## Parallel tracklines

Seed this section when the project runs concurrent implementation. Fill from
real ownership boundaries (e.g. apps vs services); leave placeholders unknown
rather than inventing product rows.

### Ownership (exclusive write paths)

| Trackline | Outcome | Exclusive write ownership (default) | Typical FREDs |
| --- | --- | --- | --- |
| {{TRACKLINE}} | {{SHORT_OUTCOME}} | {{PATHS_OR_SINGLE_CLAIM}} | {{NNN_OR_NONE}} |

### Serialization rules (shared surfaces)

| Surface | Rule |
| --- | --- |
| Shared contracts / public APIs | {{SINGLE_SERIALIZER_OR_HANDOFF}} |
| Migrations / schema | {{ONE_CLAIM_AT_A_TIME_OR_HANDOFF}} |
| Shell / chrome / shared UI | {{OWNER_OR_EXPLICIT_HANDOFF}} |
| `docs/features/ROADMAP.md`, OPERATIONS, AGENTS | Coordinator / single writer per session — implementers update only their FRED + claim row |

### Claim board — active tracklines

| Order | Trackline | FRED | State | Claim / owner | Notes |
| --- | --- | --- | --- | --- | --- |
| 1 | {{TRACKLINE}} | [{{NNN}} — {{TITLE}}](./{{NNN}}-{{slug}}.md) | Open | {{CLAIM_OR_UNCLAIMED}} | {{NOTES}} |

### Parallelism rules

- **One claim per FRED** (or an explicit FE/BE split noted on the FRED).
- No silent trackline switch: if the selected/active trackline has no eligible
  work, report its blocker rather than claiming another board’s row.
- Do not weaken acceptance to unlock parallelism.
- An agreed contract plus explicitly allowed fake can enable parallel coding;
  name assumptions and the **real integration owner**.
- Trackline scheduling does not authorize delegation, push, or deployment.

## Selection and maintenance

- Choose the named FRED, respecting prerequisites. For “next,” take the
  highest-priority ready, unclaimed Open slice in the requested or designated
  active trackline, or across tracklines if neither is named. If the selected
  trackline has no eligible work, report its blocker rather than silently
  switching. Claim work when coordinating concurrent execution; update the
  active claim board on pause and finish.
- An agreed contract plus explicitly allowed fake can enable parallel coding;
  name assumptions and the owner of real integration. Prerequisites need not
  be Closed. Setup needed for coding is an implementation prerequisite too.
- Allocate IDs here; never reuse canceled/superseded IDs. Add a row and increment
  the next unused ID. Keep source links and requirements in the FRED.
- Mirror state transitions from the FRED. Keep paths stable and preserve history.
  Canceled/superseded work gets a disposition/replacement, not a false closure.
- Implemented rows retain a date (in their FRED) and next action or delivery link.
  Periodically inspect aging gates and available verification capacity.
- Global project checks must pass before implementation review handoff and
  Implemented/Closed sign-off; see the entrypoint. Module checks are insufficient.

## Pending delivery joins

{{LINKS_TO_SHARED_OPERATIONS_FLOWS_AND_THE_FREDS_THEY_COVER_OR_NONE}}

Link to OPERATIONS rather than duplicating task steps, status, or evidence here.
Retain Closed rows or a compact linked history when the active table grows.
Scheduling does not itself authorize agent delegation, Git push, or deployment.
