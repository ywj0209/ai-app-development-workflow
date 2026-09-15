# Changelog

All notable changes to the central AI App Development Workflow are recorded here.

This changelog tracks reusable workflow changes only. Project-specific product, architecture, data model, or feature changes belong in each project repository.

## 0.1.0 — 2026-09-15

### Added

- `WORKFLOW.md` as the central development method and lifecycle.
- `DOCUMENTATION_RULES.md` for document ownership, context minimization, change discipline, and review rules.
- Eight reusable project document templates:
  - `MVP_BASELINE_TEMPLATE.md`
  - `USER_APP_STRUCTURE_TEMPLATE.md`
  - `ADMIN_STRUCTURE_TEMPLATE.md`
  - `ARCHITECTURE_BASELINE_TEMPLATE.md`
  - `DATA_MODEL_BASELINE_TEMPLATE.md`
  - `IMPLEMENTATION_BACKLOG_TEMPLATE.md`
  - `CLAUDE_TEMPLATE.md`
  - `FEATURE_SPEC_TEMPLATE.md`
- Six reusable workflow prompts:
  - `PROJECT_START_PROMPT.md`
  - `BASELINE_REVIEW_PROMPT.md`
  - `FEATURE_PLANNING_PROMPT.md`
  - `IMPLEMENT_FEATURE_PROMPT.md`
  - `FEATURE_REVIEW_PROMPT.md`
  - `PROJECT_HANDOFF_PROMPT.md`
- Central workflow version tracking through `VERSION`.

### Established

- Fix only global, high-change-cost decisions before implementation.
- One Decision, One Owner.
- Repository Markdown is the Source of Truth; chat memory is not.
- Use the minimum context required for the current task.
- Keep the Implementation Backlog small enough for one planning → implementation → verification loop.
- Create Feature Specs only when product behavior requires explicit local decisions.
- Check Baseline Impact before allowing a Feature to redefine global decisions.
- Treat the coding agent as Implementer, not product decision-maker.
- Use `PASS / FAIL / NOT_RUN / BLOCKED` for verification results.
- Require runtime verification and feedback before final Feature `DONE` when applicable.
- Move to the next Backlog Item only after the current Item is complete.
