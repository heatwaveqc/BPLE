# Pending design decisions

The original 40 review topics are retained with their stable IDs: the completed lexical batch (5 topics) and seven reorganized pending batches (35 topics). The owner approved this order after the adoption of Axiom VI. GitHub issue checklists are the source of truth for topic status. Existing issues #5–#11 are repurposed as revised trackers; their original scopes are preserved for historical context. Batch numbers below refer to the revised sequence, not the original lexical-first numbering.

| Revised batch | Tracker | Topic IDs | Priority |
|---|---|---|---|
| Completed lexical foundations | [#4](https://github.com/heatwaveqc/BPLE/issues/4) | L01–L05 | Accepted requirements |
| 1 — Extension architecture | [#5](https://github.com/heatwaveqc/BPLE/issues/5) | G01, G05, A05, R05, P01 | Primary |
| 2 — Fundamental grammar | [#6](https://github.com/heatwaveqc/BPLE/issues/6) | G02, G03, G04, E04, E05 | Primary |
| 3 — Expressions and type foundations | [#7](https://github.com/heatwaveqc/BPLE/issues/7) | E01, E02, E03, T01, T02 | Primary |
| 4 — Computational structures | [#8](https://github.com/heatwaveqc/BPLE/issues/8) | F01, F02, F03, F04, T03 | Primary |
| 5 — Runtime architecture | [#9](https://github.com/heatwaveqc/BPLE/issues/9) | T04, A01, R01, R02, R03 | Primary |
| 6 — Advanced language modules | [#10](https://github.com/heatwaveqc/BPLE/issues/10) | T05, F05, A02, A03, A04 | Later detail |
| 7 — Ecosystem and tooling | [#11](https://github.com/heatwaveqc/BPLE/issues/11) | R04, P02, P03, P04, P05 | Later detail |

Five accepted, 25 primary review topics, 10 later-detail review topics at reorganization. No original topic is deleted: Axiom VI removes forced exclusivity in some proposed alternatives, but the shared extension contracts and sensible standard defaults remain design work. Later-detail topics remain required for the mature standard distribution, not optional user prerequisites. Bring forward blockers such as host feasibility, licensing, module security or necessary standard capabilities.

## Workflow

1. Start with the earliest unresolved batch (revised batch 1 is next; lexical foundations complete); read the actual issue and existing [decision register](README.md), relevant [research survey](../research/MAINSTREAM-GRAMMAR-SURVEY.md), and [constitution](../../spec/AXIOMS.md).
2. Present up to five related questions with viable alternatives, examples, tradeoffs, a recommended option and all six axiom implications, including candidate extension interfaces and configurable features. Avoid treating sample spellings or implementation preferences as adopted grammar rules.
3. Record the owner's actual approval, rejection, or explicit deferral; give each accepted decision an ADR number using [the template](TEMPLATE.md). Record dependencies and planned conformance cases; integrate accepted normative changes into the standard.
4. Link the decision record(s) and PR on the issue before checking items off. Close the batch only after all five topics have a disposition; deferred items stay visible in linked follow-up issues. Do not close pending items merely because they have been discussed.
5. If a dependency needs earlier review, bring it forward explicitly. In particular, a bounded host/IR feasibility experiment can run independently once approved; licensing must be resolved before distribution or third-party dataset redistribution. Overlapping decisions are allowed; cite the same ADR on all resolved topics rather than duplicating standards. Split overly broad topics into follow-ups without losing the five-at-a-time discussion cadence.

Axiom VI is a cross-cutting requirement for every batch; the first revised batch addresses grammar composition, representation, dependency metadata, extension interfaces and compatibility; later batches apply these contracts to the standard language and tooling. See [ADR 0009](0009-extensibility-axiom.md). No extra checklist topics are implied.

See [standard installation](0010-standard-installation.md) for the owner-approved baseline experience.

Previously accepted decisions remain in the register; lexical foundations 0003–0007 are resolved at the requirements level. The enclosure work in G04/G05 concerns their remaining syntax and implementation choices, not re-voting on already adopted requirements. No implementation or additional normative design approval follows from creating a backlog.
