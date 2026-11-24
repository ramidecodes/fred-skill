---
name: fred-review
description: >-
  Independently review a FRED implementation against its contract, diff/code,
  and verification evidence. Use at review handoff before marking Implemented
  or Closed after an implementation round on an Open (or Implemented-candidate)
  FRED, or when the user asks to review a named FRED/diff. Not routine for
  every tiny Open FRED; not a substitute for the global check or OPERATIONS
  delivery execution. Records Required corrections / Delivery gaps / Optional
  improvements.
---

# Review FRED

Independent inspection of a slice’s **contract + diff/code + evidence** before
lifecycle promotion, or when the user asks for that review.

## When to use

**Primary trigger — yes:** end of an implementation round for an Open FRED
(handoff **before** marking Implemented or Closed), when independent inspection
is useful. That is the default time to invoke this skill.

Also use when:

- The user asks to review a named FRED, diff, or implementation handoff.
- The coordinator or user wants a consequential **mid-slice** check (shared
  contracts, migrations, security-sensitive surfaces) before continuing coding.

Do **not** treat this skill as:

- Routine for every tiny Open FRED or trivial doc-only tweak.
- A substitute for the project’s **global check** (lint/format gate).
- A substitute for **OPERATIONS** delivery execution (setup, preview/prod joins).
- Automatic model upgrade or paid-tool authorization — selecting this skill
  only loads review instructions.

## Read first

1. Follow applicable `AGENTS.md` and the project agent entrypoint, normally
   `docs/agent-guides/00-AGENT-ENTRYPOINT.md`.
2. Read the named FRED (scope, non-goals, acceptance, verification, evidence).
3. Inspect the **actual** diff/code and relevant architecture contracts — not
   only the implementer’s summary.
4. Read recorded local evidence (commands, results, not-run checks). Note
   limits when runtime access is missing.
5. Confirm the global check command/working directory from the entrypoint; do
   not invent a pass. Requiring success remains the implementer’s gate; the
   reviewer verifies the record matches the tree when possible.

Project documents govern lifecycle and permissions. This skill supplies the
review procedure and findings format. Do not rely on sibling skill paths
surviving installation.

## Review procedure

1. Compare acceptance and non-goals to the shipped change. Flag unmet criteria,
   scope creep, and unjustified weakening of checks or coverage.
2. Inspect changes to criteria, test assertions/fixtures, verification scripts,
   and CI/global-check coverage alongside feature code. Require a recorded
   rationale for contract/gate changes.
3. Check evidence honesty: command, directory/scope, date, result, revision or
   working-tree context. Label not-run checks; fixtures ≠ live compatibility.
4. Separate **code defects** from **delivery/setup** gaps (OPERATIONS).
5. Stay focused: one review pass that cites findings. Further passes need a
   concrete unresolved issue; persistent scope disagreements need a user
   decision.

Do not launch delegation or change model/cost settings without applicable
authorization. Prefer an authorized separate session/agent when true
independence is required.

## Findings format

Append a concise review record to the FRED (match
[agent-workflow](../fred/references/agent-workflow.md) independent review):

- **Required corrections:** specific unmet criteria/defects, code locations,
  expected behavior, and a way to verify the correction. **Return to Open**
  (or keep Open if not yet Implemented).
- **Delivery gaps:** linked configuration or shared-flow items. **Remain
  Implemented** when local implementation is otherwise sound.
- **Optional improvements:** proposals only — not new acceptance gates.

The reviewer may record findings, not silently soften requirements. Document
and justify scope changes under the project’s decision process. After required
corrections, the implementer reruns the global check before the next handoff.

## Finish

Report FRED id/title, whether Required corrections exist, delivery gaps,
optional notes, and the resulting lifecycle recommendation (stay Open /
Implemented with gaps / ready for Closed only when project gates say so).
Do not mark Closed from review alone. Do not push, provision, or deploy.
Honor project Git rules if the user asked to record findings in-repo.
