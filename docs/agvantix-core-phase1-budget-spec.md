# Agvantix Core — Phase 1 Budget Allocation & Sprint Optimization

## Purpose
Define a deterministic system for:
- selecting sprint work
- allocating daily budget
- controlling execution cost

This layer ensures Advantyx operates as a disciplined execution system, not an uncontrolled agent loop.

## Core Components

### 1. Sprint Optimizer
Selects the best set of tasks for a sprint based on:
- value
- cost
- dependencies
- execution risk

Objective:
Maximize delivered value under sprint budget constraints.

### 2. Budget Allocator
Allocates daily usable budget across sprint tasks.

Responsibilities:
- enforce daily budget caps
- reserve emergency capacity
- preserve an unspent daily buffer
- prioritize tasks deterministically

### 3. Budget Guard
Enforces execution discipline in real time.

Rules:
- stop on budget cap breach
- stop on retry limit
- stop on scope expansion
- require re-scoring on overrun

## Task Model
Each task must include:
- value_score
- urgency_score
- strategic_score
- dependency_score
- risk_score
- complexity_score
- estimated_cost
- retry_risk
- repo_risk

## Scoring Formula
Adjusted Value =
(value * 0.30) +
(strategic * 0.25) +
(urgency * 0.20) +
(dependency * 0.15) +
(confidence * 0.10)

Cost Burden =
(cost * 0.55) +
(retry_risk * 0.25) +
(repo_risk * 0.20)

Efficiency Score = Adjusted Value / Cost Burden

## Daily Budget Allocation
1. Reserve budget
2. Lock 3% leftover buffer
3. Fund blockers and unlockers
4. Rank remaining tasks by efficiency score
5. Allocate until budget exhausted
6. Enforce single-task max share

## Task Stop-Loss
Each task must define:
- daily_cap
- sprint_cap
- max_attempts

Execution must stop when limits are hit.

## Sprint Composition Rules
- include blockers when present
- include at least two small high-confidence tasks when available
- limit large tasks
- limit high-risk tasks

## Outcome
This system ensures:
- predictable execution
- controlled cost
- stable sprint delivery
- no runaway agent loops
