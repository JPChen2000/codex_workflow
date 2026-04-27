# Rule

## Writing Rules

- This file defines how the repository may be changed.
- Rules must be actionable and enforceable.
- Prefer `must`, `must not`, `may`, and `should`.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## Scope

This rule file governs repository-wide workflow and documentation changes unless a future policy introduces an explicit narrower override.

## Allowed Changes

- Agents may update root workflow documents under `.codex/output/` when those documents are authoritative for the active workflow design.
- Agents may create local mirrored `structure.md` for complex modules or for scopes that clearly benefit from explicit local boundary documentation.
- Agents may omit local mirrored `structure.md` for simple modules when root `.codex/output/structure.md` is sufficient.
- Agents may generate root `.codex/output/change-report.md` only for confirmed cross-module or shared-dependency requirement changes.

## Forbidden Changes

- Agents must not require local `structure.md` for every mirrored module by default.
- Agents must not create per-module `rule.md` files unless a later workflow policy explicitly changes this repository-wide rule.
- Agents must not create per-module `change-report.md` files while this root-scoped change-report policy is active.
- Agents must not skip reading a local mirrored `structure.md` when the target scope already has one.

## Naming Rules

- Root-scoped shared workflow documents must use `structure.md`, `rule.md`, and `change-report.md`.
- Module-specific workflow documents must keep canonical names from the naming standard.
- Requests that say `rules.md` should be interpreted as the repository-wide `rule.md` concept unless the user explicitly requests a filename change.

## Layering Rules

- Root workflow documents define shared constraints first.
- Local mirrored `structure.md` may refine scope-level structure but must not contradict root `.codex/output/structure.md`.
- `api.md` remains module-scoped and should be read after shared root structure and rules are loaded.
- `change-report.md` should only appear in the root workflow scope for the active confirmed cross-module change.

## State and Data Rules

- Root `.codex/output/change-report.md` represents the active change-analysis state and may be overwritten for the next confirmed qualifying change.
- Workflow metadata under `.codex/output/_meta/` must stay consistent with the active root documents.

## Error Handling Rules

- If root `.codex/output/structure.md` or root `.codex/output/rule.md` is missing, downstream implementation-oriented work must stop.
- If a target scope contains local `structure.md` and that file was not read, downstream work must stop.
- If a confirmed cross-module or shared-dependency requirement change lacks root `.codex/output/change-report.md`, downstream work must stop.

## Logging and Observability Rules

Not Applicable. This scaffold does not define runtime observability behavior.

## Testing Rules

- Workflow changes must be checked for internal consistency across `AGENTS.md`, standards, templates, role TOML files, and metadata.
- Reviews should verify both the default simple-module path and the edge case where a local mirrored `structure.md` already exists.

## Review Checklist

- Is root `.codex/output/structure.md` treated as mandatory?
- Is root `.codex/output/rule.md` treated as the shared rule source of truth?
- Are local mirrored `structure.md` files described as selective rather than universal?
- Is local `structure.md` explicitly required to be read when it already exists?
- Is root `.codex/output/change-report.md` described as conditional on a confirmed cross-module requirement change?

## Completion Standard

The document is complete only when a code-writing agent can implement changes without guessing about local conventions or boundaries.
