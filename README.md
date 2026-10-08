# FRED = **Feature Requirement Documents**

Works with Cursor, Claude Code, and Codex via the [skills CLI](https://github.com/vercel-labs/skills).

You describe what you want in plain language. An agent turns that into a scoped FRED and implements from that file. A roadmap groups implementation into tracks; operations checklists capture setup and shared UX verification. Independent review can use a separate, more capable model when useful. All of it lives in the repo, next to the code.

Linear, Notion, and Jira can still exist. For this slice of planning they are optional sources you cite as “derived from.” The documents the agent maintains and implements from are in git.

This package is methodology plus generators. It does not encode a product, cloud vendor, or app stack. The consuming project’s own agent entrypoint is the contract.

## At a glance

FRED is a repo-native workflow: one implementation slice per file, stable IDs
and paths, parallel tracks, and explicit verification evidence. Its lifecycle is
Draft → Open → Implemented → Closed. Implementation can finish while external
setup or a combined deployed journey remains pending.

## The workflow

1. **Specify.** Define scoped behavior, contracts, non-goals, and proportionate
   implementation criteria. Create applicable delivery tasks at this stage.
2. **Schedule.** Group ordered slices by outcome and ownership in ROADMAP.
   Agreed contracts and named fakes can enable parallel work; record integration
   ownership. Implementation prerequisites govern readiness, not numeric IDs.
3. **Implement and check.** Complete the behavior, local verification, and
   affected documentation. Run the project's global lint/format check from its
   documented working directory, including cascading monorepo module checks.
   A module-only pass is insufficient. Record the actual results before review
   handoff or marking Implemented.
4. **Review when appropriate.** A separate reviewer checks the contract, code,
   and evidence. Required corrections reopen work; optional suggestions do not
   expand acceptance. The project can require review for consequential changes.
5. **Verify delivery and close.** An operator or equipped agent executes linked
   setup/flow tasks. Record target, revision/deployment, and evidence, and run
   the global check again before Closed sign-off. Preview is distinct from
   production; libraries/tooling use relevant integration evidence.

Missing, blocked, or failing global checks block sign-off. Rerun after changes
to check inputs. Behavioral checks still matter: UI implementation requires
rendering and inspection, and backend slices require appropriate rule,
authorization, persistence, and integration checks. Shared deployed journeys
and third-party setup live separately so correct implementation can progress.
Planning-only Draft → Open does not require executing code checks.

## How it works in a project

```text
docs/
├── agent-guides/00-AGENT-ENTRYPOINT.md   # workflow, commands, guide pointers
└── features/
    ├── ROADMAP.md                        # IDs, ordered tracks, claims, next actions
    ├── OPERATIONS.md                     # setup and shared delivery-flow evidence
    ├── template.md                       # lean slice skeleton
    └── NNN-kebab-slug.md                 # stable path in every lifecycle state
```

- **Entrypoint and procedure guides** own project workflow and repeatable CI,
  database, and preview procedures. Load the relevant guide when needed.
- **Architecture** owns durable boundaries and contracts. Update existing docs
  when implementation changes them; avoid duplicating code/generated schemas.
- **FREDs** own slice requirements, authoritative lifecycle state, and local
  evidence. ROADMAP summarizes them and schedules work.
- **OPERATIONS** owns outstanding setup and combined UX verification. One flow
  may cover several FREDs; keep secrets out of documentation and evidence.
- **Code** establishes runtime facts. Resolve discrepancies with requirements
  and architecture explicitly.

Readiness and blockers are roadmap fields, not extra lifecycle states. Each
Implemented slice has a date and a next action or pending gate. Tracks do not
authorize delegation, Git actions, or deployments.

This skill's templates are seeds. Existing project documents govern the repo.
Architecture and CI/database/preview guides are added only when useful; link
existing documentation and maintained scripts instead of creating duplicates.

## When to use

- You are building or planning software in a repository and want features as versioned docs an agent can follow.
- You want to add a feature, ask what to implement next, or turn a messy idea into a FRED.
- You want teammates (human or agent) to coordinate implementation tracks without a board as the source of truth.

## When not to

- The chat is not about the software you are implementing: product features of some other site, a design critique of a public app, or general product-strategy talk with no repo work.
- The repo already has a different spec system you intend to keep. Ask before generating a parallel `docs/features/` tree.
- You need a project tracker for people, deadlines, and stakeholders. Keep that. Point FREDs at it with “derived from”; do not replace it unless you want to.

## Install

[skills.sh](https://skills.sh/) / [Skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add ramidecodes/fred-skill
```

Same source, full GitHub URL, skill named `fred` only:

```bash
npx skills add https://github.com/ramidecodes/fred-skill --skill fred
```

Global (user-level, all projects):

```bash
npx skills add -g ramidecodes/fred-skill
```

From a local clone:

```bash
npx skills add /path/to/fred-skill
```

Equivalents documented by the CLI: `owner/repo@fred`, or `--skill fred` (short `-s`). Default install is project-local. The CLI discovers `skills/fred/SKILL.md`.

Auto-invoke is best-effort: the skill omits `disable-model-invocation`, and the description is written for FRED work in a repository. Cursor cannot guarantee 100% load. Pair install with a pointer so teammates without the skill still get the contract:

```markdown
Agent contract: read docs/agent-guides/00-AGENT-ENTRYPOINT.md at session start.
```

## Bootstrap vs existing docs

When FRED documentation is absent, bootstrap creates the entrypoint, FRED template, ROADMAP, and OPERATIONS, filling placeholders from this repository. The entrypoint records the actual global check command and working directory. Request bootstrap explicitly, or accept the agent's offer.

Existing project contracts remain authoritative. Legacy open indexes and state folders are migrated only when requested, preserving IDs, scope, history, and actual verification evidence. An old Implemented label alone does not prove deployed closure.

## Typical prompts

```text
Users can invite people by email. Write a FRED for that, then we'll implement.

What's the next feature to implement?

Add a FRED for export-to-CSV. Keep it a slice, not the whole reporting suite.

We're missing FRED docs in this repo. Bootstrap them from the skill templates.

Implement the next ready FRED in the reporting track. Run the global check before handoff.

Review this Implemented FRED against its code and evidence. Separate required fixes from suggestions.

Migrate our FRED index to tracks, and collect pending setup and UX checks in OPERATIONS.
```

## For humans vs for agents

- **This README** is the idea: why FRED, how implementation and delivery verification fit together, how to install.
- `skills/fred/SKILL.md` is agent procedure: project authority, lifecycle gates, tracks, and document responsibilities.
- `skills/fred/references/` is detail (methodology, workflow, bootstrap) loaded when needed.
- `skills/fred/templates/` is what gets copied into a consuming repo, then edited there.

## License

Apache-2.0. See [LICENSE](LICENSE).
