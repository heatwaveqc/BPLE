# Lexical foundations

Status: accepted design requirements from decisions [0003](../docs/decisions/0003-token-roles.md), [0004](../docs/decisions/0004-lexical-profiles.md), [0005](../docs/decisions/0005-identifiers.md), [0006](../docs/decisions/0006-literals.md), and [0007](../docs/decisions/0007-speech-text.md). Exact token inventory, productions, profile schema, case normalization algorithm and escape syntax remain to be specified. Examples are illustrative unless explicitly stated as requirements.

## Universal token roles

A shared, language-independent conceptual inventory distinguishes structural keywords, identifiers, literals, operators, enclosure markers, separators, morphological role markers, and comments (non-executable lexical information). The canonical representation encodes role/concept and associated content, not the locale spelling. Internal identifiers for grammatical concepts remain stable within the specified compatibility contract. Numeric IDs and descriptive internal names are possible representations, not prescribed encodings.

Morphological role marking is optional wherever the token role is otherwise unambiguous. Where ambiguity requires a marker or delimiter, the source must provide it; the compiler must not infer intent heuristically. Profiles may employ different affixes, particles, or markers that normalize to the same universal roles. Marking cannot bypass reserved-word rules. See [enclosures](ENCLOSURES.md).

## Lexical profiles and boundaries

Profiles define versioned data mappings from localized and symbolic forms to universal grammatical concepts. Multiple aliases for one concept and multiword forms are permitted subject to deterministic recognition. Different concepts must not be indistinguishable in the same valid lexical context. No AI segmentation or semantic inference is needed to tokenize valid source.

A boundary between independently parsed word-form tokens must be explicitly identifiable. For languages normally written without spaces, require a delimiter: whitespace, a configured separator character, or a formally specified boundary-marking construction. Self-delimiting punctuation or quoted forms may establish boundaries where their distinct roles make this unambiguous. Adjacent unmarked word forms must not be segmented by guessing. A profile/user-configured delimiter must be validated and made part of the source parsing configuration, not an undocumented editor preference that changes the meaning of shared files. Exact delimiter repertoire, profile schema, recognition of multiword aliases, and escaping remain open.

## Source formats and localized editing

Two first-class source representations are supported by the compiler and tooling:

- **Canonical token-based source (default):** stores stable concept IDs and typed lexical payloads independently of any natural-language keyword spelling. The exact versioned, portable and diffable serialization remains to be designed. This is editable source, not compiled bytecode, an AST requirement or execution IR.
- **Localized plain-text source (opt-in):** stores source in a selected lexical profile; the compiler lexes it into the same canonical token model. Plain-text editing and compilation must not require a specialized IDE.

On opening or reading a file, the frontend recognizes its existing representation. The IDE edits and renders through the canonical token model, using the programmer's selected display/input profile regardless of the stored format, and supports live lexical/syntactic feedback. Changing the IDE language or default format does not silently convert, rename or retranslate an existing file. Save in the original representation, and for localized text retain the original source profile unless the user explicitly requests conversion; preserve identifiers, literals, comments and relevant source information. The IDE's configurable default applies to new files. Format switching is an explicit action.

Format recognition must be deterministic. Prefer an unambiguous format marker/version for canonical source and an explicit source-profile declaration or equivalent persisted metadata for plain text. Automatic language detection may suggest a profile, but must not silently choose between ambiguous interpretations. Both source representations use the `.bple` extension (recognize `.BPLE` and other case variants); the extension alone does not identify the stored representation or profile. See [decision 0008](../docs/decisions/0008-source-extension.md). Exact file markers, source-profile resolution precedence, versioning, handling of incomplete edits and cross-profile reserved-word collisions remain design work. A malformed canonical file must not silently fall back to localized text. See [decision 0004](../docs/decisions/0004-lexical-profiles.md).

## Identifiers

- Support Unicode identifiers across writing systems, starting from the Unicode identifier standard (UAX #31); define a versioned normalization and case-folding contract. Identifiers are case-insensitive and case-preserving: capitalization is presentation, not identity.
- Duplicate normalized bindings in the same scope must be diagnosed; scope/shadowing rules are a separate design topic. Warn about visually confusable names.
- Support multiword identifiers and optional morphological role marking. Written multiword names use single quotes, e.g. `let 'current health' be 100`. Single quotes delimit identifiers, not strings. Supply an equivalent reversible spoken form; exact escape and verbal syntax remain open.
- Reserved words are prohibited as identifiers; quoting or affixing does not turn reserved words such as English `while` into legal identifiers. A reserved-word check applies to the normalized whole identifier, including multiword keyword aliases; define the full reserved set, cross-profile collision behavior, and interop treatment in later design.
- A lexicon switch does not automatically translate user identifiers or literal payloads. Cross-profile collisions with a destination profile's reserved vocabulary must be surfaced and resolved explicitly; no silent renaming or change of binding identity.

Illustrative:

    let 'current health' be 100
    set 'current health' to 90
    let while be 5                 [invalid: reserved keyword]
    let 'while' be 5               [invalid: still reserved]

The surrounding declaration and assignment spelling is not yet standardized.

## Literals and escaping

Support conventional symbolic literal forms and deterministic localized verbal forms, including integers, decimal/scientific numeric notation, Boolean literals, and quoted text. The type system, numeric precision/range/conversion rules and eventual null/absence construct remain separate decisions. Localized number composition must have explicit lexical rules and distinguish numeric literals from expressions.

Written string literals use double quotes; verbal quotation must protect payload from keyword recognition. Preserve exact literal data, including capitalization, Unicode, line breaks, whitespace, punctuation and embedded delimiters. Do not translate or normalize the payload as part of switching lexical profiles. Written and verbal escaping/spelling must express arbitrary supported data, including the quotation terminator itself. Exact escapes and literal grammar remain open.

Illustrative:

    print "current health"
    print quote current health end quote

The latter only preserves the full value if the spoken form conveys the exact intended spelling and characters.

## Speech and text

Compact written form and fully speakable form are equally valid means of representing the same program. Every computationally meaningful element must have a lossless explicit spoken encoding, including grouping, boundaries, spelling, casing where data identity depends on it, punctuation, literal characters and escape forms. No program meaning may depend exclusively on visual formatting, vocal inflection or pause duration. Whitespace may act as a lexical separator without requiring visual indentation or pauses to carry unrecoverable semantics.

Idiomatic speech can be convenient but must not replace the canonical explicit encoding when accuracy requires spelling or disambiguation. A speech recognizer may report uncertainty; grammar and execution must not require guessing. Comments are non-executable information and have a spoken representation as well. Preserve comment content and source mapping in lossless editing/rendering workflows; exact layout/trivia storage is a tooling contract, not program semantics.

## Conformance plan

| Case | Required outcome |
|---|---|
| Unmarked unambiguous roles and equivalent explicitly marked roles | Same computational representation |
| Ambiguous unmarked token role | Diagnostic requiring disambiguation, not guessed parse |
| Equivalent profile aliases, multiword and symbolic spellings | Same concept IDs and preserved payload |
| No-space language with explicit configured delimiters | Deterministic recognition |
| Adjacent word forms lacking required boundaries | Reject/identify ambiguity; do not infer segmentation |
| Invalid delimiter/alias collision | Reject invalid configuration or ambiguous source |
| Unicode identifiers and case variants | Same normalized identity where specified, preserve display spelling |
| Duplicate normalized binding; confusable identifiers | Collision diagnostic; confusable warning where applicable |
| Single-quoted multiword identifier versus double-quoted text | Distinct token roles |
| Reserved word alone or quoted/marked as an identifier | Reject |
| Keyword inside literal payload | Preserve exact data; no keyword tokenization |
| Verbal and symbolic numbers | Equivalent literal values under the agreed type/number model |
| Arbitrary string characters, embedded quote terminators, Unicode and whitespace | Exact reversible representation |
| Spoken/written equivalents and explicitly spelled homophones | Round trip to equal computational information |
| Localized viewing of user names/literals | No implicit translation or semantic change |
| Both source representations with .bple/.BPLE extension | Recognize the content format independently; do not rename existing files |
| Canonical and localized source with equivalent tokens | Same parser input and semantics |
| Open/edit/save existing source in either format | Retain format and stored profile; preserve data and comments |
| Change IDE display/input profile or new-file default | Existing stored representation unchanged; explicit conversion only |
| Ambiguous source language or malformed canonical input | Diagnostic or explicit profile resolution; no silent reinterpretation |

All tests are planned; no executable lexer or conformance suite exists yet.
