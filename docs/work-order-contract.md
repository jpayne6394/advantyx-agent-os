# Work Order Contract

Every executable mission must be represented by one bounded work order.

## Required fields

- Work order ID
- Project ID
- Objective
- Primary execution lane
- Priority
- Inputs / source references
- In scope
- Explicitly out of scope
- Acceptance criteria
- Required evidence
- Allowed repositories / paths
- Risk level
- Human approval requirements
- Retry count
- Stop conditions

## Status model

`READY -> RUNNING -> QA -> PASS -> RELEASE_READY -> COMPLETE`

Failure paths:

- `QA -> CORRECTION -> RUNNING`
- any active state -> `BLOCKED`
- any active state -> `NEEDS_HUMAN`

## Completion rule

Executor completion is a claim, not acceptance.

A work order cannot become `PASS` until independent review or QA has evaluated the acceptance criteria.

## Evidence contract

A completion package should contain, when applicable:

- branch
- commit SHA
- pull request
- changed files
- build result
- test result
- preview URL
- screenshots or visual evidence
- known deviations
- unresolved dependencies

Missing required evidence is a QA failure, not an administrative warning.

## Retry policy

Corrections remain attached to the same work order ID unless the objective materially changes.

After three unsuccessful correction cycles, the work order is escalated to Guard / human review with a concise failure history.

## Scope rule

Executors may not improve unrelated areas opportunistically. Discovered unrelated work becomes a new backlog candidate.

## Source-conflict rule

If authoritative sources conflict and the project adapter does not define precedence, stop with `BLOCKED_SOURCE_CONFLICT` rather than guessing.