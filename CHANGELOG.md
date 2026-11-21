# Changelog

## 0.2.3 — 2026-11-21

- Built on TalaDB engine v0.13.3. That engine release fixes React Native on iOS only: the core engine, its Android build and the C ABI are unchanged, so this release behaves like 0.2.2. No API or storage format change; no index rebuild needed. Details: [engine changelog](https://github.com/taladb/taladb/blob/main/CHANGELOG.md#0133--2026-11-21).

## 0.2.2 — 2026-11-20

- Built on TalaDB engine v0.13.2. **If you use encryption, update.** In 0.2.1 and earlier, opening an encrypted database without a passphrase could damage it: from then on the correct passphrase could not open it. Now that open throws `TalaDBException` with code `ENCRYPTION` and writes nothing, as the `passphrase` docs already said. Opening a plaintext database with a passphrase also throws now, instead of leaving a `.taladb-salt` file next to it. A file already damaged by an earlier release is refused with or without the passphrase; the repair needs Rust and is described in the engine changelog.
- `count` with a filter an index fully covers no longer reads documents, and an `aggregate` pipeline that starts with `$match` then `$group` reads only the fields it uses. `updateMany`, `updateOne`, `deleteOne` and `deleteMany` no longer skip a match that another write committed at the same moment. Reads no longer wait behind a queued write; under heavy concurrent reads, writes can be slower than in 0.2.1. An indexed equality query returns each document once, and `aggregate` over `$or`, multi-field `$and` and text-search plans gives the same result on every call. No API, storage format or C ABI change; no index rebuild needed. Details: [engine changelog](https://github.com/taladb/taladb/blob/main/CHANGELOG.md#0132--2026-11-20).

## 0.2.1 — 2026-11-15

- Built on TalaDB engine v0.13.1. Text search now returns the same scores and order for the same query on the same data; before, documents matching three or more query terms could swap places between identical calls. Calling `createVectorIndex` again with HNSW options on an existing index no longer leaves the replaced graph in the vector cache, where it held memory and slowed exact search on large indexes. Results were never affected. No API, storage format or C ABI change; no index rebuild needed. Details: [engine changelog](https://github.com/taladb/taladb/blob/main/CHANGELOG.md#0131--2026-11-15).

## 0.2.0 — 2026-10-30

- Built on TalaDB engine v0.13.0: faster sorted pages, selective queries and exact vector search on large indexes. Sorting a field that holds NaN no longer crashes, and indexed queries on strings containing NUL characters now return what a full scan returns. Details: [engine changelog](https://github.com/taladb/taladb/blob/main/CHANGELOG.md#0130--2026-10-29).
- `0.12.1` on Maven Central was published by mistake: it is 0.1.1 built on engine v0.12.0. Pin `0.2.0` exactly. Version ranges (`+`, `latest.release`) and update tools such as Dependabot and Renovate rank `0.12.1` higher and would pick it.

## 0.1.2 — not released

- Prepared on engine v0.12.1 but never published; its changes are in 0.2.0.

## 0.1.1 — 2026-10-04

- Fixed: leaving a screen no longer freezes the UI while its live queries unsubscribe.
- Fixed: new live queries no longer wait behind running ones, so screens show their content immediately.
- `close()` waits for at most one poll, however many live queries are open.

## 0.1.0 — 2026-10-03

- First release: TalaDB for native Android apps in Kotlin.
- Typed and JSON collections, filters, updates, and secondary, compound, full-text and vector indexes.
- Live queries as `Flow`, with projection.
- BM25 full-text search with stopwords, vector search (flat and HNSW) and hybrid search.
- Encryption at rest and migrations.
- Built on TalaDB engine v0.12.0; `minSdk` 24.
