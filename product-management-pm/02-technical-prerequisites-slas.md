# SLIs, SLOs, SLAs, and Performance Budgets

Reliability is a product feature. Define what users need and measure it from their perspective.

## Definitions

- **SLI:** a quantitative measure of service behavior, such as successful request ratio or latency.
- **SLO:** a target for an SLI over a time window.
- **SLA:** a contractual commitment, often with remedies or credits.
- **Error budget:** the allowed unreliability implied by an SLO.

Do not confuse an internal SLO with a contractual SLA.

## Good SLI design

Choose indicators that reflect successful user journeys. A server returning HTTP 200 may still have failed the user if the response is incomplete or incorrect.

Examples:
- Availability: eligible requests completed successfully.
- Latency: proportion of eligible requests under a threshold.
- Freshness: data age below a defined bound.
- Durability: acknowledged writes not lost.
- Correctness: valid business operations completed without invariant violation.

Define exclusions carefully; overly broad exclusions can hide real failures.

## Error budgets

A consumed error budget should trigger an explicit response: investigate causes, reduce risky releases, or invest in reliability. Do not use the budget as a target to spend.

## Latency budgets

Allocate end-to-end latency across browser, network, gateway, service, database, and dependencies. Measure percentiles; do not add unrelated p95 values as if they were guaranteed end-to-end percentiles.

## Example

For an interactive search journey, define:
- SLI: successful searches with a complete result response.
- SLO: 99.9% over a rolling 28-day window.
- Latency objective: a chosen percentage of searches complete within a product-validated threshold.
- Freshness: index lag remains within a documented tolerance.

Targets must be based on user need, cost, and current capability.

## Checklist

- [ ] SLI represents user-visible success.
- [ ] Measurement window and eligibility are explicit.
- [ ] SLO has an owner and dashboard.
- [ ] Error-budget policy is agreed.
- [ ] Alerts are tied to user impact.
- [ ] Dependencies and data freshness are included.
