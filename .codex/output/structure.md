# Structure

## Writing Rules

- This file is the canonical structural description for the repository root scope.
- Keep it architecture-focused.
- Do not include detailed production code.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## Module Overview

This repository is a workflow scaffold for multi-Agent collaboration. Its primary job is to define how a coordinator and specialist Agents share authority, exchange documents, and decide when downstream work may proceed.

## Responsibilities

- Define the root coordinator contract in `AGENTS.md`.
- Define reusable workflow standards in `.codex/standards/`.
- Define specialist role contracts in `.codex/agents/`.
- Store authoritative workflow metadata in `.codex/output/_meta/`.
- Store reusable workflow templates in `.codex/output/_templates/`.
- Store root-scoped workflow artifacts directly under `.codex/output/`.

## Internal Substructures

- `AGENTS.md`: root coordinator policy and routing contract.
- `.codex/standards/`: shared lifecycle, naming, and handoff rules.
- `.codex/agents/`: TOML role definitions for specialist Agents.
- `.codex/output/_meta/`: active run metadata and project-wide workflow context.
- `.codex/output/_templates/`: canonical templates for workflow artifacts.
- `.codex/output/`: root workflow artifact scope for shared structure, rules, and active change analysis.

## Upstream Dependencies

- User requests that define or revise workflow behavior.
- Codex runtime capabilities for delegation, editing, and review.

## Downstream Consumers

- The root coordinator.
- Specialized sub-agents that read workflow documents before acting.
- Future repositories or scaffolds that reuse this workflow design.

## Data and Control Flow

User requests enter through the coordinator, which normalizes the requirement, consults root workflow context, and decides whether local module structure documents are needed. Shared repository rules come from root `.codex/output/rule.md`. Cross-module requirement changes consult root `.codex/output/change-report.md` only when that document has been generated for the active run.

## Extension Points

- Add new specialist roles under `.codex/agents/` when a stage gains clear independent ownership.
- Add new metadata or templates under `.codex/output/` when they represent stable workflow contracts.
- Add local mirrored `structure.md` files for complex modules when root structure is not specific enough.

## Risks and Boundary Notes

- The workflow becomes noisy if local `structure.md` is created for every trivial scope, so local structure must stay selective.
- Root `rule.md` is intentionally shared; if future projects need materially different subdomain rules, the workflow will need an explicit override policy.
- Root `change-report.md` is overwritten for the active change run, so teams needing history will require a later versioning policy.

## Completion Standard

The document is complete only when another agent can understand the repository's workflow boundaries without reading the code first.
