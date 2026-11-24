# Hosts, subagents, and models

Vendor product names and model labels change. Treat examples below as patterns,
not a pinned matrix. Skill selection does **not** itself change model or
authorize paid calls.

## Model roles

| Role | Prefer | Typical work |
| --- | --- | --- |
| Coordinator (session that invoked the skill) | Stronger / default session model | Routing, ID allocation, integrating results, Draft → Open, sign-off judgment |
| Scoped subagent | Lighter / faster available model | Bounded explore, research distinct contracts, implement independent chunks, section drafts |

Most harnesses can spawn subagents with a smaller or faster model. Examples
(illustrative only): Cursor Composer 2.5 and fast variants; Codex smaller
models for bounded tasks; Claude Sonnet-class models for scoped work while a
stronger model stays on the coordinator. Confirm current names and billing in
the host’s docs before assuming a label still exists.

## Subagent practice

- Give each subagent a **scoped clear task** (bounded paths, contracts, or FRED
  sections). State inputs, expected output shape, and stop conditions.
- Prefer lighter models for parallel explore/implement chunks; keep the
  coordinator on the stronger session when that is how the user invoked work.
- Integrate results in the coordinating session. Serialize shared interfaces,
  migrations, ID allocation, and conflicting shared-surface edits.
- Claim boards and trackline scheduling do **not** authorize delegation, push,
  or deployment by themselves.

## Host invocation notes

Do not hardcode maintainer machine paths. Install via the skills CLI (see the
package README); discover skills by name.

| Host | Bootstrap | Status | Review |
| --- | --- | --- | --- |
| Cursor | Invoke `fred` for `/init` / bootstrap (or ask to bootstrap FRED docs) | Invoke `fred-status` for `/status` / what’s left | Invoke `fred-review` at handoff or when asked to review a FRED/diff |
| Codex | `$fred` / bootstrap prompts; respect `agents/openai.yaml` invocation policy when set | `$fred-status` or `/status`-shaped asks | `$fred-review` when packaged; may set `policy.allow_implicit_invocation: false` for manual-only |
| Claude Code | `/fred` or natural-language bootstrap; optional `disable-model-invocation` frontmatter | `/fred-status` or status asks | `/fred-review` when packaged; optional manual-only frontmatter |

Exact slash-command and `$skill` syntax depend on the host version. Prefer the
skill **name** and the project entrypoint over absolute install paths.

See also [agent-workflow.md](./agent-workflow.md) (coordinator subagents) and
[project-skills.md](./project-skills.md) (companion packaging and invocation).
