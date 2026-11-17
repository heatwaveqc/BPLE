# Lexicon profiles

Profiles will map localized written and spoken lexical forms to stable language concepts under one Grammar version. Initial target languages: English (en), Mandarin (zh, script/variant choices pending) and Russian (ru). None is privileged.

The profile file format, alias rules, word boundaries, multiword matching, Unicode handling, verbal numbers, reserved words, identifier escaping, homophones, and canonical rendering are open design issues. A profile must never introduce independent semantic rules. Validate completeness, duplicate/ambiguous forms, reversible canonical rendering and profile/version compatibility. Use equivalent fixtures across profiles. No profile is certified merely because its words are translated.

Profiles will also provide versioned localized common-personal-name pools for optional humorous compiler-generated enclosure diagnostics (target: 1,000 names per profile). See [enclosures](../spec/ENCLOSURES.md) for licensing, provenance, disambiguation and numeric fallback requirements. These pools do not participate in parsing or semantics.

No production profiles or token inventory exist yet.
