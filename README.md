# Advantyx Agent OS

AI-native operating system for structured software delivery, product analysis, and controlled execution.

This repo is seeded from the agent-control pattern already used in `james-river-dashboard` and expanded into a reusable multi-agent framework for future projects.

## Purpose

Advantyx Agent OS provides:

- mission-driven execution
- bounded role authority
- clean agent handoffs
- drift control
- auditable delivery
- reusable repo-level agent definitions

## Core model

The system is organized into four layers:

1. **Control**
   - Planner
   - Reviewer
   - Guard
   - Release Manager
2. **Execution**
   - Backend Engineer
   - Frontend Engineer
   - Data Engineer
   - QA Engineer
3. **Analysis / Improvement**
   - Business Analyst
   - Workflow Analyst
   - Drift Analyst
   - Technical Innovator
4. **Program files**
   - `AGENT_CONTROL.md`
   - `docs/current_mission.md`
   - `docs/backlog.md`
   - `.github/agents/`

## Source of truth

- `AGENT_CONTROL.md` defines the operating model, authority, and constraints.
- `docs/current_mission.md` is the only file that active executors should implement against.
- `docs/backlog.md` holds future work and ideas.
- `.github/agents/` contains repo-scoped agent definitions.

## Initial bootstrap goal

The first milestone for this repo is to serve as a reusable base for:

- new product repos
- migration repos
- delivery teams with planner-reviewer-guard-release flow
- issue-driven worker execution with analyst support

## Working rules

- Do not execute backlog directly.
- Do not let worker agents define product direction.
- Prefer small, testable steps.
- Require completion reports.
- Treat Guard as the anti-drift authority.
- Treat Reviewer as quality authority.
- Treat Planner as sequencing authority.

## Next step

Read `AGENT_CONTROL.md`, then refine `docs/current_mission.md` for the first real build-out of the agent department.
