# LWT-HYDRO-001 — Current Head Build and Independent QA

## Status
READY

## Project
Living Well Today

## Objective
Validate the actual current head of draft PR #1 in `jpayne6394/lwt-hydrogen-hv1` before any additional storefront feature work is accepted.

## Execution target
- Repo: `jpayne6394/lwt-hydrogen-hv1`
- PR: #1 `HV2 storefront launch candidate`
- Branch: `hv2/dark-opening-art-v01`
- Observed head: `eeb3c2e3164b840964116a300f00b15de4ed7004`
- Approved homepage visual baseline recorded by PR: `d190360`

If the head moves before execution, record the new SHA and validate that exact head.

## Primary lane
Frontend Engineer -> independent QA

## Priority
P0

## Required reading
- repository `AGENTS.md`
- `docs/hv2/HV2_SOURCE_PRIORITY.md`
- `docs/hv2/HV2_ARCHITECTURE.md`
- `docs/hv2/HV2_ACCEPTANCE_MATRIX.md`
- PR #1 body and current diff

## In scope
1. run a full Hydrogen build on the exact PR head
2. run `npm run test:product-rating`
3. run lint/codegen where the current repository instructions require them
4. render `/hv2-home`
5. capture and inspect 390, 749, 750, 989, 990, 1024, and 1440 widths
6. verify protected `/hv1-home` remains unchanged according to existing repo protection rules
7. inspect console/network for material failures
8. record defects without opportunistic redesign
9. create learning records for any repeated or process-significant defect

## Out of scope
- redesigning approved sections
- regenerating/recoloring approved art
- publishing or deploying production
- modifying Shopify business data
- changing `/hv1-home`
- rebuilding the unresolved inventory/intelligence system

## Acceptance criteria
- full current-head build passes
- required focused tests pass
- `/hv2-home` renders at all seven required widths
- zero unintended horizontal overflow
- no material broken image requests
- no material console/runtime errors
- product imagery and live commerce content render as intended
- `/hv1-home` protection verification passes
- any visual deviations from approved baseline are explicitly reported
- executor completion package is reviewed independently

## Evidence required
- exact validated commit SHA
- commands and exit results
- full-page responsive screenshots
- critical-section screenshots required by repository acceptance docs
- console/network defect summary
- `/hv1-home` protection evidence
- changed-files statement (expected: none for pure validation)
- QA verdict: PASS / FAIL / BLOCKED

## Correction rule
If QA fails, keep corrections attached to `LWT-HYDRO-001` unless the objective changes. Record defect class and prevention opportunity.

## Stop conditions
Stop after independent QA verdict. Do not merge or deploy production from this work order.