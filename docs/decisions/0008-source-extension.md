# 0008 — BPLE source-file extension

- Status: Accepted
- Date: 2026-11-17
- Backlog: P03 (partial), [issue #11](https://github.com/heatwaveqc/BPLE/issues/11)
- Owner approval: explicit selection of .BPLE for source code files.

## Decision

Both canonical token-based and localized plain-text source files use the BPLE extension. The conventional display spelling is `.bple`; tooling should recognize `.BPLE` and case variants of the extension (casing convention is an agent interpretation, not an identifier rule). Do not infer which source representation or lexical profile a file uses from its extension: inspect its format marker or resolved source metadata as required by [0004](0004-lexical-profiles.md). Ordinary saves preserve representation; no new format or compiler technology is selected by this decision.

## Axioms and conformance

The extension is independent of language profile, grammar, semantics, speech/text and execution mode. Test both representations with the same extension, format-preserving saves, and case variants without renaming existing files. Tests are planned, not run. CLI naming, package formats and executable distribution remain pending in P03.
