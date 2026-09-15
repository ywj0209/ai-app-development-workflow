# AI App Development Workflow

A reusable workflow for building apps and web products with AI while keeping product decisions, implementation scope, and repository state under control.

The core approach is:

> Fix only the global decisions that are expensive to change, then plan, implement, run, review, and refine one small Feature at a time.

Current version: [`0.1.1`](VERSION)

---

## Why This Exists

AI coding agents can implement quickly, but speed becomes expensive when they are allowed to invent product behavior, redesign data models, expand scope, or rely on stale chat context.

This workflow is designed to balance:

```text
Enough upfront structure
+
Fast implementation
+
Runtime feedback
```

It is especially suited to:

- solo developers
- fast MVP development
- AI-assisted product planning
- Claude Code or other repository-capable coding agents
- products whose details become clearer during implementation

---

## Core Principles

The detailed rules live in [`WORKFLOW.md`](WORKFLOW.md) and [`DOCUMENTATION_RULES.md`](DOCUMENTATION_RULES.md).

At a high level:

1. Fix only important global decisions early.
2. One Decision has one Owner document.
3. Keep unresolved details as `TBD` until they are actually needed.
4. Plan one small Backlog Item at a time.
5. Create a Feature Spec only when product behavior needs explicit decisions.
6. A Feature Spec cannot silently redefine a Baseline.
7. The coding agent implements; it does not invent product policy.
8. Read only the documents relevant to the current task.
9. Repository Markdown is the Source of Truth, not chat memory.
10. Code generation alone is not `DONE`; verification and runtime feedback matter.

---

## Workflow Overview

```text
Project Idea
↓
Product Baselines
↓
Baseline Review
↓
Implementation Backlog
↓
Project CLAUDE.md
↓
Next READY Item
↓
Feature Planning
↓
Implementation
↓
Feature Review
↓
DONE
↓
Next Item
```

When a Feature does not need product-level planning, the Feature Spec step can be skipped.

For the full process, see [`WORKFLOW.md`](WORKFLOW.md).

---

## Repository Structure

```text
ai-app-development-workflow/
├─ README.md
├─ WORKFLOW.md
├─ DOCUMENTATION_RULES.md
├─ CHANGELOG.md
├─ VERSION
├─ templates/
│  ├─ MVP_BASELINE_TEMPLATE.md
│  ├─ USER_APP_STRUCTURE_TEMPLATE.md
│  ├─ ADMIN_STRUCTURE_TEMPLATE.md
│  ├─ ARCHITECTURE_BASELINE_TEMPLATE.md
│  ├─ DATA_MODEL_BASELINE_TEMPLATE.md
│  ├─ IMPLEMENTATION_BACKLOG_TEMPLATE.md
│  ├─ CLAUDE_TEMPLATE.md
│  └─ FEATURE_SPEC_TEMPLATE.md
└─ prompts/
   ├─ PROJECT_START_PROMPT.md
   ├─ BASELINE_REVIEW_PROMPT.md
   ├─ FEATURE_PLANNING_PROMPT.md
   ├─ IMPLEMENT_FEATURE_PROMPT.md
   ├─ FEATURE_REVIEW_PROMPT.md
   └─ PROJECT_HANDOFF_PROMPT.md
```

---

## Core Documents

| Document | Responsibility |
|---|---|
| [`WORKFLOW.md`](WORKFLOW.md) | Defines the development method, stages, role boundaries, verification loop, and `DONE` flow. |
| [`DOCUMENTATION_RULES.md`](DOCUMENTATION_RULES.md) | Defines document ownership, context rules, change discipline, naming, and review rules. |
| [`VERSION`](VERSION) | Contains the currently released central workflow version. |
| [`CHANGELOG.md`](CHANGELOG.md) | Records version-level changes to this reusable workflow. |

---

## Templates

Templates define the structure of project-specific documents. They are not project decisions by themselves.

| Template | Use When |
|---|---|
| [`MVP_BASELINE_TEMPLATE.md`](templates/MVP_BASELINE_TEMPLATE.md) | Defining what the MVP includes and excludes. |
| [`USER_APP_STRUCTURE_TEMPLATE.md`](templates/USER_APP_STRUCTURE_TEMPLATE.md) | Defining top-level user-facing areas, navigation, and flows. |
| [`ADMIN_STRUCTURE_TEMPLATE.md`](templates/ADMIN_STRUCTURE_TEMPLATE.md) | Defining a separate admin or operations surface when the project needs one. |
| [`ARCHITECTURE_BASELINE_TEMPLATE.md`](templates/ARCHITECTURE_BASELINE_TEMPLATE.md) | Defining system components, responsibilities, integration, and runtime boundaries. |
| [`DATA_MODEL_BASELINE_TEMPLATE.md`](templates/DATA_MODEL_BASELINE_TEMPLATE.md) | Defining core data meaning, relationships, states, and lifecycle. |
| [`IMPLEMENTATION_BACKLOG_TEMPLATE.md`](templates/IMPLEMENTATION_BACKLOG_TEMPLATE.md) | Defining implementation Items, dependencies, order, and status. |
| [`CLAUDE_TEMPLATE.md`](templates/CLAUDE_TEMPLATE.md) | Creating project-level rules for the coding agent. |
| [`FEATURE_SPEC_TEMPLATE.md`](templates/FEATURE_SPEC_TEMPLATE.md) | Defining the behavior of one Feature when explicit product decisions are required. |

Not every project needs every Baseline. Create only the documents that have a real independent responsibility.

---

## Prompts

The prompts operate the workflow. They do not replace the Owner documents.

| Prompt | Purpose |
|---|---|
| [`PROJECT_START_PROMPT.md`](prompts/PROJECT_START_PROMPT.md) | Determine which Baselines the project needs and which global decisions should be resolved first. |
| [`BASELINE_REVIEW_PROMPT.md`](prompts/BASELINE_REVIEW_PROMPT.md) | Review written Baselines for ownership, conflicts, duplication, missing global decisions, and premature detail. |
| [`FEATURE_PLANNING_PROMPT.md`](prompts/FEATURE_PLANNING_PROMPT.md) | Plan one READY Backlog Item and decide whether a Feature Spec is required. |
| [`IMPLEMENT_FEATURE_PROMPT.md`](prompts/IMPLEMENT_FEATURE_PROMPT.md) | Implement the approved current Feature, run supported verification, and review the diff. |
| [`FEATURE_REVIEW_PROMPT.md`](prompts/FEATURE_REVIEW_PROMPT.md) | Perform final Feature review, runtime verification, issue classification, feedback, and `DONE` eligibility. |
| [`PROJECT_HANDOFF_PROMPT.md`](prompts/PROJECT_HANDOFF_PROMPT.md) | Reconstruct current project state from the Repository when moving to a new AI session or agent. |

The normal Feature loop is:

```text
FEATURE_PLANNING_PROMPT
↓
IMPLEMENT_FEATURE_PROMPT
↓
FEATURE_REVIEW_PROMPT
↓
DONE
```

`PROJECT_HANDOFF_PROMPT.md` can be used whenever a session or agent changes.

---

## Starting a New Project

A practical starting sequence is:

1. Create or open the actual project repository.
2. Use [`PROJECT_START_PROMPT.md`](prompts/PROJECT_START_PROMPT.md) to identify the Baselines that are actually needed.
3. Create those project Baselines from the relevant templates.
4. Review them with [`BASELINE_REVIEW_PROMPT.md`](prompts/BASELINE_REVIEW_PROMPT.md).
5. Create `IMPLEMENTATION_BACKLOG.md` from [`IMPLEMENTATION_BACKLOG_TEMPLATE.md`](templates/IMPLEMENTATION_BACKLOG_TEMPLATE.md).
6. Create project `CLAUDE.md` from [`CLAUDE_TEMPLATE.md`](templates/CLAUDE_TEMPLATE.md).
7. Select one `READY` Backlog Item.
8. Use [`FEATURE_PLANNING_PROMPT.md`](prompts/FEATURE_PLANNING_PROMPT.md).
9. Implement with [`IMPLEMENT_FEATURE_PROMPT.md`](prompts/IMPLEMENT_FEATURE_PROMPT.md).
10. Review with [`FEATURE_REVIEW_PROMPT.md`](prompts/FEATURE_REVIEW_PROMPT.md).
11. Mark the current Item `DONE` only when the workflow's completion conditions are satisfied.
12. Repeat with the next Item.

Do not plan every Feature in detail before implementation begins.

---

## Source of Truth

Chat is for discussion.

The Repository is for confirmed decisions.

```text
Discussion
↓
Decision
↓
Correct Owner Markdown
↓
Git Repository
↓
Implementation
```

If a decision exists only in chat and has not been written to the correct project Owner document, do not treat it as confirmed project state.

This rule is also why [`PROJECT_HANDOFF_PROMPT.md`](prompts/PROJECT_HANDOFF_PROMPT.md) reconstructs state from the Repository instead of relying on previous conversation memory.

---

## Planner / Reviewer vs Implementer

The workflow separates product reasoning from implementation responsibility.

### Planner / Reviewer

Can be GPT, Claude, or another capable model.

Typical responsibilities:

- Baseline planning and review
- Feature planning
- product decision clarification
- Baseline Impact assessment
- implementation review
- runtime feedback interpretation

### Implementer

Can be Claude Code or another repository-capable coding agent.

Typical responsibilities:

- inspect the real Repository
- modify code
- implement approved migrations
- add relevant tests
- run actual supported verification
- inspect the diff
- report implementation results

The Implementer should not invent product scope, global states, Core Entity meaning, Architecture, or Permission policy.

---

## Verification

Verification results use four statuses:

| Status | Meaning |
|---|---|
| `PASS` | Actually executed and succeeded. |
| `FAIL` | Actually executed and failed. |
| `NOT_RUN` | Not executed. |
| `BLOCKED` | Could not be executed because of an external condition. |

An unexecuted check is never `PASS`.

Projects should use the Build, Typecheck, Lint, Test, migration, or runtime checks that actually exist in their own repositories rather than commands hard-coded by this central workflow.

---

## Versioning

The current central workflow version is stored in [`VERSION`](VERSION).

Version-level changes are recorded in [`CHANGELOG.md`](CHANGELOG.md).

A project may record which workflow version it has adopted. This is recommended when version traceability is useful, but the central workflow does not mandate a storage location or format.

A newer central workflow version is **not** automatically applied to existing projects. Projects adopt updates selectively.

---

## What This Repository Does Not Define

This repository does not contain or own:

- project-specific product requirements
- project-specific MVP scope
- project-specific Architecture choices
- project-specific Data Models
- actual application source code
- predefined product Features
- project-specific implementation decisions

Those belong in the project repository.

This repository defines **how to develop the product**, not **what the product is**.
