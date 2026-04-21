# Adaptive Control Policy

This document defines how the Agent OS should adapt based on repository health metrics.

## Objective

Convert passive metrics into deterministic control actions.

## Core adaptation rules

### 1. Stale backlog pressure
If stale open PR count is high, the system should:
- label affected PRs with `analyst:workflow`
- add `pressure:stale-backlog`
- escalate oldest blocked PRs first

### 2. Retry pressure
If too many PRs are in retry state, the system should:
- pause low-priority dispatch
- label retrying PRs with `pressure:retry-surge`
- favor high-priority retries

### 3. Test failure concentration
If test-related failures dominate, the system should:
- add `tune:tests`
- comment that Codex test discipline should be tightened

### 4. Scope failure concentration
If scope-related failures dominate, the system should:
- add `tune:scope`
- increase human escalation for routing/boundary violations

### 5. Human escalation overload
If too many PRs require human review, the system should:
- add `pressure:human-overload`
- defer low-priority execution
- flag system health risk

## Adaptation principles

- Prefer labels and comments over hidden decisions
- Never auto-expand scope
- Never bypass safety gates
- Use priority to decide who gets helped first
- Keep actions deterministic and auditable
