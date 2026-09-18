# Bootstrap FRED docs

Use only when the consuming repo **lacks** FRED files (no entrypoint and no `docs/features/`). Never overwrite existing FRED docs with skill defaults.

Ask before writing if the repo already has a different spec system.

## Generate (do not copy another product)

Copy from this skill’s `templates/`, then fill `{{PLACEHOLDERS}}` from **this** repository (name, verify commands, real tree).

| Template | Destination |
| --- | --- |
| `templates/AGENT-ENTRYPOINT.md` | `docs/agent-guides/00-AGENT-ENTRYPOINT.md` |
| `templates/feature.md` | `docs/features/template.md` |
| `templates/OPEN-FRED-INDEX.md` | `docs/features/OPEN-FRED-INDEX.md` |
| `templates/implemented-README.md` | `docs/features/implemented/README.md` |

Optional: root `AGENTS.md` containing only a pointer:

```markdown
# Agents

At session start, read [docs/agent-guides/00-AGENT-ENTRYPOINT.md](docs/agent-guides/00-AGENT-ENTRYPOINT.md).
```

If `AGENTS.md` already exists, add that one line; do not replace the file.

## Adapt the tree

The entrypoint template’s layout table is **example-shaped** (`apps/`, `packages/`, `docs/features/`, …). Rewrite it to match disk. Delete rows that do not exist. Do not invent packages.

## First FRED

If the user wants an initial slice, allocate `001`, add an open-index row, and write `docs/features/001-{{slug}}.md` from `template.md`. Keep it a slice, not the whole product.

## After bootstrap

All further edits happen on the **project** copies. The skill stays generic.
