# Advantyx Agent OS

AI-native operating system for idea development, structured planning, prompt generation, and controlled autonomous execution.

## Purpose

Advantyx Agent OS is the separate system repo for:

- broad product and workflow thinking
- deciding what to build next
- converting rough edits into precise technical prompts
- budgeting and sequencing work
- creating execution tasks automatically
- enforcing retry, drift, and budget controls

It is not tied to a single product repo.
It exists to help plan and build many product repos.

## Core operating loop

1. **Strategist** converts rough goals into scoped work
2. **Planner** selects funded tasks under budget rules
3. **Prompt Engine** converts tasks into precise technical execution packets
4. **Executor** performs bounded implementation work
5. **Verifier / Guard** stops drift, loops, and unsafe execution
6. **Reporter** records outcomes and next steps

## Core files

- `AGENT_CONTROL.md`
- `docs/current_mission.md`
- `docs/backlog.md`
- `docs/agvantix-core-phase1-budget-spec.md`
- `.github/planner/`
- `.github/executor/`
- `.github/workflows/planner.yml`
- `.github/workflows/executor-ops.yml`

## Source of truth

- `AGENT_CONTROL.md` defines operating law
- `docs/current_mission.md` defines what the system is building now
- `docs/backlog.md` holds future ideas and extensions
- planner and executor folders contain runnable control logic

## Working rules

- Prefer bounded work units
- Never spend the full daily budget
- Stop after repeated failures
- Do not let one task consume the entire day
- Use autonomous execution only inside explicit scope
- Keep product repos separate from Advantyx itself

## Initial platform objective

Make Advantyx Agent OS the reusable autonomous builder layer that can:

- take broad direction
- plan the next sprint
- generate precise execution tasks
- run bounded autonomous implementation safely
- produce reviewable pull requests
