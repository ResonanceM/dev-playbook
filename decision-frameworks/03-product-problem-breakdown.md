# Product Problem Decomposition: From Ambiguity to Delivery

A repeatable way to turn an ambiguous request into a coherent, testable engineering plan.

## The six stages

### 1. Problem and outcome
- Who experiences the problem?
- What job are they trying to complete?
- What evidence shows this matters?
- What is the baseline and desired outcome?
- What is explicitly out of scope?

Write an outcome statement, not a feature prescription. Example: “Reduce failed invoice submissions for first-time users,” rather than “Add a wizard.”

### 2. User journeys and functional behavior
Map entry points, actors, permissions, happy paths, alternate paths, and terminal states. Define acceptance criteria in observable terms.

Include empty, loading, stale, partial, duplicate, offline, timeout, cancellation, and permission-denied states. Consider concurrent edits and repeated submissions.

### 3. Non-functional requirements
Specify measurable expectations for:
- Latency: user-perceived and service-side percentiles.
- Availability and durability: which operations must work, and what data loss is tolerable?
- Scale: normal, peak, burst, and growth assumptions.
- Security/privacy: data classification, authorization, retention, residency, audit.
- Accessibility: keyboard, screen reader, contrast, motion, and semantic structure.
- Operability: ownership, alerts, dashboards, support, and recovery objectives.

### 4. Architecture and data
Define boundaries, responsibilities, contracts, source of truth, state ownership, data lifecycle, and integration patterns. Draw a context diagram and sequence diagram for the riskiest flow.

### 5. Operations and measurement
Specify logs, metrics, traces, product analytics, feature flags, dashboards, alerts, support procedures, and rollout strategy. Keep operational telemetry distinct from product analytics.

### 6. Delivery and risk
Break work into vertical slices that produce user-visible or independently verifiable value. Identify dependencies, critical path, migration steps, test environments, unknowns, and rollback constraints.

## Acceptance criteria

Prefer examples that can be tested:

**Given** an authenticated user with permission to edit an invoice  
**When** they submit a valid invoice  
**Then** the invoice is persisted once, a confirmation is shown, and a retry does not create a duplicate.

Define behavior for invalid input, expired sessions, duplicate requests, and partial downstream failure too.

## Risk-first planning

Rank unknowns by impact and uncertainty. Prototype the highest-risk assumptions early: external API behavior, data migration duration, authorization model, peak throughput, model quality, or vendor limitations.

Use a risk register:

| Risk | Likelihood | Impact | Signal | Mitigation | Owner |
|---|---|---|---|---|---|
| Migration lock contention | Medium | High | Long-running DDL in staging | Online migration and rehearsal | Backend lead |
| Vendor rate limit | High | Medium | 429 responses in load test | Backoff, queue, quota agreement | Integrations owner |

## Example: collaborative invoice editing

**Outcome:** Reduce handoff time and conflicting edits for finance teams.

**Phase 1 scope:** Presence and concurrent field updates. Non-goals: rich text collaboration, full version history, offline merge.

**Design questions:** Who owns conflict resolution? Are updates last-write-wins, field-level versioned, or CRDT-based? What is the consistency expectation? How are reconnects and authorization handled?

**Delivery slices:** permissioned session join → persisted versioned updates → presence → reconnect/recovery → progressive rollout.

**Release gates:** concurrency tests, audit coverage, reconnect tests, latency dashboard, support runbook, and rollback plan.

## Ready-for-build checklist

- [ ] User problem, evidence, outcome, and non-goals are clear.
- [ ] Primary and failure journeys are mapped.
- [ ] Acceptance criteria are testable.
- [ ] NFRs have measurable targets and workload assumptions.
- [ ] Data ownership, permissions, and lifecycle are defined.
- [ ] Integration contracts and dependencies are known.
- [ ] Highest-risk assumptions have validation plans.
- [ ] Observability, rollout, and rollback are planned.
