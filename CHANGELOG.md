# Changelog

## 0.13.0 — 2026-10-30

- Built on TalaDB engine v0.13.0: faster sorted pages, selective queries and exact vector search on large indexes. Sorting a field that holds NaN no longer crashes, and indexed queries on strings containing NUL characters now return what a full scan returns. Details: [engine changelog](https://github.com/taladb/taladb/blob/main/CHANGELOG.md#0130--2026-10-29).
- **Versions now follow the engine.** This package is released with the version of the TalaDB engine it is built on, starting with 0.13.0.
- `0.12.1` on Maven Central was published by mistake: it is 0.1.1 built on engine v0.12.0. 0.13.0 replaces it and every earlier version.

## 0.1.2 — not released

- Prepared on engine v0.12.1 but never published; its changes are in 0.13.0.

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
