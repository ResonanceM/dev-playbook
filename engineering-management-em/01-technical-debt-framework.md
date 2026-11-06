# Hantering och förhandling av teknisk skuld (EM Playbook)

Teknisk skuld är inte ett fult ord – det är ett finansiellt lån som tagits för att accelerera tid till marknad. Som Engineering Manager (EM) gäller det att hantera det strukturerat.

---

## 📊 Teknisk skuld-taxonomi

1. **Deliberate & Prudent (Medveten & Prudentlig):**
   * *Exempel:* "Vi skippar testsviten för denna funktion för att hinna till mässan på torsdag, men vi vet exakt var skuld har skapats."
   * *Åtgärd:* Planera in återbetalning i nästa sprint.
2. **Accidental & Legacy (Oavsiktlig & Föråldrad):**
   * *Exempel:* Kodbasen växte från en monolit till mikroservrar utan att gränserna rätades ut; arkitekturen matchar inte dagens krav.
   * *Åtgärd:* Refaktorera inkrementellt i samband med att nya funktioner byggs i samma modul.
3. **Bit Rot (Mjukvaruröta):**
   * *Exempel:* Beroenden, ramverksversioner eller Node-runtimes som når EOL (End of Life) och drar med sig säkerhetsrisker.
   * *Åtgärd:* Dedikera en fast andel av kapaciteten till uppgraderingar.

---

## ⚖️ Den gyllene 20%-regeln för teknikalisering
Förhandla med produktchefen (PM) om en fast fördelning av teamets totala kapacitet:
* **70% Feature Velocity:** Kundvärde och nya funktioner.
* **20% Architecture & Tech Debt:** Refaktorisering, uppgraderingar, prestanda och testtäckning.
* **10% Innovation & Spikes:** R&D, utforskande av nya verktyg och AI-experiment.
