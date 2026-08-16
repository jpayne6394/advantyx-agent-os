# Inventory Intelligence Adapter Foundation

Inventory Intelligence is an optional P3PO feature.

## Feature key

`inventory_intelligence`

Default: disabled.

## Integration capability

`inventory_backend`

Development binding: `inventory_backend_dev`.

## Current development source

The current Supabase staging backend contains legacy inventory/intelligence tables. P3PO will use them for development, but their physical names and historical origin are not part of the P3PO feature contract.

## Initial table families observed

- suppliers and supplier snapshots
- source items
- product mappings
- product signals
- product variants
- shopper behavior/search/product signals
- recommendations
- sync and intelligence runs
- action items/notes
- weekly briefs
- agent-memory documents/chunks/logs

## Adapter rule

The adapter must map legacy storage into neutral P3PO domain interfaces. Core P3PO code must not query legacy table names directly.

Example domain operations:

- list inventory sources
- retrieve product/source state
- retrieve supplier state
- retrieve product signals
- retrieve recommendations
- retrieve sync/run health
- record an approved inventory action when write authority is enabled

## Read/write policy

Foundation phase: read-first.

Write operations require an explicit capability declaration and acceptance tests. Existing legacy jobs and tables must not be modified merely to make the P3PO adapter simpler.

## Portability

A future customer may implement `inventory_backend` with Supabase, Postgres, Shopify, an ERP, WMS, CSV pipeline, or custom API. The feature contract should remain stable while provider adapters vary.
