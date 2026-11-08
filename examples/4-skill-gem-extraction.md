---
title: skill/gem-extraction — the conversation capture path
icon: 💎
type: element-card
status: draft
description: Identifies vault-worthy gems produced during a conversation and routes each — new candidate, one-line refinement, or exclude. The only capture path whose source is a chat rather than a document.
domain: ai-systems
element_id: skill/gem-extraction
kind: unit
level: skill
parent: kf/capture
grading_class: n/a
created: 2026-08-03
updated: 2026-11-08
tags:
  - knowledge-factory
  - role/process
---
## Job
Identify vault-worthy "gems" produced during a conversation and **route each
one** — new candidate · one-line refinement on an existing note · exclude.

It exists because the most valuable output of a working session is usually
generated *in* the session and lost with it: no document holds it, so no other
capture path can see it.

## Input → Output
A substantive conversation → entries in the candidates folder, **or** a
one-line refinement appended to an existing concept.

## Owner / Halt Point
**Conversation-scoped, not index-first** — so the index-freshness gate does not
apply. The agent proposes; the **human reviews candidates downstream** at
`kf/process`. Nothing it writes enters the vault proper without that pass.

## Contract
- **Three routes, and "exclude" is a real outcome** — most of a conversation is
  not vault-worthy, and a skill that never excludes is producing noise.
- **A refinement is one line.** If it needs more, it is a candidate, not a
  refinement.
- **It does NOT fire** for coding, drafting, sanity-check, or short (< 20-message)
  chats. The trigger discipline is what keeps the candidates folder reviewable.
- Output is **proposed, never promoted** — candidates sit in that folder
  until the human moves them.
- A gem must be something the conversation actually
  established, not a plausible-sounding generalisation of it.

## Gate
**Routing discipline** — candidate vs refine vs exclude, and the trigger
conditions above. No catalogue id: this skill produces raw feedstock, which is
graded downstream at `kf/process` by `GATE-KF-01`.

## Examples
Prior candidates: gems that existed only in a
conversation and would otherwise have been lost.

## Auto-fix
n/a — a misrouted gem is corrected by the human at review, not mechanically.

## Log
- **Run record** — pair of git audit commits + a health report
- **EVAL_LOG** — none
- **Git** — none of its own
- **When** — per invocation

## Drift Compare
n/a — feeds raw feedstock, which is not exemplar-graded.

## Links
- Parent: [kf/capture](3-stage-kf-capture.md) (this skill backs that engine)
- Children: n/a
- Produces: `artefact/inbox-note` (via the candidates folder)
- Carrying Decision: Factory-Unit Documentation Standard (in the author's system, not included)
- Gate rules: the author's gate catalogue (not included)
