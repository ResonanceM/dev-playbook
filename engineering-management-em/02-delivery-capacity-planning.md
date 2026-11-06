# Delivery Capacity and Planning

Planning is a model of uncertainty, not a promise that every estimate will be exact.

## Capacity

Start with actual available working time after leave, support, on-call, meetings, maintenance, and other commitments. Use historical throughput or cycle time where possible. Avoid planning every person at 100% utilization; high utilization increases queues and makes delivery less predictable.

A buffer is a risk response, not a fixed universal percentage. Size it from historical variance, dependency uncertainty, and novelty.

## Decompose work

Prefer vertical slices that produce testable outcomes. Separate discovery, implementation, migration, security review, rollout, and operational readiness when they have distinct risks.

Break large items until:
- Acceptance criteria are clear.
- Dependencies are visible.
- Work can be reviewed and tested independently.
- Progress can be demonstrated within a short feedback loop.

## Estimation

Use ranges and confidence levels. State assumptions. For novel work, time-box discovery or a spike and update the estimate with evidence. Avoid converting estimates into individual performance commitments.

## Dependency management

Identify external teams, vendors, data migrations, approvals, environments, and release windows. Assign owners and dates to critical dependencies. Reduce coordination by agreeing contracts early and using mocks/contract tests.

## Flow metrics

Track lead time, cycle time, throughput, work in progress, blocked time, and escaped defects. Use trends to improve the system; do not use metrics to rank individuals.

## Delivery review

At each checkpoint ask: what changed, what is blocked, what risk increased, what can be de-scoped, and what evidence changes the forecast?
