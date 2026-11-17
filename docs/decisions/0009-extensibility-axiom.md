# 0009 — Axiom VI: Deliberate extensibility

- Status: Accepted constitutional amendment (owner request)
- Date: 2026-11-17
- Depends on: [0000](0000-foundation.md)
- Backlog: cross-cutting; G01/G05, R05 and P01/P03/P04 are primary design follow-ups.

## Problem and decision

The owner explicitly requested a sixth axiom: make The Grammar deliberately extensible in every meaningful way that can be modular, configurable or programmatically extended by a compiler mod without breaking the language itself. Code may declare required compiler modules in file headers. Features that can sensibly be compiler toggles should be designed as such.

Adopt [Axiom VI](../../spec/AXIOMS.md) and the accompanying [extension requirements](../../spec/EXTENSIBILITY.md). Favor a protected kernel, common extension contracts, selectable standard capabilities, third-party compiler modules, and explicit module/semantic-option requirements. Prefer the same extension surfaces for first-party and community features when practical. Preserve all previous axioms: universal grammar applies to a shared kernel and deterministic composition under a declared standard and extension set; lexical profiles do not become independent grammar implementations. Do not allow a plugin or installed setting to silently redefine existing programs.

## Alternatives and scope

A monolithic compiler would simplify initial implementation but force forks for many feature requests. Library-only extensibility cannot cover syntax, type analysis or lowering. Unrestricted patching would make meaning and compatibility unpredictable. Select deliberate, documented extension interfaces and explicit composition/configuration, with necessary invariant boundaries. No exact API, plugin language, header syntax, dependency resolver, trust policy, operator/type design, host or backend is adopted by this amendment.

## Axiom compatibility

I: added concept IDs use the common lexical-profile/rendering model. II: compatible extensions compose into one deterministic grammar for a declared configuration. III: semantics and meaningful settings are explicit, not hidden in the machine's plugin inventory. IV: compatible constructs need reversible speech/text forms. V: supported execution modes implement the same declared semantics; unsupported targets report incompatibility. VI: meaningful modularity and extensibility are the default; non-extensible decisions need a justification.

## Verification

Plan positive extension examples and failures for absent/incompatible modules, conflict resolution, kernel replacement, reproducibility, lexical and spoken rendering, configuration changes and supported execution-mode parity. No plugin code, API or executable tests exist yet.
