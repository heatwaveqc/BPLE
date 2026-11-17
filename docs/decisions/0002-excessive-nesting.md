# 0002 — Dedicated excessive-nesting diagnostic

- Status: Accepted (owner requested custom error at 1,000 genuinely nested containers; default severity, nickname and illustrative wording are implementation/design interpretations, open to refinement)
- Date: 2026-11-17
- Depends on: [0001 — Named grammatical enclosures](0001-named-enclosures.md)

## Problem and decision

A compilation unit may have thousands of individually reasonable enclosures. However, 1,000 simultaneously nested syntactic enclosures indicate exceptional structural complexity and deserve a dedicated compile-time diagnostic, not an accidental parser stack overflow or name-pool exhaustion message.

Distinguish nesting depth from aggregate count and runtime recursion. Emit a dedicated error by default when the 1,000th enclosure opens in any diagnostic naming mode, identifying its depth and source location and recommending decomposition/refactoring. The working nickname is the Kevin Limit. A humorous localized message may accompany the structural information. Numeric fallback for the name pool continues to operate independently, including in large shallow programs.

The owner requested the diagnostic; default hard-error severity at the threshold is an agent interpretation, not a decision to prohibit all future configurable overrides. No override policy, exact message catalog, diagnostic code or parser implementation has been selected.

## Axioms and conformance

The threshold operates over universal grammar, not localized names, and measures the same nesting in text and spoken forms. Diagnostic rendering is metadata and independent of execution mode. Count equivalent source constructs consistently and test 999 versus 1,000 active nested enclosures, flat programs with over 1,000 enclosures, mixed enclosure types, named and anonymous variants, runtime recursion, and pool exhaustion. See [the standard](../../spec/ENCLOSURES.md#excessive-nesting-the-kevin-limit). Tests are planned, not executed.
