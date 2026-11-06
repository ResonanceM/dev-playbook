# Production Readiness, Incident Response, and Learning

A production service needs more than a successful deployment. It needs ownership, observability, support, and recovery.

## Readiness review

- Named service owner and escalation path.
- Documented dependencies and data classification.
- SLOs, dashboards, and actionable alerts.
- Structured logs, traces, and correlation IDs.
- Capacity and load-test evidence.
- Backup/restore and disaster-recovery expectations.
- Security review and vulnerability response.
- Deployment, rollback, and migration procedure.
- Runbook for common failure modes.
- Customer/support communication plan.

## Incident response

1. Detect and acknowledge.
2. Assign incident commander and technical leads.
3. Establish impact, scope, and timeline.
4. Mitigate user harm; restore service before pursuing root cause.
5. Communicate status at an agreed cadence.
6. Verify recovery with telemetry and user journeys.
7. Preserve evidence and document timeline.
8. Run a blameless review and assign follow-up actions.

## Severity

Define severity based on customer impact, data/security risk, scope, and duration. Avoid severity inflation. Establish who can declare, downgrade, and close an incident.

## Post-incident review

Focus on contributing conditions and system defenses, not individual blame. Ask what made the incident possible, what made detection/recovery slow, and which changes reduce recurrence or blast radius.

Actions should have owners, due dates, and verification criteria. Track systemic themes across incidents.

## Runbook template

- Service and owner
- Symptoms and impact
- Dashboards and queries
- Immediate mitigation
- Diagnostic steps
- Dependency status
- Recovery/rollback
- Escalation contacts
- Customer communication guidance
- Follow-up link

## Checklist

- [ ] On-call knows how to identify and mitigate common failures.
- [ ] Alerts are actionable and tested.
- [ ] Restore and rollback are rehearsed.
- [ ] Incident roles and communication are clear.
- [ ] Reviews result in owned, verified improvements.
