# Dependency Map

## Purpose

This file records project-wide dependency and ownership relationships that should inform module architecture and change analysis.

## Current State

The repository is in scaffold mode, so no concrete source-module dependency graph exists yet.

## Seed Rules

- Use this file to record high-level module dependency directions once real source modules are added.
- Keep dependencies directional and explicit.
- Note forbidden dependency directions when architectural boundaries require them.

## Suggested Format

Use entries like:

```text
producer: src/core/config
consumer: src/features/auth
relationship: reads configuration values
direction: consumer depends on producer
notes: auth must not write back into config state
```

## Update Guidance

- Update this file whenever a new module boundary or cross-module dependency is introduced.
- Keep this file aligned with module `structure.md` documents.
