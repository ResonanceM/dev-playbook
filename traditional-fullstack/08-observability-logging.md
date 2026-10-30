# Observability, Structured Logging & Tracing

Senior engineers treat frontend & fullstack monitoring not as an afterthought, but as a core requirement for production readiness.

---

## 📊 Observability Triad

| Pillar | Definition | Primary Tools |
| :--- | :--- | :--- |
| **Logs** | Discrete structured events (`{ level: 'error', userId, context }`) | Datadog, Pino, Winston |
| **Metrics** | Aggregated numerical health metrics (p95 latency, error rate %) | Prometheus, Grafana |
| **Traces** | End-to-end request lifecycle across frontend & backend microservices | OpenTelemetry, Datadog APM, Sentry |

---

## 🛡️ Logging Best Practices for Senior Developers

1. **Structured JSON Logs:** Never log raw text (`print("error happened")`). Always output JSON with standardized fields (`timestamp`, `trace_id`, `user_id`, `environment`).
2. **Never Log Sensitive Data (PII/Secrets):** Strip passwords, credit cards, JWT tokens, and PII before shipping logs to third-party providers.
3. **Trace Context Propagation:** Pass `x-request-id` or OpenTelemetry headers from client fetch calls to backend APIs so a single click can be traced end-to-end.

---

## 🔗 Essential Resources & Repositories
* [getsentry/sentry-javascript](https://github.com/getsentry/sentry-javascript) — Cross-platform error tracking and performance monitoring.
* [open-telemetry/opentelemetry-js](https://github.com/open-telemetry/opentelemetry-js) — Vendor-agnostic observability framework.
* [pinojs/pino](https://github.com/pinojs/pino) — Super fast, low-overhead Node.js/browser logger.
