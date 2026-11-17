# Architecture — provisional

This is a proposed decomposition, not an implementation commitment.

    canonical source (default)     localized text / speech
              |                              |
      canonical decoder             selected lexical profile
              |                              |
              +------ canonical token stream +
                   |
          universal grammar parser
                   |
        abstract syntax tree (AST)
                   |
      semantic analysis / typed form
                   |
      intermediate representation (IR)
           /          |          \
    interpreter     JIT        AOT executable

A text frontend and eventual speech adapter share a deterministic normalization contract. The speech adapter may use recognition technology, but its output is a constrained representation, not guessed code. A profile controls spellings, aliases and segmentation within a shared lexical model; profile-specific executable parsing rules are not assumed. Preserve source maps through stages so errors can refer to original locations and be localized.

[Lexical requirements](../spec/LEXICAL-FOUNDATIONS.md) are accepted; exact canonical token/AST/IR formats, grammar notation, Unicode normalization, delimiter handling, precedence, number and string syntax, identifier spelling, scoped imports and evaluation rules remain open. Canonical token-based source is the configurable new-file default; localized plain text is an opt-in first-class format. A shared frontend recognizes both, and the IDE's localized display/input layer provides live feedback and preserves existing storage format and source profile on save. Exact canonical serialization and recognition protocol remain open (see [decision 0004](decisions/0004-lexical-profiles.md)). Do not conflate canonical syntax with semantic equivalence (binding and literal preservation matter).

Candidate implementation: .NET hosting, possible managed JIT and Native AOT strategy, with an embedded interpreter for dynamic scripts where native runtime code generation is unavailable. Evaluate alternatives against interoperability, portability, semantic parity, executable packaging and tooling before adoption. Verify actual backend capabilities with versioned primary sources and a minimal experiment; do not promise a specific output format before the prototype proves it.

Proposed component names (not finalized): Sermo (compiler/runtime), Lexis (lexicon and translation tooling), Canon (standard library), Scriptorium (package manager). Directory layout currently uses neutral role names so those names can change.

## Ownership boundaries

- spec/: normative shared contracts.
- lexicons/: profile data and future schema; not runtime language plugins.
- src/: shared frontend, semantics, IR, execution backends and tooling.
- tests/: language-independent conformance cases and implementation checks.
- examples/: illustrative or verified programs, explicitly labeled.
- docs/: vision, architecture decisions, milestones and evidence.

The canonical spec owns observable behavior. Common mechanics belong in shared core abstractions. Renderers, profiles, and backends consume those semantics rather than inventing parallel rules.
