# API-arkitekturer: REST vs tRPC vs GraphQL vs WebSockets

---

## 📊 Jämförelsetabell

| Protokoll | Optimalt scenario | Typsäkerhet | Nätverkseffektivitet |
| :--- | :--- | :--- | :--- |
| **tRPC** | Fullstack TypeScript-monorepos (Next.js/Node) | 100% end-to-end | Hög |
| **REST** | Publika API:er, mobila appar, flerspråkiga klienter | Kräver OpenAPI / Swagger | Måttlig |
| **GraphQL** | Djupt nästlade relationer med varierande klientkrav | Schemastyrd | Hög (inga over-fetches) |
| **WebSockets** | Realtidschattar, live-dashboards, samarbete | Manuell / Protokollstyrd | Låg latens (streaming) |
