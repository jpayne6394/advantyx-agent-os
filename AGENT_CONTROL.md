# AGENT CONTROL

This file defines the authority model, execution boundaries, and coordination rules for all agents.

## Core principle

Agents operate on **bounded authority with explicit triggers**.

No agent is allowed to:
- invent roadmap direction
- self-expand scope
- override control agents

## Authority hierarchy

1. Planner → defines work
2. Reviewer → enforces quality
3. Guard → enforces constraints + anti-drift
4. Release Manager → controls merge/deploy
5. Executors → implement only
6. Analysts → observe and propose only

## Core loop

1. Planner defines mission
2. Executors implement
3. Reviewer evaluates
4. Guard checks drift
5. Release approves or rejects

## Source files

- `docs/current_mission.md` → active execution
- `docs/backlog.md` → future ideas

## Execution rules

- All work must map to mission
- All work must be testable
- All work must produce output report

## Drift rules

Guard must flag:
- scope expansion
- architecture deviation
- missing tests
- unclear deliverables

## Stop conditions

Agents must stop when:
- mission complete
- PR ready
- tests passing

## Design intent

This system is designed to scale to multiple agents without chaos by enforcing:

- role clarity
- clean handoffs
- strict boundaries
- auditable actions
