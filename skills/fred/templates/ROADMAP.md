# {{PRODUCT_NAME}} — FRED roadmap

**Updated:** {{DATE}}. **Next unused FRED ID:** `{{NEXT_NNN}}`.

[Entrypoint](../agent-guides/00-AGENT-ENTRYPOINT.md) owns project workflow.
FRED headers own detailed lifecycle state and evidence; this roadmap summarizes
work and scheduling. [OPERATIONS](./OPERATIONS.md) owns delivery-task status.

## Tracks in priority order

{{TRACK_OUTCOMES_OWNERS_SHARED_CONTRACT_OWNERS_AND_INTEGRATION_POINTS}}

Keep slices ordered within each track. Group by bounded outcome and ownership;
identify shared contracts and shared-file/migration coordination. Filename IDs
are stable identity, not execution order. A diagram is optional.

| Track | FRED | State | Implementation prerequisites | Readiness / claim | Next action / owner |
| --- | --- | --- | --- | --- | --- |
| {{TRACK}} | [{{NNN}} — {{TITLE}}](./{{NNN}}-{{slug}}.md) | Draft | {{CONTRACT_OR_IMPLEMENTED_DEPENDENCY_OR_NONE}} | {{READY_CLAIMED_BLOCKED_AND_REASON}} | {{NEXT_ACTION_AND_OWNER}} |

## Selection and maintenance

- Choose the named FRED, respecting prerequisites. For “next,” take the
  highest-priority ready, unclaimed Open slice in the requested track, or across
  tracks if none is named. Claim work when coordinating concurrent execution.
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
Scheduling does not itself authorize agent delegation, Git actions, or deployment.
