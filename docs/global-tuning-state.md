# Global Tuning State

This file stores persistent cross-run tuning signals for the Agent OS.

It is updated automatically by `.github/workflows/global-tuning.yml`.

## Purpose

Track repeated system-level patterns across runs and convert them into stable default prompt adjustments.

## Fields

- dominant_failure_mode
- test_failure_count
- scope_failure_count
- quality_failure_count
- human_escalation_count
- retry_surge_count
- stale_backlog_count
- recommended_default_tuning
- last_updated

## Current state

```yaml
dominant_failure_mode: none
test_failure_count: 0
scope_failure_count: 0
quality_failure_count: 0
human_escalation_count: 0
retry_surge_count: 0
stale_backlog_count: 0
recommended_default_tuning: []
last_updated: not_set
```
