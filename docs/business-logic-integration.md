# Business Logic Integration Plan

This document defines how to move from Agent OS infrastructure into real product and domain execution.

## Objective

Connect the autonomous delivery system to actual product work instead of only meta-system work.

## Phase 1: Mission quality

Before business logic automation is trusted, each mission must clearly specify:
- business objective
- in-scope files
- out-of-scope files
- acceptance criteria
- test expectations
- risk class

## Phase 2: Domain lanes

Extend agent lanes beyond technical surface areas.

Recommended domain lanes:
- `domain:opportunity`
- `domain:supplier`
- `domain:workflow`
- `domain:pricing`
- `domain:compliance`
- `domain:analytics`

These should be mapped to actual code areas in target product repos.

## Phase 3: Business logic safety classes

Every mission should carry one of these labels:
- `risk:low`
- `risk:medium`
- `risk:high`

### Low risk
- display-only changes
- additive read paths
- tests and docs

### Medium risk
- business rule adjustments
- workflow orchestration changes
- data mapping logic

### High risk
- pricing decisions
- compliance logic
- readiness gating
- irreversible data changes

## Phase 4: Domain-specific validation

Add validation workflows per product area:
- business-rule regression checks
- fixture-based domain tests
- decision snapshot comparisons
- migration safety checks

## Phase 5: Human boundary policy

Business logic may still be autonomous, but only with graded controls.

Recommended policy:
- low risk: fully autonomous path allowed
- medium risk: autonomous implementation + strict reviewer/guard
- high risk: autonomous draft + required human confirmation before merge

## Deliverables to add in target product repos

- domain-to-path mapping file
- risk-class mapping file
- snapshot fixtures for decision logic
- mission templates with business acceptance criteria

## Success criteria

- autonomous work can operate against real product logic safely
- business rules are testable and auditable
- high-risk changes are identifiable before merge
