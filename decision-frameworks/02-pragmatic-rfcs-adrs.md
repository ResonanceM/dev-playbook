# Pragmatiska RFCs och ADRs (Inspirerat av Gergely Orosz)

Ett ramverk för att driva igenom tekniska beslut i tillväxtbolag och skala upp utan att drabbas av byråkrati eller "analysis paralysis".

---

## ⚖️ Typ 1 vs. Typ 2-beslut

1. **Typ 1-beslut (Irreversibla / Envågsdörrar):** 
   * Val av primär databas, publika API-kontrakt, molnleverantör, övergripande autentiseringsarkitektur.
   * *Krav:* Kräver formell **RFC (Request for Comments)** och bred förankring bland tech leads och ledning.
2. **Typ 2-beslut (Reversibla / Tvåvägsdörrar):**
   * Val av UI-komponentbibliotek, mindre tillståndsbibliotek, interna verktyg eller lint-regler.
   * *Krav:* Kan tas snabbt på teamnivå utan omständiga processer. Om det visar sig fel kan man enkelt byta spår.

---

## 📄 Standardstruktur för en Pragmatisk RFC

```markdown
# RFC: [Titel på initiativet]
**Författare:** [Ditt Namn] | **Datum:** [YYYY-MM-DD] | **Status:** Draft / Under granskning / Godkänd

## 1. Executive Summary & Affärspåverkan
Vilket problem löser detta för användaren och bolaget? Vilka mätetal (KPI:er) påverkas?

## 2. Icke-mål (Non-Goals)
Vad är medvetet UTESTÄNGT från detta förslag för att undvika scope creep?

## 3. Övergripande lösningsdesign
Systemskisser, dataflöden och gränssnitt mot existerande system.

## 4. Konsekvenser för drift, säkerhet och ekonomi
Hostingkostnader, licenser, GDPR-aspekter samt underhållsbörda för framtida team.
```
