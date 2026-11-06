# Renderingstrategier: SPA vs SSR vs SSG vs ISR

En djupgående guide för när du ska välja vilken renderingstrategi för webbapplikationen.

---

## 📊 Jämförelsetabell

| Strategi | Passar bäst för | Initial TTFB | SEO-påverkan | Hosting-komplexitet |
| :--- | :--- | :--- | :--- | :--- |
| **SPA** (Client-Side) | SaaS-dashboards, interna adminverktyg | Blixtsnabb | Dålig (kräver JS-exekvering) | Minimal (statisk CDN) |
| **SSR** (Server-Side) | E-handel med realtidslager, personliga flöden | Måttlig (kräver serverberäkning) | Utmärkt | Hög (Node/Edge-runtime krävs) |
| **SSG** (Static Site) | Dokumentation, företagsbloggar, marknadssajter | Blixtsnabb | Perfekt | Minimal (statisk CDN) |
| **ISR** (Incremental) | Stora e-handelskataloger, nyhetssajter | Snabb (cachat på edge) | Utmärkt | Måttlig (Next.js/Vercel-stil) |
