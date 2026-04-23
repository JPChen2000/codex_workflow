# Rule Template

## Writing Rules

- This file defines how the mirrored module may be changed.
- Rules must be actionable and enforceable.
- Prefer `must`, `must not`, `may`, and `should`.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## Scope

State the exact module scope this rule file governs.

## Allowed Changes

List the kinds of changes the implementation agent may make safely.

## Forbidden Changes

List changes that must not be made without architectural or product approval.

## Naming Rules

Define naming conventions for files, types, functions, variables, or domain concepts in this module.

## Layering Rules

Define allowed dependency directions and forbidden coupling patterns.

## State and Data Rules

Define constraints around mutable state, persistence, caching, or data ownership.

## Error Handling Rules

Define how this module should report, propagate, or translate errors.

## Logging and Observability Rules

Define logging, metrics, or tracing expectations if relevant.

## Testing Rules

Define what kinds of tests are required and what behaviors are most important to verify.

## Review Checklist

Provide a short checklist a reviewer can use to catch common violations.

## Completion Standard

The document is complete only when a code-writing agent can implement changes without guessing about local conventions or boundaries.
