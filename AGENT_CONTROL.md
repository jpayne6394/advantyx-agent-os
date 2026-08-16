# P3PO AGENT CONTROL

This file defines the authority model, execution boundaries, routing rules, merge policy, feature boundaries, and learning controls for P3PO.

## Core principle

Agents operate on **bounded authority with explicit triggers**.

No agent may:
- invent roadmap direction
- self-expand scope
- override control agents
- approve its own implementation
- enable optional business features without deployment configuration
- merge changes that have not satisfied policy
- promote customer-specific knowledge into core memory without generalization

## Authority hierarchy

1. Supervisor / Planner → defines work, priority, and execution lane
2. Reviewer → validates implementation quality and completeness
3. Guard → enforces scope, architecture, policy, and anti-drift rules
4. Release Controller → determines release readiness and merge eligibility
5. Executors → implement only within assigned work orders
6. Analysts / Specialists → observe, diagnose, or operate only within enabled capabilities

## Core autonomous loop

1. Supervisor classifies the task and creates a bounded work order
2. Routing policy assigns one primary lane
3. Executor implements within lane boundaries
4. Reviewer validates code quality, tests, and deliverables
5. QA independently checks acceptance criteria and evidence
6. Guard validates scope, architecture, and policy compliance
7. Release Controller determines release eligibility
8. Material defects or successful patterns are evaluated for durable learning

## Product isolation

P3PO core files must remain company-neutral.

Customer or project deployments belong behind adapter/configuration boundaries and must not introduce customer names, brand rules, business facts, customer-only repository paths, or customer-specific data assumptions into core orchestration.

A project may narrow P3PO authority but may not broaden it.

## Optional feature policy

Business capabilities such as Inventory Intelligence, Content Operations, SEO Operations, or Analytics are modules, not core assumptions.

- modules are disabled by default unless deployment configuration enables them
- module code must depend on a capability interface, not a customer system name
- physical backends are referenced through neutral integration keys
- disabling a module must not break core work-order, QA, learning, or release functions

## Source files

- `docs/current_mission.md` → active P3PO product work
- `docs/backlog.md` → future ideas
- `docs/project-adapter-contract.md` → deployment boundary
- `docs/work-order-contract.md` → executable work standard
- `docs/learning-system.md` → learning and defect memory
- `docs/feature-module-contract.md` → optional capability standard
- `.github/agent-routing.yml` → lane assignment and merge strategy
- `.github/workflows/agent-routing.yml` → PR labeling and route detection
- `.github/workflows/auto-merge.yml` → autonomous merge gate

## Routing rules

Routing is determined by the strongest matching lane from changed paths, work-order metadata, and labels.

Core lanes:
- `agent:backend`
- `agent:frontend`
- `agent:data`
- `agent:qa`
- `agent:platform`

Feature specialists may be routed only when the relevant deployment feature is enabled.

If multiple lanes match, Supervisor or Guard must collapse the work order to one primary lane before merge or explicitly authorize a bounded multi-lane mission.

## Execution rules

- all implementation must map to an active work order
- all work must be testable or explain why a deterministic test is impossible
- all work must produce an evidence-backed completion report
- executors may only work inside authorized repositories, paths, integrations, and capabilities
- discovered unrelated work becomes backlog, not opportunistic scope expansion

## Reviewer and QA rules

Reviewer and QA must confirm:
- implementation matches the work order
- acceptance criteria were evaluated
- tests exist or the no-test reason is explicit
- required evidence exists
- changes are internally coherent
- protected behavior did not regress

Executor completion is a claim, not acceptance.

## Guard rules

Guard must flag:
- scope expansion
- architecture deviation
- missing tests or evidence
- unclear deliverables
- cross-lane drift without authorization
- customer-specific leakage into core
- unauthorized feature enablement
- merge policy mismatch

## Learning rules

Material failures must enter the defect/lesson process.

- first occurrence: record and correct
- second occurrence: add regression protection or document why automation is impossible
- third occurrence: Guard performs process-level review and tightens controls
- customer-specific lessons remain deployment-scoped unless generalized
- no invisible self-tuning may be the sole learning mechanism

## Autonomous merge policy

### Preferred mode
Use GitHub native auto-merge when repository settings allow it and branch protection rules require checks and/or reviews.

### Fallback mode
If native auto-merge is unavailable, release automation may merge directly only when all required policy gates are satisfied, including:
- PR is not draft
- routing lane is resolved
- reviewer/QA requirements pass
- Guard requirements pass
- required release label or work-order state is present
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
- `qa:fail`
- `needs-human`
- `do-not-merge`
- `routing:unresolved`

## Stop conditions
Agents must stop when:
- work order is complete
- PR/evidence package is ready for the next independent gate
- policy outcome is reached
- an unresolved source conflict or authorization boundary is reached

## Human escalation
Human escalation is mandatory when:
- routing is unresolved
- security/compliance risk is identified
- destructive or production-risking change is proposed without standing authorization
- required credentials/authorization are missing
- authoritative sources conflict without precedence
- maximum correction cycles are exhausted

## Design intent

P3PO is designed to scale across organizations without chaos by enforcing role clarity, portable configuration, strict feature boundaries, auditable evidence, independent verification, deterministic routing, and explicit operational learning.
