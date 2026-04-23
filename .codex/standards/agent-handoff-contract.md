# Agent Handoff Contract

## Purpose

This document defines the minimum handoff contract between workflow agents.

## General Rule

Every handoff must answer five questions:

1. What was completed?
2. Which files are authoritative now?
3. What is still missing?
4. What is the next valid stage?
5. What risks remain?

When the workflow starts from a vague user request, the first authoritative handoff should come from `requirement-normalizer`, and it should include `.codex/output/_meta/requirement-analysis.md`.

## Required Handoff Fields

Every agent handoff should provide:

- `requirement_document`: the canonical requirement-analysis document path, or `Not Applicable` only if the workflow genuinely does not need requirement normalization
- `scope`: the module or project scope that was analyzed or changed
- `completed_outputs`: the documents or files produced
- `authoritative_inputs_used`: the source documents used during the stage
- `open_gaps`: missing information, conflicts, or blocked items
- `next_agent`: the next valid agent to run
- `risk_notes`: residual risks or caution points

## Blocked Handoff Rules

If a stage cannot finish:

- do not invent the missing prerequisite
- state exactly which document or decision is missing
- name the module paths affected
- recommend the specific upstream agent required to unblock the task

## Conflict Rules

If two authoritative inputs conflict:

- stop the handoff
- summarize the contradiction in plain language
- identify which upstream owner must resolve it

## Completion Rules

A handoff is considered complete only when:

- outputs are stored in canonical locations
- required sections are complete
- the next stage can begin without guessing

## Example Handoff Shape

```text
scope: src/layer/auth
requirement_document:
- .codex/output/_meta/requirement-analysis.md
completed_outputs:
- .codex/output/src/layer/auth/structure.md
authoritative_inputs_used:
- .codex/output/_meta/requirement-analysis.md
- .codex/output/_meta/project-context.md
- .codex/standards/naming-conventions.md
open_gaps:
- Not Applicable
next_agent: code-rules
risk_notes:
- Module boundary with src/layer/session should be rechecked if session persistence is added later.
```
