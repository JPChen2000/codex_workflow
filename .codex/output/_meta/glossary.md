# Glossary

## Purpose

Use this file to keep naming consistent across all agents and modules.

## Seed Terms

### Main Agent

The root user-facing workflow coordinator defined in `Agent.md`.

### Sub-Agent

A specialized Codex agent defined in `.codex/agents/*.toml` with a narrow responsibility.

### Requirement Normalizer

The pre-routing analysis agent that converts raw user requests into repository-aware, execution-ready requirements.

### Requirement Analysis Document

The canonical file at `.codex/output/_meta/requirement-analysis.md` produced by the requirement normalizer and used as the authoritative request interpretation for downstream agents in the current workflow run.

### Root Structure Document

The repository-wide structural document at `.codex/output/structure.md` that every downstream implementation-oriented stage must read.

### Complex Module

A module scope whose responsibilities, internal substructure, or dependency surface are large enough that it requires its own mirrored `structure.md`.

### Root Rule Document

The repository-wide rule document at `.codex/output/rule.md` that defines shared modification constraints for downstream implementation and review.

### Active Change Report

The root document at `.codex/output/change-report.md` that is generated only for the active confirmed cross-module or shared-dependency requirement change.

### Mirrored Output Tree

The `.codex/output/` directory structure that mirrors repository-relative module paths.

### Module Artifact

Any canonical workflow document stored in a mirrored module directory, such as `structure.md`, `rule.md`, or `api.md`.

### Hard Stop

A condition that must block downstream implementation or review until the missing prerequisite is resolved.

### Parallel Dispatch

The act of launching multiple sub-agents at the same workflow stage for independent scopes whose prerequisites are already satisfied.

### Write Set

The files, mirrored documents, or implementation paths that a workflow branch is expected to modify.

### Join Condition

The explicit condition that requires parallel branches to rejoin through the main agent before downstream work can continue safely.

## Update Guidance

- Add terms only when they are reused across multiple modules or agents.
- Prefer one stable term per concept.
- When renaming a concept, update affected standards and templates together.
