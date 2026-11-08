# Element Card — fill guide

How to fill [the blank card](../templates/element-card-template.md), which documents
**any single element of a system**. One element, one card, one file — that is the
atom. [The examples](../examples/) show one finished card at each level.

**Self-similarity is the mechanism.** Every element carries every field. A field
that does not apply is written `n/a` — the key is never deleted. Any two cards
read side by side, and a missing line means an unfinished card rather than a
different schema.

---

## Properties

| Property | Values | Notes |
|---|---|---|
| `title` | free text | human-readable name, e.g. `af/design — Design Stage` |
| `icon` | an emoji | a convention, not required |
| `type` | `element-card` | fixed |
| `status` | `draft` \| `final` | the only two statuses |
| `description` | one sentence | what this element is, for search |
| `domain` | free text | e.g. `ai-systems` |
| `element_id` | see *Naming* | the stable key everything joins on |
| `kind` | `unit` \| `script` \| `artefact` \| `spec` | |
| `level` | `system` \| `factory` \| `stage` \| `skill` | `kind: unit` only, else `n/a` |
| `parent` | an `element_id` | `n/a` for the top-level system card only |
| `grading_class` | `deliverable` \| `bulk` \| `n/a` | stable word; the rules behind it live in the gate catalogue, so the card does not change when a rule does |
| `created` · `updated` | ISO date | convention |
| `tags` | list | convention |

## Naming (`element_id`)

Path-like, lowercase, no spaces. This is the key run records, gate bindings and
any census of elements join on — chosen once, never edited.

| kind | pattern | real examples |
|---|---|---|
| unit · system | `system/<name>` | `system/harness` |
| unit · factory | `<factory>` | `kf` · `af` · `gov` |
| unit · stage | `<factory>/<stage>` | `af/design` · `gov/decide` |
| unit · skill | `skill/<name>` | `skill/architect` |
| script | `script/<filename>` | `script/generate_index.py` |
| artefact | `artefact/<filename>` | `artefact/VAULT_INDEX.json` |
| spec | `spec/<filename>` | `spec/gate-catalogue.md` |

`parent` is the element that contains or owns it — `af/design` → `af`;
`script/generate_index.py` → `system/harness`; an artefact's parent is its **sole
writer**, so `artefact/VAULT_INDEX.json` → `script/generate_index.py`.

---

## Which sections carry a value, by kind

`req` = a real value · `n/a` = write it, do not delete the heading ·
`opt` = fill when true

| Section | unit | script | artefact | spec |
|---|---|---|---|---|
| `## Job` | req | req | req | req |
| `## Input → Output` | req | req | req | req |
| `## Owner / Halt Point` | req | req | req | req |
| `## Contract` | opt | req | req | req |
| `## Gate` | req | req | req | opt |
| `## Examples` | req | n/a | opt | n/a |
| `## Auto-fix` | req | req | n/a | n/a |
| `## Log` | req | req | opt | n/a |
| `## Drift Compare` | req | n/a | n/a | n/a |

One rule explains the whole table: **`Examples`, `Drift Compare` and
`grading_class` belong only to elements that produce judgeable output.** A script
is deterministic, an artefact is a container, a spec is a rule — none are graded,
so the measurement vector does not apply to them.

**One exception, for `Examples` only.** An artefact that is
*rendered output a human judges* — such as a diagram, a report or a
decision record — may carry `## Examples` (`opt`), holding
promoted exemplars of good output. A container such as a JSON manifest, an index
or a log may not. `Drift Compare` and `grading_class` stay `n/a` for every
artefact: exemplars show the standard, they do not make the artefact graded.

---

## Section guidance

**Job** — mission and purpose merged, one line. If it needs two, it is probably
two elements.

**Input → Output** — the handoff boundary. For an artefact, read it as *what is
written into it → what reads it*. For a spec, *what it governs → who must follow
it*.

**Owner / Halt Point** — the position on the autonomy slider, not a person's
name. Where does a human approve? For passive kinds: who may change this, and
under what gate.

**Contract** — the invariants that must hold for the element to be correct,
independent of any single run. Distinct from `Gate`: the gate is *checked at an
event*, the contract is *always true*. This is where a script's guarantees and
an artefact's schema live.

**Gate** — catalogue check ids with their event bindings for deterministic
checks, rubric dimensions for judgment ones. Never copy hook configuration into
a card: hooks are harness machinery configured once, and the card states *which
catalogue checks bind to which events*.

**Examples** — promoted, never authored. Seed three once a pattern has
repeated at least three times; the per-run improvement loop matures the set to 5–10. At factory level these are
worked releases compared by *property*, not similarity.

**Auto-fix** — *simple* means a deterministic check with a mechanical remedy,
capped at 1–2 retries and always logged. Everything else escalates. Silent
self-healing is forbidden: it starves the improvement loop of the signal it
exists to read.

**Log** — four bullets, always in this order. **Run record** says where the
element's runs are recorded; **EVAL_LOG** says what a run meant; **Git** says a run
happened; **When** says at which moment the element logs. Only the factory root
writes EVAL_LOG. Only run-bracketing levels (system, factory) touch git.

**Drift Compare** — state the comparison and where the result is routed. A drift
result is a trigger routed to eval, **never a verdict** — exemplar similarity is
a weak signal in both directions.

---

## Worked example — a passive element

`artefact/element-card`, the card that describes cards, filled to show what `n/a`
looks like in practice:

```markdown
---
title: Element card — the card that describes cards
icon: 🃏
type: element-card
status: draft
description: One card per element of the system on a fixed schema, where a missing line means an unfinished card.
domain: ai-systems
element_id: artefact/element-card
kind: artefact
level: n/a
parent: system/harness
grading_class: n/a
created: 2026-08-02
updated: 2026-11-08
tags:
  - governance
---
## Job
Document any single element of the system on one schema, so that any two elements
can be read side by side.

## Input → Output
An element of the system (a unit, script, artefact or spec) → one card file → read
by the human, by governance when auditing coverage, and by run records and gate
bindings that join on `element_id`.

## Owner / Halt Point
Human-authored from the blank. The schema itself may only change through governance.

## Contract
- One element, one card, one file.
- Every card carries every field. A field that does not apply is written `n/a`; the
  key is never deleted.
- `element_id` is the join key — chosen once, never edited.

## Gate
No catalogue id.

## Examples
n/a — artefacts are containers, not graded output.

## Auto-fix
n/a

## Log
- **Run record** — pair of git audit commits + a health report
- **EVAL_LOG** — none
- **Git** — tracked
- **When** — n/a

## Drift Compare
n/a

## Links
- Parent: `system/harness`
- Blank: `templates/element-card-template.md`
```

---

## Links
- [Blank card](../templates/element-card-template.md)
- Examples: [system](../examples/1-system-harness.md) · [factory](../examples/2-factory-kf.md) · [stage](../examples/3-stage-kf-capture.md) · [skill](../examples/4-skill-gem-extraction.md)
