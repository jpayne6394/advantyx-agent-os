# AGENT CONTROL

This file defines the authority model, execution boundaries, routing rules, and merge policy for all agents.

## Core principle

Agents operate on **bounded authority with explicit triggers**.

No agent is allowed to:
- invent roadmap direction
- self-expand scope
- override control agents
- merge changes that have not satisfied policy

## Authority hierarchy

1. Planner → defines work and selects the execution lane
2. Reviewer → enforces implementation quality and completeness
3. Guard → enforces constraints, anti-drift, and scope fidelity
4. Release Manager → controls merge mode and release readiness
5. Executors → implement only within assigned lane
6. Analysts → observe, diagnose, and propose only

## Core autonomous loop

1. Planner classifies the task
2. Routing policy assigns the execution lane
3. Executor implements within lane boundaries
4. Reviewer validates code quality, tests, and deliverables
5. Guard validates scope, architecture, and anti-drift rules
6. Release Manager chooses merge method and approves auto-merge eligibility

## Source files

- `docs/current_mission.md` → active execution
- `docs/backlog.md` → future ideas
- `.github/agent-routing.yml` → lane assignment and merge strategy
- `.github/workflows/agent-routing.yml` → PR labeling and route detection
- `.github/workflows/auto-merge.yml` → autonomous merge gate

## Routing rules

Routing is determined by the strongest matching lane from changed paths and labels.

Current lanes:
- `agent:backend`
- `agent:frontend`
- `agent:data`
- `agent:qa`
- `agent:platform`

If multiple lanes match, Planner or Guard must collapse the mission to one primary lane before merge.

## Execution rules

- All work must map to mission
- All work must be testable
- All work must produce output report
- Executors may only work inside their assigned lane unless mission explicitly authorizes cross-lane work

## Reviewer rules

Reviewer must confirm:
- implementation matches mission
- tests exist or the no-test reason is explicit
- deliverables are complete
- changes are internally coherent

## Guard rules

Guard must flag:
- scope expansion
- architecture deviation
- missing tests
- unclear deliverables
- cross-lane drift without authorization
- merge policy mismatch

## Autonomous merge policy

### Preferred mode
Use GitHub native auto-merge when repository settings allow it and branch protection rules require checks and/or reviews.

### Fallback mode
If native auto-merge is unavailable, the release workflow may merge directly only when all of the following are true:
- PR is not draft
- routing lane is resolved to exactly one primary lane
- `review:pass` label is present
- `guard:pass` label is present
- `automerge` label is present
- no blocking labels exist

### Merge method policy
- frontend/UI heavy work → `squash`
- backend/domain logic work → `squash`
- data/migration or generated-history-sensitive work → `rebase`
- docs/meta-only work → `squash`
- mixed or ambiguous work → `squash`

## Blocking labels
Any of the following must block merge:
- `guard:fail`
- `review:fail`
- `needs-human`
- `do-not-merge`
- `routing:unresolved`

## Stop conditions
Agents must stop when:
- mission complete
- PR ready
- policy outcome reached

## Human escalation rule
nHuman involvement is minimized, but escalation is mandatory when:
- routing is unresolved
- a PR spans multiple primary lanes without explicit mission approval
- security/compliance risk is identified
- a destructive migration or production-risking change is proposed

## Design intent

This system is designed to scale to multiple agents without chaos by enforcing:

- role clarity
- clean handoffs
- strict boundaries
- auditable actions
- deterministic routing
- policy-based autonomous merging
