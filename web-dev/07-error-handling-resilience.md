# Felhantering och Systemresiliens

En senior utvecklare bygger applikationer som tål att delar av systemet går sönder utan att hela användarupplevelsen kraschar.

---

## 🛡️ Arkitekturella motståndskraftsmönster

1. **Granular React Error Boundaries:** 
   * Placera aldrig en enda felgräns högst upp i roten för hela appen. Bygg inkapslade gränser runt widgets, tabeller och sidofält så att ett fel i en komponent bara döljer den komponenten med en lokal "Kunde inte ladda"-knapp.
2. **Exponential Backoff & Circuit Breakers:**
   * Vid tillfälliga nätverksfel ska klienten göra om anropet med exponentiell backoff och jitter. Om servern ligger nere helt ska en *Circuit Breaker* bryta anropen direkt och returnera cachetrad data.
3. **Lokalt bevarande av formulärdata:**
   * Om nätverket fallerar under en spar- eller checkout-process ska användarens ifyllda data sparas lokalt (LocalStorage/IndexedDB) så att de inte förlorar sitt arbete vid en sidomdatering.
