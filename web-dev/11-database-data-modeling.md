# Database Design, Transactions, and Data Lifecycle

The database is part of the product contract. Design around invariants and access patterns, then validate with real query plans.

## Modeling

- Identify entities, relationships, ownership, and lifecycle.
- Normalize to reduce update anomalies; denormalize intentionally for measured read needs.
- Define constraints in the database where possible: foreign keys, uniqueness, checks, and not-null rules.
- Choose identifiers and timestamp semantics consistently.
- Document soft-delete versus hard-delete behavior and retention requirements.

## Indexing

Index actual query patterns. Consider selectivity, composite index order, write overhead, storage, and query planner behavior. Use `EXPLAIN`/query plans and production-like data distributions. Too many indexes slow writes and complicate migrations.

## Transactions and concurrency

Use transactions to protect invariants across related writes. Choose isolation based on anomalies the business can tolerate. Use optimistic concurrency/version columns for collaborative edits; use locking when necessary and bounded. Never assume application-level read-then-write logic is race-free.

## Migrations

Prefer expand-and-contract:
1. Add compatible schema.
2. Deploy code that can read/write old and new forms as needed.
3. Backfill in bounded, observable batches.
4. Verify consistency.
5. Switch reads/writes.
6. Remove obsolete schema only after old code is gone.

Rehearse migrations on production-like data. Understand lock duration, replication lag, rollback limits, and backup requirements. A destructive migration may not be safely reversible.

## Data lifecycle

Define classification, ownership, retention, archival, deletion, export, backup, restore, and legal hold processes. Backups are only useful if restoration is tested. Encrypt backups and restrict access.

## Checklist

- [ ] Constraints protect critical invariants.
- [ ] Query plans and indexes are measured.
- [ ] Concurrency and transaction boundaries are explicit.
- [ ] Migrations are backward-compatible and rehearsed.
- [ ] Backups and restore objectives are tested.
- [ ] Retention and deletion requirements are implemented.
