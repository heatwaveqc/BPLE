# Extension requirements

Status: accepted design direction from [Axiom VI](AXIOMS.md) and [decision 0009](../docs/decisions/0009-extensibility-axiom.md). Specific APIs, formats, algorithms and feature partitions are not standardized.

## Extensible by design

Prefer meaningful configurable, modular and programmatic extension points to hard-coded feature sets. Review each design decision for extension seams and compiler toggles. When practical, build first-party features on the same extension contracts available to third parties; do not require compiler forks for supported capability additions. Do not introduce gratuitous configuration for implementation details or expose an invariant as a toggle when doing so would break the axioms. Document protected boundaries and the rationale.

Distinguish ordinary runtime libraries, lexical profiles (data mapping concepts to human-language expressions), language/compiler modules (programmatic additions to the shared frontend/semantics/lowering or related capabilities), and tooling extensions. Potential extension surfaces include token concepts, grammar productions, types, operators, semantic checks, language constructs, optimizations, backends, diagnostics and IDE features. This is a design agenda, not a finalized partition of the kernel.

## Standard installation

Extensibility is a feature, not a prerequisite for ordinary programming. The normal BPLE installation must include and enable a coherent, fully functional general-purpose standard language environment comparable in breadth of ordinary programming capabilities to a standard Python or C# installation. Users must not need to discover, separately install, or manually declare multiple compiler extensions just to use ordinary language features. A versioned standard feature bundle is the default environment; its exact capabilities and module boundaries will be specified as the language develops. Explicit changes to the effective module set or semantics must remain reproducible and visible. A small kernel or hosted subset may be useful, but is not the normal user-facing installation. This is a target for the mature distribution, not a claim that the bootstrap implementation already has these features.

## Explicit compilation environment

Programs must be able to declare required compiler modules and meaningful semantic feature settings in a file header or equivalent specified source/project metadata. Both canonical and localized source need a deterministic bootstrap protocol for resolving requirements before parsing extension-dependent bodies. The declaration is itself independent of human-language spelling. Use stable module identities, version/compatibility information and a reproducible effective dependency/configuration set. Exact manifest format, header syntax, precedence, per-file versus project scope, lock mechanism and dependency solver are open.

Different modules may add different capabilities. The combined grammar and semantics for a declared, compatible set must be deterministic, not depend on incidental load order, editor locale or ambient installation. Reject missing dependencies and incompatible or ambiguous compositions with actionable diagnostics. Installing an extra module must not silently change unrelated source. Meaning-affecting toggles must be distinguishable from presentation, profiling and semantics-preserving optimization preferences.

## Boundaries

Protect the six axioms and the kernel's invariant contracts. Added concepts must have stable, conflict-safe identities and cross-profile and spoken representations; the exact namespacing and fallback protocol remains open. Supported execution modes must preserve declared semantics; when a module cannot support a mode or target, report that rather than silently substituting different behavior. Do not introduce arbitrary language-specific parsing rules as part of a lexicon. Extension requirements must not imply automatic execution of untrusted downloaded code; trust, installation, capabilities and isolation require an explicit design before plugins run.

## Conformance targets

- Introduce a nontrivial feature through a public module interface without editing kernel sources.
- A declared compatible set composes deterministically in canonical and localized source.
- Missing dependencies, incompatible versions, ambiguous syntax or conflicting concept IDs produce diagnostics.
- Unrelated installed plugins and display options do not change a program's meaning.
- Declared semantics-affecting settings and dependency resolution reproduce across supported environments.
- Extension concepts round-trip through supported lexical profiles and speakable representations.
- Extension semantics agree across supported execution modes, with explicit errors for unsupported targets.
- Attempts to violate protected kernel invariants are rejected or treated as non-conforming forks.

Implementation, security model, third-party distribution and executable tests remain pending.