# Bootstrap and migration

## Bootstrap (`/init`)

Use when the user requests FRED setup, `/init`, “bootstrap FRED”, “set up FRED
docs”, or accepts an offer to bootstrap. Follow **scan → propose → write**.
Reuse project knowledge; do not overwrite an existing contract or introduce a
competing system without a user request. Never copy another product's slices.
Do not invent product feature maps or stacks; do not auto-generate companion
skill suites.

### 1. Scan

Inspect the consuming repository before writing:

- Package manager and monorepo layout (workspace roots, apps vs services).
- Root scripts: lint, format, check, test, build — derive a real
  `{{GLOBAL_CHECK_COMMAND}}` and working directory.
- CI workflows (GitHub Actions or equivalent) and CONTRIBUTING/README pointers.
- Existing `AGENTS.md`, agent guides, architecture docs, design docs.
- Any legacy feature index, open-FRED folders, or operations checklists.

### 2. Propose (derive placeholders)

From the scan, fill template placeholders honestly:

- Global check command + working directory from real scripts; mark unknown if
  none exists and report that the gate must be resolved before sign-off.
- Deploy / provisioning and integration-baseline placeholders from what exists,
  or mark unknown.
- Initial **tracklines** from ownership boundaries when obvious (e.g. apps vs
  services); otherwise leave trackline seeds as placeholders.
- Entrypoint defaults from upgraded templates: **commit ≠ push** (agents may
  commit when authorized; never push/provision/deploy without user auth),
  Conventional Commits with FRED id in the **body** (`Refs: NNN`), status
  reports section (prefer `fred-status` when installed), subagent scoping note,
  runtime-truth (Draft/Open ≠ shipped).
- Optional thin root `AGENTS.md` pointer to the entrypoint (append; do not
  replace existing AGENTS content).
- Optional `docs/decisions/` using `templates/decision.md` when the project
  wants recorded decisions — do not invent product decision IDs.

Show the derived plan briefly when useful; then write only what is missing.

### 3. Write

| Template | Project destination |
| --- | --- |
| `templates/AGENT-ENTRYPOINT.md` | `docs/agent-guides/00-AGENT-ENTRYPOINT.md` |
| `templates/feature.md` | `docs/features/template.md` |
| `templates/ROADMAP.md` | `docs/features/ROADMAP.md` |
| `templates/OPERATIONS.md` | `docs/features/OPERATIONS.md` |
| `templates/decision.md` (optional) | `docs/decisions/` when the project wants recorded decisions — copy as needed; do not invent product decision IDs |

Optional root AGENTS pointer:

```markdown
Agent contract: read docs/agent-guides/00-AGENT-ENTRYPOINT.md at session start.
```

Append to existing AGENTS instructions; do not replace them. Rewrite entrypoint
pointers for the actual tree. Create architecture/CI/database/preview guides
only for missing knowledge that materially helps work; otherwise link existing
docs and maintained scripts. Do not invent stacks or unavailable surfaces.

Route guides by task, section, and responsibility in the entrypoint. Summaries
help discovery but never replace the linked source. Document maintained startup,
test-data setup, and smoke commands where repeated work needs them; do not
invent an environment launcher or run it during planning-only sessions.
Do not generate companion skills by default. When the user wants recurring
procedures packaged as skills, use the optional companion guidance linked from
SKILL.md, preserving existing guides as authority and host invocation policies.
If `create-fred`, `implement-fred`, `fred-status`, and `fred-review` are
available, list their roles in the project entrypoint without assuming they
are installed. Bootstrap does not copy their definitions into the consuming
project. Do not add `fred-init` / `fred-close` skills or auto-generate product
FREDs from a codebase scan.

The first requested slice uses the next unused ID (001 in a new project), has
a ROADMAP row (and claim-board seed when tracklines apply), and stays Draft
until implementation decisions are sufficiently resolved. Create its delivery
items in OPERATIONS while specifying it. Stable paths cover all four states; no
state-folder READMEs or extra counts are needed. All subsequent project work
edits project copies, not these templates.

### Stop

Report what was **created** vs **linked**. Do not invent product slices. Do not
commit or push unless the user also asked. Offer migration when legacy FRED-ish
docs already exist (see below).

## Explicit migration of existing projects

Existing project contracts remain in force until migration is requested.
Migration is the same skill’s second mode: inventory → consolidate → classify.

1. Inventory existing FRED IDs, status conventions, evidence, architecture,
   index/roadmap, and operator checklists. Preserve scope and history.
2. Consolidate scheduling into ROADMAP, grouped by tracks / tracklines. Split
   implementation prerequisites from delivery gates; retain links to source
   material. Preserve historical inventory boards when useful; designate one
   **active** claim board for new claims.
3. Consolidate outstanding setup and shared-flow work into OPERATIONS with
   stable task IDs, owners, pass conditions, and FRED links.
4. Classify FREDs from actual evidence: unfinished scope stays Open; completed
   local implementation with pending delivery stays Implemented; Closed needs
   the declared target evidence and check gate. Preserve legacy closure history
   but mark missing evidence unknown/pending rather than inventing a new pass.
5. Prefer stable paths. If moving legacy state-folder files, repair incoming
   and relative links and keep only one authoritative copy. Projects choosing
   state folders should keep equal depth and avoid per-folder status tables.
6. Update the entrypoint and references to the new workflow and global check
   (including commit≠push, status reporting, trackline seeds). Retire the old
   index/status tables once their information is preserved; remove or replace
   external navigation pointers as needed.

Do not mass-close legacy Implemented files, erase genuine deployed evidence,
or execute deployments just to migrate documentation.
