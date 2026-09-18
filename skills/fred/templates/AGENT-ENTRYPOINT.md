# {{PRODUCT_NAME}} — agent entrypoint

**Product:** {{PRODUCT_NAME}} ({{PRODUCT_URL_OR_N_A}}).  
**Repo:** {{REPO_OR_PACKAGE_SCOPE}}.

Foundation status: {{FOUNDATION_STATUS}}. Do not invent shipped features.

**Authority:** {{PRODUCT_SOURCE}} owns product intent. {{ARCHITECTURE_DOC}} owns local stack/layout. **Code** owns what runs. **FREDs** own how to implement a slice. {{REQUIREMENTS_DOC_OR_N_A}} records source reconciliation if used.

## Do not

- Commit, push, stage, or open PRs unless this conversation explicitly asks. *(Delete or rewrite this bullet if the project wants different git norms — this file wins over the FRED skill default.)*
- Deploy, provision cloud, or publish unless explicitly asked.
- Start a later FRED before its listed dependencies exist in code (or the task names an allowed fake).
- Bypass {{COMMAND_LAYER_OR_APP_BOUNDARY}} from agents, workflows, or UI.
- Treat documentation browsing as a live provider probe.
- Trust model training memory for third-party package APIs — versions and docs change.

**Human operator tasks:** secrets, DNS, billing, dashboard webhooks, and similar stay on a human checklist ({{OPERATOR_CHECKLIST_LINK_OR_N_A}}). Do not claim those are done from the agent session.

## Package APIs and docs

Prefer current package docs, repo skills, and official references over remembered SDK shapes. When writing integration code, verify against the **installed** version (lockfile / package manifest) and that version’s docs.

## Where things live

| Need | Go here |
| --- | --- |
| Next FRED to build | [OPEN-FRED-INDEX](../features/OPEN-FRED-INDEX.md) execution table — **not** filename order |
| Why that order | {{ROADMAP_DOC_OR_INDEX}} |
| System picture | {{ARCHITECTURE_DOC}} |
| Domain / data model | {{SCHEMA_DOC_OR_N_A}} |
| Workflows / transitions | {{WORKFLOW_DOC_OR_N_A}} |
| New FRED shape | [template](../features/template.md) |
| UI brand / style | {{DESIGN_DOC_OR_N_A}} |
| Shipped FREDs | [implemented/](../features/implemented/) |
| Operator / env setup | {{OPERATOR_GUIDES_OR_N_A}} |

Next unused FRED number: **{{NEXT_FRED_NUMBER}}**. Open: {{OPEN_COUNT}}. Implemented: {{IMPLEMENTED_COUNT_AND_IDS}}.

## Pick the next FRED

1. Open the index. Work the first open row whose dependencies are implemented (or the operator named a specific FRED).
2. {{START_SEQUENCE_NOTES}}
3. Drafts: fill feature-owned contracts (schema, events, guards, timeouts, recovery) against shipped dependencies before coding.
4. When a FRED ships, move it to `implemented/` and repair links. Do not duplicate FRED checklists in this file.

## Tree

High-level layout only (generated/vendor dirs omitted). Architecture docs own intended system law; this map is **what exists on disk**. Adapt folders to this repo; delete rows that are not present.

```text
.
├── apps/                    # deployable application roots (adapt names)
│   ├── app/                 # example: primary product
│   └── {{OTHER_APP_OR_OMIT}}
├── services/                # example: workers, agents, orchestration (or omit)
├── packages/                # example: shared libraries (or omit)
├── docs/
│   ├── agent-guides/        # this entrypoint + operator guides
│   ├── architecture/        # stack, schema, workflow law
│   ├── deploy/              # optional deploy map
│   └── features/            # open FREDs; implemented/ when shipped
├── .agents/skills/          # optional repo agent skills
├── .cursor/rules/           # optional always-on editor rules
├── .github/workflows/       # optional CI
├── scripts/                 # optional repo scripts
├── {{LOCKFILE_OR_WORKSPACE_MANIFEST}}
└── {{ENV_EXAMPLE}}          # env **names** only; never commit secrets
```

**What goes where** *(rewrite to match this repo)*

- `apps/` — deployable UI/API roots. Tests for an app typically live with that app.
- `services/` — long-running or worker roots if the repo has them.
- `packages/` — shared libraries. Prefer no connect-on-import in libraries.
- `docs/` — agent orientation, architecture, FRED specs. Next work: `docs/features/OPEN-FRED-INDEX.md`, not filename order.
- `.agents/skills/` — skills used while implementing. `.cursor/rules/` — always-on agent rules.
- CI and root tooling — as this repo actually uses.
- Copy env **names** from `{{ENV_EXAMPLE}}`; do not document secret values.

Stack: {{STACK_SUMMARY}}. Hierarchy / domain model: {{DOMAIN_HIERARCHY_OR_N_A}}.

## Verify

Replace with this repo’s real commands:

```bash
{{INSTALL_COMMAND}}
{{FORMAT_COMMAND}}
{{CHECK_COMMAND}}
{{BUILD_COMMAND}}
{{SMOKE_OR_TEST_COMMAND}}
```

After implementing a slice, run `{{CHECK_COMMAND}}` (or the project equivalent) before considering the work done.

Record blocked live probes honestly. Libraries should not connect on import unless this repo documents otherwise. Deploy map: {{DEPLOY_DOC_OR_N_A}}.
