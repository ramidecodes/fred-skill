# FRED methodology

## What a FRED is

A **Feature Requirement Document** is one implementable slice: goal, contracts, tasks, and acceptance. Not a product bible and not a dump of architecture.

- Filename: `{NNN}-{kebab-case-slug}.md`
- Title: `FRED NNN — Human Name`
- Allocate `NNN` from the open index’s **Next FRED number**; never reuse a closed ID.

## Authority

1. Product and architecture docs named by the **project entrypoint** own intent and local layout/stack.
2. **Code** owns runtime truth.
3. FREDs own how to implement a slice against those two.

If they disagree, say so. Do not silently invent a fourth source of truth.

## Index vs IDs

`docs/features/OPEN-FRED-INDEX.md` owns:

- Next number
- Open rows in **execution order** (dependency-valid, not filename order)
- Depth (draft vs detailed)
- Dependencies
- Status / remaining work
- Recently closed summary

Numeric IDs stay stable when order changes. Independent work may proceed against named fakes only if the task or index allows it.

## Depth rule

| Depth | Allowed | Before coding |
| --- | --- | --- |
| Draft | User outcomes, authority, acceptance, non-goals | Fill feature-owned SQL/APIs/events/guards/timeouts/recovery against **implemented** dependencies |
| Detailed / implementable | Exact contracts for this slice | Implement; do not start later FREDs whose deps are missing |

Do not treat a draft as ready because the number is next.

## Header metadata (every FRED)

Required in the file header (before section 1):

- Architectural authority → entrypoint
- Derived from (source pages, prerequisite FREDs)
- Specification reference (architecture / README as this repo uses)
- Status
- Roadmap / stage if the project has one
- Dependencies (linked FREDs)

## Template sections

The skeleton always includes **all 11 numbered sections**. Fill what the slice needs; leave a short “N/A — …” rather than deleting a section.

| # | Section | Typical |
| --- | --- | --- |
| — | Surfaces Touched | **Mandatory** table of routes/packages/folders |
| 1 | Goal | **Mandatory** |
| 2 | User Story | **Mandatory** |
| 3 | Functional Requirements | **Mandatory** (include non-goals; other 3.x as relevant) |
| 4 | Data Requirements | **Mandatory** (even if “none”) |
| 5 | User Flow | **Mandatory** |
| 6 | Implementation Tasks | **Mandatory** |
| 7 | Acceptance Criteria | **Mandatory**; 7.1 Test Matrix **recommended** |
| 8 | Edge Cases | **Mandatory** (table may be empty with one N/A row) |
| 9 | Non-Functional Requirements | **Mandatory** (or N/A) |
| 10 | Manual Steps / Rollout | **Mandatory** (operator/secrets/DNS) |
| 11 | Decisions and Open Validation | **Mandatory** — locked decisions vs local proposals vs blocked live gates |

## Close-out

When the slice is implemented:

1. Move `docs/features/{NNN}-{slug}.md` → `docs/features/implemented/` (same name).
2. Repair relative links inside the moved file.
3. Update the open index: remove the open row; add recently closed; bump the Updated date; recount open/implemented.
4. Do **not** leave a stub in `docs/features/`.

## Honesty

- Record blocked live probes (missing credentials, unsigned webhooks, unpaid APIs).
- Reading docs is not a live validation of a provider.
- Do not claim APIs from model memory; check the installed version.
- Label fixtures and simulators so they are not mistaken for production evidence.
