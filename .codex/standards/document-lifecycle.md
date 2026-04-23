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
- Create a module document only in its mirrored output directory.
- Use the matching template as the starting structure.
- Fill every required section before the document becomes authoritative.

## Review

- A newly created document is considered usable only after its required sections are complete.
- If a document is incomplete, mark the relevant workflow state as `blocked` or `needs_revision`.

## Use

- `requirement-analysis.md` is the request interpretation source of truth for the current workflow run.
- `structure.md` is the structural source of truth for module ownership and boundaries.
- `rule.md` is the modification source of truth for coding behavior and constraints.
- `api.md` is the contract source of truth for interface behavior.
- `change-report.md` is the planning source of truth for impact and coordination.
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
- If a contradiction is discovered, stop and escalate instead of guessing.
- Production code must not be treated as authority over approved design documents when the task is still in design-first mode.

## Placeholder Policy

- Placeholder markers are not allowed in final workflow documents.
- If information is unknown, block the workflow and state what is missing.

## Ownership Summary

- `requirement-normalizer` owns `requirement-analysis.md` for the current run
- `project-architect` owns `structure.md`
- `code-rules` owns `rule.md`
- `interface-designer` owns `api.md`
- `change-analyst` owns `change-report.md`
- `code-reviewer` owns `review-report.md`

The main agent coordinates, but does not silently override ownership boundaries.
