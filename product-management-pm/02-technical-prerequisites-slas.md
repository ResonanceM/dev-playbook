# Non-Functional Requirements (NFRs), SLAs och Latensbudgetar

Som PM måste du definiera de icke-funktionella kraven tillsammans med tech leads tidigt i produktcykeln.

---

## 🎯 Skillnaden mellan SLI, SLO och SLA

```text
SLI (Indicator)  ──► Faktisk mätning i drift (t.ex. 99.4% lyckade anrop)
SLO (Objective)  ──► Det interna tekniska målet (t.ex. 99.9% tillgänglighet)
SLA (Agreement)  ──► Det legala avtalet med kunden (t.ex. 99.5% med ekonomisk kompensation vid brott)
```

---

## 📊 Latensbudgetar per interaktionstyp

| Användarflöde | Max tillåten $p95$-latens | Teknisk lösning |
| :--- | :--- | :--- |
| **UI-respons** (Klick på knapp, toggle) | $< 100	ext{ms}$ | Optimistiska UI-uppdateringar |
| **Sidnavigering / Laddning** | $< 1.0	ext{s}$ | Server-side rendering (SSR) + Edge Caching |
| **Tunga sökningar / Filter** | $< 2.0	ext{s}$ | Debouncerade anrop + indexerade databaser |
| **Bakgrundsjobb / AI-analys** | Asynkront | Progress-bar med webhooks eller polling |
