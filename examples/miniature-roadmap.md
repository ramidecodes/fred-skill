# Northwind Notes — FRED roadmap (miniature example)

**Updated:** 2026-11-24. **Next unused FRED ID:** `006`.
**Active / focus trackline(s):** Notes UI · Notes API.

Fake product for illustration only. Paths below are examples, not a real tree.

[Entrypoint](../skills/fred/templates/AGENT-ENTRYPOINT.md) would own project
workflow in a real repo. FRED headers own detailed lifecycle state; this file
summarizes scheduling. OPERATIONS would own delivery-task status.

A **trackline** is a named parallel claim board with ordered FRED rows, a
claim/owner, exclusive write paths or serialization rules, and no silent
cross-trackline switch. Historical inventory boards may sit beside an **active**
claim board without duplicating authority — only the active board schedules
new claims unless a row is explicitly re-claimed.

## Tracks in priority order

| Track | FRED | State | Implementation prerequisites | Readiness / claim | Next action / owner |
| --- | --- | --- | --- | --- | --- |
| Foundation | 001 — Repo check and CI | Closed | None | Done | — |
| Notes API | 002 — Note schema + list API | Implemented | 001 Closed | Done locally | OP-001 preview join |
| Notes UI | 003 — Notes list page | Open | Agreed Note DTO + MSW fake OK | Claimed (UI) | Finish list empty/error states |
| Notes API | 004 — Create note endpoint | Open | 002 Implemented | Ready / unclaimed | Implement create + validation |
| Notes UI | 005 — Create-note form | Draft | 004 contract (Open OK with fake) | Blocked: Draft decisions | Resolve Draft → Open |

## Parallel tracklines

### Ownership (exclusive write paths)

| Trackline | Outcome | Exclusive write ownership (default) | Typical FREDs |
| --- | --- | --- | --- |
| Notes UI | Operator can browse and create notes in the app | `apps/web/src/notes/**`, shared note list fixtures under `apps/web/src/mocks/notes/**` | 003, 005 |
| Notes API | Persist and serve notes over HTTP | `services/api/src/notes/**`, note migrations under `packages/db/migrations/notes/**` | 002, 004 |
| Shared contracts | Single serializer for public note shapes | `packages/contracts/src/notes/**` — one writer per session | Owned by API trackline unless handoff noted |

### Serialization rules (shared surfaces)

| Surface | Rule |
| --- | --- |
| Shared contracts / public APIs | One claim at a time on `packages/contracts/src/notes/**`; UI consumes agreed DTO or named fake |
| Migrations / schema | One migration claim at a time; API trackline owns note schema edits |
| Shell / chrome / shared UI | Notes UI owns notes routes only; shell chrome changes need explicit handoff |
| `docs/features/ROADMAP.md`, OPERATIONS, AGENTS | Coordinator / single writer per session — implementers update only their FRED + claim row |

### Claim board — active tracklines

| Order | Trackline | FRED | State | Claim / owner | Notes |
| --- | --- | --- | --- | --- | --- |
| 1 | Notes UI | 003 — Notes list page | Open | UI agent A | Empty/error states remaining |
| 2 | Notes API | 004 — Create note endpoint | Open | Unclaimed | Ready; exclusive API paths |
| 3 | Notes UI | 005 — Create-note form | Draft | — | Not claimable until Open |

### Historical inventory (optional, non-authoritative)

A completed-wave board may sit beside the active board for humans (e.g. wave-0
foundation rows). It does **not** schedule new claims; do not copy claim/owner
authority onto both boards. Re-claim a historical row on the **active** board
if work reopens.

### Parallelism rules

- **One claim per FRED** (or an explicit FE/BE split noted on the FRED).
- No silent trackline switch: if the selected/active trackline has no eligible
  work, report its blocker rather than claiming another board’s row.
- Do not weaken acceptance to unlock parallelism.
- An agreed contract plus explicitly allowed fake can enable parallel coding;
  name assumptions and the **real integration owner**.
- Trackline scheduling does not authorize delegation, push, or deployment.
