# P3PO Feature Module Contract

Optional business capabilities are modules, not core assumptions.

## Required properties

Every feature module must declare:

- stable feature key
- human-readable name
- default state (`disabled` unless explicitly core)
- required integration capabilities
- required agent/specialist roles
- read/write authority
- data ownership and source precedence
- acceptance checks
- failure behavior when the module is disabled or unavailable

## Core rule

Core P3PO functions must continue to work when any optional module is disabled.

Core functions include work orders, routing, QA, Guard, evidence, learning, releases, and project/deployment state.

## Integration rule

Feature code depends on neutral integration keys, never physical customer/backend names.

Example:

- feature: `inventory_intelligence`
- integration capability: `inventory_backend`
- development binding: `inventory_backend_dev`

A later deployment can bind the same capability to another database, API, ERP, or commerce system without changing the feature contract.

## Inventory Intelligence v1

Inventory Intelligence is optional and disabled by default.

Initial capability surface:

- inventory/source item inspection
- supplier and snapshot inspection
- product mapping
- product and shopper signals
- recommendations
- sync/run history
- agent memory associated with inventory intelligence

The current development backend may contain additional tables. They are not automatically part of the public module contract.

## Security

- no service-role key in browser/client code
- exposed tables require intentional Data API access and RLS
- prefer private schemas or server-side adapters for control-plane state
- module writes require explicit deployment permission
- secrets are referenced, never committed in deployment configuration
