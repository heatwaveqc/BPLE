# Vision

BPLE is a project to develop The Grammar, a general-purpose programming language that humans can read, write and speak, and machines can parse mechanically. Python inspires readability and ease of entry; Lojban inspires formally parseable grammatical structure and linguistic regularity. Neither language's syntax is inherited wholesale.

The [six axioms](../spec/AXIOMS.md) are authoritative. Design goals include human readability; deterministic parsing; speech equivalence; linguistic neutrality; regular and composable syntax; general-purpose programming; interactive execution, runtime compilation and ahead-of-time native executable production (including Windows EXE as a target).

The project seeks controlled language, not unrestricted natural-language programming or AI interpretation. English, Mandarin and Russian are useful early lexical profiles; they are intended test cases, not distinct dialect grammars. Additional profiles should be pluggable without modifying the parser's semantic rules.

Extensibility is a foundational goal: the kernel should expose modular compiler and language extension points, with program-declared requirements and configurable features where meaningful. See [Axiom VI](../spec/AXIOMS.md#axiom-vi--the-grammar-is-deliberately-extensible) and the [extension requirements](../spec/EXTENSIBILITY.md). Avoid forcing a compiler fork for supported new capabilities. The default installation should provide a full general-purpose standard environment comparable in breadth to Python or C#, with no mandatory extension-management burden for ordinary use ([decision 0010](decisions/0010-standard-installation.md)).

Procedural, functional and object-oriented capabilities are long-term design goals, not committed syntax. Strong typing with inference, explicit dynamic escape hatches, garbage collection, symbolic aliases, tagged arguments and .NET are proposals from inception discussion, not accepted specifications.

A successful early milestone is a tiny program that can be written in multiple profiles, rendered in spoken form, parsed into an equivalent canonical representation and executed with matching results. Expand after that proof.
