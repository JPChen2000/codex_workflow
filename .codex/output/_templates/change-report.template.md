# Change Report Template

## Writing Rules

- This file records the impact of the active confirmed cross-module or shared-dependency requirement change before implementation.
- Separate mandatory coordinated changes from optional follow-ups.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.
- This root document is overwritten for the active change run rather than versioned per module by default.

## Change Request Summary

Summarize the requested change in one clear paragraph.

## Affected Modules

List the mirrored module scopes affected by this change.

## Affected Interfaces

List the interface contracts that will change, be added, or require verification.

## Dependency Impact

Explain which dependency relationships are touched and why.

## Required Coordinated Changes

List changes that must happen together to keep the system correct.

## Risk Assessment

Describe the main implementation, integration, or migration risks.

## Migration / Rollback Notes

Describe rollout, migration, fallback, or rollback expectations when relevant.

## Implementation Order Suggestion

Recommend a safe execution sequence for the downstream implementation agent.

## Completion Standard

The document is complete only when an implementation agent can tell what must change together and what risks need active management.
