# BPLE — repository-wide agent instructions

Applies to all agents, automated contributors, development chats, and branches. BPLE is the project/searchable name; The Grammar is the official programming language. GitHub is the source of truth for specifications, decisions, implementation, profiles, tests and handoffs.

## Non-negotiable language principles

Read [the five axioms](spec/AXIOMS.md) before design or implementation. Every language change must preserve all five; only the owner can authorize amendments. Read the [Standard index](spec/README.md), [decision register](docs/decisions/README.md), and the narrowest relevant contract before editing. Do not derive rules from sample syntax, compiler accidents, or chat conjecture. Mark proposals as proposals; distinguish approved requirements, accepted specifications, experimental implementations and verified behavior. No agent may silently promote a proposal to a standard.

- One language, one shared grammar and semantics. Natural-language lexicons are replaceable data profiles, not language forks or executable features. No privileged English parser or locale-specific semantic branch.
- Treat speech as a first-class representation, not arbitrary natural-language interpretation. Require a deterministic path between spoken/written forms and semantic tokens; do not quietly guess ambiguity. Preserve literals, identifiers, boundaries, diagnostics and Unicode safety.
- Execution targets share semantics and test vectors. Do not hide implementation-defined behavior or target divergence behind backend-specific syntax. Language features belong to the shared specification and core, not a particular rendering or backend.
- Prefer regular composable rules over special cases. Test counterexamples across structurally different natural languages, scripts and execution modes. Do not invent translations or claim native-speaker review without evidence.
- Design public contracts before implementation. A new keyword, grammar rule, observable behavior or compatibility break needs a recorded proposal, rationale, axiom impact and conformance plan; owner approval is required before normative adoption. Agents may autonomously prototype on clearly identified experimental branches.

## Before starting or resuming a task

1. Read these instructions and the relevant scoped documents. Inspect current default branch tip through GitHub; record full commit SHA. Do not assume a local checkout or another conversation is current.
2. Discover relevant existing issues, PRs, branches, decisions, and integrated code. Continue the existing workstream rather than duplicate it.
3. Work from current accepted main (or a documented approved subsystem base) on a dedicated collision-resistant branch, e.g. `design/grammar-boundaries-20261117-a1`, `feature/lexer-...`, `fix/...`, or `maintenance/...`.
4. Identify scope, ownership, dependencies, acceptance criteria and intended checks. Keep task changes bounded; do not opportunistically change unrelated components.
5. Use a local checkout for code edits and actual tests when available; use the GitHub connector for remote truth, recoverable commits, PRs and integration if local credentials are unavailable. Never fabricate shell access or keep retrying unavailable capabilities.

## Concurrency, ownership and integration

- Main is the accepted baseline. One writer per task branch; one designated integration writer at a time for a shared branch or coordinated cross-component merge. Do not write to another active branch without an explicit transfer. Begin with short-lived task branches; add long-lived subsystem branches only after an approved need.
- The specification owns language behavior; the shared frontend/core owns lexical normalization, parsing, semantic analysis and canonical representation; profiles own only validated lexical data; backends own lowering/execution, not independent language semantics. Tests encode the approved contracts. See [architecture](docs/ARCHITECTURE.md) for provisional layout.
- Shared contract changes require a coordinated PR, not divergent local copies. Split dependent work into core and consumer PRs if useful, and state their order. Pin external inputs, dependency versions and donor commits where reproducibility matters; never depend on a moving temporary branch for accepted builds.
- Commit coherent increments to the task branch. Re-fetch head before shared integration; preserve concurrent changes. Open a PR with a concise summary, decisions/proposal status, exact changed areas, dependencies, tests and blockers. Avoid giant directory replacements or stale snapshot replays.
- For routine in-scope work, merge a clean PR without extra owner confirmation after required checks are green and ownership is clear. Leave normative design decisions that need approval, unresolved conflicts and failed checks open. Do not force-update main, bypass protection or skip required CI. Initial empty-repository bootstrap may create the first commit directly; this exception is not a standing permission.
- Verify the integrated main content and resulting SHA. Auto-delete normally merged temporary branches when repository settings permit; otherwise report remaining branches. For bulk stale-branch cleanup, inventory unique work, open PR heads/bases and pinned references; preserve useful work first. Use a reviewed exact-ref/full-SHA allowlist and read-only dry run, recheck refs before deletion, and verify results. Never fake merges or revive obsolete code just to delete a branch; no unattended destructive cleanup.

## Validation and release discipline

Read [testing](tests/README.md). Routine static checks, scoped builds, unit tests and fast integration/conformance checks are allowed automatically. Full distribution builds, broad platform matrices, expensive benchmarks, publishing releases, tags, signed artifacts or deployments require explicit owner authorization for that run. Do not configure automatic expensive/publishing workflows or circumvent approval with alternate triggers. Keep CI least-privilege and secrets out of changes and logs. Once workflows exist, check their triggers before editing them. Branch protection is a repository setting, not enforced by this file alone.

Test the failure path as well as the happy path. Add regression tests with any observable behavior fix. For cross-profile changes, prove same canonical representation and semantics; for backends, prove parity at the same specification revision. Record exact commands, environment/SDK versions, commit, results, and skipped tests. Never call a static read a compilation, compilation an execution, or successful execution a native executable test. No `[skip ci]` on implementation or contract changes.

Do not commit credentials, personal data, private source material, generated binaries, caches or third-party content without authorization and appropriate licensing. Verify dependency source, version and license; pin what is needed for reproducible builds. Use disposable test data and restrict execution of untrusted code.

## Retrieval, context and research

Start with known paths and targeted file reads; search narrowly by component or decision ID. Return compact tool results (IDs, exact paths, SHAs, relevant excerpts, check outcomes) rather than entire repository trees, logs or API payloads. Expand only to diagnose a specific failure. Prefer official specifications, primary documentation and version-matched sources. Record relevant URLs/version and distinguish verified findings from hypotheses. Keep one canonical owner for structured data; generate dependent views rather than copy fields. Do not expose unrelated private project material in this public repository.

## Durable handoff and reporting

Before ending a substantive task, push recoverable work when possible and put status in the PR or issue (not only in chat). Record goal, base/head SHA, branch/PR, paths changed, decision status, tests actually run/results, blockers, remaining work and exact next actions. Link superseded work and preserve provenance. Verify any claimed merge or workflow result. When blocked, complete safe independent steps first, explain the exact limitation and distinguish attempted from verified work. Keep [roadmap](docs/ROADMAP.md) and relevant decision/test records current without rewriting history.

## Design discussion cadence

Use [the pending design backlog](docs/decisions/PENDING.md) and linked GitHub issues for unresolved design topics. Discuss five related pending items at a time unless the owner directs otherwise; preserve explicit decisions with ADRs, spec updates, and conformance plans. Mark issue checklist items disposed only after linking the decision record/PR; keep unresolved or deferred items tracked. Batch numbering and backlog topic IDs are not ADR numbering or language specification. Never treat a pending topic as approved merely because it has an issue.
