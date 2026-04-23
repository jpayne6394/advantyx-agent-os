# CURRENT MISSION

## Objective

Build the core autonomous planner + executor system for Advantyx Agent OS.

## Scope

- implement deterministic planner
- implement budget allocation rules
- implement retry / anti-loop controls
- implement executor workflow
- enable issue → execution → PR loop

## Constraints

- must respect budget rules
- must enforce retry limits
- must prevent infinite loops
- must keep work bounded

## Deliverables

- working planner system
- working executor system
- GitHub workflows for automation
- ability to generate and execute tasks

## Success criteria

- planner selects tasks correctly
- executor stops on failure conditions
- system does not burn full budget
- system produces reviewable changes
