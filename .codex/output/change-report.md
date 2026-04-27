# Change Report

## Writing Rules

- This file records the impact of the active confirmed cross-module workflow-policy change before implementation.
- Separate mandatory coordinated changes from optional follow-ups.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## Change Request Summary

The active request changes how the scaffold scopes and reads workflow documents. Root `.codex/output/structure.md` and root `.codex/output/rule.md` become the default shared prerequisites, local mirrored `structure.md` becomes selective instead of universal, and root `.codex/output/change-report.md` becomes conditional and active-run specific.

## Affected Modules

- repository root scope
- `.codex/standards`
- `.codex/agents`
- `.codex/output/_templates`
- `.codex/output/_meta`

## Affected Interfaces

- The coordinator contract in `AGENTS.md`
- The standard handoff and lifecycle contracts in `.codex/standards/`
- The required input contracts in `.codex/agents/*.toml`

## Dependency Impact

- All downstream implementation-oriented roles now depend on root `.codex/output/structure.md` and root `.codex/output/rule.md`.
- Local mirrored `structure.md` changes from universal prerequisite to selective prerequisite.
- Cross-module requirement changes now depend on a single root `.codex/output/change-report.md` instead of mirrored per-module change reports.

## Required Coordinated Changes

- Update `AGENTS.md` to describe the new read and generation rules.
- Update standards so naming, lifecycle, and handoff behavior match the new root-scoped policy.
- Update role TOML files so their required inputs and hard stops use root `rule.md`, conditional root `change-report.md`, and selective local `structure.md`.
- Update templates and metadata so future runs inherit the revised behavior.
- Create root `.codex/output/structure.md` and root `.codex/output/rule.md` to make the new policy immediately usable.

## Risk Assessment

- If any role contract still expects per-module `rule.md` or `change-report.md`, downstream agents may misread prerequisites.
- If local `structure.md` is treated as optional even when it already exists, scope-specific boundary information may be ignored.
- If the repository later needs historical change analysis, root overwrite behavior may become insufficient.

## Migration / Rollback Notes

- Migration is in-place: update the contracts and begin using the new root documents immediately.
- Rollback would require restoring the previous module-scoped `rule.md` and `change-report.md` assumptions across all standards and role definitions.

## Implementation Order Suggestion

1. Update requirement and standards metadata.
2. Update `AGENTS.md`.
3. Update role TOML contracts.
4. Update templates and root workflow documents.
5. Recheck metadata indexes and workflow-state guidance.

## Completion Standard

The document is complete only when an implementation agent can tell what must change together and what risks need active management.
