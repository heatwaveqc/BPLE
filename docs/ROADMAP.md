# Roadmap

Status: project inception. No implementation milestones have been completed.

| Stage | Deliverable | Exit criteria |
|---|---|---|
| 0 — Foundation | Naming, axioms, governance and repository scaffold | Baseline documents integrated; open decisions recorded |
| 1 — Language kernel design | Formal lexical model, grammar notation, minimal semantics and speech encoding | Accepted decisions; unambiguous grammar cases and cross-profile examples |
| 2 — Proof of concept | Tiny lexer/parser and evaluator | Variables, literals, simple arithmetic, output and control flow as agreed; positive/negative executable tests |
| 3 — Multilingual parity | Initial English, Mandarin and Russian profiles | Shared canonical tokens/AST, round-trip checks, collisions and Unicode cases |
| 4 — General-purpose core | Functions, collections, modules, types, errors and object/functional features as approved | Versioned specification and shared conformance suite |
| 5 — Execution parity | Interactive runner, runtime compilation and standalone native executable experiment | Verified same program semantics on supported modes; Windows target exercise |
| 6 — Tooling | Formatter, diagnostics, editor/debugging, libraries and packaging | Repeatable toolchain and documented interoperability |
| 7 — Speech interface | Spoken renderer and grammar-aware input | Lossless canonical round trips; recognition and ambiguity handling tests |

Stages are dependency guidance, not fixed dates. Prototype critical cross-profile and speech risks early, not only at stage 7. A completed proposal is not a completed implementation; a merged feature is not automatically a tested release.

## Next work

Agree on the smallest viable lexical and grammatical kernel: token classes, statement/phrase boundaries, literals and identifiers, language-profile structure, and reversible speech. Compare alternative designs before selecting specific words. Decide the first implementation host and target using a bounded prototype. See [decision register](decisions/README.md) and the [pending design discussion backlog](decisions/PENDING.md), organized in batches of five.
