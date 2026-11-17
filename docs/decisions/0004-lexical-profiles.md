# 0004 — Lexical profiles and explicit token boundaries

- Status: Accepted design requirements
- Date: 2026-11-17
- Backlog: L02 (resolved), [issue #4](https://github.com/heatwaveqc/BPLE/issues/4)
- Owner approval: lexical foundations review, 2026-11-17.

## Decision and rationale

Accept external versioned profile mappings with deterministic aliases and explicit identifiable word-token boundaries. In languages without spaces, require some delimiter; permit validated configurable spaces, characters or a formally specified marker construction. A user configuration must be reproducible and cannot silently change shared file parsing. Reject unrestricted or inferred word segmentation. Exact delimiter protocol and profile schema remain to be designed.

### Accepted — IDE, source selection and storage

The owner selected canonical token-based source as the default storage format, with opt-in localized plain-language files. The IDE uses a localized display/input layer above the canonical concept model, offering live parsing/feedback for either file representation. The frontend recognizes the existing format on read; ordinary saves retain it, including the stored profile for localized source. The IDE preference can change the default for new files; conversion of existing files must be explicit. Both formats compile without requiring the IDE.

This selects a dual-source architecture over localized-text-only storage, compulsory canonical files, or automatic conversion on save. Preserve identifiers, literal payloads, comments and source mapping across view changes. Prefer a portable, diffable, versioned canonical serialization, independent of execution IR. Deterministic format recognition and explicit source-profile metadata are recommended; assisted auto-detection must not guess when interpretations conflict. Specific markers/extensions, encoding, profile precedence, malformed/incomplete editing recovery, and destination keyword collisions remain design details for subsequent grammar/tooling work. Owner clarification, 2026-11-17: canonical default; opt-in regular text; live recognition; retain format on save; user-configurable IDE default.

## Axiom impact and conformance

I: any profile can map equivalent concepts; II–III: explicit boundaries and alias validation ensure deterministic meaning; IV: delimiter roles are speakable; V: profile/rendering does not alter execution. Verify no-space scripts, profile aliases and invalid delimiters; both source formats and IDE views require round trips, format-preserving saves, ambiguity/collision tests, and default-change isolation.

See [lexical foundations](../../spec/LEXICAL-FOUNDATIONS.md) for normative requirements and planned test cases. No executable verification has taken place.
