# AdviceKit JS

AdviceKit JS is the TypeScript implementation of an open-source toolkit for building evidence-aware financial-advice software. It turns source material into reviewable, source-linked proposals without pretending that generated output is accepted client information.

Chunkbase builds the working system that advice firms use. AdviceKit is developer infrastructure. Keep that boundary clear.

## What makes AdviceKit worth building?

### Evidence survives every transformation

A proposed value must retain a usable route back to the source that supports it. Summaries may help a person read a meeting, but summary prose is not evidence for a fact-find.

### Uncertainty is part of the result

Unknown, conflicting, unsupported, ambiguous, and potentially outdated information must remain visible. A blank is safer than a confident invention.

### People control consequential state

AdviceKit may locate, classify, compare, validate, and propose. It does not approve facts, decide suitability, give regulated advice, or silently write to an authoritative client record.

### Provider-neutral does not mean provider-blind

Common contracts should make integrations easier without erasing provider identifiers, permissions, unsupported fields, raw references, or provider-specific behaviour.

### Public names should stay stable

Treat exported names and serialised schemas as promises, including before 1.0. Prefer a deprecation and migration path over a rename. Do not create a `classic`, `legacy`, or `v2` namespace to escape a naming mistake.

## A note from Rohan

Build the smallest truthful model of the work. Do not add machinery because another agent framework has it. Start with what an adviser, paraplanner, or reviewer needs to inspect and decide.

AdviceKit should make difficult parts explicit: where information came from, what it means, what remains uncertain, and who must review it. If an abstraction makes those questions harder to answer, it is the wrong abstraction.

## What AdviceKit is not

- It is not an autonomous adviser.
- It is not a back-office system or provider API proxy.
- It is not the private Chunkbase Advice Harness.
- It is not the `financial-advice-ai` learning repository.
- It is not a generic agent framework with financial terminology added on top.

## Shared language

Read [CONTEXT.md](./CONTEXT.md) before changing domain types or names. Use its terms in code, tests, examples, and documentation.

The most important distinction is this: an `Observation` or `Claim` may be machine-generated, while a `Fact` has been accepted by an authorised reviewer. Confidence never changes one into the other.

## The five ways to damage the model

1. **Promoting output by confidence.** A high score does not make a claim true or reviewed.
2. **Losing the evidence address.** A citation must identify the source revision and exact supporting span, not just a document name.
3. **Flattening uncertainty.** Do not turn unknowns, conflicts, missing values, and unsupported claims into `undefined` without meaning.
4. **Hiding provider behaviour.** Preserve native identifiers, permissions, write receipts, and fields the common contract cannot represent.
5. **Breaking language parity quietly.** A shared contract change is unfinished until the Python and TypeScript implementations agree on names, serialisation, and conformance fixtures.

## Hit every contract

Before calling a contract change complete, check each applicable part:

- **Domain meaning.** Does the name still mean the same thing in `CONTEXT.md`?
- **TypeScript API.** Are exports, parameter names, return types, and errors compatible?
- **Wire format.** Do JSON names, required fields, enums, and null or absent behaviour remain compatible?
- **AdviceKit Python.** Does the sibling repository implement or explicitly reject the same change?
- **Adapters.** Can provider-specific data survive a round trip?
- **Runtimes.** Does the change stay within the package's declared Node, Bun, browser, serverless, or edge support?
- **Examples and docs.** Do they teach the supported API rather than an internal shortcut?
- **Migration.** If callers must change, is the break deliberate, documented, and versioned?

Do not claim cross-language parity from similar-looking types. Prove it with shared serialised fixtures.

## Repository state

This repository is currently at bootstrap. It contains the project boundary and domain language, but no published TypeScript package yet. Do not describe planned modules as if they exist.

When the package scaffold lands:

- use Bun for dependencies, workspaces, locking, scripts, tests, and releases;
- do not add npm, pnpm, Yarn, or another package manager;
- keep TypeScript strict and avoid `any` in public code;
- use standards-based runtime APIs unless a package is explicitly Bun-only;
- separate offline unit tests from tests that require credentials or network access;
- keep deterministic conformance fixtures free of client data and model calls.

Update this section with the real package map, supported runtimes, and exact commands in the same change that creates them.

## Verification

At bootstrap, verify documentation links, repository names, and consistency between `AGENTS.md`, `CONTEXT.md`, and the README.

Once tooling exists, agents must run the narrowest relevant Bun scripts for formatting, linting, type checking, builds, and tests. Never claim a check passed if the script or configuration does not yet exist.

Contract tests should be strict about schema, subject identity, evidence location, explicit unknowns, conflicts, review state, persistence, and serialisation. Do not make them brittle about generated prose, arbitrary field counts, or model wording.

## Versioning and releases

- Use Semantic Versioning.
- Treat breaking changes during `0.x` as real breaking changes and explain the migration.
- Keep release notes in user language: what changed, who must change code, and how.
- Do not rename public concepts only to make the API look tidier.
- Do not publish a package until installation, typed imports, a minimal example, runtime compatibility, and release automation have been tested from a clean environment.

## Documentation and work tracking

Code and public docs belong in this repository. Active work, decisions still being debated, and implementation checklists belong in Linear or the owning issue. Do not commit agent scratch notes or duplicate the roadmap in markdown files.

Public examples must use fictional or synthetic data. Never add client transcripts, provider credentials, access tokens, private API documentation, or firm material without explicit permission and a suitable public licence.

## Pull requests

Read [CONTRIBUTING.md](./CONTRIBUTING.md). All normal changes reach `main` through a pull request.

- One coherent change per pull request.
- Explain the user or developer problem before the implementation.
- Call out public API, schema, runtime, or cross-language compatibility changes.
- Include focused tests for behaviour changes.
- Open a draft pull request early when a change crosses repositories or more than one working session.

Public contracts, domain vocabulary, evidence authority, provider authentication or writes, package releases, runtime support, and breaking changes are Governed. They require a named human reviewer. The agent that produced the change cannot approve or merge it.

## Taste

- Prefer a small explicit contract to a clever framework.
- Put provider complexity in adapters, not in the domain model.
- Make invalid or unreviewed states hard to mistake for accepted facts.
- Choose names that an adviser and a developer can both understand.
- Keep examples executable and honest about what is mocked.
- If a rule here conflicts with real domain evidence, stop and raise the conflict instead of coding around it.
