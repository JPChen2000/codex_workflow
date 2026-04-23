# Workflow State

## Purpose

Track which workflow stages exist for each module or project scope.

## Allowed Status Values

- `not_started`
- `in_progress`
- `completed`
- `blocked`
- `needs_revision`

## Global Scaffold Status

| Scope | requirement_analysis | structure | rules | api | change_analysis | implementation | review |
| --- | --- | --- | --- | --- | --- | --- | --- |
| repository_scaffold | completed | completed | completed | completed | completed | completed | completed |

## Module Tracking Template

Use rows like:

| Scope | requirement_analysis | structure | rules | api | change_analysis | implementation | review |
| --- | --- | --- | --- | --- | --- | --- | --- |
| src/example/module | not_started | not_started | not_started | not_started | not_started | not_started | not_started |

## Update Guidance

- Add one row per mirrored module scope when real project modules are introduced.
- Update statuses after every completed or blocked workflow stage.
- If a document becomes stale or contradicted, move the affected stage to `needs_revision`.
