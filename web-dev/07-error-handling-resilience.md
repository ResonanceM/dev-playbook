# Error Handling and Resilience

Resilience is the ability to provide useful behavior under failure—not the ability to hide every error.

## Error taxonomy

Classify errors by action:
- Validation/business rule: correct the input or explain the rule.
- Authentication/authorization: re-authenticate or request access.
- Conflict: refresh, merge, or resolve concurrent changes.
- Rate limit: wait and retry according to server guidance.
- Transient dependency/network: bounded retry may help.
- Permanent dependency/configuration: alert and fail clearly.
- Unknown defect: preserve diagnostics and return a safe response.

Use typed/domain errors internally and stable, non-sensitive error responses externally.

## Timeouts and deadlines

Set explicit timeouts for outbound calls. Propagate an overall deadline through downstream work so nested services do not continue processing after the caller has given up. Choose timeouts based on measured latency and user expectations.

## Retry policy

Retry only operations that are safe to repeat or protected by idempotency. Use bounded exponential backoff with jitter, respect `Retry-After`, cap total attempts and elapsed time, and avoid retry storms.

## Circuit breakers and bulkheads

Circuit breakers can stop repeated calls to a failing dependency, but need clear open/half-open behavior and monitoring. Bulkheads isolate resource pools so one slow dependency cannot exhaust all capacity. Use them where dependency behavior and workload justify the complexity.

## Queue and worker resilience

Use bounded queues, dead-letter handling, poison-message policy, idempotent consumers, visibility/lease renewal, and replay procedures. Monitor queue age as well as depth. Define ordering guarantees explicitly.

## Frontend resilience

Provide scoped error boundaries, meaningful retry affordances, stale-data behavior, and preserved user input where safe. Do not show raw server exceptions. Distinguish a failed save from a failed confirmation; the server may have committed even if the response was lost.

## Anti-patterns

- Infinite retries.
- Catch-and-ignore exceptions.
- Retrying non-idempotent writes blindly.
- One global error boundary with no recovery path.
- Fallbacks that silently corrupt or misrepresent data.
- Circuit breakers without a recovery owner or alert.

## Checklist

- [ ] Timeouts and deadlines are explicit.
- [ ] Retries are bounded, jittered, and safe.
- [ ] Writes are idempotent or deduplicated.
- [ ] Queues are bounded and observable.
- [ ] Partial failure is represented in the API/UI.
- [ ] Error responses are safe and actionable.
- [ ] Recovery paths are tested.
