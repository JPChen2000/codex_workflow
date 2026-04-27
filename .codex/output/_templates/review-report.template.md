# Review Report Template

## Writing Rules

- This file evaluates the implementation against the approved request and design artifacts.
- Findings should come before summary.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## Review Scope

Define which modules, files, and documents were reviewed.

## Requirement Alignment

State whether the implementation matches the requested outcome and note any gaps.

## Rule Compliance

Check whether the implementation follows root `.codex/output/rule.md` and any applicable scoped constraints derived from the approved structure documents.

## API Contract Compliance

Check whether the implementation follows the module `api.md` where relevant.

## Code Quality Findings

List correctness, maintainability, readability, or coupling concerns.

## Risk Findings

List unresolved risks, hidden assumptions, or regression concerns.

## Test Coverage Notes

State what is covered, what is missing, and what remains risky.

## Final Verdict

State one of: aligned, blocked, or needs_revision.

## Required Fixes

List mandatory follow-up fixes if any exist. If none exist, say `Not Applicable`.

## Completion Standard

The document is complete only when another agent or human can understand whether the implementation is safe to accept and what must be fixed next.
