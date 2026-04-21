# Self-Tuning Prompt Policy

This document defines how Codex prompts adapt based on repository health labels.

## Purpose

Convert adaptive-control labels into deterministic prompt changes for execution and retry workflows.

## Tuning labels

### `tune:tests`
Effect:
- increase test discipline
- require explicit edge-case coverage
- require verification focus before completion

### `tune:scope`
Effect:
- tighten scope boundaries
- emphasize file-lane containment
- discourage opportunistic cleanup or refactor work

## Pressure labels

### `pressure:retry-surge`
Effect:
- bias toward minimal targeted fixes
- avoid broad rewrites
- prioritize fast stabilization

### `pressure:stale-backlog`
Effect:
- prefer smallest complete fix
- reduce exploratory changes
- finish bounded work quickly

### `pressure:human-overload`
Effect:
- avoid escalation-triggering behavior
- stay strictly within mission and lane
- prioritize deterministic, reviewable diffs

## Prompt adaptation principles

- Labels change prompts, not safety rules.
- Prompt tuning must never bypass tests, guard, or merge controls.
- Tuning is per-PR and auditable through labels and comments.
