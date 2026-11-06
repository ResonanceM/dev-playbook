# System Design Fundamentals

A reliable design starts with workload and invariants, not a diagram full of fashionable components.

## Clarify the workload

Estimate normal and peak request rates, burst shape, read/write ratio, payload size, data growth, geographic distribution, concurrency, and latency expectations. Distinguish measured facts from assumptions.

## Data and consistency

Choose storage based on access patterns, transactions, query needs, durability, operational skills, and recovery requirements. Relational databases are strong defaults for structured data and transactional invariants. Document stores, key-value stores, search engines, and analytical warehouses solve different problems; they are not interchangeable.

Define consistency requirements per operation. “Eventually consistent” must specify acceptable staleness and user-visible behavior.

## Caching

Cache only when there is a clear performance or cost benefit. Define key, TTL, invalidation, stale behavior, stampede protection, and privacy boundary. Cache invalidation is a correctness problem, not just a performance setting.

## Asynchronous work

Use queues for buffering, decoupling, and long-running tasks. Design for duplicate delivery, retries, poison messages, ordering constraints, and replay. Exactly-once processing is rarely a simple broker setting; idempotent effects are usually the practical goal.

## Scale patterns

- Horizontal scaling for stateless compute.
- Read replicas for suitable read-heavy workloads.
- Partitioning/sharding only when simpler options are insufficient.
- Backpressure and admission control during overload.
- CDN/edge caching for suitable static or safely cacheable content.
- Bulkheads to isolate critical resources.

## Design for evolution

Prefer additive schema changes, compatibility windows, explicit contracts, and gradual migrations. Keep service boundaries aligned with domain ownership and team autonomy. Distributed systems add network failure, deployment coordination, observability, and data consistency costs.

## Capacity thinking

Use Little's Law as a useful queueing relationship: average work in system = throughput × average time in system. It is not a substitute for load testing or tail-latency analysis.

## Checklist

- [ ] Workload and SLO assumptions are explicit.
- [ ] Data invariants and source of truth are defined.
- [ ] Failure modes and overload behavior are understood.
- [ ] Cache and async semantics are documented.
- [ ] Migrations and backward compatibility are planned.
- [ ] Cost and operational ownership are visible.
