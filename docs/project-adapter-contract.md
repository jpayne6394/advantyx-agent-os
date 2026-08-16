# Project Adapter Contract

## Purpose

Project adapters connect Advantyx Agent OS to a specific product without contaminating the reusable core with product-specific assumptions.

The core owns orchestration, authority, evidence, quality gates, learning rules, work-order state, and release policy.

A project adapter owns product-specific repositories, integrations, constraints, approved references, risk rules, acceptance checks, and specialist dependencies.

## Isolation rule

The reusable core MUST NOT contain project names, brand rules, product copy, business facts, credentials, commerce data, or project-specific visual rules.

Those belong under `projects/<project-id>/` or in external systems referenced by the adapter.

A lesson may be promoted from project scope into core scope only when it is demonstrably reusable across projects.

## Required adapter fields

Each `projects/<project-id>/project.json` must declare:

- `projectId`
- `displayName`
- `status`
- `primaryRepository`
- `executionRepositories`
- `sourceSystems`
- `specialists`
- `releasePolicy`
- `learningPolicy`
- `humanEscalation`

## Source-of-truth precedence

Each adapter must explicitly rank authoritative systems by data class. Agents may not silently choose between conflicting sources.

Example classes:

- source code
- commerce data
- business facts
- visual approvals
- work-order state
- release evidence

If two sources conflict and precedence is not defined, return `BLOCKED_SOURCE_CONFLICT`.

## Specialist dependency rule

Existing project-specific bots, services, or data systems are treated as dependencies behind an adapter boundary.

The Agent OS core must not be rewritten around them.

If a dependency cannot be positively identified, the adapter may register it as `unresolved` and use it only after discovery.

## Agent authority

Project adapters may narrow core authority but may not broaden it.

For example, a project may prohibit automatic production deployment even if the core release system supports it.

## Portability target

A new project should be bootstrappable by copying only:

1. the adapter template
2. the project's rules and source mappings
3. required specialist bindings

No core orchestration file should require product-specific edits.