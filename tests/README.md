# Validation and conformance

Keep specification-level fixtures independent of backend or profile when possible. Future suites should cover lexicon completeness and collisions, Unicode and segmentation, invalid/ambiguous grammar, precedence and scoping, literal/identifier round trips, localized/symbolic/spoken representation equivalence, semantics and diagnostics, and interpreter/JIT/AOT parity. Extension conformance must additionally exercise documented plugin interfaces, missing and incompatible modules, conflicts, explicit feature configurations, profile/spoken equivalence, protected kernel behavior and supported execution-mode parity. Record the effective extension and semantic-option versions with test evidence.

## Evidence levels

| Level | Scope |
|---|---|
| Repository CI | Structure, links, schemas, lint and static validation |
| Module CI | Component compilation and unit tests |
| Language Conformance | Shared positive and negative grammar/semantic fixtures, profile and speech round trips |
| Execution Smoke | Actual execution via specified supported mode, platform and toolchain |
| Distribution Acceptance | Built executable/package installed or run in a clean target environment; release gates |

Routine scoped CI and conformance are expected; broad full-platform matrices, distribution publishing and expensive runs require owner approval. Levels are independent of how evidence is collected (offline source/tool reads, actual command execution, or manual interactive/speech/platform validation). Report exact level and scope; do not imply a downstream level passed.

Record commit SHA, standard/profile versions, environment, command, expected and observed outcome, statuses PASS/FAIL/BLOCKED/NOT RUN, and links to logs when available. Tests not implemented are NOT RUN, not passing. No executable test suite or CI workflow is present at bootstrap.
