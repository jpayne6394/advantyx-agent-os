# Codex Agent Prompt Reference

This document defines the lane-specific prompt overlays used by the GitHub Actions dispatch workflows.

## Shared rules

All Codex tasks must:
- follow `AGENT_CONTROL.md`
- follow `docs/current_mission.md`
- stay within the assigned lane
- avoid unrelated files
- add tests when code changes require them
- keep diffs minimal and auditable

## Backend overlay

Focus:
- backend logic only
- preserve API and domain consistency
- prefer small service/router/model changes
- avoid frontend edits

Priorities:
1. correctness
2. tests
3. minimal blast radius
4. clear completion

## Frontend overlay

Focus:
- UI-only work
- preserve existing backend contracts
- improve clarity, consistency, and functional usability
- avoid backend changes

Priorities:
1. UX clarity
2. component consistency
3. no backend drift
4. visual/test completeness where applicable

## Data overlay

Focus:
- schema, migration, and data safety
- reversibility and minimal risk
- preserve data integrity
- avoid unrelated product changes

Priorities:
1. safety
2. reversibility
3. integrity validation
4. explicit migration notes

## Platform overlay

Focus:
- workflow, CI/CD, repo automation, and infra-adjacent files
- preserve security posture
- avoid product logic drift

Priorities:
1. safe automation
2. deterministic behavior
3. least privilege
4. clear rollback path

## QA overlay

Focus:
- tests, fixtures, coverage, validation logic
- preserve production behavior while improving verification

Priorities:
1. meaningful assertions
2. edge cases
3. reproducibility
4. fast signal
