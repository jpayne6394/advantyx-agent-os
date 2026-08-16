# Deployment Adapter Contract

## Purpose

Deployment adapters connect P3PO to a customer, project, or product without contaminating the reusable core with deployment-specific assumptions.

P3PO core owns orchestration, authority, evidence, quality gates, learning rules, work-order state, feature contracts, and release policy.

A deployment adapter owns repositories, integrations, constraints, approved references, risk rules, acceptance checks, source precedence, and enabled specialist capabilities for that deployment.

## Isolation rule

The reusable core MUST NOT contain customer names, project names, brand rules, product copy, business facts, credentials, commerce data, or deployment-specific visual rules.

Those belong in deployment configuration or external systems referenced by the adapter.

A lesson may be promoted from deployment scope into core scope only when it is demonstrably reusable and has been stripped of deployment-specific information.

## Required adapter fields

Each deployment configuration must declare:

- `deploymentId`
- `displayName`
- `status`
- `repositories`
- `sourceSystems`
- `features`
- `specialists`
- `releasePolicy`
- `learningPolicy`
- `humanEscalation`

## Source-of-truth precedence

Each adapter must explicitly rank authoritative systems by data class. Agents may not silently choose between conflicting sources.

Typical classes include:

- source code
- operational/business data
- business facts
- design/approval references
- work-order state
- release evidence

If authoritative sources conflict and precedence is not defined, return `BLOCKED_SOURCE_CONFLICT`.

## Feature and specialist dependency rule

Existing bots, services, databases, or data systems are dependencies behind neutral adapter keys.

P3PO core must not be rewritten around a particular vendor, customer, project, table name, repository, or backend instance.

Examples:

- `inventory_backend`
- `source_control`
- `document_store`
- `commerce_backend`

Physical provider details belong in deployment configuration.

## Agent authority

Deployment adapters may narrow P3PO authority but may not broaden it.

For example, a deployment may prohibit automatic production deployment even if P3PO supports release automation.

## Portability target

A new customer or project should be bootstrappable by supplying:

1. a deployment configuration
2. source mappings and precedence
3. enabled feature modules
4. integration bindings
5. deployment-specific rules and acceptance checks

No P3PO core orchestration file should require customer-specific edits.
