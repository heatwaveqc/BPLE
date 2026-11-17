# 0010 — Complete standard installation

- Status: Accepted
- Date: 2026-11-17
- Owner approval: explicit agreement that the standard modules should be as functional as a basic installation of C# or Python; extensibility is a feature, not a requirement.
- Depends on: [0009](0009-extensibility-axiom.md)
- Follow-up: P02, P03, P01, R05 and individual language-feature decisions.

## Decision

Ship a coherent standard bundle enabled by default, offering complete ordinary general-purpose programming capabilities. Modules may implement official features internally, but users should not need to install or explicitly activate extensions for ordinary programming. A program can require additional modules or explicitly select a different compatible feature configuration. The standard bundle and its semantic configuration must be versioned and reproducible. Minimal kernel-only and specialized environments may exist without becoming the default experience.

## Alternatives and consequences

A minimal default with separately installed basic features would place unnecessary burden on newcomers. A monolithic default would undermine deliberate extensibility. A cohesive standard bundle permits both familiarity and extensible implementation. Exact standard module inventory, package format, declaration mechanism and release scope remain to be decided. Comparison to Python/C# is a functional breadth target, not a requirement to duplicate either language or all their APIs.

## Axioms and verification

I–V: the effective standard bundle is independent of chosen vocabulary/presentation and has deterministic grammar and semantics across supported execution modes. VI: official capabilities should use public extension seams where practical without requiring module management for routine use. Test a clean default installation with ordinary representative programs, no separately installed third-party modules, explicit alternative configurations and consistent profile/backend behavior. No executable tests exist yet.
