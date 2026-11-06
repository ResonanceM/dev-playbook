# 6-stegs ramverk för problemnedbrytning (Software Product Decomposition)

När du står inför ett komplext eller luddigt produktproblem ska du inte börja skriva kod direkt. Följ denna sexstegsprocess för att säkerställa att alla tekniska, affärsmässiga och operationella aspekter täcks in.

---

## 🔍 De 6 stegen i detalj

### Steg 1: Problem & Scope (Avgränsning)
* **Kärnvärde:** Exakt vilken användarfriktion eliminerar vi?
* **Explicita icke-mål:** Vad ska vi *inte* göra i denna version? (Ex: "Vi bygger realtidschatt i v1, men avstår från filöverföringar").
* **Yttre ramar:** Deadlines, regulatoriska krav och budget.

### Steg 2: Functional Specs & Edge Cases (Funktionella krav)
* **Huvudflöde:** Det gyllene flödet från start till mål.
* **Kritiska kantfall (Edge Cases):**
  * Nätverksavbrott mitt i en transaktion (offline-läge).
  * Samtidiga uppdateringar från flera användare (race conditions / optimisternas lås).
  * Tomma tillstånd (Empty states), laddningsskelett (skeletons) och felmeddelanden.

### Steg 3: Technical NFRs (Icke-funktionella krav)
* **Prestandabudget:** Maximal tillåten $p95$-latens (t.ex. $< 200	ext{ms}$) och max storlek på JS-bundle.
* **Skalbarhet & Last:** Förväntat antal QPS (Queries Per Second) vid toppar.
* **Säkerhet & Compliance:** Rollbaserad behörighet (RBAC), HttpOnly-cookies, CSP-huvuden och GDPR-krav.

### Steg 4: System Architecture (Systemarkitektur)
* **Rendering:** SPA vs. SSR vs. ISR baserat på SEO-krav och dynamiskt innehåll.
* **State Taxonomy:** Strikt uppdelning mellan Server State (TanStack Query), Client UI State (Zustand) och URL State.
* **API-protokoll:** tRPC för fullstack-monorepos, REST för publika integrationer, WebSockets för realtid.

### Steg 5: Operations & Telemetry (Drift & Mätbarhet)
* **Felhantering:** Lokala React Error Boundaries så att ett trasigt widget-kort inte kraschar hela skärmen.
* **Strukturerade loggar:** JSON-loggar med `trace_id` och bortrensning av känslig PII-data.
* **Produktanalys:** Event-taxonomi enligt `[Entity] [Action]` (t.ex. `invoice_created`).

### Steg 6: Delivery & Risk Management (Leverans & WBS)
* **Work Breakdown Structure:** Bryt ner i pull requests som vardera är under 250 rader kod.
* **Riskklassificering:** Identifiera Type 1 vs Type 2-risker.
* **Kapacitetsbuffert:** Applicera 20% buffert för oförutsedd teknisk skuld.
