# {{PRODUCT_NAME}} — agent entrypoint

**Repo:** {{REPO_OR_PACKAGE_SCOPE}}. **Foundation:** {{FOUNDATION_STATUS}}.

{{PRODUCT_SOURCE}} owns product intent; {{ARCHITECTURE_DOC}} owns intended
boundaries and durable contracts. Code establishes what runs. FREDs own slice
requirements and evidence. Resolve discrepancies explicitly.

## Project workflow

- Git / PR policy: {{GIT_AND_PR_POLICY}}.
- Deploy / provisioning policy: {{DEPLOY_AND_PROVISIONING_POLICY}}.
- Integration baseline for Implemented: {{INTEGRATION_BASELINE_POLICY}}.
- Independent review requirements: {{REVIEW_POLICY_OR_RISK_BASED}}.
- Application / command boundaries: {{COMMAND_LAYER_OR_APP_BOUNDARY}}.

Follow applicable AGENTS instructions and existing user authorization. Record
blocked actions honestly; scheduling a task does not authorize external actions.
Check third-party APIs against installed versions and their official docs.
Label fixtures and proposals. Keep secret values out of docs and evidence.

## Where to go

| When needed | Document / relevant section | What it owns |
| --- | --- | --- |
| Choose work, inspect tracks or claims | [ROADMAP](../features/ROADMAP.md) | Scheduling, prerequisites, next actions |
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

## Work and lifecycle

Select the requested FRED, or the highest-priority ready, unclaimed Open slice
in the requested track. Respect implementation prerequisites; an explicitly
agreed contract and allowed fake may enable parallel work. Record the real
integration owner. Delivery gates normally block Closed, not coding; setup
needed for implementation is also an implementation prerequisite.

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
of correct behavior. UI changes require rendering and inspecting the changed
surface, layout, responsive behavior, and relevant states. Keep local rule,
authorization, persistence, and necessary integration verification with the
implementation. Shared deployed journeys and external setup go in OPERATIONS.

Other relevant commands/procedures: {{BUILD_TEST_AND_LOCAL_RUN_REFERENCES}}.
Actual tree/stack pointers: {{PROJECT_LAYOUT_AND_STACK_REFERENCES}}.

Update existing architecture docs for changed durable contracts and boundaries,
and guides for changed procedures, before Implemented sign-off. Do not duplicate
architecture or connection recipes in each FRED.
