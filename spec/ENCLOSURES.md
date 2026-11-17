# Enclosures and diagnostic identities

Status: accepted design requirements under [decision 0001](../docs/decisions/0001-named-enclosures.md). Exact written and spoken forms, formal productions and allocation algorithm are pending. Examples are illustrative, not runnable source.

## Enclosure requirements

- A grammatical enclosure groups a nested region, such as an expression, argument region or statement block. Its grammatical kind and its identity are separate.
- Enclosures may be explicitly named or anonymous. Anonymous symbolic and verbal delimiters remain legitimate forms where supported by the eventual grammar.
- Explicit names must match at the opening and closing boundary. Simultaneously open explicit enclosures cannot share a name. Enclosures must properly nest; overlapping/crossing closures are rejected. Name equality and normalization will follow an explicitly specified lexical contract.
- Names are structural metadata, not bindings, values, runtime control-transfer labels or library-defined grammar. Consistent renaming or removing a name while preserving enclosure kind and contents does not change program semantics.
- A profile may mark arbitrary enclosure names with an unambiguous affix, particle or equivalent morphology. Japanese-inspired suffix notation such as -san is illustrative, not a reserved universal spelling. Profile-specific morphology must normalize to common token roles.
- Identical open/close markers are permitted only if the formal grammar determines direction unambiguously; if that cannot be guaranteed, specify distinct directional markers. Do not silently guess from indentation, pauses, or a matching name alone. The grammar must define statement boundaries independently; not every statement needs a named enclosure.

Illustration:

    while project is not complete Kevin-san
        for each task in project Susan-san
            call execute task
        Susan-san
    Kevin-san

Expression alternatives (same intended semantic grouping):

    (a + b) * c
    group a plus b end group times c
    sum-san a plus b sum-san times c

## Compiler-generated identities

Every enclosure receives a unique internal structural identifier within the relevant compilation unit, irrespective of its spelling. Explicit labels are retained; anonymous enclosures get generated diagnostic labels. Allocate identity when an opening construct is recognized in the frontend (including compile, check, interpret or runtime compilation paths), rather than only after successful parsing. Malformed/unclosed enclosures must have identities too whenever their openings are identifiable. Where no opener can be identified, report the actual unexpected token and source location; do not fabricate a matching opener.

Generated labels are metadata in the token/parse/source-map pipeline. They do not rewrite user source, change evaluation or become runtime symbols. Compilers and diagnostic tools must preserve the originating source span. Diagnostics should report the enclosure identity, kind, opening location, offending closing token/location where present, and expected closure. When reporting both expected and encountered enclosures, distinguish their identities, even if they are anonymous and of the same kind.

### Numeric rendering (ordinary mode)

Use explicit numeric labels for anonymous enclosures, e.g. group #1, group #2. A deterministic encounter-order allocator is a proposed initial strategy; exact algorithm and stability across source edits are not finalized. Same source, specification, profile and settings should produce reproducible labels. Internal identities must remain distinct across explicit and generated labels; diagnostics include an internal disambiguator or source location if display names collide.

Illustrative diagnostic for a missing close in nested anonymous grouping:

    Unclosed group #2 (opened at line 2, column 5).
    Expected the closing delimiter for group #2 before end of input.
    Enclosing group: #1 (opened at line 1, column 1).

For a crossing named close:

    Expected Susan-san (enclosure #2), encountered Kevin-san (enclosure #1).
    Close Susan-san before Kevin-san.

### Localized common-name rendering (humorous mode)

Provide an opt-in diagnostic presentation assigning anonymous enclosures personal names drawn from a versioned, ranked pool of the 1,000 most common names for the active lexical language profile. Use language-appropriate names, not an English list for every profile. A name such as Kevin-san or Susan-san is only an example, not a researched ranking. The compiler's canonical identities remain numeric or equivalent stable unique keys; humorous names are presentation aliases.

The profile owns its name pool as data. Source and locale/region, population/time period, normalization, ranking tie-breaks and redistribution license must be documented; no fabricated popularity data. The definition of "most common" remains open. Humorous allocation uses the source filename as its deterministic pseudorandom seed; for the same filename, source, versioned pool and configuration, names must reproduce across platforms. Use a specified portable hash/PRNG rather than implementation-dependent process hashing. The precise filename normalization (including whether a logical relative path disambiguates identical basenames), unnamed-input seed, generator and allocation algorithm remain open. Renaming a file may change display names but not its meaning.

Allocate aliases from the pool for simultaneously active nested enclosures only; release aliases when their enclosures close so later non-overlapping enclosures may reuse names. No total-per-file consumption of the pool. Active generated aliases must be distinct; avoid collision with active explicit names or provide an unambiguous numeric disambiguator. If missing/incomplete pool data, unsuitable names or collisions exhaust available aliases at a supported depth, use numeric fallback. Historical diagnostics referencing reused names must retain their unique internal identity and source span. Never use the finite name list as a program-size or nesting constraint; the separate excessive-nesting policy below is independent of naming. Numeric identities/source spans remain available in all modes. Diagnostic rendering cannot depend on availability of external services.

Example of the same anonymous-closure diagnostic in name mode:

    Unclosed Susan-san (group #2, opened at line 2, column 5).
    Expected the closing delimiter for Susan-san before end of input.
    Enclosing group: Kevin-san (#1).

Humorous naming is a diagnostic/display option, not a source requirement. A future formatter may optionally render generated labels as named source where that transformation preserves token roles and semantics; automatic source edits are not part of compilation.

## Excessive nesting: the Kevin Limit

A dedicated compile-time diagnostic is required when genuine syntactic enclosure depth exceeds 1,000 simultaneously open containers, regardless of enclosure kind, explicit or generated name, profile, or diagnostic naming mode. Count active nested enclosures, not total enclosures in a compilation unit, repeated sequential groups, or runtime function recursion. The threshold is a code-structure policy independent of the 1,000-name presentation pool. Default severity is an error at the opening of the 1,001st enclosure; an override for generated code or other exceptional use is not specified and remains a future design question. Detect excessive depth before exhausting the parser's own call stack or resource budget, and retain a meaningful source span and the current enclosure identity when possible.

Illustrative default humorous message (localized equivalents and exact diagnostic code pending):

    Excessive nesting — depth 1,001.
    You have nested 1,001 grammatical enclosures. The maximum depth is 1,000.
    The compiler has run out of names. You appear to have run out of functions.
    Consider refactoring your code.

The joke is not the technical reason for rejection: it applies even in numeric mode and when all enclosures are explicitly named. Ordinary diagnostics may use a neutral explanation. The special error must never fire merely because a flat program contains more than 1,000 enclosures or the humorous name pool is exhausted.

## Conformance plan (not yet implemented)

| Case | Required outcome |
|---|---|
| Named, verbal anonymous and symbolic groups | Same semantic form/results for equivalent contents |
| Nested distinct explicit names | Valid matching |
| Simultaneously open duplicate explicit name | Reject |
| Crossing/mismatched named close | Report expected and encountered identities and locations |
| Nested anonymous groups; missing inner/outer close | Distinguish recognized openings and relevant incomplete structure |
| Unexpected closing delimiter without identifiable opener | Report unexpected token/location without invented identity |
| Explicit/generated display label clash | Distinct diagnostic identities |
| More than 1,000 sequential or shallow anonymous enclosures | Release/reuse aliases after closure; no aggregate-count restriction; distinct internal IDs/source spans |
| 999 and 1,000 nested enclosures | No excessive-nesting diagnostic |
| 1,001 genuinely nested enclosures, including mixed kinds/names | Dedicated excessive-nesting error; same behavior across naming modes and profiles |
| Runtime recursion or sequential enclosures beyond 1,000 | No syntactic-depth diagnostic merely from those counts |
| Missing profile name data | Numeric fallback |
| Same filename, source, profile/pool and configuration repeated across platforms | Reproducible identity/alias rendering |
| Different filenames | Filename seeds affect alias sequence; no guarantee against chance equal names; no semantic change |
| Reused names in non-overlapping regions | Distinct internal IDs and source spans; no ambiguity in multi-location diagnostics |
| Numeric vs humorous display, across profiles | No change to parsing or program semantics |
| Written/spoken and localized delimiters | Same structural roles and name identity; reversible representation |

## Open design work

Token classes and delimiter morphology; direction markers; grammar productions and statement terminators; normalized name identity and reserved-word escaping; precise compilation-unit IDs and source-map format; canonical equivalence tests; numeric/ humorous configuration interface; qualified, reproducible name-pool sourcing and fallback; parser recovery strategy. No compiler or name-list data is shipped by this decision.
