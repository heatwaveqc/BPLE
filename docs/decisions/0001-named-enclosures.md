# 0001 — Named grammatical enclosures and generated identifiers

- Status: Accepted (design requirements; concrete syntax remains open)
- Date: 2026-11-17
- Owner approval: owner proposed named delimiters using a Japanese-style suffix, approved optional named/anonymous enclosures and explicitly requested compile-time identifier generation with numeric and humorous localized common-name modes.
- Depends on: [0000](0000-foundation.md)

## Problem

Conventional interchangeable delimiters make deeply nested structures difficult to read, dictate, and diagnose. Anonymous grouping is convenient but diagnostics such as "expected end group" fail to identify exactly which group is implicated.

## Decision

Adopt optional explicit names on grammatical enclosures, including expression grouping and statement/block enclosures. Named enclosures use matching names; unnamed symbolic and verbal forms remain available. Every recognized enclosure, including anonymous ones, receives a unique compiler-internal identity and an explicit diagnostic label during frontend processing, early enough to diagnose malformed source. Names are structural metadata, not runtime identifiers or control-transfer labels.

Support ordinary numeric generated labels and an optional humorous rendering using the 1,000 most common personal names for the selected lexical language profile. The name list is profile data, not grammar. Numeric labels remain available for exhaustion, invalid/conflicting names, or unsupported profile data. Exact name ranking, locale selection, data licensing, morphology, deterministic allocation, and presentation configuration are pending design/implementation. See [enclosure requirements](../../spec/ENCLOSURES.md) for the accepted behavioral contract and remaining questions.

## Alternatives considered

- Anonymous punctuation/keywords only: familiar but difficult to distinguish in nested diagnostics.
- Mandatory names: clear but excessive ceremony for short expressions.
- Optional names without generated identities: improves explicitly named source only.
- Optional names with compiler-assigned identity: preserves convenience while making diagnostics precise; selected.
- Random humorous names: not selected as a requirement; reproducible diagnostic identity is preferred.

## Axiom compatibility

1. Vocabulary: delimiter role and diagnostic identity are canonical; localized morphology and name pools are data.
2. Grammar: matching is deterministic, properly nested, and explicitly validated; direction ambiguity must be settled by formal rules.
3. Meaning: naming or renaming a well-formed enclosure does not alter program semantics.
4. Speech/text: every delimiter role/name and numeric fallback needs lossless verbal encoding.
5. Execution: identities are frontend metadata; backends share semantics regardless of label or rendering option.

## Verification and follow-up

The standard records requirements and illustrative examples, not final productions. Future tests must cover matching, mismatches, collisions, incomplete anonymous structures, mode/locale fallback and semantic parity. Implementation, profile data and executable tests do not yet exist.
