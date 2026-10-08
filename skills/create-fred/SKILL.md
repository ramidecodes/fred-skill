---
name: create-fred
description: >-
  Create or refine a Feature Requirement Document (FRED) in the current
  repository. Use to turn a feature idea into a scoped specification, gather
  requirements, resolve implementation questions, or make a Draft ready for
  implementation. Produces a FRED plus roadmap and delivery-task updates.
---

# Create FRED

Turn the user's intended outcome into a slice another agent can implement
without guessing. Work conversationally; ask only questions whose answers
materially affect scope, behavior, contracts, or verification.

## Read the project contract

Follow applicable AGENTS instructions and the project's agent entrypoint,
normally `docs/agent-guides/00-AGENT-ENTRYPOINT.md`. Read its FRED template,
ROADMAP, existing related slices, and relevant architecture/code. Load procedure
guides only when needed. Project documents and user instructions govern scope,
paths, lifecycle, commands, and permissions; this skill adds a creation workflow.

Use the project's legacy index/layout if it has not migrated. Do not load a
sibling skill by relative filesystem path: this skill can be installed alone.
If FRED infrastructure is missing, use the available `fred` bootstrap workflow
when requested or accepted. Otherwise continue useful requirement gathering
and offer bootstrap before creating a competing document structure. Do not
silently migrate an existing project or code the feature during specification.

## Gather and resolve requirements

1. Establish the intended user/operator, outcome, current behavior, and scope.
   Reuse supplied context and existing requirements rather than asking again.
2. Inspect affected code and architecture for actual capabilities, reusable
   contracts, and constraints. Separate implemented facts from proposals.
3. Identify consequential unknowns: permissions, data/state ownership, external
   behavior, compatibility, error recovery, and deployment/configuration needs.
   Ask a small focused set of clarifying questions with recommendations and
   tradeoffs. Progress on independent inspection while answers are pending.
4. Research genuinely uncertain contracts or integrations using the installed
   versions and relevant official sources. Record source links and assumptions;
   browsing documentation is not proof of a live integration. Avoid research
   unrelated to a decision the slice needs.
5. Propose an implementable slice with explicit non-goals. If the requested
   outcome needs several slices, explain the split and integration points;
   respect the user's scope before expanding into a product-wide backlog.

Straightforward requests need no mandatory interview. Use stated assumptions
for low-impact choices; unresolved decisions that materially change the
implementation keep the FRED Draft. Do not invent answers or treat silence as
approval of a required decision.

## Specify the slice and its place in the roadmap

- Use the project template; allocate the next unused stable ID from ROADMAP
  (or its legacy equivalent). Account for all existing states/history and
  concurrent allocation; never reuse an ID. Preserve the ID when refining a draft.
- Describe goal/non-goals, observable behavior, contracts/affected surfaces,
  tasks, implementation acceptance, evidence expectations, and delivery links.
  Add schema/API/event, UI, migration, timeout/recovery, or policy detail only
  where it changes implementation decisions.
- Assign a bounded-outcome track and identify shared contract/migration owners.
  Distinguish prerequisites requiring an agreed interface from those requiring
  implemented code. Allowed fakes name assumptions, limitations, and the owner
  of real integration. Check for dependency cycles and shared-surface conflicts.
- Define proportionate implementation checks. UI slices retain rendering/layout
  and state inspection; backend slices retain relevant rule, authorization,
  persistence, and integration checks. Include the project's global lint/format
  check before implementation review handoff and Implemented/Closed sign-off,
  including cascading monorepo checks; module checks cannot replace it.
- Create applicable OPERATIONS items now for external setup and shared deployed
  journeys. Each has an owner, prerequisites, what it blocks, target, executable
  steps, pass condition, and evidence destination. One flow may cover several
  FREDs. Setup needed to discover a contract or code behavior is also an
  implementation prerequisite, not merely a closure gate.

## Write and hand off

Write or update the FRED and synchronize ROADMAP and applicable OPERATIONS
links. Keep paths stable. Mark Open only when scope/contracts and local
acceptance are sufficiently defined under project rules; otherwise retain
Draft with the exact unresolved question and next action. An Open slice may
still be blocked by an explicit prerequisite. Planning-only Draft → Open does
not require running code checks or claim implementation/verification success.

Link existing architecture and guides. Record relevant research where it is
useful, and label proposed architectural changes; do not describe them as
implemented. Add a new document only for knowledge that merits maintenance.
Record justified changes to existing acceptance or verification expectations,
without weakening them merely to permit sign-off. Keep secrets out of specs.

Finish with the FRED link, state/track, consequential assumptions or unresolved
questions, and implementation readiness. When specification stops unfinished,
leave concise resume notes. Honor existing Git/deploy authorization; allocating
a slice or creating an operator task does not authorize external actions.
