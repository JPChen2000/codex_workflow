# Structure Template

## Writing Rules

- This file is the canonical structural description for either the repository root scope or one complex mirrored module scope.
- Keep it architecture-focused.
- Do not include detailed production code.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.
- Root `.codex/output/structure.md` is mandatory for active work.
- Local mirrored `structure.md` is optional by default and should be created only when the module is complex or needs explicit local boundary documentation.

## Module Overview

Describe what the module is for and where it fits in the project.

## Responsibilities

List the responsibilities this module owns directly.

## Internal Substructures

Describe major internal components, folders, or layers inside the module.

## Upstream Dependencies

List the modules, services, or abstractions this module depends on.

## Downstream Consumers

List the known modules or layers that consume this module.

## Data and Control Flow

Explain how data enters, moves through, and leaves this module.

## Extension Points

Describe safe extension points or customization surfaces.

## Risks and Boundary Notes

Call out ambiguous ownership, sensitive dependencies, or boundary risks.

## Completion Standard

The document is complete only when another agent can understand the module's boundaries without reading the code first.
