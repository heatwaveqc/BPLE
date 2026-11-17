# Design decision register

Record material design decisions in numbered Markdown files such as 0001-lexical-model.md. Use [the template](TEMPLATE.md). Statuses: proposed, accepted (owner-approved), rejected, superseded. An accepted proposal is normative only where incorporated into the standard. Preserve superseded records and link replacement decisions.

| ID | Decision | Status |
|---|---|---|
| 0000 | [Project identity and constitutional axioms](0000-foundation.md) | Accepted |
| 0001 | [Named grammatical enclosures and generated identifiers](0001-named-enclosures.md) | Accepted (design requirements) |

| 0002 | [Dedicated excessive-nesting diagnostic](0002-excessive-nesting.md) | Accepted (diagnostic requirement) |

## Pending design decisions

Use the [discussion backlog](PENDING.md) to find the next batch of five. GitHub issues hold pending questions and their review status; this register records actual decision documents and must not treat backlog items as approved specifications.

## Open questions (not decisions)

Formal grammar notation and statement boundaries; token IDs and profile schema; segmentation across scripts, Unicode identifiers and escapes; spoken representation (including arbitrary literal/identifier spelling); type and effect systems; arithmetic and evaluation order; implementation host and backend strategy; standard library and localization; file extension and CLI names; compatibility/versioning; software license.

Create a proposal when work begins on a question; do not assign decisions merely because an agent uses a provisional example.
