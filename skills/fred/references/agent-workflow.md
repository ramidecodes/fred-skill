# Agent workflow

## Choose and prepare

Read the project contract, ROADMAP, and the named or highest-priority ready,
unclaimed Open FRED in the requested or roadmap-designated active track. Use
cross-track priority only when neither is designated. If that track has no
eligible work, report its blocker rather than silently switching. Check implementation prerequisites,
including explicitly agreed interfaces/fakes. Deepen Draft scope before coding.
Claim work and record next action when coordinating concurrent implementation.
Read only relevant architecture and procedure guides; discover missing pointers.

Use entrypoint descriptions and section links to find the needed source, then
read it. On resumed work, inspect the actual checkout and local changes against
the FRED's baseline/resume notes. Confirm relevant environment state when
uncertain; old notes do not prove a server, database, or deployment is current.
Use maintained setup and smoke commands when this is needed for the task, not
as an automatic startup requirement for planning sessions.

Confirm the global check command and its working directory from the entrypoint
and actual project tooling. It should invoke the project's aggregate lint and
format checks, cascading through modules in a monorepo. Do not substitute a
module check or invent a command from the skill template. If undocumented,
inspect project scripts and document the supported command; if none exists,
report the missing gate and resolve it before sign-off.

## Implement and verify

Stay within scope and project boundaries. Update tasks and criteria as work
progresses. Use proportionate tests for rules, permissions, persistence, and
contracts. For UI changes, render and inspect the changed layout and states;
record inaccessible checks honestly. Execute existing relevant automation.
Update affected architecture and reusable procedure docs. Create/refine linked
OPERATIONS items for external setup and combined deployed flows.

Before review handoff or Implemented sign-off:

1. Complete scoped behavior and required local checks.
2. Run the global check command at its documented scope on the final work.
3. Resolve failures within scope. If a failure is unrelated or a check is blocked,
   report it and its next action; do not silently broaden work or sign off.
4. Record command, directory/scope, date, result, and revision/working-tree
   context. If checks fix formatting, inspect the changes and rerun as needed
   to establish a pass on the resulting tree. Rerun after later changes.
5. Set Implemented, implementation date, and integration baseline only when
   the gates pass. Update ROADMAP and its pending next action.

Global checks are necessary but do not replace behavior checks, independent
review, or deployed evidence. Routine documentation edits recording results
need not cause an endless check loop; rerun if they affect check inputs.

## Pause and resume

When unfinished work stops or changes hands, refresh a short Resume notes
section in its FRED: date and baseline, completed and remaining work, check
results including not-run checks, blocker, and the next concrete action. Point
to existing evidence rather than duplicating logs. Keep the lifecycle state
honest; pausing does not earn Implemented. Update ROADMAP's next action and
claim/owner to show whether work remains claimed or is available for pickup.
Resolve an ambiguous existing claim before taking concurrent ownership.

Omit resume notes for a short slice finished in one session. Remove resolved
temporary notes or fold durable facts into the appropriate sections. Keep
secrets out of notes, and verify their baseline before resuming.

## Independent review when applicable

Use project/user review requirements; otherwise select based on consequence
and uncertainty. A separate reviewer or stronger available model can inspect
the FRED, actual diff/code, relevant architecture, and local evidence. Do not
launch delegation or change model/cost settings without applicable authorization.

Inspect changes to criteria, test assertions/fixtures, verification scripts,
and CI/global-check coverage alongside feature code. Require a recorded reason
for contract/gate changes. A legitimate correction can change verification;
disabling or weakening it merely to make failing behavior pass is a defect.
Review findings should cite actual code and evidence, not just repeat the
implementation agent's completion summary.

Append a concise review record to the FRED:

- Required corrections: specific unmet criteria/defects, code locations,
  expected behavior, and a way to verify the correction. Return to Open.
- Delivery gaps: linked configuration or shared-flow items. Remain Implemented.
- Optional improvements: proposals, not new acceptance gates.

The reviewer may record findings, not silently soften requirements. Document
and justify scope changes under the project's decision process. Default to a
focused review, correction pass, and recheck of cited findings. Further passes
need a concrete unresolved issue; persistent scope disagreements need a user
decision. Run the global check again after corrections before the next handoff.
Review without runtime access must label the limits of its evidence.

## Execute delivery and close

Follow the linked OPERATIONS steps and relevant environment guides. Record
target/deployment or revision, date, executor, result, and evidence. Failed
code behavior reopens its owning FRED; setup/access blockers stay in OPERATIONS
and leave correct implementation Implemented. Changed work needs affected
flows revalidated. Required independent review must be resolved before closure.

Before Closed sign-off, rerun the global check command on the relevant current
integration baseline and require success. Confirm local evidence and applicable
delivery gates still cover that revision. If the operator cannot run the global
check, retain Implemented until an equipped agent completes that gate. Record
closure evidence and update the FRED/ROADMAP together, retaining stable paths.
Preview closure records preview explicitly; production validation is a separate
operation when required. Tooling/libraries use relevant integration evidence.
