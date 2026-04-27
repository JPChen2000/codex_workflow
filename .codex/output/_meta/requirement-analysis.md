# Requirement Analysis

## Requirement Summary

- Task Name: Refine workflow document scope and read rules
- Request Date: 2026-04-27
- Workflow Status: active_for_workflow_refactor

## User Intent

The user wants this repository to evolve into a more practical Agent-collaboration scaffold by reducing per-module document overhead.
The workflow should require shared root documents by default, create local structure documents only where they add value, and generate change analysis only for confirmed cross-module requirement changes.

## Current Implementation Understanding

- The current workflow requires every target module to have `structure.md` and `rule.md` before implementation.
- `change-report.md` is currently modeled as a mirrored module document for cross-module or dependency-affecting work.
- The root coordinator guidance in `AGENTS.md`, the standards under `.codex/standards/`, and the role contracts in `.codex/agents/*.toml` all assume that `rule.md` and `change-report.md` are module-scoped artifacts.
- The templates under `.codex/output/_templates/` reflect the same assumptions.

## Normalized Requirement

- Keep the workflow document-first, but change document scope rules as follows:
- Root `.codex/output/structure.md` must exist for active work on the repository.
- Local mirrored `structure.md` is mandatory only for the repository root and complex modules.
- For simple modules, local `structure.md` may be omitted.
- If the target mirrored module directory already contains `structure.md`, downstream agents must read it before design, implementation, or review decisions for that scope.
- Replace per-module `rule.md` generation with a single repository-wide root `.codex/output/rule.md`.
- Downstream agents should read root `.codex/output/rule.md` once as the shared rule source of truth.
- Replace mirrored per-module `change-report.md` generation with a single root `.codex/output/change-report.md`.
- Generate and read root `.codex/output/change-report.md` only when the workflow has confirmed a requirement change that affects multiple modules or shared dependencies.
- Update the root coordinator contract, standards, templates, and all role TOML files so they consistently describe this revised workflow.

## In Scope

- `AGENTS.md`
- `.codex/standards/document-lifecycle.md`
- `.codex/standards/agent-handoff-contract.md`
- `.codex/standards/naming-conventions.md`
- `.codex/agents/agent-requirement-normalizer.toml`
- `.codex/agents/agent-project-architect.toml`
- `.codex/agents/agent-code-rules.toml`
- `.codex/agents/agent-interface-designer.toml`
- `.codex/agents/agent-change-analyst.toml`
- `.codex/agents/agent-code-implementer.toml`
- `.codex/agents/agent-code-reviewer.toml`
- `.codex/output/_templates/structure.template.md`
- `.codex/output/_templates/rule.template.md`
- `.codex/output/_templates/change-report.template.md`
- `.codex/output/_meta/project-context.md`
- `.codex/output/_meta/glossary.md`
- `.codex/output/_meta/dependency-map.md`
- `.codex/output/_meta/document-index.md`
- `.codex/output/_meta/workflow-state.md`
- root `.codex/output/structure.md`
- root `.codex/output/rule.md`
- root `.codex/output/change-report.md`

## Out of Scope

- Introducing new sub-agent roles
- Changing the core ownership rule that only `code-implementer` writes implementation code
- Adding versioned history for change reports
- Redesigning API or review-report file placement

## Affected Code Areas

- Workflow policy documents
- Agent role contracts
- Root and template workflow artifacts
- Workflow metadata used as shared context for future runs

## Affected Modules

- repository root scope -> requires root `.codex/output/structure.md`
- `.codex/standards` -> can rely on root structure for this refactor
- `.codex/agents` -> can rely on root structure for this refactor
- `.codex/output/_templates` -> can rely on root structure for this refactor
- `.codex/output/_meta` -> can rely on root structure for this refactor

## Execution Notes for Downstream Agent

- Treat this task as a workflow-policy refactor rather than a product feature.
- Keep file names aligned with current canonical names unless the requirement explicitly changes the file name.
- Use root `.codex/output/rule.md` as the single shared rules document.
- Create or update local mirrored `structure.md` only when a scope is complex or already documented that way.
- Root `.codex/output/change-report.md` is required for this run because the request explicitly changes cross-module workflow requirements.

## Acceptance Criteria

- `AGENTS.md`, standards, templates, and all role TOML files consistently state that root `.codex/output/structure.md` is mandatory, local mirrored `structure.md` is selective, root `.codex/output/rule.md` is shared, and root `.codex/output/change-report.md` is conditional.
- The repository contains root `.codex/output/structure.md` and root `.codex/output/rule.md` with content that matches the revised workflow.
- The repository contains root `.codex/output/change-report.md` for this active cross-module workflow-policy change.
- A downstream reader can tell when a local `structure.md` must be created, when it must be read, when root `rule.md` must be read, and when root `change-report.md` is required.
- Edge case: the documents must clearly state that a simple module without local `structure.md` may proceed using root structure, but a module directory that already contains local `structure.md` must read it.

## Assumptions / Open Questions

- Assumption: the user's phrase `rules.md` refers to the existing canonical `rule.md` concept and changes its scope rather than renaming the file.
- Assumption: `main directory` means the root `.codex/output/` workflow scope.
- Open Question: none blocking for this repository refactor.

## Suggested Handoff Task

Update the coordinator contract, standards, templates, and role files to enforce root-scoped `structure.md`, root-scoped `rule.md`, conditional root-scoped `change-report.md`, and selective local `structure.md` usage.

## Document Usage

This document is the authoritative requirement input for downstream architecture, rules, interface, change, implementation, and review stages until superseded by a later requirement-analysis update.
