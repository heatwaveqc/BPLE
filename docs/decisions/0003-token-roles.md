# 0003 — Canonical token roles and optional morphology

- Status: Accepted design requirements
- Date: 2026-11-17
- Backlog: L01, [issue #4](https://github.com/heatwaveqc/BPLE/issues/4)
- Owner approval: lexical foundations review, 2026-11-17.

## Decision and rationale

Accept shared token classes: structural keywords, identifiers, literals, operators, enclosure markers, separators, morphological markers and non-executable comments. Canonical concept identity is independent of natural-language spelling. Prefer optional morphological marking over mandatory markers for every token or unconstrained contextual inference. Require explicit disambiguation where necessary. Exact token IDs and role spellings are not selected.

## Axiom impact and conformance

Axioms I–II: profiles map forms to common roles, without ambiguous recognition. III and V: role markers cannot change meaning of equivalent syntax or execution. IV: all meaningful forms require spoken equivalents. Test marked/unmarked equivalence and ambiguous role rejection.

See [lexical foundations](../../spec/LEXICAL-FOUNDATIONS.md) for normative requirements and planned test cases. No executable verification has taken place.
