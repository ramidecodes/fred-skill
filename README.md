# FRED = **Feature Requirement Documents**

You describe what you want in plain language. A larger, more capable model turns that into a structured FRED. A smaller, faster agent implements from that file. An open index records what is done and what is next. All of it lives in the repo, next to the code.

Linear, Notion, and Jira can still exist. For this slice of planning they are optional sources you cite as “derived from.” The documents the agent maintains and implements from are in git.

This package is methodology plus generators. It does not encode a product, cloud vendor, or app stack. The consuming project’s own agent entrypoint is the contract.

## At a glance

FRED is a repo-native spec workflow: one slice per file, an ordered open index, close-out into `implemented/`. Install the skill, bootstrap (or keep existing docs), then specify → implement → close. Boards stay optional; the files in `docs/features/` are what agents follow.

## The two-agent workflow

Unstructured ideas are cheap. Agents that implement from chat are expensive: they guess scope, skip contracts, and forget sequence.

1. **Specify.** A capable model turns needs into one slice-sized FRED (goal, contracts, tasks, acceptance).
2. **Implement.** A faster agent reads the index, opens the named FRED, and builds that slice only.
3. **Close out.** The file moves to `implemented/`. The index drops the open row and notes what shipped.

You can run both steps in one session. The split still helps: the FRED is the handoff artifact, not a transcript.

## How it works in a project

After bootstrap (or if you already have the files), a consuming repo looks like:

```text
docs/
├── agent-guides/00-AGENT-ENTRYPOINT.md   # this repo's agent contract
└── features/
    ├── OPEN-FRED-INDEX.md                # IDs, order, status, next number
    ├── template.md                       # skeleton for a new FRED
    ├── NNN-kebab-slug.md                 # one open slice
    └── implemented/                      # shipped FREDs
```

- **Entrypoint** owns contributor workflow, verify commands, and where things live in _this_ tree.
- **Index** owns sequence. Filename numbers are stable identity, not “implement 003 because 003 > 002.”
- **FRED files** own how to implement one slice. Architecture docs are read only when the entrypoint or FRED links them.
- **Code** owns what actually runs. If docs and code disagree, say so.

This skill’s templates are seeds. Once the project files exist, they win. Do not overlay skill defaults on top of them.

## When to use

- You are building or planning software in a repository and want features as versioned docs an agent can follow.
- You want to add a feature, ask what to implement next, or turn a messy idea into a FRED.
- You want teammates (human or agent) to share one sequence without a board as the source of truth.

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

If the project has no entrypoint and no `docs/features/`, the agent should offer to generate them from `skills/fred/templates/`, filling placeholders from **this** repository.

If those files already exist, they are authority. The skill does not overwrite them with defaults and does not copy another product’s FRED 001–N.

## Typical prompts

```text
Users can invite people by email. Write a FRED for that, then we'll implement.

What's the next feature to implement?

Add a FRED for export-to-CSV. Keep it a slice, not the whole reporting suite.

We're missing FRED docs in this repo. Bootstrap them from the skill templates.

Implement the next open FRED. Don't start later ones whose deps aren't shipped.
```

## For humans vs for agents

- **This README** is the idea: why FRED, how the two models split work, how to install.
- `skills/fred/SKILL.md` is agent procedure: session start, authority, bootstrap, close-out.
- `skills/fred/references/` is detail (methodology, workflow, bootstrap) loaded when needed.
- `skills/fred/templates/` is what gets copied into a consuming repo, then edited there.

## License

Apache-2.0. See [LICENSE](LICENSE).
