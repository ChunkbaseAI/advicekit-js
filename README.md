# AdviceKit JS

AdviceKit JS is the TypeScript implementation of AdviceKit, an open-source toolkit for building evidence-aware financial-advice software.

It helps applications turn transcripts, notes, documents, and provider records into sourced observations, explicit unknowns and conflicts, review items, and draft fact-finds. Generated output remains proposed until an authorised person reviews it.

This repository is at the design and bootstrap stage. Public interfaces are not yet stable.

The Python implementation lives in [ChunkbaseAI/advicekit](https://github.com/ChunkbaseAI/advicekit).

## What belongs here

- Stable TypeScript contracts for evidence, observations, review, and draft advice records
- Validation and transformation tools that do not hide uncertainty
- Provider adapters that preserve provider-native identifiers and unsupported fields
- Tests and fixtures that demonstrate the same behaviour as AdviceKit Python

Bun will manage development, dependencies, tests, and releases. The published library should remain usable from its declared JavaScript runtimes and must not rely on Bun-only runtime APIs without an explicit package boundary.

## What does not belong here

- Autonomous financial advice or suitability decisions
- Silent writes to authoritative client records
- Chunkbase's private evaluation and production workflow logic
- Tutorial collections and architecture demonstrations, which belong in `financial-advice-ai`

## Licence

Apache License 2.0. See [LICENSE](./LICENSE).

## Contributing

Read [AGENTS.md](./AGENTS.md), [CONTEXT.md](./CONTEXT.md), and [CONTRIBUTING.md](./CONTRIBUTING.md) before making a change.
TypeScript contracts and tools for evidence-aware financial-advice software.
