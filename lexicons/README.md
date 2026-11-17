# Lexicon profiles

Profiles will map localized written and spoken lexical forms to stable language concepts under one Grammar version. Initial target languages: English (en), Mandarin (zh, script/variant choices pending) and Russian (ru). None is privileged.

The [lexical foundations](../spec/LEXICAL-FOUNDATIONS.md) establish deterministic aliases, explicit word-token boundaries (including configurable delimiters for no-space scripts), Unicode/case-insensitive identifiers, reserved words, and reversible written/spoken forms. The exact profile file format, delimiter/alias matching, normalization, verbal number grammar, reserved vocabulary, escapes, homophones, and canonical rendering remain to be specified. Canonical token-based source is the default, with first-class opt-in localized text; IDE display/input profiles are independent of storage, and ordinary saves retain the existing representation. See [decision 0004](../docs/decisions/0004-lexical-profiles.md). A profile must never introduce independent semantic rules. Validate completeness, duplicate/ambiguous forms, reversible canonical rendering and profile/version compatibility. Use equivalent fixtures across profiles. No profile is certified merely because its words are translated.

Profiles will also provide versioned localized common-personal-name pools for optional humorous compiler-generated enclosure diagnostics (target: 1,000 names per profile). See [enclosures](../spec/ENCLOSURES.md) for licensing, provenance, disambiguation and numeric fallback requirements. These pools do not participate in parsing or semantics. The filename seeds deterministic alias allocation; names are released when an enclosure closes and may be reused in non-overlapping regions.

No production profiles or token inventory exist yet.
