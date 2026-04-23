# Agent Handoff Contract

## Purpose

This document defines the minimum handoff contract between workflow agents.

## General Rule

Every handoff must answer five questions:

1. What was completed?
2. Which files are authoritative now?
3. What is still missing?
4. What is the next valid stage or stages?
5. What risks remain?

When the workflow starts from a vague user request, the first authoritative handoff should come from `requirement-normalizer`, and it should include `.codex/output/_meta/requirement-analysis.md`.

## Required Handoff Fields

Every agent handoff should provide:

- `requirement_document`: the canonical requirement-analysis document path, or `Not Applicable` only if the workflow genuinely does not need requirement normalization
- `scope`: the module, dependency cluster, or explicit scope set that was analyzed or changed
- `completed_outputs`: the documents or files produced
- `authoritative_inputs_used`: the source documents used during the stage
- `open_gaps`: missing information, conflicts, or blocked items
- `dispatch_mode`: `serial` or `parallel`
- `next_agent`: the next valid agent to run when the work must stay serial
- `next_agents`: the next valid agent and scope pairings when the work is ready to fan out in parallel
- `join_condition`: the condition that requires the parallel branches to rejoin before proceeding further
- `risk_notes`: residual risks or caution points

Use `next_agent` when `dispatch_mode` is `serial`.
Use `next_agents` and `join_condition` when `dispatch_mode` is `parallel`.
Do not mark work as `parallel` unless the downstream scopes can proceed without overlapping write sets or unresolved shared ownership.

## Blocked Handoff Rules

If a stage cannot finish:

- do not invent the missing prerequisite
- state exactly which document or decision is missing
- name the module paths affected
- recommend the specific upstream agent required to unblock the task
- if a parallel branch discovered a shared conflict, say that the affected branches must rejoin before downstream work continues

## Conflict Rules

If two authoritative inputs conflict:

- stop the handoff
- summarize the contradiction in plain language
- identify which upstream owner must resolve it

If two parallel branches conflict on shared ownership, dependencies, or interface boundaries:

- stop the affected branches
- identify the scopes that must rejoin
- route the work back through the smallest upstream owner that can repair the shared contract

## Completion Rules

A handoff is considered complete only when:

- outputs are stored in canonical locations
- required sections are complete
- the next stage or parallel branch set can begin without guessing

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
dispatch_mode: serial
next_agent: code-rules
risk_notes:
- Module boundary with src/layer/session should be rechecked if session persistence is added later.
```

```text
scope:
- src/layer/auth
- src/layer/session
requirement_document:
- .codex/output/_meta/requirement-analysis.md
completed_outputs:
- .codex/output/src/layer/auth/structure.md
- .codex/output/src/layer/session/structure.md
authoritative_inputs_used:
- .codex/output/_meta/requirement-analysis.md
- .codex/output/_meta/project-context.md
- .codex/output/_meta/dependency-map.md
open_gaps:
- Not Applicable
dispatch_mode: parallel
next_agents:
- agent: code-rules
  scope: src/layer/auth
- agent: code-rules
  scope: src/layer/session
join_condition:
- Rejoin before any change-analysis or implementation step that modifies shared session persistence contracts.
risk_notes:
- The auth and session modules may continue independently until a shared persistence interface is introduced.
```
