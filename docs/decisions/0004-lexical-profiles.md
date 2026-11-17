# 0004 — Lexical profiles and explicit token boundaries

- Status: Accepted design requirements (source selection and storage proposal remains pending)
- Date: 2026-11-17
- Backlog: L02 (partially resolved), [issue #4](https://github.com/heatwaveqc/BPLE/issues/4)
- Owner approval: lexical foundations review, 2026-11-17.

## Decision and rationale

Accept external versioned profile mappings with deterministic aliases and explicit identifiable word-token boundaries. In languages without spaces, require some delimiter; permit validated configurable spaces, characters or a formally specified marker construction. A user configuration must be reproducible and cannot silently change shared file parsing. Reject unrestricted or inferred word segmentation. Exact delimiter protocol and profile schema remain to be designed.

### Pending proposal — IDE, source selection and storage

The owner proposed IDE-localized rendering and entry normalized to concept IDs, and is considering automatic source-language detection or an explicit top-of-file flag for text editing. Recommended but not yet accepted: separate IDE display/input profile from source decoding profile; allow localized human-readable on-disk text, with an explicit profile declaration or equivalent project/file metadata, plus a compiler default for unbound input. Detection may assist and suggest a profile, but must not silently choose among interpretations; resolve and persist the choice before reproducible builds. Investigate an optional portable canonical token-based text serialization for multilingual collaboration; do not require a specialized IDE. Maintain user-defined names and literal payloads, source mapping and comments. Profile version, precedence, declaration syntax, canonical serialization, destination keyword collisions and editing recovery are unresolved. A canonical format must be diffable and must not be confused with the execution IR. Keep L02 open for explicit owner approval of selection/storage policy.

## Axiom impact and conformance

I: any profile can map equivalent concepts; II–III: explicit boundaries and alias validation ensure deterministic meaning; IV: delimiter roles are speakable; V: profile/rendering does not alter execution. Verify no-space scripts, profile aliases and invalid delimiters; eventual IDE mode requires round trips and ambiguity/collision tests.

See [lexical foundations](../../spec/LEXICAL-FOUNDATIONS.md) for normative requirements and planned test cases. No executable verification has taken place.
