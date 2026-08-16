# P3PO Architecture Foundation

## Product boundary

P3PO is a company-neutral control and operations platform. Deployments attach through adapters and feature flags.

## Layers

1. Control plane
   - Supervisor / Planner
   - Reviewer
   - Guard
   - Release Controller
2. Execution plane
   - engineers
   - QA
   - data workers
   - enabled specialists
3. State plane
   - tenants
   - projects
   - feature flags
   - integrations
   - work orders/events
   - evidence
   - defects/lessons/playbooks
   - releases
4. Integration plane
   - source control
   - database/backend
   - document systems
   - commerce/ERP/CRM/custom systems
5. Presentation plane
   - command center UI
   - project views
   - feature-specific views shown only when enabled

## Persistence

The initial development state store uses a private `p3po` schema in Supabase.

Control-plane tables are not granted to `anon` or `authenticated`; initial access is server-side/service-role only until a dedicated application authorization model is implemented.

## Development inventory backend

The optional Inventory Intelligence feature is currently bound to a neutral integration key `inventory_backend_dev`.

The physical Supabase project is a development dependency only. Its original project name is not part of P3PO identity or module behavior.

The existing inventory-related tables remain untouched during the foundation phase. P3PO reads/writes them only through a future adapter contract after schema mapping and permission review.

## Portability

A production/customer deployment should be reproducible from:

- P3PO core version
- deployment configuration
- enabled feature set
- integration bindings
- secrets supplied outside source control
- deployment-specific rules/playbooks

No customer-specific fork of P3PO core should be required for normal use.
