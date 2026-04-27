# Document Lifecycle

## Purpose

This document defines how workflow documents are created, updated, superseded, and trusted.

## Lifecycle Stages

1. Create
2. Review
3. Use
4. Update
5. Supersede

## Create

- Create a global requirement-analysis document in `.codex/output/_meta/` for each active workflow run before architecture work begins.
- Create root-scoped workflow documents directly in `.codex/output/` when they are repository-level by design.
- Create a module document only in its mirrored output directory when the contract is module-specific.
- Use the matching template as the starting structure.
- Fill every required section before the document becomes authoritative.
- Root `.codex/output/structure.md` must exist for active work on the repository.
- Root `.codex/output/rule.md` must exist before implementation or review begins.
- Create local mirrored `structure.md` only for complex modules or when a scope benefits from an explicit local boundary document.
- Create root `.codex/output/change-report.md` only when a confirmed requirement change needs coordinated cross-module or shared-dependency analysis.

## Review

- A newly created document is considered usable only after its required sections are complete.
- If a document is incomplete, mark the relevant workflow state as `blocked` or `needs_revision`.

## Use

- `requirement-analysis.md` is the request interpretation source of truth for the current workflow run.
- root `.codex/output/structure.md` is the shared structural source of truth for repository ownership and boundaries.
- local mirrored `structure.md` is an additional structural source of truth for a complex or explicitly documented module when that file exists.
- root `.codex/output/rule.md` is the modification source of truth for coding behavior and constraints across the repository.
- `api.md` is the contract source of truth for interface behavior.
- root `.codex/output/change-report.md` is the planning source of truth for impact and coordination only for the active confirmed cross-module requirement change that caused it to be generated.
- `review-report.md` is the evaluation source of truth for alignment and findings.

## Update

- Update an existing document instead of creating a parallel variant whenever the same module and contract type already exist.
- Preserve historical meaning. Do not rewrite a document so heavily that prior stages become impossible to interpret.
- If a document becomes materially outdated, refresh the content and record the workflow status accordingly.

## Supersede

- Supersede content in place unless the project later adds versioned document history.
- If older assumptions are no longer valid, make the new state explicit rather than silently deleting context.

## Trust Rules

- Downstream agents must trust upstream documents unless a contradiction is discovered.
- Parallel downstream branches must trust the same authoritative upstream documents until a join condition or contradiction requires re-evaluation.
- If a contradiction is discovered, stop and escalate instead of guessing.
- Production code must not be treated as authority over approved design documents when the task is still in design-first mode.

## Placeholder Policy

- Placeholder markers are not allowed in final workflow documents.
- If information is unknown, block the workflow and state what is missing.

## Ownership Summary

- `requirement-normalizer` owns `requirement-analysis.md` for the current run
- `project-architect` owns root `.codex/output/structure.md` and any local complex-module `structure.md`
- `code-rules` owns root `.codex/output/rule.md`
- `interface-designer` owns `api.md`
- `change-analyst` owns root `.codex/output/change-report.md` for the active confirmed cross-module requirement change
- `code-reviewer` owns `review-report.md`

The main agent coordinates, but does not silently override ownership boundaries.
