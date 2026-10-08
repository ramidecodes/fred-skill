# Optional companion and project skills

Read when deciding whether to add skills to this package or a consuming project.
The package includes `fred`, `create-fred`, and `implement-fred`. Project rules
remain in the consuming entrypoint/documents, with further detail loaded on demand.

## Decide whether a skill adds value

Use a guide for facts, contracts, command recipes, and occasional procedures.
Use a script for repeated deterministic mechanics. Consider a skill when a
distinct multi-step task repeatedly needs the same judgment and handoff, and
can be described with clear triggers, inputs, outputs, and stopping conditions.
An invocable skill can load its procedure only when relevant, but overlapping
descriptions still create routing and maintenance costs. Start with the smallest
useful set and expand from observed repeated work.

The recurring creation and implementation tasks have distinct conversational
and execution workflows, so they are packaged separately. Further skills need
their own demonstrated use; do not add one per state, FRED, track, or submodule.
Names should identify a workflow; narrow descriptions should distinguish it
from the core skill. Companions remain optional and preserve lifecycle/check gates.

## Candidates and recommendation

| Packaged skill | Inputs → result |
| --- | --- |
| `fred` | Project/workflow request → bootstrap, migration, track/gate coordination |
| `create-fred` | Feature idea or Draft + project context → scoped Draft/Open specification, roadmap and operation links |
| `implement-fred` | Named FRED or next/track request + project contract → implemented slice with evidence, or precise blocker/resume notes |

The task skills are self-contained consumers of project documents, with no
assumed sibling installation. They do not select different models automatically.
Their descriptions route ordinary creation and coding away from the core;
the core still supports those tasks when explicitly invoked or installed alone.

Further candidates:

| Candidate | Inputs → result | Where it fits / when worthwhile |
| --- | --- | --- |
| `fred-review` | FRED + code/diff + relevant contracts/evidence → actionable review record | First portable candidate if independent reviews recur; use project review criteria and the existing FRED findings format. |
| `project-delivery-check` | Named OPERATIONS items + target/access + guides → executed results or precise blockers | Project-local when combined UX checks recur and tooling/access differ by project. |
| `project-ci-diagnose` | Revision/run or failure + CI guide → diagnosed cause and scoped remedy | Project-local when log analysis and remediation recur; a simple check command alone needs no skill. |
| `project-data-verify` | Expected behavior + target/tenant + DB guide → relevant data evidence | Project-local when data inspection needs repeatable judgment beyond an existing script. |

The further candidates are illustrative proposals, not packaged skills.
Bootstrap remains in `fred`. Avoid extracting review merely to force expensive
models or adding all further candidates as a suite.

Invoking a review skill selects instructions; it does not itself select a
stronger model or create an independent reviewer context. When independence
is required, use an authorized separate session/agent with the FRED, code,
contracts, and evidence, rather than relying on a role change in the same chat.

## Package versus consuming repository

Reusable, stack-neutral companions could live beside `skills/fred/` in this
distribution repository. Keep the core usable when only `fred` is installed;
do not reference an optional sibling as an assumed dependency. Share generic
rules through explicitly resolvable packaged resources rather than copying a
second lifecycle/check policy. Do not rely on sibling source paths surviving
installation of just one skill.

Environment-specific procedures belong in the consuming project's supported
skill directory, for example `.agents/skills/project-data-verify/SKILL.md` where
the host discovers it. Other hosts use their own supported locations. Reference
the actual project entrypoint, guides, and scripts using a documented repo-root
convention; do not hardcode a maintainer's machine paths or credentials.

Keep architecture in architecture docs, procedure details in guides/scripts,
and FRED/operation results in their existing files. Skills supply task execution
guidance rather than duplicating those sources. If a guide changes, update its
consumer only when invocation or expected input/output changes too.

## Invocation and permissions

List only available companions in the project entrypoint with trigger,
invocation policy, required input, and destination for results. A FRED or
operation can name a relevant skill without making it a mandatory dependency.
Load only the requested/relevant workflow; do not chain every companion at every
transition. Do not auto-invoke a manual-only companion through the core skill.
If unavailable, use project guides and permitted tools or record a real blocker.

Preserve existing invocation policy. When a user wants explicit-only invocation,
use the host's supported setting; this is not a portable Agent Skills field:

- Codex: in that companion's `agents/openai.yaml`, set
  `policy.allow_implicit_invocation: false`; explicit `$skill-name` remains
  available. Do not change unrelated interface/dependency metadata. For example:

  ```yaml
  policy:
    allow_implicit_invocation: false
  ```

- Claude Code: set `disable-model-invocation: true` in that companion's
  SKILL.md frontmatter; invoke it with `/skill-name`.

For other hosts, verify current support rather than assuming these settings
work universally. Keep ordinary FRED discovery enabled unless the user asks
otherwise. Invocation does not grant extra database access, deployment rights,
paid model calls, delegation, or permission to weaken verification gates.

Sources for progressive loading and host-specific controls:
[Agent Skills specification](https://agentskills.io/specification) and
[Codex skill metadata](https://learn.chatgpt.com/docs/build-skills#optional-metadata),
plus [Claude Code skill invocation](https://code.claude.com/docs/en/skills#control-who-invokes-a-skill).
