# Observerbarhet, Strukturerad Loggning och Tracing

För att felsöka i produktion krävs strukturerad data, inte godtyckliga `console.log`-rader.

---

## 📊 Observerbarhetens tre pelare
1. **Logs (Loggar):** Diskreta, strukturerade JSON-händelser (`{ level: 'error', userId, message }`).
2. **Metrics (Mätetal):** Aggregerade numeriska mätvärden (felprocent %, p95-latens).
3. **Traces (Spårning):** End-to-end livscykel för ett anrop som passerar från klienten genom API-gateway till mikrotjänster och databas via OpenTelemetry.

---

## 🛠️ Regler för senior loggning
* **Aldrig rå text:** Logga alltid i strikt JSON-format med fält som `timestamp`, `trace_id`, `user_id` och `environment`.
* **PII-maskering:** Rensa bort lösenord, kreditkortsnummer, tokens och personnummer innan loggar skeppas till Datadog eller Sentry.
* **Context Propagation:** Skicka alltid med `x-request-id` i HTTP-huvuden mellan frontend och backend.
