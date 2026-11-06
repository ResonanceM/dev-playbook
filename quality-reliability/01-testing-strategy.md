# Testing Strategy: Confidence at the Right Cost

Testing should provide fast feedback and meaningful confidence. The goal is not maximum test count.

## Test portfolio

- **Unit tests:** pure logic and small isolated behavior.
- **Component tests:** UI or service components with controlled dependencies.
- **Integration tests:** real interactions with databases, queues, or services.
- **Contract tests:** compatibility between producers and consumers.
- **End-to-end tests:** critical user journeys across system boundaries.
- **Performance tests:** load, stress, soak, and capacity behavior.
- **Security tests:** authorization, abuse, dependency, and configuration checks.
- **Exploratory tests:** unexpected behavior and usability.

Use a balanced portfolio; end-to-end tests are valuable but slower and more brittle.

## Test quality

Tests should be deterministic, isolated, readable, and focused on behavior. Avoid asserting implementation details. Use realistic data and representative edge cases. Quarantine flaky tests only with an owner and expiry date.

## Test data

Create synthetic or appropriately anonymized data. Avoid copying production personal data into lower environments. Make test setup reproducible and clean up created resources.

## Critical scenarios

Test permissions, duplicate requests, concurrency, timeout, retry, partial failure, migration compatibility, empty states, accessibility, and recovery—not only happy paths.

## CI strategy

Run fast checks on every change; run heavier suites at appropriate stages. Make failures diagnosable and preserve artifacts. Track flaky-test rate and time-to-feedback.

## Checklist

- [ ] Test layers match system boundaries.
- [ ] Critical business invariants are covered.
- [ ] Authorization and negative cases are tested.
- [ ] Concurrency and failure behavior are tested.
- [ ] Test data is safe and reproducible.
- [ ] Flaky tests have accountable owners.
- [ ] Production-like performance and migration tests exist where needed.
