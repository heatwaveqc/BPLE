# The Grammar — Constitution

Status: foundational; approved axioms established and amended at project inception, 2026-11-17. The explanations below are design interpretations and test obligations, not a finalized syntax specification.

## Axiom I — Vocabulary is interchangeable.

No natural language is the privileged basis of The Grammar. Keywords and equivalent spoken forms are replaceable lexical profiles over stable language concepts. Choosing a profile at source parsing or interactive evaluation must not change program meaning. A language's words and orthography are a presentation layer. Identifier and library-display localization require separate explicit contracts; strings are data, not keywords.

Design test: equivalent programs authored in supported lexical profiles resolve to the same canonical semantic form, preserving literal values and bindings.

## Axiom II — Grammar is universal.

All conforming profiles implement one formally specified grammatical system. Localized spellings and permitted lexical segmentation are not an invitation to create separate grammars. The grammar must be mechanically parseable and unambiguous; a valid program has exactly one syntactic interpretation under its declared specification, compatible extension set and lexical profile. Modules may add capabilities through the universal extension contract without introducing locale-specific grammars or silently redefining the common kernel. Changes are explicit, versioned decisions.

Design test: grammatically equivalent normalized token sequences parse identically; ambiguity is rejected or resolved by a specified rule, never an undocumented guess.

## Axiom III — Meaning is deterministic.

A program's meaning is assigned by formal semantics, not natural-language inference. Each construct has defined binding, typing, evaluation and error rules. Deterministic meaning does not prohibit randomness, concurrency, external inputs or I/O; their observable behavior and allowed nondeterminism must be specified.

Design test: equivalent programs under the same specified conditions exhibit the same permitted observable behavior.

## Axiom IV — Speech and text are equivalent representations.

Every valid written grammatical construct must have a precise speakable equivalent, and every valid spoken construct must have a lossless written representation of its program information. Whitespace, formatting and punctuation may aid reading but cannot supply meaning that has no explicit spoken encoding. Literal data and identifiers need reversible spoken spelling/escaping rules, not necessarily natural pronunciation. Speech recognition may err; the grammar must not depend on guessing among acoustically ambiguous interpretations.

Design test: canonical written and spoken renderings round-trip to the same program representation, including boundaries, grouping, identifier identity and literal data.

## Axiom V — Execution is independent of expression.

Lexical profile, speech/text presentation, and selected execution mechanism are separable from meaning. Interpretation, runtime compilation and ahead-of-time compilation should implement the same standard semantics. Explicitly specified platform dependencies and effects may limit portable observables; silent backend semantic divergence is not acceptable.

Design test: execute shared conformance cases across supported execution modes and compare specified results, effects and diagnostics.

## Axiom VI — The Grammar is deliberately extensible.

Any meaningful language, compiler, runtime, diagnostic or tooling capability that can be modular, configurable or programmatically extensible without breaking the language's foundational guarantees should be designed accordingly. Prefer reusable, documented extension interfaces, data-driven contracts and selectable features over unnecessary hard-coded behavior. Programs may declare required compiler modules and meaning-affecting configuration in source metadata; supported extensions may add grammatical constructions, types and behavior within an explicitly composed, validated contract.

Extensibility does not authorize breaking the other axioms or silently changing the meaning of the kernel. The same declared standard, compatible modules and semantic settings must yield one grammatical interpretation and specified semantics, with equivalent written/spoken representations across supported lexical profiles and execution modes. Missing or conflicting dependencies must be diagnosed. Changing the selected feature set is an explicit change to a program's declared compilation environment, not an implicit consequence of an editor preference, machine or installed module. Keep language-defining invariants protected; justify necessary non-extensible boundaries.

Design test: implement and load a meaningful capability through a documented extension interface without modifying the kernel; verify module/configuration resolution, deterministic composition, conflict rejection, lexical/speech equivalence, and execution parity in supported modes. See [extension requirements](EXTENSIBILITY.md).

## Governance

Axioms constrain all accepted specifications and implementations. New features must demonstrate compatibility with all six. Only explicit owner approval may amend an axiom; record the rationale and consequences in a versioned design decision. Ambiguous or conflicting proposals remain provisional until resolved.
