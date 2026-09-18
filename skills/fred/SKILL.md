---
name: fred
description: >-
  Applies Feature Requirement Documents (FREDs) and the consuming project's
  agent entrypoint for planning, implementing, reviewing, debugging, and
  bootstrapping software. Use at the start of every session and whenever
  coding, implementing, planning, scaffolding, reviewing PRs, or choosing
  next work in a repository that uses or should use FREDs, Feature Requirement
  Documents, agent entrypoints, OPEN-FRED-INDEX, docs/features, or
  00-AGENT-ENTRYPOINT.md. Locates and reads the project's entrypoint before
  other work; bootstraps FRED docs only when they are missing.
---

# FRED

**FRED** = Feature Requirement Document. One implementation slice per file.

This skill is methodology + generators. The **consuming project's** entrypoint, index, architecture, and code are authority — never this skill's templates once those files exist.

## 0. Session start (always)

Before other work this session:

1. Find and **READ** the project agent entrypoint. Prefer, in order:
   - `docs/agent-guides/00-AGENT-ENTRYPOINT.md`
   - `AGENTS.md` (root or `docs/`)
   - a README / AGENTS.md pointer to the entrypoint
2. If found: follow **that** file. Do not overlay skill defaults on top of it.
3. If missing and the user is starting or growing a product/codebase: offer to bootstrap (see [references/bootstrap.md](references/bootstrap.md)). Do not dump templates into an unrelated repo without asking.
4. Then read `docs/features/OPEN-FRED-INDEX.md` when the task is implementation or “what next.”
5. Read a FRED file when implementing or specifying that slice. Read architecture docs **only as linked** from the entrypoint/FRED — not as a substitute for the index.

Do not paste this skill's templates into the conversation as product truth. Generate into the project only during bootstrap, then edit the **project** copies.

Recommend consuming repos add a one-liner in `AGENTS.md` or README so teammates without this skill still load the contract:

```markdown
Agent contract: read docs/agent-guides/00-AGENT-ENTRYPOINT.md at session start.
```

## Git, deploy, PRs

Follow the project entrypoint. If it is silent: do not commit, push, open PRs, or deploy unless the user asks. Entrypoint wins.

## Authority

| Layer | Owns |
| --- | --- |
| Product / architecture docs (as linked from the entrypoint) | Product intent, stack/layout **for this repo** |
| **Code** | What actually runs |
| FREDs | How to implement **one slice** |
| Open index | Sequence, status, dependencies — **not** filename sort |

IDs (`NNN`) are stable identity. Execution order is the index table.

Do not invent shipped surfaces. Label local proposals as proposals. Docs browsing ≠ live provider/SDK validation. Do not claim third-party APIs from training memory — verify installed versions and current docs. Record blocked probes honestly.

## FRED files

- Path: `docs/features/{NNN}-{kebab-slug}.md`
- One slice per file. Next `NNN` from the index, not from guessing.
- Header: status, dependencies, derived-from, specification references.
- **Depth:** drafts may state outcomes/acceptance; before coding, fill feature-owned contracts (schema, events, guards, timeouts, recovery) against **implemented** dependencies.
- Close-out: move the file to `docs/features/implemented/`, repair relative links, remove the open-index row, add a recently-closed line. **No stub** left in `docs/features/`.

Full skeleton (all 11 numbered sections): [templates/feature.md](templates/feature.md). Methodology: [references/methodology.md](references/methodology.md). Workflow: [references/agent-workflow.md](references/agent-workflow.md).

## Optional patterns (use when they fit; not law)

- Simulator / fake adapter **before** live third-party writes.
- **Labeled fixtures** for UI/modules that are not real yet.
- Feature-owned schema vs shared contracts — later slices own their tables; do not migrate the world in one FRED.
- Cross-cutting controls (pause, budgets, retention) ship **with** the feature that needs them, not as folklore.
- Human operator checklists for secrets, DNS, dashboards — do not pretend the agent can complete those.

## Bootstrap (only if FRED docs are missing)

Generate from templates with `{{PLACEHOLDERS}}` filled from **this** repo. Never copy another product's FREDs.

Creates:

- `docs/agent-guides/00-AGENT-ENTRYPOINT.md`
- `docs/features/template.md`
- `docs/features/OPEN-FRED-INDEX.md`
- `docs/features/implemented/README.md`
- optional root `AGENTS.md` pointer

Details: [references/bootstrap.md](references/bootstrap.md).

## Do not

- Treat this skill as product/stack law (no required Next/Clerk/Neon/etc.).
- Override existing FRED docs with skill defaults.
- Encode another product's hierarchy, publication order, or FRED 001–N contents.
- Trust remembered SDK shapes over lockfile + docs.
