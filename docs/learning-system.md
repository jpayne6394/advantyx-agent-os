# P3PO Learning and Defect Memory

## Objective

Make P3PO improve from completed work without pretending model weights are retrained by each run.

P3PO learns operationally by converting observed outcomes into durable rules, regression checks, playbooks, routing changes, feature safeguards, and escalation thresholds.

## Learning scopes

- `core` — generic rules safe to reuse across deployments
- `tenant` — organization-wide rules that remain private to one deployment/customer
- `project` — project-specific rules and history

Customer-specific information never becomes core memory unless it is generalized and stripped of identifying or business-specific details.

## Learning record

Every material failure or unusually successful pattern should record:

- learning ID
- scope
- deployment/project reference
- type: defect, success-pattern, decision, or risk
- area
- observed behavior
- root cause when supported by evidence
- correction
- preventive rule
- regression protection
- first observed work order
- recurrence count
- status

## Failure-to-control loop

When QA, Guard, or Release detects a material defect:

1. record the defect
2. determine root cause when evidence supports one
3. correct the active work order
4. add or strengthen a deterministic check where possible
5. update the relevant deployment rule or playbook
6. track recurrence
7. promote only generalized lessons into core

A defect is not considered fully learned because it was fixed once.

Preferred terminal state: `protected`, meaning a repeat is blocked or reliably detected by control.

## Recurrence rules

- first occurrence: record and correct
- second occurrence of same class: mandatory regression protection or explicit reason automation is impossible
- third occurrence: Guard performs a process-level review and tightens routing, acceptance, or executor controls
- repeated human escalations of the same type: create a durable decision rule where safe

## Success-pattern learning

A process may become a reusable playbook when:

- it succeeds across at least two comparable work orders, or
- an authorized human explicitly approves it as a standard

## Required metrics

Track at minimum:

- first-pass QA rate
- correction cycles per work order
- defect recurrence rate
- defects converted to regression protection
- human escalations by class
- average age of blocked work
- false-done rate: executor completion claims later rejected by independent QA
- feature-specific defect rates when optional modules are enabled

## No hidden tuning

Adaptive changes must be visible in versioned rules, database state, labels, tests, playbooks, or configuration.

Invisible prompt mutation cannot be the sole learning mechanism.
