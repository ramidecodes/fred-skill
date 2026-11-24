# {{PRODUCT_NAME}} — agent entrypoint

**Repo:** {{REPO_OR_PACKAGE_SCOPE}}. **Foundation:** {{FOUNDATION_STATUS}}.

{{PRODUCT_SOURCE}} owns product intent; {{ARCHITECTURE_DOC}} owns intended
boundaries and durable contracts. Code establishes what runs. FREDs own slice
requirements and evidence. Resolve discrepancies explicitly.

**Runtime truth:** do not treat Draft/Open FREDs or intended architecture as
shipped behavior. Runtime facts come from code and from FRED/OPERATIONS headers
marked **Implemented** or **Closed**.

## Project workflow

- **Git policy (default):** agents may commit their own changes after required
  checks succeed when the conversation or project allows commits. **Do not
  push, provision, or deploy** without user authorization. PR / branch policy:
  {{GIT_PR_POLICY_OR_DEFAULT_CONVENTIONAL_COMMITS}}.
- **Conventional Commits (required when committing):**
  `type(scope): imperative summary` (lowercase type; subject describes *what
  changed*). **Scope** is a product or area name (`repo`, `ci`, `db`, `docs`,
  …) — **not** a FRED id. Put FRED linkage in the **body**, e.g. `Refs: NNN`
  and/or `Implements FRED NNN (title).` Prefer grouped semantic commits over
  one commit per FRED when the tree changes together. Do not use
  `feat(001):` / `chore(002):` style scopes.
- Deploy / provisioning policy: {{DEPLOY_AND_PROVISIONING_POLICY}}.
- Integration baseline for Implemented: {{INTEGRATION_BASELINE_POLICY}}.
- Independent review requirements: {{REVIEW_POLICY_OR_RISK_BASED}}.
- Application / command boundaries: {{COMMAND_LAYER_OR_APP_BOUNDARY}}.

Follow applicable AGENTS instructions and existing user authorization. Record
blocked actions honestly; scheduling a task does not authorize external actions.
Check third-party APIs against installed versions and their official docs.
Label fixtures and proposals. Keep secret values out of docs and evidence.

### Subagents

When spawning subagents, give **scoped clear tasks** (bounded paths, contracts,
or FRED sections). Prefer lighter/faster models for bounded parallel work
(research, exploration, independent drafts); keep the coordinating session on
the stronger model when that is how the user invoked the work. Track
scheduling and claim boards do **not** themselves authorize delegation, Git
push, or deployment.

## Where to go

| When needed | Document / relevant section | What it owns |
| --- | --- | --- |
| Choose work, inspect tracks or claims | [ROADMAP](../features/ROADMAP.md) | Scheduling, tracklines, prerequisites, next actions |
| **Status / “what’s left” for a human** | Prefer `fred-status` when installed; else [Status reports](#status-reports-roadmap--implementation) · [ROADMAP](../features/ROADMAP.md) | Plain-language posture + per-item name/id/state/done/left/unblocks — never bare FRED/OP codes |
| Execute setup or shared delivery flows | [OPERATIONS](../features/OPERATIONS.md) | Task steps, pass conditions, results |
| Specify a slice | [FRED template](../features/template.md) | Slice requirements and evidence shape |
| Understand/change system boundaries | {{ARCHITECTURE_DOC}} | Durable system boundaries and decisions |
| Change domain data or shared interfaces | {{SCHEMA_OR_CONTRACT_DOC_OR_N_A}} | State ownership and canonical contracts |
| Implement UI layout and states | {{DESIGN_DOC_OR_N_A}} | Design requirements |
| Diagnose CI or verify required workflows | {{CI_GUIDE_OR_EXISTING_CONTRIBUTING_DOC}} | Workflows, commands, run/log inspection |
| Connect to a database and verify data | {{DATABASE_VERIFICATION_GUIDE_OR_N_A}} | Environment selection and data inspection |
| Start/access preview and identify deployment | {{PREVIEW_GUIDE_OR_N_A}} | Startup, access, smoke checks, deployment context |

Load the relevant guide when its task arises. Guides own repeatable procedures;
OPERATIONS owns outstanding tasks and results. Reuse existing docs and scripts.
Use section links where useful. Routing summaries help select sources; read
the source before relying on its contract. Avoid a separate index until scale
or repeated discovery failures justify one.

When recurring procedures warrant optional project skills, list only available
skills here with their trigger, invocation policy, and inputs/results. They
reuse these guides and write evidence into existing documents. Ordinary FRED
stages need no separate skills; manual invocation does not expand authorization.

## Status reports (roadmap / implementation)

When the user asks for roadmap status, what’s left, dogfood readiness, or “how
much of X is done,” answer for a **product owner**. Prefer the `fred-status`
skill when installed; otherwise follow this contract.

Lead with 1–3 sentences of product posture, then itemize. For each item:
**Name** (title + id), **State**, **What it is**, **Done**, **Left**,
**Unblocks**. Group Closed/Implemented · Open ready · Blocked on ops ·
Deferred. Ban bare ID lists. When the project uses “dogfood,” mean *using the
product yourself* to find gaps — not a separate feature. Link ROADMAP and named
FREDs/OPs for depth; do not invent Closed/Passed.

## Work and lifecycle

Select the requested FRED, or the highest-priority ready, unclaimed Open slice
in the requested or roadmap-designated active trackline; use cross-track
priority only when neither is designated. Report a selected trackline's lack of
eligible work rather than silently switching. Respect implementation
prerequisites; an explicitly agreed contract and allowed fake may enable
parallel work. Record the real integration owner. Delivery gates normally block
Closed, not coding; setup needed for implementation is also an implementation
prerequisite.

Keep FRED paths stable. Draft → Open resolves implementation decisions.
Open → Implemented requires scoped behavior, required local checks, the global
check below, updated affected documentation, and linked pending delivery gates.
Implemented → Closed requires the global check and applicable review/setup/flow
evidence in the declared target. Preview is distinct from production; tooling
and libraries use relevant integration evidence. Update FRED and ROADMAP
summaries together. Code defects reopen work; configuration blockers leave
correct implementations Implemented with a linked next action.

When unfinished work stops, leave concise resume notes in the FRED and update
ROADMAP's owner/claim and next action. On resume, compare the recorded baseline
with the checkout and local changes; confirm relevant environment state.

## Global check — required before implementation handoff/sign-off

**Working directory:** `{{GLOBAL_CHECK_WORKING_DIRECTORY}}`.
**Command:**

```bash
{{GLOBAL_CHECK_COMMAND}}
```

This is the project-wide lint/format check. In a monorepo it cascades through
all applicable modules. Run it before handing implementation to review and
before marking a FRED Implemented or Closed. A module-only check is insufficient.
Require success on the current work, rerun after subsequent changes to check
inputs, and record command, directory/scope, result, date, and revision or
working-tree context in the FRED. A missing, blocked, or failing command blocks
sign-off; report the cause and next action instead of marking it passed.
Planning-only Draft → Open does not require executing code checks.

Record and justify changes to acceptance, check scripts, or CI/global-check
scope. Review those changes with the implementation; do not disable or weaken
verification just to obtain a passing sign-off.

Also run the FRED's proportionate behavioral checks; lint/format is not proof
of correct behavior. After the global check, run additional QA (including
browser or render inspection when relevant) only when the FRED's verification
criteria or QA section calls for it. Prefer available browser tooling for
UI/browser-shaped checks; if tooling, auth, or environment is missing, report
not-run honestly. Keep necessary local rule, authorization, persistence, and
integration verification with the implementation when the FRED requires them.
Shared deployed journeys and external setup go in OPERATIONS.

Other relevant commands/procedures: {{BUILD_TEST_AND_LOCAL_RUN_REFERENCES}}.
Actual tree/stack pointers: {{PROJECT_LAYOUT_AND_STACK_REFERENCES}}.

Update existing architecture docs for changed durable contracts and boundaries,
and guides for changed procedures, before Implemented sign-off. Do not duplicate
architecture or connection recipes in each FRED.
