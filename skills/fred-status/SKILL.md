---
name: fred-status
description: >-
  Report FRED roadmap and implementation posture for a human product owner.
  Use for /status, roadmap status, what's left, dogfood readiness, how much of
  a track or feature is done, or implementation posture questions. Reads the
  project entrypoint and ROADMAP; does not change lifecycle or invent Closed.
---

# FRED status

Answer roadmap / implementation questions for a **product owner**, not as an
agent checklist dump. The project `docs/features/ROADMAP.md` is the ID index;
each FRED/OP owns the detail. Never assume the reader remembers what bare
codes mean.

## Read first

1. Follow applicable `AGENTS.md` and the project agent entrypoint, normally
   `docs/agent-guides/00-AGENT-ENTRYPOINT.md`.
2. Read `docs/features/ROADMAP.md` (active tracklines / claim boards, next
   actions). Open named FREDs and OPERATIONS items only as needed for the ask.
3. Prefer FRED/OPERATIONS headers marked **Implemented** or **Closed**, plus
   code, as runtime facts. Do **not** invent Closed/Passed or treat Draft/Open
   as shipped.

Project documents govern; this skill supplies the report shape. Prefer this
skill when installed; the entrypoint may also seed the same contract.

## Report shape

**Lead with posture (1–3 sentences):** what the product can do today vs what
still blocks feeling “done” for the asked track (e.g. dogfood, a named
surface). Then itemize.

**For each item, include:**

| Field | Content |
| --- | --- |
| **Name** | Human title first, then FRED/OP id in parentheses |
| **State** | Closed / Implemented / Open / Draft / Partial / Blocked — as in the FRED or OPERATIONS header |
| **What it is** | One plain-language sentence |
| **Done** | What already works in the app or in the declared target |
| **Left** | What remains before Implemented/Closed or before the asked goal feels complete |
| **Unblocks** | Who or what (Operator OP, dependency FRED, product decision) |

Prefer a short table or bullets. **Avoid bare ID lists.** Group when helpful:

- **Closed / Implemented recently** — shipped or code-complete; note remaining ops gates if any
- **Open ready for agents** — claimable code work
- **Blocked on Operator / ops** — live send, deploy, browser QA the agent cannot invent Passed for
- **Deferred / parked** — explicitly out of the current batch

**Dogfood:** when the project uses that word, it means *using the product
yourself* to find gaps before pilot — not a separate feature. Say that in one
clause and name the human surfaces that matter for the ask.

**Optional extras (include when useful, skip when noise):** rough % or
qualitative depth by trackline; a concrete “try this in the app” path; top risk
or false-green caution (fixtures ≠ live; Partial ≠ Passed); next decision the
user must make.

Keep the reply concise enough to scan; link ROADMAP and the named FREDs/OPs for
depth rather than pasting full acceptance tables.

## Stop conditions

Reporting only. Do **not** flip lifecycle states, rewrite claim boards, or
commit unless the user also asked for those document updates. Do not push,
provision, or deploy. Track scheduling and status questions do not authorize
external actions.
