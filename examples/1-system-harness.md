---
title: system/harness — the harness
icon: ⚙️
type: element-card
status: draft
description: Runs any prompt through planification and per-step execution, with context assembled fresh each run.
domain: ai-systems
element_id: system/harness
kind: unit
level: system
parent: n/a
grading_class: n/a
created: 2026-11-08
updated: 2026-11-08
tags:
  - role/process
---
## Job
Run any prompt through planification → per-step execution, with context assembled
fresh each run.

## Input → Output
Prompt → verified deliverable.

## Owner / Halt Point
Human at decide and ship; the agent plans and executes between.

## Contract
n/a

## Gate
Catalogue references and event bindings, for example `GATE-KF-02` (index freshness).

## Examples
n/a — worked examples live at factory level.

## Auto-fix
Hook feedback: a failing hook returns its message and the agent retries. A retry
breaker stops a run on an outage it cannot fix.

## Log
- **Run record** — pair of git audit commits + a health report
- **EVAL_LOG** — none (evals belong to the factory that ran)
- **Git** — open and close audit commits bracket each run
- **When** — at run launch and close

## Drift Compare
Measured drift per period (slow loop).

## Links
- Parent: n/a
- Children: [kf](2-factory-kf.md) · `af` · `gov`
- Carrying Decision: Factory-Unit Documentation Standard (in the author's system, not included)
- Gate rules: the author's gate catalogue (not included)
