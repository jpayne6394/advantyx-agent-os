# LWT-PILOT-001 — Baseline and Agent Loop Validation

## Status
PASS — inspection complete; execution handoff required

## Project
Living Well Today

## Objective
Establish the current Hydrogen storefront baseline and validate the first complete Agent OS delivery loop without redesigning the storefront.

## Primary lane
Frontend / QA

## Priority
P0

## Baseline findings

- Primary repo: `jpayne6394/lwt-hydrogen-hv1`
- Default `main` head: `4a0079b2c6bfc40600cdbba7116f56ab0eff2810`
- Active storefront work is NOT on `main`; it is in draft PR #1: `HV2 storefront launch candidate`
- Active branch: `hv2/dark-opening-art-v01`
- Active branch head observed: `eeb3c2e3164b840964116a300f00b15de4ed7004`
- PR #1 is draft, open, and mergeable
- PR records the approved homepage visual baseline as `d190360`
- PR records previous responsive homepage tests as 9/9 PASS at 390, 749, 750, 989, 990, 1024, and 1440
- PR explicitly requires a full Hydrogen build and rendered review on the current head before merge
- No commit status checks were returned for the current head
- No `.github/workflows` directory was discoverable on the active branch through the connected GitHub interface

## Discovered commands

From active-branch `package.json`:

- `npm run build` -> `shopify hydrogen build --codegen`
- `npm run dev` -> `shopify hydrogen dev --codegen`
- `npm run preview` -> `shopify hydrogen preview --build`
- `npm run lint` -> ESLint
- `npm run codegen`
- `npm run test:product-rating`

Playwright is installed as a dev dependency and PR instructions already require responsive capture at the seven approved widths.

## Source / guardrail observations

PR #1 includes durable `AGENTS.md` rules protecting `/hv1-home`, restricting HV2 work to `/hv2-home` unless explicitly authorized, preserving live HTML/Shopify data, and requiring responsive evidence.

These project-specific constraints belong in the LWT adapter / source references and must not be generalized into the Agent OS core.

## Inventory / intelligence dependency

Repository searches did not positively identify the existing LWT inventory/intelligence system by the terms available.

Status remains `discover-before-use`.

Do not rebuild or guess its interface.

## CI gap

The active head currently has no returned commit status checks. This means executor completion is not yet protected by repository-level automated acceptance.

Initial recommendation: add CI only after confirming it will not interfere with the current owner-preview branch and after the current head is independently built/reviewed.

## Required next work

Create `LWT-HYDRO-001` to validate the actual current PR head:

1. full Hydrogen build
2. focused product-rating test
3. lint / codegen as appropriate
4. rendered `/hv2-home` review
5. responsive evidence at the seven approved widths
6. regression verification for protected `/hv1-home`
7. defects converted into correction work + learning records

## Explicitly out of scope

- redesigning homepage sections
- replacing approved assets
- altering Shopify product data
- changing production
- rebuilding the existing LWT inventory/intelligence system

## Human approval
Required before production deployment or destructive changes.

## Stop result
Inspection is complete. The next step is current-head execution and independent QA, not more architecture planning.