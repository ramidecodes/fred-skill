# FRED {{NNN}} — {{FEATURE_NAME}}

**Status:** Draft
**Track:** {{TRACK}}
**Authority:** [Agent entrypoint](../agent-guides/00-AGENT-ENTRYPOINT.md)
**Derived from:** {{SOURCE_OR_LOCAL}}
**Architecture / contracts:** {{RELEVANT_DOCUMENT_LINKS}}
**Implementation prerequisites:** {{FRED_LINKS_AND_REQUIRED_CONTRACT_OR_IMPLEMENTATION_OR_NONE}}
**Delivery gates:** {{OPERATIONS_ITEM_LINKS_OR_NONE}}

Scheduling and readiness: [ROADMAP](./ROADMAP.md). Keep this path stable across
Draft / Open / Implemented / Closed. Remove template instructions when filled.

## Goal and non-goals

{{SCOPED_OUTCOME_AND_EXPLICIT_EXCLUSIONS}}

## Behavior, contracts, and surfaces

{{TESTABLE_BEHAVIOR_AND_AFFECTED_ROUTES_PACKAGES_OR_WORKFLOWS}}

<!-- Add detail only when relevant: state ownership, data reads/writes/schema,
API/event shapes, guards, timeouts/recovery, compatibility/migrations, UI flow
and design states, performance/security constraints, env names and policy.
Contracts must be sufficiently defined before Open. When using an allowed fake,
name the agreed contract, limitations, owner, and real integration responsibility.
Keep requirements here; shared verification execution steps live in OPERATIONS. -->

## Implementation tasks

- [ ] {{IMPLEMENTATION_TASK}}
- [ ] Update affected architecture and procedure docs, if changed.
- [ ] Create/refine applicable setup and flow-verification items in OPERATIONS.

## Implementation acceptance

- [ ] {{OBSERVABLE_SLICE_CRITERION}}
- [ ] Required behavioral checks pass; UI changes were rendered and inspected.
- [ ] Project global check passes at its documented scope on the final work.

<!-- Define proportionate checks, including relevant rules, permissions,
persistence, contracts, and local integration. Existing cheap relevant E2E
checks still run. Never quietly weaken criteria to fit the implementation. -->

<!-- Changes to acceptance, verification scripts, or CI/global-check coverage
need a recorded rationale under the project decision process. Review those
changes with the feature; do not disable checks merely to obtain a pass. -->

## Verification and handoff evidence

**Integration baseline:** {{REVISION_OR_WORKING_TREE_CONTEXT}}
**Implemented date:** {{DATE_OR_PENDING}}

| Check / inspection | Command or method / scope | Result and evidence | Date / revision |
| --- | --- | --- | --- |
| Global check | Project entrypoint command and working directory | Pending | |
| Slice behavior / UI inspection | {{REQUIRED_METHOD}} | Pending | |

Before review handoff or Implemented/Closed sign-off, run the global command
from the entrypoint, including its cascading module checks. Module-only checks
do not replace it. Rerun after changes to check inputs; blocked/failed checks
block sign-off. Record actual results, not expected results.

**Independent review:** {{NOT_REQUIRED_OR_PENDING_OR_LINKED_FINDINGS}}
<!-- When applicable, append required corrections, delivery gaps, and optional
improvements separately. Required corrections return this FRED to Open. -->

## Delivery and closure

Linked [OPERATIONS](./OPERATIONS.md) items: {{APPLICABLE_TASK_IDS_OR_NONE}}.
**Next action / owner:** {{PENDING_GATE_OR_NEXT_ACTION_AND_OWNER}}
**Closed date / target:** {{DATE_AND_PREVIEW_PRODUCTION_OR_INTEGRATION_TARGET_OR_PENDING}}
**Closure evidence:** {{GATE_RESULTS_AND_DEPLOYMENT_OR_REVISION_LINKS_OR_PENDING}}

Implemented requires scoped behavior, local checks, global check, and updated
docs. Closed additionally requires applicable delivery/review evidence and a
current global-check pass. A mock cannot prove an integrated outcome. Record
preview versus production explicitly; tooling/libraries use relevant integration
proof. Configuration blockers leave correct code Implemented; code defects reopen it.

<!-- Add decisions/open questions only when needed. Record justified scope
changes and source decisions; optional improvements become follow-up proposals. -->

<!-- Optional Resume notes: include only when work stops unfinished or changes
hands. Keep a concise current summary, not a session log:
Last worked: date and revision / working-tree context
Completed / remaining: actual work and immediate unfinished tasks
Verification: passed, failed, and not-run checks; link existing evidence
Blocker: specific cause or none
Next action / owner: concrete step and current claim
On resume, compare notes with the checkout and relevant environment. Remove
resolved temporary notes or fold durable facts into the sections above. -->
