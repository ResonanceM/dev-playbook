# Product Analytics, Event Taxonomy, and Privacy

Product analytics explains how people use a product. It should complement—not replace—qualitative research, support feedback, and operational telemetry.

## Start with decisions

Before adding an event, state which product question it will answer and what decision could change. If no decision depends on the data, do not collect it.

## Event design

A consistent event contract may include:
- `event_name` with stable naming such as `checkout_started`.
- `event_version` for schema evolution.
- `occurred_at` and ingestion timestamp.
- `anonymous_id` or pseudonymous actor ID where appropriate.
- `session_id` where justified.
- `source` and application version.
- Explicit properties with documented types and allowed values.

Prefer past-tense business events over UI implementation events. Avoid names tied to button labels or component names.

## Taxonomy example

| Event | Trigger | Useful properties |
|---|---|---|
| `trial_started` | Trial is successfully created | plan, acquisition channel |
| `invoice_created` | Invoice persistence succeeds | currency, item_count |
| `payment_failed` | Payment provider reports failure | safe failure category |
| `report_exported` | Export is ready | format, row_count_band |

Do not send raw emails, names, payment details, secrets, or free-text fields by default.

## Data quality

Validate schemas, required fields, event volume, duplicate behavior, and identity stitching. Define whether events are emitted client-side, server-side, or both. Server-side events are usually more authoritative for completed business actions.

## Privacy and governance

Apply data minimization, purpose limitation, retention limits, access controls, consent/opt-out requirements, and deletion workflows according to applicable law and policy. Pseudonymous identifiers may still be personal data. Involve privacy/legal experts for jurisdiction-specific interpretation.

## Analytics versus observability

Product analytics measures user behavior and outcomes. Observability measures system health and request behavior. Keep separate access controls, retention, sampling, and naming conventions where needs differ.

## Checklist

- [ ] Every event answers a defined question.
- [ ] Event owner and schema are documented.
- [ ] Schema validation and versioning exist.
- [ ] Sensitive data is excluded or explicitly governed.
- [ ] Consent, retention, deletion, and access are addressed.
- [ ] Business-critical events are emitted from authoritative sources.
