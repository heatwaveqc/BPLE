# Mainstream grammar survey and evaluation

Status: research and recommendations, 2026-11-17. Not normative; no syntax, keyword, operator, type-system or implementation decision is accepted by this document. Owner direction: retain the familiar shared programming model of Python, C, Java, JavaScript and similar languages, and examine each convention for meaningful improvements.

## Evaluation rule

Proposed design heuristic, subordinate to the six [axioms](../../spec/AXIOMS.md): prefer familiarity unless departure provides a demonstrable benefit. Distinguish computational concepts, grammatical structure, and surface notation. Retain the transferable mental model whenever the notation can be improved independently. Evaluate departures against determinism, linguistic neutrality, speakability, readability, expressiveness, safety, performance/tooling, and migration cost. A familiar construct that violates an axiom must be adapted, not exempted. Under Axiom VI, evaluate modular seams and meaningful configuration for all candidates; see [extension requirements](../../spec/EXTENSIBILITY.md).

This is a representative survey, not a claim that every listed construct occurs in every language. The common structured imperative baseline coexists with expression-oriented, functional, event-driven and declarative programming. Orthographic choices do not necessarily define the computational model.

## Inventory

| Concept | Recommendation | Evaluation / next question |
|---|---|---|
| Tokens and lexical classes | Retain | Stable internal token identities; validate profile mapping. |
| Keywords and operators | Adapt | Separate canonical concepts from localized and symbolic forms; avoid conflicting aliases. |
| Identifiers | Adapt | Unicode, normalization, exact identity, reserved-word escape, case and reversible speech spelling. |
| Literals | Adapt | Preserve types and values; localized numerals, decimals, exponent notation, strings, escapes and arbitrary Unicode must not depend on a locale guess. |
| Expressions | Retain | Values compose recursively; specify precedence, evaluation order and effects. |
| Statements | Retain | Actions and control; evaluate expression statements and value-producing blocks without requiring a strict separation everywhere. |
| Declarations | Retain | Explicit binding introduction, optional inferred types; separate from updating storage. |
| Blocks and termination | Adapt | Speech-capable structural delimiters; visual indentation alone cannot be the only encoding. |
| Nesting and grouping | Retain | Explicit grouping; test nested calls and control structures. |
| Scope and name resolution | Retain | Prefer lexical scope; specify shadowing, lifetime and capture separately. |
| Comments/documentation | Adapt | Reversible spoken delimiter and escape model; comments do not alter execution. |
| Bindings, storage and constants | Retain | Compare immutable-by-default binding with explicit mutation; binding immutability is not deep object immutability. |
| Assignment | Retain concept; adapt syntax | Unambiguous separation from equality, initialization and binding; consider restricting assignment expressions. |
| Types | Retain | Evaluate static typing and inference, explicit dynamic values, nullability, conversions and numeric semantics. |
| Arithmetic, bitwise and relational operators | Adapt | Conventional mathematical precedence; separate logical/bitwise concepts and specify all associativity, overflow and less intuitive precedence. |
| Boolean logic and comparisons | Retain | Explicit booleans in conditions proposed; short-circuit behavior, equality vs identity, coercion and chained comparisons need rules. |
| Sequential execution | Retain | Explicitly define observable evaluation order and effect sequencing. |
| Conditionals | Retain | Familiar if/else structure; decide conditional expressions separately. |
| Iteration and control transfers | Retain | Counted, collection and condition-based loops; specify range boundaries, break/continue and return; C-style loop not required initially. |
| Functions, return values and recursion | Retain | Specify call evaluation, return convention, first-class functions and recursive support; tail calls are open. |
| Parameters and arguments | Adapt | Positional and universally tagged named syntax; define missing, duplicate, default, variadic and ordering behavior. |
| Errors and optional values | Reevaluate | Compare explicit result/option types, exceptions, cleanup and interoperability, not silently failing operations. |
| Pattern matching | Retain candidate | Structural matching, exhaustiveness and binding rules; later than MVP. |
| Collections | Retain | Lists, maps, sets and tuples; evaluate indexing, bounds, mutability and iteration. |
| Objects and encapsulation | Retain candidate | Separate data and behavior, public contracts and visibility. |
| Inheritance | Reevaluate | Compare single inheritance, composition, interfaces and traits; no forced deep hierarchy. |
| Polymorphism, interfaces, generics | Retain candidates | Static/dynamic dispatch and type constraints to be specified. |
| Closures and higher-order functions | Retain candidates | Capture by value/reference, lifetime and mutation rules. |
| Modules and imports | Retain | Stable identity, versioning, dependency resolution and localized presentation of APIs. |
| Asynchrony and concurrency | Retain candidates | Explicit control/effects; structured concurrency and memory model; nondeterminism must be specified. |
| Metaprogramming | Reevaluate | Prefer structured AST/IR rather than text macros; syntax extensions must compose deterministically through the common extension contract. |
| Memory and resource management | Reevaluate | Garbage collection vs ownership and deterministic resource cleanup; no host decision yet. |

## Priority questions and proposed alternatives

### Boundaries and orthography
Python indentation, C/Java braces, and JavaScript automatic semicolon insertion illustrate differing presentation choices. The Grammar should have spoken equivalents of every meaningful boundary. Prefer explicit open/close particles, including distinct closing roles where beneficial; punctuation may be a reversible alias. Explore omission of terminators only through formally specified grammar productions with one parse, not heuristic insertion or interpretation of pauses. Ordinary whitespace may separate tokens; line layout need not define block semantics. Test flattened and nested code, adjacent complete statements, dangling else, empty blocks, and quotation boundaries.

### Expressions and assignment
Keep conventional infix arithmetic, standard precedence and explicit grouping. Proposed spoken examples (not valid code yet): "two plus three times four" -> 14; "group two plus three end group times four" -> 20. Specify less familiar operator tiers, associativity, unary/binary meanings, chained comparisons and evaluation of effectful operands. Distinguish declaration, updating a binding, and equality (illustratively: "let x be 5", "set x to 10", "x equals 10"). Restricting assignment expressions would make accidental assignment in a condition impossible; assess real use cases. Investigate immutable bindings by default, explicitly mutable ones, object mutation vs binding reassignment, and scope. No operator spelling or mutability default adopted.

### Calls and control
Keep recognizable function calls, positional arguments, named arguments, if/else, iteration, return and recursion. Investigate a shared tagged argument grammar: "call move with entity as player destination as castle speed as 5 end call". Reordering labels is not automatically semantic equivalence if evaluation order changes observable effects; define order explicitly. Library-defined natural phrasing ("move player to castle at speed 5") is a more speculative extension, not a baseline requirement: arbitrary custom grammar risks dialects and ambiguous parses. Favor intent-expressive repetition, foreach and while; evaluate range endpoints, indexing, and control transfers.

### Types, logic and error model
Strong static typing with inference and an explicit dynamic mechanism is a proposal, not a decision. Compare inferred and annotated bindings, numeric promotion, precision/overflow, nullable values and optional types. Consider strict Boolean conditions instead of general truthiness, independent bitwise and logical tokens, and explicit short-circuit semantics. Compare tagged results/option types and exceptions; specify recoverable error vs programmer fault, structured cleanup and host interop. Pattern matching could support explicit result handling. Do not make every error disappear or require unnatural nesting.

### Object model and wider paradigms
Preserve familiar modular and procedural programming; investigate functions as values, closures, object/data models, encapsulation, interfaces, generics and composition. Evaluate inheritance instead of treating it as the default abstraction. Preserve separate research tracks for concurrency, async, memory management, resource lifetime and metaprogramming after the kernel. Avoid committing to a host-specific behavior in the spec.

### Profile neutrality and speech
Identifiers, comments, arbitrary literal payloads, numbers, punctuation, grouping, boundaries and case need deterministic spoken representation, including explicit spelling/escaping where ordinary pronunciation is insufficient. Written symbols and spoken words should produce equal canonical information. Avoid mechanically translating English filler words into other languages; test structural markers and segmentation in Mandarin and Russian as well as English. A profile may not change canonical semantics or silently reinterpret identifiers. The role of built-in and library names/localized display names needs separate decisions. Diagnostics should retain original source location and profile.

## Work order for kernel design

1. Define token classes and lexical profile model (including identifiers, literals, escapes, Unicode, written and spoken alias mapping).
2. Define statement and block boundaries, nesting and grouping. Compare complete forms and formally permitted omission.
3. Define expression grammar, operators, precedence, associativity, equality and evaluation order.
4. Define declarations, assignment, binding/scope, type and mutation rules for the kernel.
5. Define basic function signatures, call and argument binding, return, control flow and iteration.
6. Select minimal runtime semantics and independently compare candidate host technologies; prototype English plus a structurally different profile and canonical speech round trips from the outset.

Each decision requires owner approval for normative adoption, a six-axiom review, and positive/negative conformance cases. Use equivalent cross-profile fixtures; distinguish syntax ambiguity, semantic uncertainty, and recognition errors. This research does not authorize implementation or finalize concrete grammar.

## Reference baseline

Representative official specifications/reference docs (consulted 2026-11-17; version-specific where appropriate):
- [Python language reference](https://docs.python.org/3/reference/), [lexical analysis](https://docs.python.org/3/reference/lexical_analysis.html), [expressions](https://docs.python.org/3/reference/expressions.html), [compound statements](https://docs.python.org/3/reference/compound_stmts.html).
- [C language reference (cppreference, secondary)](https://en.cppreference.com/c/language), [statements](https://en.cppreference.com/c/language/statements).
- [Java SE 25 language specification, blocks/statements/patterns](https://docs.oracle.com/javase/specs/jls/se25/html/jls-14.html), [expressions](https://docs.oracle.com/javase/specs/jls/se25/html/jls-15.html).
- [ECMAScript 2026 specification](https://262.ecma-international.org/index.html), §12.10 automatic semicolon insertion.
- [C# specification, statements](https://learn.microsoft.com/dotnet/csharp/language-reference/language-specification/statements), [expressions](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/expressions), [patterns](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/patterns).
- [Lojban community typography and terminators](https://tiki.lojban.org/typography), [Lojban formal grammar](https://vrici.lojban.org/~gleki/cll_build/build/xhtml_chapter_chunks/chapter-grammars.html).
