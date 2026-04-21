# Multi-Repo Rollout Plan

This document defines how to apply the Agent OS system across multiple repositories.

## Objective

Make Agent OS reusable, portable, and consistent across products.

## Core concept

Agent OS becomes a **control layer**, not tied to one repo.

## Step 1: Standardize labels

All repos must share:
- agent:* (routing)
- priority:*
- failure:*
- pressure:*
- tune:*
- queue:*
- merge:*

## Step 2: Workflow package

Copy these workflows into each repo:

- codex-dispatch.yml
- retry-execution.yml
- auto-merge.yml
- priority queue workflows
- adaptive-control.yml
- global-tuning.yml
- metrics-dashboard.yml

## Step 3: Repo configuration layer

Each repo adds:

- domain mapping file
- risk classification rules
- mission templates

## Step 4: Central monitoring (optional but recommended)

Create a separate repo:

`advantyx-agent-control`

This repo aggregates:
- metrics across repos
- failure patterns
- global tuning signals

## Step 5: Versioning

Agent OS should be versioned:

- v1: base system
- v2: adaptive + tuning
- v3: multi-repo + centralized control

## Step 6: Bootstrap checklist

Each new repo must:

1. copy workflows
2. define domain paths
3. set label schema
4. verify CI passes
5. run first controlled mission

## Step 7: Isolation rules

Each repo must remain independent:

- no cross-repo file changes
- no shared state without explicit control repo

## Success criteria

- system runs identically across repos
- failures are predictable and manageable
- rollout requires minimal manual effort
