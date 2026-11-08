---
title: kf/capture — the loading dock
icon: 🚚
type: element-card
status: draft
description: Engine 1 of the Knowledge Factory — get every idea in with zero friction, so no idea is lost because filing it felt like a chore.
domain: ai-systems
element_id: kf/capture
kind: unit
level: stage
parent: kf
grading_class: n/a
created: 2026-08-03
updated: 2026-11-08
tags:
  - knowledge-factory
  - role/process
---
## Job
Get every idea in with zero friction — never lose an idea because filing it felt
like a chore.

## Input → Output
Shower thoughts · reading notes · NotebookLM extractions · AI gem propositions →
one inbox note in the processing inbox (or an Idea in the ideas folder).

## Owner / Halt Point
**Human.** The loading dock is a human act — the agent never decides what is
worth capturing. The gem-extraction skill may *propose* candidates into
a separate candidates folder, but promotion into the pipe is the human's.

## Contract
- **The folder is the status.** A note advances by being moved, not by a field:
  to read → stock → processing inbox → (processed bin). Only the processing inbox is
  read by `kf/process`, and only it is scanned by the indexer.
- **An inbox file is never deleted.** Processed originals move
  to the processed bin, which is why that folder counts as evidence, not derived output.
- Capture has **no quality bar by design** (see Gate). Sorting and validation
  happen downstream.
- *Cheap* applies to the thinking, never to the frontmatter: an Idea missing
  `description`/`domain`/`created`/`updated` fails `GATE-KF-01` and is invisible
  to every index-first command. A capture the index cannot see has not been
  captured.
- An agent may fetch a genuinely missing source and retain it with the sources. The
  human halt point is unchanged: nothing downstream trusts an agent-fetched source
  more than a human-collected one.

## Gate
**Readiness, not quality.** A note entering the processing inbox must be **understandable by someone else,
written in plain language, and carry the required structural fields**. That is a
bar on *legibility*, not on correctness — it asks "can this be processed?", never
"is this good?". Judging the idea here would reintroduce the friction the engine
exists to remove.

`GATE-KF-01` is the first *content* gate, and it fires downstream at
`kf/process` — or immediately on an Idea note, which is indexed on write.

**Review-time, not capture-time — the retroactive half.** `GATE-KF-13`/
`GATE-KF-14` fire *before* the agent, blocking a fabrication from ever becoming
a note. A fidelity ledger is the counterpart
that closes the loop on everything captured *before* those gates existed, or
that passed them but still drifted: `GATE-KF-15` catches a source-location breadcrumb
naming the wrong document; `GATE-KF-16` catches an `Example` presented as fact
against a source too thin to plausibly contain it.
Both are lints, not blocks — they run on-demand against notes that already
exist, so there is nothing left to prevent, only to find and fix.

## Examples
Ideas exemplifying "an unproven hypothesis, cheaply held, written as if for
someone else": a minimum viable Idea of a few hundred characters · a best-formed
one with its origin and declared boundaries · an evidence-first one that opens on
a measured discrepancy rather than an argument.

## Auto-fix
n/a — nothing to repair; a malformed capture is triaged by the human, not
patched.

## Log
- **Run record** — pair of git audit commits + a health report
- **EVAL_LOG** — none (rolls up into the `kf` entry)
- **Git** — none of its own (rides the run bracket)
- **When** — at stage entry/exit

## Drift Compare
n/a — raw feedstock is not exemplar-graded.

## Links
- Parent: [kf](2-factory-kf.md) · next `kf/process` *(first engine — no prev)*
- Children: [skill/gem-extraction](4-skill-gem-extraction.md)
- Produces: `artefact/inbox-note` · `artefact/idea-note`
- Reads and sometimes writes: `artefact/source-file`
- Carrying Decision: Factory-Unit Documentation Standard (in the author's system, not included)
- Gate rules: the author's gate catalogue (not included)
