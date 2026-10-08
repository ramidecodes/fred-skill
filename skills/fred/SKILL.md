---
name: fred
description: >-
  Plan, implement, and review repository features using Feature Requirement
  Documents (FREDs), parallel implementation tracks, and delivery checklists.
  Use when writing or implementing a FRED, choosing the next slice, coordinating
  tracks, bootstrapping FRED documentation, or reviewing against a project agent
  entrypoint. Applies to software work in the current repository.
---

# FRED

**FRED** = Feature Requirement Document. One implementation slice per file.

This skill supplies methodology and templates. Existing project documents and
user instructions govern the consuming repository; templates are seeds.

## Start and route

1. Read the project agent contract: prefer
   `docs/agent-guides/00-AGENT-ENTRYPOINT.md`, following applicable `AGENTS.md`
   instructions and README pointers. Follow the project's documented workflow.
2. For planning, implementation, or “what next,” read
   `docs/features/ROADMAP.md` and the relevant FRED. For setup or delivery
   verification, also read the linked items in `docs/features/OPERATIONS.md`.
3. Load architecture and procedure guides relevant to the task through those
   pointers; discover missing relevant documentation when necessary.
4. If FRED docs are absent and the user wants this methodology, use
   [references/bootstrap.md](references/bootstrap.md). Offer bootstrap when it
   has not been requested. Do not impose a competing spec system.

Existing projects may still use `OPEN-FRED-INDEX.md` and state folders. Follow
their contract until migration is requested; do not silently reorganize them.

## Document responsibilities

| Document | Owns |
| --- | --- |
| Product / architecture | Intent, durable boundaries, contracts, decisions |
| Agent entrypoint / guides | Project workflow, commands, environment procedures |
| FRED | Slice scope, criteria, authoritative lifecycle state, evidence |
| ROADMAP | Stable IDs, tracks, priority, dependency and state summaries, claims, next actions |
| OPERATIONS | Setup tasks and shared delivery flows, their status and evidence |

Code establishes runtime facts. Resolve discrepancies with intended contracts;
do not rewrite architecture or acceptance merely to justify incorrect code.

## Lifecycle and sign-off

Keep files at `docs/features/{NNN}-{kebab-slug}.md`; update their status headers
and roadmap summaries without moving files. IDs are stable, not execution order.

| State | Meaning / gate |
| --- | --- |
| Draft | Scope or contracts need decisions. |
| Open | Approved slice with sufficiently defined scope, contracts, and implementation criteria; required implementation work or checks remain. |
| Implemented | Scoped behavior is in the project's designated integration baseline, required local checks pass, affected documentation is updated, and remaining delivery gates are linked. |
| Closed | Applicable review, setup, and delivery gates pass in the declared target environment, with evidence. |

**Global check gate:** before handing an implementation to review or signing off
as Implemented or Closed, run the project's global check command from its
documented working directory on the current work and require success. This
command covers project-wide linting and formatting, including cascading checks
across monorepo modules. Module-only checks do not replace it. Also run the
slice's required behavioral checks. Record command, scope, result, date, and
revision or working-tree context in the FRED. Rerun after subsequent changes
before sign-off; a prior pass on different code is insufficient. A missing,
blocked, or failing command blocks sign-off: report the cause and next action,
retain the current state, and do not mark the checks passed. Planning-only
Draft → Open does not require executing code checks.

UI implementation still requires rendering and inspecting the changed surface,
layout, responsive behavior, and relevant states. Backend implementation still
requires proportionate rule, authorization, persistence, and integration checks.
Defer shared deployed journeys and external setup, not slice correctness.

Deployable features close with preview or production evidence specifying which
environment passed. Tooling and libraries close with relevant integration
evidence. Implemented does not mean “most code exists”; mocks cannot establish
an integrated outcome promised by the slice.

## Tracks and dependencies

- Allocate the next unused ID from ROADMAP; never reuse an ID. Specify or deepen
  the slice before coding. Use [templates/feature.md](templates/feature.md).
- Group ordered slices by bounded outcome and ownership. Identify shared
  prerequisites and contracts before opening independent tracks.
- Implementation prerequisites block coding or integration. An agreed contract
  and explicitly allowed fake may enable parallel work before the provider is
  implemented; record assumptions and the owner of real integration.
- Delivery gates block closure. Setup actually necessary to discover a contract
  or implement behavior must also be named as an implementation prerequisite.
  Downstream work need not wait for prerequisites to be Closed.
- For “next,” choose the highest-priority ready, unclaimed Open slice in the
  requested track, or across tracks if none is named. Respect a named FRED's
  prerequisites. Readiness, claims, and blockers are roadmap fields, not states.
- Track scheduling does not authorize delegation, Git actions, or deployment.

Planning and state details: [references/methodology.md](references/methodology.md).
Implementation, review, and sign-off: [references/agent-workflow.md](references/agent-workflow.md).

## Delivery and documentation

Create applicable OPERATIONS items while specifying the slice. Link their stable
IDs from the FRED; keep execution steps and task status in OPERATIONS. One flow
may validate several FREDs. Each Implemented FRED has a date and a next action
or linked pending gate so deferred work remains visible.

Update existing architecture docs for changed durable contracts and boundaries,
and project guides for changed procedures, before implementation sign-off.
Reuse existing docs and scripts. Add conditional data, UX, migration, or policy
detail only when relevant; there is no fixed eleven-section requirement.

## Review and permissions

Independent review is optional unless the project or user requires it. Consider
it for consequential changes and cross-track integration. Use an available
reviewer/model within authorized scope; this skill does not require a provider
or authorize paid model calls. Record required corrections separately from
delivery gaps and optional improvements. Document and justify scope changes;
never quietly weaken acceptance. Review approval does not replace execution.

Follow the project's Git/deploy rules and existing conversation authorization.
If silent, do not commit, push, open PRs, or deploy without a user request.
Do not claim provider behavior from remembered SDK shapes or documentation
browsing: check installed versions and relevant official docs, and record
blocked live probes. Label fixtures. Keep secrets out of specs and evidence.

Bootstrap creates an entrypoint, FRED template, ROADMAP, and OPERATIONS, plus an
optional root AGENTS pointer. Migration is explicit and preserves existing
scope, IDs, history, and verification evidence; see bootstrap guidance.
