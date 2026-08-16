# Learning and Defect Memory

## Objective

Make the Agent OS improve from completed work without pretending that model weights are retrained by each run.

The system learns operationally by converting observed outcomes into durable rules, regression checks, playbooks, routing changes, and escalation thresholds.

## Learning record

Every material failure or unusually successful pattern should create a learning record with:

- `learningId`
- `projectId`
- `scope`: `project` or `core`
- `type`: `defect`, `success-pattern`, `decision`, `risk`
- `area`
- `observedBehavior`
- `rootCause`
- `correction`
- `preventiveRule`
- `regressionProtection`
- `firstObservedWorkOrder`
- `recurrenceCount`
- `status`

## Failure-to-control loop

When QA or Release detects a material defect:

1. record the defect
2. identify the cause when evidence supports one
3. correct the active work order
4. add or strengthen a deterministic check where possible
5. update the relevant project rule or playbook
6. track recurrence
7. promote a project lesson into core only when it is product-independent

A defect is not considered fully learned merely because it was fixed once.

Preferred terminal state: `prevented-by-control`.

## Recurrence rules

- first occurrence: record + correction
- second occurrence of same class: mandatory regression protection or explicit reason why automation is impossible
- third occurrence: route to Guard for process-level review and tighten executor instructions
- repeated human escalations of the same type: create a decision rule or require a durable project decision record

## Success-pattern learning

Learning also records processes that reliably reduce defects or correction cycles.

A success pattern may become a playbook when:

- it succeeds across at least two comparable work orders, or
- a human explicitly approves it as the project standard

## Metrics

Track at minimum:

- first-pass QA rate
- correction cycles per work order
- defect recurrence rate
- defects converted to regression protection
- human escalations by class
- average age of blocked work
- false-done rate: executor completion reports later rejected by QA

## No hidden tuning

Adaptive changes must be visible in repository state, labels, rules, tests, or versioned configuration.

Do not rely on invisible prompt mutation as the only learning mechanism.