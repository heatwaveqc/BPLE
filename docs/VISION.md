# Vision

BPLE is a project to develop The Grammar, a general-purpose programming language that humans can read, write and speak, and machines can parse mechanically. Python inspires readability and ease of entry; Lojban inspires formally parseable grammatical structure and linguistic regularity. Neither language's syntax is inherited wholesale.

The [five axioms](../spec/AXIOMS.md) are authoritative. Design goals include human readability; deterministic parsing; speech equivalence; linguistic neutrality; regular and composable syntax; general-purpose programming; interactive execution, runtime compilation and ahead-of-time native executable production (including Windows EXE as a target).

The project seeks controlled language, not unrestricted natural-language programming or AI interpretation. English, Mandarin and Russian are useful early lexical profiles; they are intended test cases, not distinct dialect grammars. Additional profiles should be pluggable without modifying the parser's semantic rules.

Procedural, functional and object-oriented capabilities are long-term design goals, not committed syntax. Strong typing with inference, explicit dynamic escape hatches, garbage collection, symbolic aliases, tagged arguments and .NET are proposals from inception discussion, not accepted specifications.

A successful early milestone is a tiny program that can be written in multiple profiles, rendered in spoken form, parsed into an equivalent canonical representation and executed with matching results. Expand after that proof.
