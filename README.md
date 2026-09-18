# fred-skill

**FRED** = Feature Requirement Document.

A public Agent Skill for running agentic coding with slice-sized specs: an agent entrypoint, an ordered open index, one FRED file per feature, and a close-out folder when work ships.

This repo is **methodology + generators**. It does not encode any particular product, cloud vendor, or application stack. A consuming project’s own `00-AGENT-ENTRYPOINT.md` is the contract.

## Install

Global (recommended if you want FRED behavior in every repo):

```bash
npx skills add -g ramidecodes/fred-skill
```

Project-local:

```bash
npx skills add ramidecodes/fred-skill
```

From a local clone:

```bash
npx skills add /Users/you/dev/fred-skill
```

The CLI discovers `skills/fred/SKILL.md`. Auto-invoke is **best-effort**: the skill omits `disable-model-invocation`, and the description is written for general software work in FRED-using (or FRED-ready) repos. Cursor cannot guarantee 100% load. Pair install with a pointer in the consuming repo:

```markdown
Agent contract: read docs/agent-guides/00-AGENT-ENTRYPOINT.md at session start.
```

## What the agent does

1. **Session start:** locate and read the consuming project’s entrypoint (`docs/agent-guides/00-AGENT-ENTRYPOINT.md` or `AGENTS.md`). Existing FRED docs always win over skill defaults.
2. **Implement:** index owns sequence; FRED files own the slice; code owns runtime truth.
3. **Missing docs:** offer to generate entrypoint, `template.md`, `OPEN-FRED-INDEX.md`, and `implemented/README.md` from `skills/fred/templates/`.

## Layout in this repo

```text
skills/fred/
├── SKILL.md
├── references/          # methodology, workflow, bootstrap
└── templates/           # copy into a consuming repo, then fill {{PLACEHOLDERS}}
```

## License

Apache-2.0. See [LICENSE](LICENSE).
