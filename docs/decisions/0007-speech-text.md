# 0007 — Lossless spoken and written representation

- Status: Accepted design requirements
- Date: 2026-11-17
- Backlog: L05, [issue #4](https://github.com/heatwaveqc/BPLE/issues/4)
- Owner approval: lexical foundations review, 2026-11-17.

## Decision and rationale

Accept compact written and expanded verbal representations, lossless computational round trips, canonical explicit disambiguation/spelling, speakable comments, and no meaning available exclusively through visual formatting, pauses or inflection. Delimiters/separators may be whitespace or symbolic so long as meaningful boundaries have spoken equivalents. Speech recognition remains an adapter, not a semantic oracle. Exact spoken syntax and layout/comment serialization remain future tooling and grammar design.

## Axiom impact and conformance

I–II: shared normalized representation with profile-local renderings; III: no guessing about program meaning; IV: explicit speech/text round trips; V: execution independent of source surface. Test ambiguous pronunciation, arbitrary literal spelling, comments and token boundary equivalence.

See [lexical foundations](../../spec/LEXICAL-FOUNDATIONS.md) for normative requirements and planned test cases. No executable verification has taken place.
