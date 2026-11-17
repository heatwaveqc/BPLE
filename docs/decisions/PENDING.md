# Pending design decisions

The initial backlog comprises 40 review topics, grouped into eight batches of five. This is a prioritized discussion agenda, not 40 accepted design decisions or a promise of a fixed implementation sequence. Stable topic IDs in the issues are separate from sequential decision-record IDs. The source of truth for pending/disposed status is the issue checklists; do not copy or maintain duplicate status here.

| Batch | Pending discussion / tracker | Topic IDs |
|---|---|---|
| 1 | [Lexical foundations](https://github.com/heatwaveqc/BPLE/issues/4) | L01–L05 |
| 2 | [Structural grammar](https://github.com/heatwaveqc/BPLE/issues/5) | G01–G05 |
| 3 | [Expressions and bindings](https://github.com/heatwaveqc/BPLE/issues/6) | E01–E05 |
| 4 | [Types and data](https://github.com/heatwaveqc/BPLE/issues/7) | T01–T05 |
| 5 | [Functions and control flow](https://github.com/heatwaveqc/BPLE/issues/8) | F01–F05 |
| 6 | [Abstraction and reliability](https://github.com/heatwaveqc/BPLE/issues/9) | A01–A05 |
| 7 | [Runtime and engineering](https://github.com/heatwaveqc/BPLE/issues/10) | R01–R05 |
| 8 | [Ecosystem and release](https://github.com/heatwaveqc/BPLE/issues/11) | P01–P05 |

## Workflow

1. Start with the earliest unresolved batch (batch 1 resolved; batch 2 is next); read the actual issue and existing [decision register](README.md), relevant [research survey](../research/MAINSTREAM-GRAMMAR-SURVEY.md), and [constitution](../../spec/AXIOMS.md).
2. Present up to five related questions with viable alternatives, examples, tradeoffs, a recommended option and all six axiom implications, including candidate extension interfaces and configurable features. Avoid treating sample spellings or implementation preferences as adopted grammar rules.
3. Record the owner's actual approval, rejection, or explicit deferral; give each accepted decision an ADR number using [the template](TEMPLATE.md). Record dependencies and planned conformance cases; integrate accepted normative changes into the standard.
4. Link the decision record(s) and PR on the issue before checking items off. Close the batch only after all five topics have a disposition; deferred items stay visible in linked follow-up issues. Do not close pending items merely because they have been discussed.
5. If a dependency needs earlier review, bring it forward explicitly. In particular, a bounded host/IR feasibility experiment can run independently once approved; licensing must be resolved before distribution or third-party dataset redistribution. Overlapping decisions are allowed; cite the same ADR on all resolved topics rather than duplicating standards. Split overly broad topics into follow-ups without losing the five-at-a-time discussion cadence.

Axiom VI is a cross-cutting requirement for every batch; G01/G05 should address extensible grammar and representation, R05 the module API and composition, and P01/P03/P04 compatibility, distribution and tooling. See [ADR 0009](0009-extensibility-axiom.md). No extra checklist topics are implied.

Previously accepted decisions remain in the register; lexical foundations 0003–0007 are resolved at the requirements level. The enclosure work in G04/G05 concerns their remaining syntax and implementation choices, not re-voting on already adopted requirements. No implementation or additional normative design approval follows from creating a backlog.
