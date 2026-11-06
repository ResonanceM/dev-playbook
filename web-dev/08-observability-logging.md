# Observability: Logs, Metrics, Traces, and OpenTelemetry

Observability helps teams explain system behavior from emitted evidence. It is not synonymous with collecting more data.

## Three complementary signals

- **Metrics:** aggregated numeric behavior over time; ideal for alerting and trends.
- **Logs:** discrete events with context; useful for diagnosis and audit.
- **Traces:** causal path across services; useful for latency and dependency analysis.

Use correlation identifiers and distributed trace context to connect signals.

## Structured logging

Prefer structured fields over interpolated prose. A useful event may include timestamp, severity, service, environment, version, trace ID, request ID, operation, outcome, and duration. Add user or tenant identifiers only when justified, protected, and non-sensitive.

Never log passwords, session cookies, access tokens, raw payment data, or unnecessary personal data. Apply redaction at source and access controls at the logging platform.

## Metrics

Useful service metrics include request rate, error rate, duration distributions, saturation, queue age, and dependency health. Use histograms for latency percentiles where supported. Avoid high-cardinality labels such as raw user IDs, request IDs, or arbitrary URLs.

## Distributed tracing

Instrument inbound requests, outbound dependencies, database calls, queue producers/consumers, and important business operations. Propagate context across async boundaries. Add spans for meaningful work, not every trivial function.

## OpenTelemetry

OpenTelemetry provides vendor-neutral APIs, SDKs, semantic conventions, and exporters for traces, metrics, and logs. Establish consistent resource attributes and sampling policy. Tail sampling may preserve high-value traces such as errors or slow requests while controlling volume.

## Alerting

Alert on user impact and actionable symptoms, preferably tied to SLO burn rates. A page should have an owner and a clear next action. Use tickets or dashboards for lower-urgency trends.

## Checklist

- [ ] Every service has owner, version, and environment attributes.
- [ ] Trace context crosses service and queue boundaries.
- [ ] Logs are structured and redacted.
- [ ] Metrics avoid unbounded cardinality.
- [ ] Dashboards show traffic, errors, latency, and saturation.
- [ ] Alerts are actionable and tested.
- [ ] Sampling, retention, and access are cost/privacy aware.
