# Requirement Analysis Template

## Writing Rules

- This file is the canonical requirement document for the active workflow run.
- It must be written before architecture or implementation planning begins when the request is ambiguous, mixed, or large.
- Write for downstream agents, not for product narration.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## Requirement Summary

State the task name, request date, and current workflow status.

## User Intent

Restate the user's goal in one or two sentences.

## Current Implementation Understanding

Summarize the current behavior based on the codebase and mention relevant files, modules, components, or services.

## Normalized Requirement

Rewrite the request into precise, implementation-aware language using repository terminology.

## In Scope

List the exact behaviors, files, or areas that should change.

## Out of Scope

List related areas that should remain unchanged unless separately requested.

## Affected Code Areas

Provide likely files, modules, components, services, routes, or APIs involved.

## Affected Modules

List the repository-relative module scopes that downstream agents should map into `.codex/output/`.

## Execution Notes for Downstream Agent

Include constraints, conventions, dependency expectations, and reuse guidance.

## Acceptance Criteria

Provide concrete, testable outcomes, including one normal path and one edge or failure path when relevant.

## Assumptions / Open Questions

List only the uncertainties that materially affect implementation.

## Suggested Handoff Task

End with a concise execution-ready instruction for the next agent.

## Document Usage

State that this document is the authoritative requirement input for downstream architecture, rules, interface, change, implementation, and review stages until superseded.

## Completion Standard

The document is complete only when downstream agents can start architecture or change planning without re-interpreting the user's original wording.
