# P3PO

P3PO is a reusable agent operations platform for controlled project delivery, business operations, verification, release management, and continuous operational learning.

P3PO is company-neutral by design. Customer or project names, business rules, repositories, data sources, and optional capabilities are configured outside the reusable core.

## Core capabilities

- bounded agent authority
- supervisor-driven work orders
- independent QA and review
- guardrails and anti-drift controls
- evidence-backed release gates
- durable project state
- defect and lesson memory
- reusable playbooks
- integration adapters
- optional business feature modules

## Core layers

1. **Control**
   - Supervisor / Planner
   - Reviewer
   - Guard
   - Release Controller
2. **Execution**
   - engineering agents
   - data agents
   - QA agents
   - configurable specialists
3. **Learning**
   - defects
   - lessons
   - regression protections
   - success playbooks
   - recurrence metrics
4. **Integrations**
   - source control
   - databases
   - business systems
   - document systems
   - custom adapters
5. **Optional features**
   - Inventory Intelligence
   - Content Operations
   - SEO Operations
   - Analytics
   - customer-defined modules

## Product isolation rule

The P3PO core must contain no customer names, customer-specific business facts, private repositories, brand rules, or customer-only logic.

Development and customer deployments attach through configuration and adapters. A customer-specific lesson may be promoted to the core only after it is generalized and stripped of customer-specific information.

## Source of truth

- `AGENT_CONTROL.md` — authority and operating policy
- `docs/project-adapter-contract.md` — external project/deployment boundary
- `docs/work-order-contract.md` — executable work contract
- `docs/learning-system.md` — operational learning model
- `docs/feature-module-contract.md` — optional capability boundary
- `docs/current_mission.md` — active P3PO product work
- `docs/backlog.md` — future product work
- `.github/agents/` — reusable agent definitions

## Development backend

P3PO may use an existing development database or service while the product is being built. Physical backend names are not product identity and must be hidden behind neutral integration keys.

The initial development inventory backend is connected only through the `inventory_backend_dev` adapter and can be replaced without changing P3PO core behavior.

## Working rules

- Executors do not approve their own work.
- Optional modules are disabled by default unless a deployment enables them.
- Do not execute backlog directly.
- Prefer bounded, testable work orders.
- Require evidence for completion.
- Convert repeated defects into deterministic controls.
- Never let customer-specific logic leak into the reusable core.
