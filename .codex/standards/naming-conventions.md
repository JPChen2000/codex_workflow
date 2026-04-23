# Naming Conventions

## Purpose

This document defines the stable naming and path rules shared by all workflow agents.

## Path Mirroring

- Mirror repository-relative module paths under `.codex/output/`.
- Do not prefix the mirrored tree with an extra repository name.
- Use forward structural equivalence even when the repository uses mixed path separators.

Examples:

- `src/layer/auth` -> `.codex/output/src/layer/auth`
- `apps/web/routes/login` -> `.codex/output/apps/web/routes/login`
- `packages/core/cache` -> `.codex/output/packages/core/cache`

## Module Document Names

Each mirrored module directory may contain only these canonical workflow files:

- `structure.md`
- `rule.md`
- `api.md`
- `change-report.md`
- `review-report.md`

Do not invent alternate names such as `rules.md`, `apis.md`, `review.md`, or `impact.md`.

## Global Metadata Names

Use these exact names under `.codex/output/_meta/`:

- `requirement-analysis.md`
- `project-context.md`
- `glossary.md`
- `dependency-map.md`
- `workflow-state.md`
- `document-index.md`

## Template Names

Use these exact names under `.codex/output/_templates/`:

- `structure.template.md`
- `rule.template.md`
- `api.template.md`
- `change-report.template.md`
- `review-report.template.md`
- `requirement-analysis.template.md`

## Agent File Names

Use lowercase kebab-case names for TOML files.

Workflow agents currently use two accepted naming patterns:

- pre-routing requirement analysis agent:
  - `agent-requirement-normalizer.toml`
- staged workflow agents:
  - `agent-project-architect.toml`
  - `agent-code-rules.toml`
  - `agent-interface-designer.toml`
  - `agent-change-analyst.toml`
  - `agent-code-implementer.toml`
  - `agent-code-reviewer.toml`

## Status Values

Only these workflow status values are allowed:

- `not_started`
- `in_progress`
- `completed`
- `blocked`
- `needs_revision`

## Dispatch Mode Values

Use these exact values in handoff documents:

- `serial`
- `parallel`

## Workflow Columns

Use these canonical workflow stage names when tracking stage completion:

- `requirement_analysis`
- `structure`
- `rules`
- `api`
- `change_analysis`
- `implementation`
- `review`

## Workflow Coordination Columns

Use these coordination column names when tracking parallel workflow branches:

- `Parent Scope`
- `Parallel Group`
- `Depends On`
- `Owner Agent`
- `Notes`

## Handoff Field Names

Use these exact field names in structured workflow handoffs:

- `dispatch_mode`
- `next_agent`
- `next_agents`
- `join_condition`

## Section Behavior

- Required document sections must stay in the order defined by the templates unless there is a strong reason to append extra sections.
- Non-applicable sections must be written as `Not Applicable` with a reason.
- Final documents must not contain `TODO`, `TBD`, or placeholder markers.
