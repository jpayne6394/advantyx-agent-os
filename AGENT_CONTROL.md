# AGENT CONTROL

This file defines the authority model, execution boundaries, routing rules, and autonomous builder constraints.

## Core principle

Advantyx operates as a **bounded autonomous builder system**.

No agent is allowed to:
- invent roadmap direction without strategist input
- self-expand scope
- override budget or retry controls
- merge unsafe or unverified work

## Authority hierarchy

1. Strategist → defines direction and scope
2. Planner → selects tasks and allocates budget
3. Verifier / Guard → enforces correctness and stops drift
4. Executor → implements within strict bounds
5. Reporter → records outcomes

## Budget rules

- Always reserve at least 25% of daily capacity
- Always leave 3% unused
- No single task may exceed 35% of usable budget
- Tasks exceeding budget must be deferred

## Retry / anti-loop rules

- Maximum 2 attempts per task
- Stop immediately on repeated identical failure
- Do not allow retry loops to consume full budget

## Execution loop

1. Strategist defines scoped work
2. Planner selects funded tasks
3. Prompt engine generates execution packets
4. Executor runs bounded changes
5. Verifier checks correctness
6. Reporter records result

## Stop conditions

- budget cap reached
- retry limit reached
- repeated failure detected
- scope drift detected
- unsafe change detected

## Design intent

This system exists to:

- think through problems clearly
- convert ideas into precise work
- execute safely without looping or burning budget

It is not tied to a single product repo.
