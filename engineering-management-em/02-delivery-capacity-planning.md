# Kapacitetsplanering, Järntriangeln och Buffertar

Som EM är ditt primära ansvar att skydda teamet från utbrändhet samtidigt som du levererar förutsägbara resultat till affären.

---

## 📐 Järntriangeln (Scope, Tid, Resurser)

```text
               Scope (Innehåll)
                /               /                /        Resurser ────── Tid (Deadline)
```

* **Regeln:** Du kan bara hålla två hörn låsta. Om *Tid* (exakt datum för release) och *Resurser* (teamets storlek) är fasta, **måste Scope vara variabelt**. Det är ditt jobb att kommunicera detta till intressenterna i tid.

---

## 📊 Formel för verklig sprintkapacitet

Basera aldrig kapaciteten på 100% fokuserade utvecklingstimmar. Använd följande modell:

$$	ext{Reell Kapacitet} = (	ext{Utvecklare} 	imes 	ext{Arbetsdagar}) - (	ext{Semester/PTO} + 	ext{On-Call Jour} + 	ext{Möten} + 	ext{Context Switching})$$

* **80%-buffertregeln:** Planera aldrig mer än 80% av teoretisk maxkapacitet. Resterande 20% äts upp av ad-hoc-frågor, code reviews och smärre incidenter i produktion.
