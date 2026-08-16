# P3PO Database Foundation

## Development state store

P3PO currently uses an existing Supabase staging project as a development dependency.

The reusable product does not depend on the physical project name. It references the backend through the neutral integration binding `inventory_backend_dev`.

## P3PO control schema

A private `p3po` schema stores control-plane state:

- `schema_meta`
- `tenants`
- `projects`
- `feature_catalog`
- `project_features`
- `integrations`
- `agents`
- `work_orders`
- `work_order_events`
- `evidence`
- `defects`
- `lessons`
- `playbooks`
- `releases`

RLS is enabled on all P3PO tables. `anon` and `authenticated` have no grants to the schema or tables. Initial access is server-side only via privileged application infrastructure.

This is intentional until the Command Center authentication and tenant-membership model is implemented.

## Inventory module

The existing public inventory/intelligence tables remain in place and are not renamed or mutated during the foundation phase. P3PO treats them as a legacy development backend behind the Inventory Intelligence adapter.

The public table inventory currently includes product/source mappings, supplier data, snapshots, sync runs, signals, recommendations, shopper behavior/search data, action tracking, briefs, and agent-memory tables.

The Inventory Intelligence public contract will be defined from a schema map rather than by exposing every legacy table automatically.

## Security notes

Supabase security advisor reports `rls_enabled_no_policy` informational notices on the private P3PO tables. This is expected because browser roles have no grants and no browser policies are intentionally defined yet.

The advisor also reports a legacy `vector` extension installed in `public`; that predates the P3PO foundation and is not changed here.

## Performance notes

The initial advisor run identified unindexed P3PO foreign keys. Migration `20260816020430 index_p3po_foreign_keys` added covering indexes and common project/status indexes. A follow-up advisor run no longer reports unindexed foreign keys in the `p3po` schema. Newly created indexes may be reported as unused until real workload accumulates.

## Migration history

- `20260816020050 create_p3po_foundation`
- `20260816020430 index_p3po_foreign_keys`

## Production rule

A production customer deployment should receive its own database/project or an explicitly approved tenant-isolated database design. The current shared staging backend is for development and validation only.
