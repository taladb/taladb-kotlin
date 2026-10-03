# Changelog

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
