# FRED methodology

## Slice and readiness

A FRED is one implementable slice with goal/non-goals, contracts and affected
surfaces, tasks, implementation criteria, evidence, and delivery links. Add data,
user-flow, migration, failure/recovery, or operational constraints when needed.
Drafts can be brief; before Open, resolve decisions needed to implement without
guessing. The filename is `{NNN}-{kebab-slug}.md`; the title is
`FRED NNN — Human Name`. Allocate from ROADMAP's next unused ID, considering all
states and retained history. Never reuse canceled or superseded IDs.

The FRED header owns lifecycle state; ROADMAP summarizes it. Status changes
update both together. OPERATIONS owns task status and delivery evidence.
Avoid extra counts, per-folder tables, and mandatory dependency diagrams.

## Track planning

1. Identify bounded outcomes and the surfaces each needs.
2. Establish shared prerequisites, contract owners, and migration ownership.
3. Group slices into tracks with minimal cross-track implementation dependencies.
4. Order work within each track and identify where integration will occur.
5. Create setup and flow-verification items covering those joins.

Prefer capability tracks over a default frontend/backend split. A track is a
schedule, not a long-lived branch or automatic multi-agent runtime. Coordinate
shared-file edits and claims through ROADMAP when work is concurrent.

Prerequisites distinguish an agreed interface from an available implementation.
For work against a fake, specify the agreed contract, its owner, the fake's
limitations, and the real integration responsibility. Check cycles: mutually
dependent slices usually need a shared contract or a clearer scope split.

## Lifecycle

Draft → Open requires enough scope and contracts to start, not deployed evidence.
Open → Implemented requires scoped behavior, required local verification, the
global check gate in SKILL.md, documentation updates, and linked delivery work.
Implemented → Closed requires that gate again and all applicable delivery and
required review evidence. A prerequisite need not be Closed to enable coding.

Use the project's designated integration baseline: identify the revision or
working tree. If the project requires a merge before Implemented, unmerged
branch work remains Open. Do not infer permission to merge or deploy.

Readiness is ready / claimed / blocked in ROADMAP, with owner and specific next
action. Keep a blocked approved slice Open rather than moving it to Draft.
Each Implemented FRED records its implementation date and pending next action.
Periodically inspect aging gates, at a cadence appropriate to the project;
prefer clearing them before starting more work when verification capacity is full.

## Verification boundary

Implementation acceptance describes behavior the slice owns. Keep necessary
local tests and integration checks with it, including UI inspection when UI
changes. Linting/formatting success alone is not behavioral verification.
Run relevant existing inexpensive automated E2E checks when available.

OPERATIONS holds executable setup and shared flow procedures. Create items
during specification and refine them as implementation clarifies prerequisites.
Each records owner/executor, what it blocks, target, steps, pass condition,
status, and evidence. Agent-executable work can be performed by a suitably
equipped agent within authorization; human access requirements stay explicit.
Record env names and public key/account identifiers, never secret values.

One flow can cover several FREDs; link only gates applicable to each scope.
Code defects reopen the owning FRED; missing configuration leaves correct code
Implemented. Optional improvements become follow-up proposals. Revalidate flows
affected by later contract/code/configuration changes; retain historical evidence
with its revision and environment rather than claiming it covers changed work.
Canceled/superseded work gets an explicit disposition and replacement link,
not a fictitious successful closure.

## Living project knowledge

Architecture owns durable boundaries, state ownership, schemas/interfaces, and
important decisions. Update affected existing docs with the implementation.
Label proposed future behavior; resolve deviations rather than blessing them
after the fact. Link code/generated schema for detail already maintained there.
Decision records are useful for consequential choices, not mandatory per slice.

The entrypoint routes to reusable guides only when needed. CI guides identify
relevant workflows, local equivalents, run/log inspection, and rerun policies.
Database guides identify environment selection, supported credential sources,
tenant context, inspection commands, allowed test writes/cleanup, and evidence.
Preview guides explain startup/access and deployment identification. Reuse
scripts for repeated mechanics; put one-time setup work in OPERATIONS.

Make routing descriptions identify when to read a document, which section is
relevant, and what it owns. Use source links rather than copying contracts into
summaries; a source update should not require editing several parallel indexes.
Keep knowledge navigation separate from the implementation dependency graph.
Optional companion skills orchestrate a repeated task using guides/scripts;
they do not become a competing source of architecture, status, or permissions.

Keep next IDs and scheduling in ROADMAP, detailed slice evidence in FREDs, and
operation results in OPERATIONS. Do not duplicate command recipes or global
architecture inside every FRED.
