# Card, Check, Loop

**A worked example of how to document an AI system and its factories, so that every element can be read the same way.**

Introduction Video: https://www.youtube.com/watch?v=X5_JfXsu_8s

A better prompt fixes one workflow. It cannot keep twenty aligned. Card, Check, Loop is the framework around the workflows: how each one is defined, checked and improved, and how a new one joins without starting from zero.

> This repository is an **example**, not a tool and not a standard. It shows the documentation: a blank card, the guide for filling it in, and real cards from a working system, one at each level. It enforces nothing by itself; the video explains why the checks belong in your tools.

---

## 1. The framework

- **Card: what each part is.** The same card works at every level: a skill, a stage, a factory, and the system. It gives the element its purpose, what goes in and what comes out, who owns it, the checks it must pass, worked examples, what it may fix by itself, and a log of its measures.
- **Check: what each step must pass.** Prevent, stop and signal, applied at every step and enforced by the tools. A new rule is one check, written once, and every station that names it applies it.
- **Loop: what makes the next run better.** One improvement loop runs over every factory, so a mistake found in one factory becomes a check in all of them.

## 2. What is here

| Path | What it is |
|---|---|
| [`templates/element-card-template.md`](templates/element-card-template.md) | The blank card |
| [`docs/element-card-guide.md`](docs/element-card-guide.md) | How to fill every field, and which fields apply to which kind of element |
| [`examples/1-system-harness.md`](examples/1-system-harness.md) | A card at **system** level |
| [`examples/2-factory-kf.md`](examples/2-factory-kf.md) | A card at **factory** level: the Knowledge Factory |
| [`examples/3-stage-kf-capture.md`](examples/3-stage-kf-capture.md) | A card at **stage** level: its Capture engine |
| [`examples/4-skill-gem-extraction.md`](examples/4-skill-gem-extraction.md) | A card at **skill** level: the skill behind Capture |

Read the four examples in order: each card names the one above it as its `parent`.

## 3. Document your own system

1. List your elements: the system, each factory, each stage, each skill.
2. Copy the blank card once per element, and give each a permanent `element_id`.
3. Fill every field using the guide. If a field does not apply, write `n/a` and keep the heading, so a missing line always means an unfinished card.
4. Name the checks each element must pass in `## Gate`, then make your tools run them.

## 4. Reading the examples

The cards are real, from the author's own system, with private references removed. They mention things that are not in this repository: gate ids such as `GATE-KF-01`, other elements such as `af` (an application factory) and `gov` (governance), and the vault (the author's knowledge base). Treat those as illustrations of what your own cards would name. The Knowledge Factory itself is public at [Brunimir/Knowledge-Factory](https://github.com/Brunimir/Knowledge-Factory).

All example cards are `status: draft`, and part of this card schema is still being settled in the author's own system.

## License

Card, Check, Loop by Bruno Bodson is licensed under [CC BY 4.0](LICENSE).
