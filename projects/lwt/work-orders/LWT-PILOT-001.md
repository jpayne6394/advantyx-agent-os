# LWT-PILOT-001 — Baseline and Agent Loop Validation

## Project
Living Well Today

## Objective
Establish the current Hydrogen storefront baseline and validate the first complete Agent OS delivery loop without redesigning the storefront.

## Primary lane
Frontend / QA

## Priority
P0

## Inputs
- Primary repo: `jpayne6394/lwt-hydrogen-hv1`
- Current `main` branch
- Existing approved project references
- LWT project adapter configuration

## In scope
- identify current baseline commit and active PR state
- verify build/test commands
- verify current preview/deployment path if available
- capture current homepage evidence at required widths when execution environment supports browser screenshots
- identify existing CI checks and missing acceptance gates
- produce a bounded next storefront work order from observed evidence

## Explicitly out of scope
- redesigning homepage sections
- replacing approved assets
- altering Shopify product data
- changing production
- rebuilding the existing LWT inventory/intelligence system

## Acceptance criteria
- baseline commit recorded
- current PR / branch situation recorded
- existing automated checks documented
- evidence requirements for future homepage changes defined
- no storefront code changed unless required solely to restore a broken baseline and separately authorized
- next executable storefront work order proposed from evidence

## Required evidence
- commit SHA
- branch / PR state
- build and test command discovery
- CI status
- preview status if discoverable
- blocker list

## Risk
Low for inspection; medium if code changes are proposed.

## Human approval
Required before production deployment or destructive changes.

## Retry count
0

## Stop conditions
Stop after baseline evidence and the next bounded storefront work order are produced.