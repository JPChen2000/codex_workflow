# API Template

## Writing Rules

- This file defines one module's interface contract.
- Be explicit about names, inputs, outputs, and failure behavior.
- Avoid placeholders and implied behavior.
- Every required section must exist.
- If a section does not apply, write `Not Applicable` and explain why.

## API Overview

Summarize the purpose and scope of the module's interface surface.

## Interface Inventory

List each interface, method, endpoint, command, or callable contract covered by this document.

## Input Contract

Define required inputs, optional inputs, validation rules, and accepted ranges or formats.

## Output Contract

Define return values, payload shapes, side effects, and success semantics.

## Error Codes

Define explicit error codes, categories, or failure outcomes.

## Transaction Boundary

Define transactional scope, atomicity expectations, and consistency boundaries when relevant.

## Compatibility Notes

Define backward-compatibility expectations and consumer impact.

## Versioning Notes

Define any versioning or migration expectations.

## Example Call Flows

Provide representative usage flows that make the contract concrete.

## Completion Standard

The document is complete only when an implementation agent can build the interface and a reviewer can verify conformance without guessing.
