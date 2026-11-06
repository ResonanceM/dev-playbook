# API Architecture: REST, GraphQL, RPC, Events, and WebSockets

Select a communication style based on consumer needs, coupling, latency, consistency, and operational capability.

## Comparison

| Style | Strengths | Costs / risks | Typical fit |
|---|---|---|---|
| REST/HTTP | Familiar, cacheable, broad tooling | Resource modeling and multiple round trips | Public and service APIs |
| GraphQL | Client-selected shape; typed schema | Resolver performance, authorization complexity, caching | Many clients with differing data needs |
| RPC / tRPC / gRPC | Explicit procedure contracts; efficient typed calls | Coupling to service contracts or generated clients | Internal service calls and strongly typed apps |
| WebSockets | Bidirectional low-latency updates | Connection lifecycle, fan-out, auth refresh, scaling | Collaboration, live status |
| Server-Sent Events | Simple server-to-client stream | One-way; reconnect semantics | Notifications and live feeds |
| Async messaging | Decoupling and buffering | Eventual consistency, duplicates, ordering | Background jobs and integration workflows |

## API contract design

- Use explicit request/response schemas and validation at trust boundaries.
- Define stable error codes and machine-readable error shapes.
- Specify pagination, sorting, filtering, and maximum page size.
- Define authentication and authorization per operation and object.
- Use idempotency keys for retryable create/payment-like operations.
- Version deliberately; prefer additive evolution and compatibility windows.
- Set request size limits, deadlines, and rate limits.
- Document examples, limits, and deprecation policy.

## Error model

Separate validation errors, authentication failures, authorization failures, conflicts, rate limits, transient dependency errors, and unexpected server errors. Do not return stack traces or internal details to clients.

## Retries and idempotency

A client may not know whether a timed-out request completed. For non-idempotent operations, use an idempotency key and persist the outcome for a defined retention period. Retry only transient failures, with bounded exponential backoff and jitter. Do not retry validation or authorization errors.

## Choosing

- Prefer REST for straightforward resource APIs and broad interoperability.
- Use GraphQL when flexible client data composition justifies schema and resolver governance.
- Use RPC for explicit internal contracts and efficient service-to-service calls.
- Use streaming only when the product needs ongoing updates; define reconnect, replay, and authorization behavior.
- Use messaging for work that should be decoupled from the request lifecycle.

## Contract checklist

- [ ] Schema and examples are version-controlled.
- [ ] AuthN and object-level AuthZ are tested.
- [ ] Limits, timeouts, pagination, and rate limiting are explicit.
- [ ] Errors are stable and safe.
- [ ] Duplicate delivery and retries are safe.
- [ ] Compatibility and deprecation are documented.
