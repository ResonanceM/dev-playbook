# System Design Review Framework

A system design review should expose assumptions, failure modes, and operational cost before they become production incidents.

## Review sequence

1. **Requirements:** users, use cases, traffic profile, data sensitivity, consistency, latency, availability, and cost constraints.
2. **Boundaries:** system context, trust boundaries, ownership, external dependencies, and domain responsibilities.
3. **Data:** entities, access patterns, invariants, indexes, retention, migration, backup, and restore.
4. **Flow:** request lifecycle, synchronous versus asynchronous work, idempotency, retries, and ordering.
5. **Scale:** bottlenecks, concurrency, hot keys, queues, fan-out, caching, and backpressure.
6. **Failure:** dependency outage, partial success, overload, region loss, poison messages, and recovery.
7. **Security:** identity, authorization, secrets, encryption, abuse cases, audit, and supply chain.
8. **Operations:** SLOs, telemetry, alerts, runbooks, ownership, deployment, and rollback.

## Core questions

- What is the source of truth for each important datum?
- Which invariants must always hold?
- What happens when a request is delivered more than once?
- Can a user observe stale or partial state? Is that acceptable?
- What happens if a downstream dependency is slow rather than unavailable?
- How is load shed before the system collapses?
- How can operators determine what happened to one request?
- Can the system be restored from backup, and has restoration been tested?
- What is the smallest design that meets the measured requirement?

## Common failure patterns

- Microservices before clear domain boundaries or independent team ownership.
- A cache treated as the source of truth without a consistency strategy.
- Unbounded queues or fan-out that convert overload into delayed failure.
- Retries without timeouts, jitter, or idempotency.
- Database migrations that assume table size and lock behavior are negligible.
- “High availability” claims without tested failover and recovery procedures.
- Security checks performed only in the UI.
- Shared databases that couple service deployments invisibly.

## Review output

Record: decision, rejected alternatives, assumptions, risks, operational owner, validation experiments, rollout stages, and conditions that would trigger redesign.
