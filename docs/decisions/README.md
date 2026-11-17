# Design decision register

Record material design decisions in numbered Markdown files such as 0001-lexical-model.md. Use [the template](TEMPLATE.md). Statuses: proposed, accepted (owner-approved), rejected, superseded. An accepted proposal is normative only where incorporated into the standard. Preserve superseded records and link replacement decisions.

| ID | Decision | Status |
|---|---|---|
| 0000 | [Project identity and constitutional axioms](0000-foundation.md) | Accepted |
| 0001 | [Named grammatical enclosures and generated identifiers](0001-named-enclosures.md) | Accepted (design requirements) |
| 0002 | [Dedicated excessive-nesting diagnostic](0002-excessive-nesting.md) | Accepted (diagnostic requirement) |
| 0003 | [Canonical token roles and optional morphology](0003-token-roles.md) | Accepted |
| 0004 | [Lexical profiles and explicit token boundaries](0004-lexical-profiles.md) | Accepted |
| 0005 | [Unicode, case-insensitive and quoted identifiers](0005-identifiers.md) | Accepted |
| 0006 | [Symbolic and verbal literals](0006-literals.md) | Accepted |
| 0007 | [Lossless spoken and written representation](0007-speech-text.md) | Accepted |
| 0008 | [BPLE source-file extension](0008-source-extension.md) | Accepted |
| 0009 | [Axiom VI — Deliberate extensibility](0009-extensibility-axiom.md) | Accepted |

## Pending design decisions

Use the [discussion backlog](PENDING.md) to find the next batch of five. GitHub issues hold pending questions and their review status; this register records actual decision documents and must not treat backlog items as approved specifications.

## Open questions (not decisions)

Formal grammar notation and statement boundaries; exact token IDs and profile schema; delimiter configuration, canonical source serialization and profile resolution details (L02/G05/P01/P04); Unicode normalization/folding, escapes, and exact spoken representation (including arbitrary literal/identifier spelling); type and effect systems; arithmetic and evaluation order; implementation host and backend strategy; standard library and localization; CLI names and packaging formats; compatibility/versioning; extension boundaries, module headers, APIs, dependency resolution, feature toggles and trust model; software license.

Create a proposal when work begins on a question; do not assign decisions merely because an agent uses a provisional example.
