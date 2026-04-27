# Workflow State

## Purpose

Track which workflow stages exist for each module or project scope and record how parallel branches are coordinated.

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

Use one row per independently tracked scope or dependency cluster.
Sibling scopes may share a `parallel_group` when they are allowed to progress simultaneously.
If two scopes would touch the same implementation write set, do not mark both rows as `implementation: in_progress` at the same time.

| Scope | Parent Scope | Parallel Group | Depends On | Owner Agent | requirement_analysis | structure | rules | api | change_analysis | implementation | review | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| src/example/module | repository_scaffold | design_wave_1 | repository_scaffold:requirement_analysis | main-agent | not_started | not_started | completed | not_started | not_started | not_started | not_started | If this simple scope has no local `structure.md`, mark `structure` complete only after confirming root `.codex/output/structure.md` is the governing structure input |

## Update Guidance

- Add one row per independently dispatched mirrored scope or dependency cluster when real project modules are introduced.
- Update statuses after every completed or blocked workflow stage.
- Use `Parallel Group` to mark branches that may run concurrently after their dependencies are satisfied.
- Use `Depends On` to record shared prerequisites, upstream scopes, or join points that must complete before the row may advance.
- Use `Owner Agent` to record the current active worker for the row, or `main-agent` when the main coordinator is holding the join point.
- If a document becomes stale or contradicted, move the affected stage to `needs_revision`.
- For simple scopes without local `structure.md`, use the `Notes` column to say that root `.codex/output/structure.md` is the governing structure input.
