# FRED XX — Feature Name

<!-- All 11 numbered sections stay in every FRED. Prefer a short "N/A — …" over deleting a section. -->

> **Architectural authority:** [../agent-guides/00-AGENT-ENTRYPOINT.md](../agent-guides/00-AGENT-ENTRYPOINT.md)
>
> **Derived from:** ({{SOURCE_PAGES}}, prerequisite FREDs)
>
> **Specification reference:** {{ARCHITECTURE_AND_README_LINKS}}

**Status:** {{STATUS}} — e.g. High-level draft (not implemented) / Detailed specification (not implemented) / Implemented (then this file should live under `implemented/`)

**Roadmap ID / stage:** {{ROADMAP_ID_OR_N_A}}

**Dependencies:** (linked prerequisite FREDs)

**Depth rule:** Drafts specify user outcomes, authority, and acceptance now; finalize feature-owned schema, route/API/event contracts, guards, timeouts, and recovery against **implemented** dependencies before coding.

Execution order comes from [OPEN-FRED-INDEX.md](./OPEN-FRED-INDEX.md), not the numeric ID.

Replace `XX` in the title and filename with the next three-digit number from the index. Filename: `{NNN}-{kebab-case-slug}.md`.

---

**Local notes:** Restate only what **this repo’s** entrypoint/architecture already decided. Label any extra ideas as **local proposals**. Do not invent shipped surfaces.

---

## Surfaces Touched

<!-- Mandatory. Routes, packages, workflows, and folders this FRED modifies or depends on. -->

| Surface | Role |
| ------ | ---- |
| (TBD) | |

---

## 1. Goal

<!-- Mandatory. Why this feature exists. One to three paragraphs. -->

---

## 2. User Story

<!-- Mandatory. One or two stories. -->

**As a [role]**, I want [goal], so that [benefit].

---

## 3. Functional Requirements

<!-- Mandatory. Numbered subsections. Be specific and measurable. -->

### 3.1 Subsection Name

- Requirement details

### 3.2 State Ownership

<!-- Fill when this slice introduces or changes client/workflow/server state; otherwise N/A. -->

- Source of truth
- URL vs persisted vs local UI state

### 3.3 Canonical Contract

<!-- Fill when routes, APIs, events, or persisted shapes change; otherwise N/A. -->

- Canonical shape
- Compatibility aliases (separate from canonical)

### 3.4 Compatibility / Migration

<!-- Optional to flesh out; keep the heading. -->

- Temporary inbound compatibility
- What is intentionally not migrated yet

### 3.5 Non-Goals

<!-- Mandatory content. What this slice will not change. -->

-

### 3.6 Autonomy, approvals, and policy

<!-- Fill when humans/agents/gates matter; otherwise N/A. -->

- Who may approve what
- Whether unattended actions are in scope
- Policy/version pins if relevant

---

## 4. Data Requirements

<!-- Mandatory. Stores, APIs, env vars. Use "none" rather than deleting. -->

**Read:**

**Write:**

**New tables / collections:**

**Modified client / workflow state:**

**Environment Variables:**

| Variable | Required | Description |
| -------- | -------- | ----------- |

---

## 5. User Flow

<!-- Mandatory. Happy path first, then alternatives and errors. -->

1. Step one
2. Step two
3. Step three

---

## 6. Implementation Tasks

<!-- Mandatory. Ordered work items. -->

- [ ] Task one
- [ ] Task two
- [ ] Task three

---

## 7. Acceptance Criteria

<!-- Mandatory. Testable definition of done. -->

- [ ] Criterion one
- [ ] Criterion two
- [ ] Touched surfaces match architecture / this FRED
- [ ] Verification from [00-AGENT-ENTRYPOINT.md](../agent-guides/00-AGENT-ENTRYPOINT.md) was run (when scripts exist)

### 7.1 Test Matrix

<!-- Recommended. Keep the heading; N/A the rows if not applicable. -->

| Area | What to verify |
| --- | --- |
| Parsing / validation | |
| Navigation / routing | |
| Persistence | |
| Approvals / gates | |
| Evidence / audit | |
| Kill switch / pause | |
| External adapters | |

---

## 8. Edge Cases

<!-- Mandatory heading. -->

| Case | Behavior |
| ---- | -------- |
| | |

---

## 9. Non-Functional Requirements

<!-- Mandatory heading. Performance, security, UX, constraints. -->

| Requirement | Target |
| ----------- | ------ |
| | |

---

## 10. Manual Steps / Rollout Checklist

<!-- Mandatory. Human operator work: secrets, DNS, dashboards. -->

- [ ] Document dashboard, DNS, or secret wiring this feature needs
- [ ] Production deploy only when the task asks for it

---

## 11. Decisions and Open Validation

<!-- Mandatory. Separate locked decisions, operator-resolved policy, local proposals, and remaining live validation gates. Name which tasks are blocked and which may proceed against fakes. -->
