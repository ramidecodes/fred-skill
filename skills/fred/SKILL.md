---
name: fred
description: >-
  Bootstrap (/init), migrate, and maintain the FRED methodology in a software
  repository. Use for /init, bootstrap FRED, set up FRED docs, migrate legacy
  indexes, coordinate parallel tracklines/claim boards, manage delivery gates,
  or review the project workflow. Routine slice specification and coding use
  create-fred and implement-fred when available; human status reports use
  fred-status when available.
---

# FRED

**FRED** = Feature Requirement Document. One implementation slice per file.

This skill supplies methodology and templates. Existing project documents and
user instructions govern the consuming repository; templates are seeds.

For routine tasks, use available `create-fred` to gather requirements and write
or refine a slice, and `implement-fred` to select and execute agreed work.
Use available `fred-status` for roadmap / “what’s left” / dogfood posture
reports. Those skills read the consuming project's contract directly. Do not
assume optional siblings are installed or resolve them through relative source
paths. When only `fred` is available, its template and references still support
these tasks. Bootstrap (`/init`) and migration remain here — there is no
separate `fred-init` skill. No model change or delegation is implied by
selecting a skill.

## Start and route

1. Read the project agent contract: prefer
   `docs/agent-guides/00-AGENT-ENTRYPOINT.md`, following applicable `AGENTS.md`
   instructions and README pointers. Follow the project's documented workflow.
2. For planning, implementation, or “what next,” read
   `docs/features/ROADMAP.md` and the relevant FRED. For setup or delivery
   verification, also read the linked items in `docs/features/OPERATIONS.md`.
3. Load architecture and procedure guides relevant to the task through those
   pointers. Route by task, document responsibility, and section; read the
   source before relying on its contracts. Summaries aid discovery, not authority.
   Discover missing relevant documentation when necessary.
4. If FRED docs are absent and the user wants this methodology — including
   `/init`, “bootstrap FRED”, or “set up FRED docs” — use
   [references/bootstrap.md](references/bootstrap.md) (**scan → propose →
   write**). Offer bootstrap when it has not been requested. Do not impose a
   competing spec system.

Existing projects may still use `OPEN-FRED-INDEX.md` and state folders. Follow
their contract until migration is requested; do not silently reorganize them.

## Document responsibilities

| Document | Owns |
| --- | --- |
| Product / architecture | Intent, durable boundaries, contracts, decisions |
| Agent entrypoint / guides | Project workflow, commands, environment procedures |
| FRED | Slice scope, criteria, authoritative lifecycle state, evidence |
| ROADMAP | Stable IDs, tracks/tracklines, priority, dependency and state summaries, claim boards, next actions |
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

After the global check, run additional QA (including browser or render
inspection when relevant) only when the FRED's verification criteria or QA
section calls for it. Prefer available browser tooling for UI/browser-shaped
checks; report not-run honestly when tooling, auth, or environment is missing.
Backend slices still need proportionate rule, authorization, persistence, and
integration checks when those criteria apply. Defer shared deployed journeys
and external setup, not slice correctness the FRED owns.

Deployable features close with preview or production evidence specifying which
environment passed. Tooling and libraries close with relevant integration
evidence. Implemented does not mean “most code exists”; mocks cannot establish
an integrated outcome promised by the slice.

## Tracks, tracklines, and dependencies

- Allocate the next unused ID from ROADMAP; never reuse an ID. Specify or deepen
  the slice before coding. Use [templates/feature.md](templates/feature.md).
- Group ordered slices by bounded outcome and ownership. Identify shared
  prerequisites and contracts before opening independent tracks.
- **Tracklines** are parallel claim boards with exclusive write ownership and
  serialization rules; see ROADMAP template and methodology. Historical
  inventory boards may exist beside an active claim board without duplicating
  authority.
- Implementation prerequisites block coding or integration. An agreed contract
  and explicitly allowed fake may enable parallel work before the provider is
  implemented; record assumptions and the owner of real integration. Do not
  weaken acceptance to unlock parallelism.
- Delivery gates block closure. Setup actually necessary to discover a contract
  or implement behavior must also be named as an implementation prerequisite.
  Downstream work need not wait for prerequisites to be Closed.
- For “next,” choose the highest-priority ready, unclaimed Open slice in the
  requested or roadmap-designated active trackline, or across tracklines if
  neither is named. If that trackline has no eligible work, report its blocker
  rather than silently switching. Respect a named FRED's prerequisites.
  Readiness, claims, and blockers are roadmap fields, not states.
- Trackline scheduling does not authorize delegation, push, or deployment.
  Default Git policy: agents may commit when authorized; do not push without
  user authorization.

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

Changes to acceptance, verification scripts, or CI/global-check scope need a
recorded rationale under the project's decision process. Do not disable checks
or narrow coverage just to obtain a pass; reviewers inspect these changes too.

When stopping with unfinished work or handing it off, leave concise resume
notes in the FRED: baseline, completed/remaining work, checks, blocker, and next
action. Refresh the current summary rather than adding a session transcript.
On resume, compare notes with the actual checkout and relevant environment.

Follow the project's Git/deploy rules and existing conversation authorization;
when committing, follow the entrypoint Git/PR policy (Conventional Commits by
default; FRED id in the commit **body**, not the scope). Agents may commit
their own changes when authorized; **do not push**, open PRs, provision, or
deploy without a user request. If silent on commits, do not commit either.
Do not claim provider behavior from remembered SDK shapes or documentation
browsing: check installed versions and relevant official docs, and record
blocked live probes. Label fixtures. Keep secrets out of specs and evidence.

Bootstrap (`/init`) creates an entrypoint, FRED template, ROADMAP (with
trackline seed), and OPERATIONS, plus an optional root AGENTS pointer —
scan → propose → write; see bootstrap guidance. Migration is explicit and
preserves existing scope, IDs, history, and verification evidence.

## Optional companion skills

The package includes `create-fred`, `implement-fred`, and `fred-status` for
specification, coding, and human status reports. Shared project rules live in
the entrypoint and project documents; companions load the task guidance they
need.
Consider a separate skill only for a recurring, distinct workflow with clear
inputs, outputs, and invocation boundaries. Project guides remain authority;
companions consume them and write results into existing FRED/OPERATIONS files.
Keep FRED usable without companions, and preserve its global check gate.
For candidate workflows, packaging versus project-local placement, and manual
invocation policies, read [references/project-skills.md](references/project-skills.md)
when evaluating or adding further skills. Do not bootstrap a project skill suite
by default.
