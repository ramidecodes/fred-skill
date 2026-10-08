---
name: implement-fred
description: >-
  Implement a named FRED or select the next ready, unclaimed Open FRED from
  the requested or active roadmap track in the current repository. Use for
  coding from an agreed FRED, resuming its implementation, or choosing the next
  implementation slice. Records verification and implementation handoff.
---

# Implement FRED

Implement an agreed slice and leave evidence another agent/operator can use.
The project contract supplies lifecycle rules, commands, permissions, and
integration baseline. This skill supplies work selection and execution.

## Read and select

Follow applicable AGENTS instructions and the project agent entrypoint,
normally `docs/agent-guides/00-AGENT-ENTRYPOINT.md`. Read ROADMAP (or the
project's legacy index), then select:

1. A user-named FRED, respecting prerequisites and existing ownership.
2. Otherwise, the requested track, or the roadmap-designated active/focus track.
3. Its highest-priority ready, unclaimed Open FRED in track execution order.
   If no track is designated, use roadmap priority across tracks.

IDs are identities, not execution order. Check readiness against actual code
or explicitly agreed contracts/allowed fakes; prerequisites need not be Closed.
If a requested/designated track has no eligible work, report its precise
blocker or completed state instead of silently switching tracks. Do not take
another agent's claim without resolving ownership. Claim selected work and
record the next action when the project coordinates concurrent execution.

Read the selected FRED, source contracts, linked relevant architecture, and
necessary guides. Compare resume notes with the actual checkout/local changes
and relevant environment state. Do not assume old checks or running services
remain current. A named Draft needs specification resolved before coding: use
available `create-fred` guidance when appropriate, or resolve it through the
project template. Do not guess consequential missing requirements. A named
Implemented/Closed slice needs an explicit corrective task or remaining gate,
not automatic reimplementation.

Use existing project layout/rules without automatic migration. Do not rely on
sibling skill paths surviving installation. If infrastructure is missing, use
an available `fred` bootstrap workflow when authorized; otherwise report the
missing contract and offer setup before treating a chat idea as an agreed FRED.

## Implement the selected scope

- Follow contracts, affected surfaces, and non-goals. Use established command
  boundaries and coordinate shared interfaces/migrations. Label fakes; they
  cannot establish live compatibility or an integrated outcome promised by scope.
- Resolve routine implementation choices from the project. Record consequential
  discoveries and justified specification changes; unresolved product decisions
  need clarification. Do not expand into adjacent features without user scope.
- Update tasks and criteria as work proceeds. Update affected durable architecture
  and reusable procedure guides with changed contracts/boundaries/procedures.
- Keep necessary behavioral verification with implementation, including relevant
  rules, permissions, persistence, and local integration. For UI changes, render
  and inspect the changed surface, layout, responsive behavior, and relevant
  interaction states. Run relevant existing inexpensive automation too.
- Keep external setup and combined deployed journeys in linked OPERATIONS
  items; refine their steps/owners/pass conditions as needed. Missing required
  slice behavior remains unfinished implementation rather than an operator task.

## Verify and sign off

Find the global check command and working directory in the project entrypoint
and actual tooling. If undocumented, identify and document the supported command;
if absent or unavailable, report the missing gate. Never invent a passing check.

Before handing implementation to review or marking Implemented or Closed,
**run and require success from the global lint/format check on the current work**.
It must cascade across applicable modules in a monorepo; module-only checks do
not replace it. Also require the slice's local behavioral checks. If checks
modify formatting, inspect the result and establish a pass on the resulting
tree. Rerun after subsequent changes to check inputs. Record command, directory/
scope, result, date, and revision or working-tree context in the FRED.

A failed, blocked, or missing check prevents sign-off. Fix causes within scope;
report unrelated failures with a next action instead of silently broadening
work or disabling the gate. Changes to acceptance, check scripts, assertions,
or CI coverage need a recorded rationale and review alongside implementation.
Do not weaken verification just to obtain a pass.

Mark Implemented only after scoped behavior, required local checks, the global
check, and affected documentation are complete in the project's integration
baseline. Update FRED/ROADMAP together with date, baseline, remaining delivery
links, next action, and ownership. Required review follows project policy; a
separate model/session needs applicable authorization. Findings distinguish
required corrections (reopen), delivery gaps, and optional improvements.

Successful coding normally ends at Implemented. Closed additionally needs
applicable review/setup/flow evidence in the declared target and a current
global-check pass covering the relevant baseline. Follow the project closure
policy when the task includes this work; do not deploy to satisfy a status
transition without authorization. Preview differs from production; tooling/
libraries use relevant integration evidence. Configuration blockers leave
correct code Implemented; code defects reopen their owning slice.

## Finish or pause

Report selected FRED/track, implemented behavior, check results, state, and next
action. If unfinished, retain Open and refresh concise resume notes with baseline,
completed/remaining work, passed/failed/not-run checks, blocker, and next step.
Update the roadmap claim to reflect whether work is still owned or available.
Work one selected slice unless the user requested a broader sequence; choose
another only within that scope. Follow project Git/deploy rules and existing
conversation authorization. Track scheduling never grants extra external access.
