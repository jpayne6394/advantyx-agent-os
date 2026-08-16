# LWT Project Adapter

Living Well Today is the first production pilot for Advantyx Agent OS.

## Pilot goal

Finish the current Shopify Hydrogen storefront to production-candidate quality while validating a reusable multi-agent operating model.

The storefront remains the primary deliverable. Agent infrastructure must justify itself by making delivery faster, safer, or more repeatable.

## Initial agent chain

1. Planner / Supervisor
2. Frontend Engineer
3. Reviewer
4. QA
5. Guard
6. Release Manager

The executor does not approve its own work.

## Parallel work principle

Agent OS development must not block storefront completion. Add controls incrementally while real LWT work continues.

## LWT-specific boundaries

LWT-specific rules, references, visual approvals, Shopify constraints, health-content constraints, and specialist integrations stay in this directory or in external project systems.

They must not be copied into core orchestration rules unless they are proven generally reusable.

## Existing inventory / intelligence system

An existing LWT inventory/intelligence system has been referenced by the project owner, but has not yet been positively identified in the accessible repositories.

Status: `discover-before-use`.

Rules:

- do not rebuild it yet
- do not infer its interface
- do not hard-code core Agent OS behavior around it
- once identified, register it as an LWT specialist dependency

## First production loop

The first live validation should use a real bounded Hydrogen storefront work order and run:

Planner -> Engineer -> independent QA -> Guard -> Release decision.

Every defect found during that loop must be evaluated for a learning record and regression protection.