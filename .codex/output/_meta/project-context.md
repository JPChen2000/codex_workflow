# Project Context

## Project Purpose

This repository is intended to generate a Codex-oriented agent workflow scaffold.

The scaffold defines:

- a root user-facing coordinator in `AGENTS.md`
- a requirement-normalization stage before architecture and implementation planning
- a canonical requirement document at `.codex/output/_meta/requirement-analysis.md`
- role-scoped sub-agents under `.codex/agents/`
- shared standards under `.codex/standards/`
- root workflow artifacts at `.codex/output/structure.md`, `.codex/output/rule.md`, and `.codex/output/change-report.md`
- mirrored module-specific structure, API, and review artifacts under `.codex/output/`

## Workflow Assumptions

- The workflow is document-first.
- Ambiguous requests should be normalized before architecture or implementation starts.
- Downstream agents should read `requirement-analysis.md` instead of relying on transient chat phrasing.
- Root `.codex/output/structure.md` is the shared structural prerequisite for downstream work.
- Root `.codex/output/rule.md` is the shared rule prerequisite for downstream work.
- Local mirrored `structure.md` is required only for complex modules and any mirrored directory that already contains that file.
- Root `.codex/output/change-report.md` is generated and read only for confirmed cross-module or shared-dependency requirement changes.
- Large requests should be decomposed into smaller module-scoped tasks.
- Independent module-scoped stages may be parallelized after shared prerequisites are satisfied and their write sets do not overlap.
- Sub-agents should stay within narrow responsibilities to reduce implementation drift.
- Design artifacts should preserve both module-level detail and project-wide consistency.

## Global Constraints

- Downstream implementation must not bypass missing upstream documents.
- Mirrored output paths are the canonical storage for module workflow artifacts.
- Repository-wide workflow artifacts live at the root of `.codex/output/`.
- Shared standards should be reused before repeating generic instructions inside each agent file.

## Current Repository State

- Initial scaffold phase
- No real source tree has been mirrored yet
- Templates and standards are expected to seed future project-specific outputs

## Update Guidance

- Update this file when the project purpose, global workflow strategy, or repository-wide conventions materially change.
- Keep the language stable and project-wide. Avoid module-specific details here.
