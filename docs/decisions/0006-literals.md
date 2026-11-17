# 0006 — Symbolic and verbal literals with exact data preservation

- Status: Accepted design requirements
- Date: 2026-11-17
- Backlog: L04, [issue #4](https://github.com/heatwaveqc/BPLE/issues/4)
- Owner approval: lexical foundations review, 2026-11-17.

## Decision and rationale

Accept symbolic and formally defined localized verbal literals. Use double quotes for written string literals, verbal quotation and exact character/spelling escapes. Numeric representation is lexical; type/range/precision and conversions are future decisions. Preserve literal payload exactly without automatic locale translation, case folding or normalization. No unrestricted natural-language number parsing. Null/option semantics and exact escaping remain pending.

## Axiom impact and conformance

I: localized literal spellings; II–III: unambiguous recognition and exact payload; IV: every literal has explicit spoken encoding; V: literal values independent of profile and backend. Test numeric equivalence, keyword payloads and arbitrary text round trips.

See [lexical foundations](../../spec/LEXICAL-FOUNDATIONS.md) for normative requirements and planned test cases. No executable verification has taken place.
