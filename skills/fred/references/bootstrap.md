# Bootstrap and migration

## Bootstrap

Use when the user requests FRED setup or accepts an offer to bootstrap. Inspect
existing docs, scripts, and CI first. Reuse project knowledge; do not overwrite
an existing contract or introduce a competing system without a user request.
Fill template placeholders from this repository, including the real global
check command and its working directory. Never copy another product's slices.

| Template | Project destination |
| --- | --- |
| `templates/AGENT-ENTRYPOINT.md` | `docs/agent-guides/00-AGENT-ENTRYPOINT.md` |
| `templates/feature.md` | `docs/features/template.md` |
| `templates/ROADMAP.md` | `docs/features/ROADMAP.md` |
| `templates/OPERATIONS.md` | `docs/features/OPERATIONS.md` |

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
If `create-fred` and `implement-fred` are available, list their creation and
execution roles in the project entrypoint without assuming they are installed.
Bootstrap does not copy their definitions into the consuming project.

The first requested slice uses the next unused ID (001 in a new project), has
a ROADMAP row, and stays Draft until implementation decisions are sufficiently
resolved. Create its delivery items in OPERATIONS while specifying it. Stable
paths cover all four states; no state-folder READMEs or extra counts are needed.
All subsequent project work edits project copies, not these templates.

## Explicit migration of existing projects

Existing project contracts remain in force until migration is requested.

1. Inventory existing FRED IDs, status conventions, evidence, architecture,
   index/roadmap, and operator checklists. Preserve scope and history.
2. Consolidate scheduling into ROADMAP, grouped by tracks. Split implementation
   prerequisites from delivery gates; retain links to source material.
3. Consolidate outstanding setup and shared-flow work into OPERATIONS with
   stable task IDs, owners, pass conditions, and FRED links.
4. Classify FREDs from actual evidence: unfinished scope stays Open; completed
   local implementation with pending delivery stays Implemented; Closed needs
   the declared target evidence and check gate. Preserve legacy closure history
   but mark missing evidence unknown/pending rather than inventing a new pass.
5. Prefer stable paths. If moving legacy state-folder files, repair incoming
   and relative links and keep only one authoritative copy. Projects choosing
   state folders should keep equal depth and avoid per-folder status tables.
6. Update the entrypoint and references to the new workflow and global check.
   Retire the old index/status tables once their information is preserved;
   remove or replace external navigation pointers as needed.

Do not mass-close legacy Implemented files, erase genuine deployed evidence,
or execute deployments just to migrate documentation.
