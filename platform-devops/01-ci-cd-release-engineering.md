# CI/CD and Release Engineering

A delivery pipeline should make safe changes routine, fast, repeatable, and recoverable.

## Pipeline stages

1. Format, lint, type-check, and static analysis.
2. Unit and component tests.
3. Build immutable artifacts.
4. Dependency, secret, and artifact security checks.
5. Integration and contract tests.
6. Deploy to a representative environment.
7. Smoke tests and progressive production rollout.
8. Verify health and business signals; automatically halt or roll back when defined thresholds fail.

Adapt stages to risk and system architecture. Avoid pipelines that take so long that teams bypass them.

## Build once, promote many

Build a versioned artifact once and promote the same artifact through environments. Keep environment configuration external and auditable. Generate provenance and retain release metadata.

## Deployment strategies

| Strategy | Benefit | Risk / requirement |
|---|---|---|
| Rolling | Resource efficient | Mixed versions must be compatible |
| Blue/green | Fast traffic switch | Duplicate environment cost; data compatibility |
| Canary | Limits blast radius | Requires good telemetry and traffic control |
| Feature flag | Decouples deploy from exposure | Flag lifecycle and stale-flag debt |

## Safe database releases

Use expand-and-contract migrations and maintain compatibility between old and new application versions during rollout. Rollback of code does not necessarily roll back data; plan forward fixes where needed.

## Release checklist

- [ ] Artifact is immutable and traceable.
- [ ] Tests and security checks pass.
- [ ] Migration is compatible and rehearsed.
- [ ] Rollout and abort thresholds are defined.
- [ ] Feature flags have owners and expiry/review dates.
- [ ] Health and business metrics are monitored.
- [ ] Rollback or forward-recovery procedure is tested.
