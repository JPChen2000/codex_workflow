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

### Mirrored Output Tree

The `.codex/output/` directory structure that mirrors repository-relative module paths.

### Module Artifact

Any canonical workflow document stored in a mirrored module directory, such as `structure.md`, `rule.md`, or `api.md`.

### Hard Stop

A condition that must block downstream implementation or review until the missing prerequisite is resolved.

## Update Guidance

- Add terms only when they are reused across multiple modules or agents.
- Prefer one stable term per concept.
- When renaming a concept, update affected standards and templates together.
