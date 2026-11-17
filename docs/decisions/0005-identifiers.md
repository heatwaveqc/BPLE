# 0005 — Unicode, case-insensitive and quoted identifiers

- Status: Accepted design requirements
- Date: 2026-11-17
- Backlog: L03, [issue #4](https://github.com/heatwaveqc/BPLE/issues/4)
- Owner approval: lexical foundations review, 2026-11-17.

## Decision and rationale

Accept Unicode identifiers, case-insensitive identity with case-preserving display, optional role markers, explicit multiword names and confusable warnings. Written quoted names use single quotes, e.g. `'current health'`; reserve double quotes for strings. Unlike the previous review proposal, reserved keywords such as `while` must not be usable as identifiers, even if quoted or morphologically marked. The recommended interpretation is whole-name matching against normalized reserved forms, not substring prohibitions. Exact keyword sets, normalization/folding algorithm, escapes and cross-profile/interop collision handling remain open.

## Axiom impact and conformance

I: Unicode supports diverse scripts; II–III: normalized identity and reservation rules prevent ambiguity; IV: case-insensitive names and explicit delimiting/spelling permit speech; V: names bind consistently across modes. Test case collisions, multiword names, quoted reserved words and exact literal/identifier distinction.

See [lexical foundations](../../spec/LEXICAL-FOUNDATIONS.md) for normative requirements and planned test cases. No executable verification has taken place.
